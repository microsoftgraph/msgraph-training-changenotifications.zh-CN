<!-- markdownlint-disable MD002 MD041 -->

通知的订阅过期, 需要定期续订。

打开**NotificationsController.cs** , 并将`Get()`方法替换为以下代码:

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;

[HttpGet]
public ActionResult<string> Get()
{
  var graphServiceClient = GetGraphClient();

  var sub = new Microsoft.Graph.Subscription();
  sub.ChangeType = "updated";
  sub.NotificationUrl = config.Ngrok + "/api/notifications";
  sub.Resource = "/users";
  sub.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);
  sub.ClientState = "SecretClientState";

  var newSubscription = graphServiceClient
    .Subscriptions
    .Request()
    .AddAsync(sub).Result;

  Subscriptions[newSubscription.Id] = newSubscription;

  if(subscriptionTimer == null)
  {
      subscriptionTimer = new Timer(CheckSubscriptions, null, 5000, 15000);
  }

  return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
}
```

在文件顶部添加以下 using 语句。

```csharp
using System.Threading;
```

上面的代码添加了一个将每15秒触发一次的后台计时器, 并检查订阅以查看是否已过期。

添加以下新方法:

```csharp
private void CheckSubscriptions(Object stateInfo)
{
  AutoResetEvent autoEvent = (AutoResetEvent)stateInfo;

  Console.WriteLine($"Checking subscriptions {DateTime.Now.ToString("h:mm:ss.fff")}");
  Console.WriteLine($"Current subscription count {Subscriptions.Count()}");

  foreach(var subscription in Subscriptions)
  {
    // if the subscription expires in the next 2 min, renew it
    if(subscription.Value.ExpirationDateTime < DateTime.UtcNow.AddMinutes(2))
    {
      RenewSubscription(subscription.Value);
    }
  }
}

private void RenewSubscription(Subscription subscription)
{
  Console.WriteLine($"Current subscription: {subscription.Id}, Expiration: {subscription.ExpirationDateTime}");

  var graphServiceClient = GetGraphClient();

  subscription.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);

  var foo = graphServiceClient
    .Subscriptions[subscription.Id]
    .Request()
    .UpdateAsync(subscription).Result;

  Console.WriteLine($"Renewed subscription: {subscription.Id}, New Expiration: {subscription.ExpirationDateTime}");
}
```

计时器`CheckSubscriptions`每15秒调用一次此方法。 对于生产用途, 应将此设置为更合理的值, 以减少对图形的不必要调用次数。 该`RenewSubscription`方法将续订订阅, 并且仅在以下两分钟内订阅即将过期时才会调用该方法。

选择 "**调试" > "启动调试**" 以运行应用程序。 导航到以下 url `*http://localhost:5000/api/notifications` , 以注册新的订阅。

每15秒大约在 Visual Studio Code `DEBUG OUTPUT`窗口中显示以下输出。  这是检查订阅是否过期的计时器。

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

等待几分钟, 当订阅需要续订时, 您将看到以下内容:

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

这表示订阅已续订并显示新的过期时间。
