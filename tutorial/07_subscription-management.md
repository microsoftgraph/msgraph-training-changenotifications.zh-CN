<!-- markdownlint-disable MD002 MD041 -->

通知的订阅过期, 需要定期续订。 以下步骤将演示如何续订通知

打开 **> NotificationsController.cs**文件的控制器

向`NotificationsController`类中添加以下两个成员声明:

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

添加以下新方法。 这些将实现将每15秒运行一次的后台计时器, 以检查订阅是否已过期。 如果有, 则将续订它们。

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

计时器`CheckSubscriptions`每15秒调用一次此方法。 对于生产用途, 应将此设置为更合理的值, 以减少对 Microsoft Graph 不必要的调用次数。

该`RenewSubscription`方法将续订订阅, 并且仅在以下两分钟内订阅即将过期时才会调用该方法。

找到该方法`Get()` , 并将其替换为以下代码:

```csharp
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

将以下语句添加到文件顶部`using`的现有语句之后:

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a>测试更改:

在 Visual Studio Code 中, 选择 "**调试" > 启动调试**以运行应用程序。
导航到以下 url: **http://localhost:5000/api/notifications**。 这将注册新的订阅。

在 Visual Studio Code**调试控制台**窗口中, 大约每隔15秒, 请注意计时器检查订阅是否过期:

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

等待几分钟, 当订阅需要续订时, 您将看到以下内容:

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

这表示订阅已续订并显示新的过期时间。