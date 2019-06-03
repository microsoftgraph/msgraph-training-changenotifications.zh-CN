<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="d2823-101">通知的订阅过期, 需要定期续订。</span><span class="sxs-lookup"><span data-stu-id="d2823-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span>

<span data-ttu-id="d2823-102">打开**NotificationsController.cs** , 并将`Get()`方法替换为以下代码:</span><span class="sxs-lookup"><span data-stu-id="d2823-102">Open **NotificationsController.cs** and replace the `Get()` method with the following code:</span></span>

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

<span data-ttu-id="d2823-103">在文件顶部添加以下 using 语句。</span><span class="sxs-lookup"><span data-stu-id="d2823-103">Add the following using statement at the top of the file.</span></span>

```csharp
using System.Threading;
```

<span data-ttu-id="d2823-104">上面的代码添加了一个将每15秒触发一次的后台计时器, 并检查订阅以查看是否已过期。</span><span class="sxs-lookup"><span data-stu-id="d2823-104">This code above adds a background timer that will fire every 15 seconds and check subscriptions to see if they have expired.</span></span>

<span data-ttu-id="d2823-105">添加以下新方法:</span><span class="sxs-lookup"><span data-stu-id="d2823-105">Add the following new methods:</span></span>

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

<span data-ttu-id="d2823-106">计时器`CheckSubscriptions`每15秒调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="d2823-106">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="d2823-107">对于生产用途, 应将此设置为更合理的值, 以减少对图形的不必要调用次数。</span><span class="sxs-lookup"><span data-stu-id="d2823-107">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Graph.</span></span> <span data-ttu-id="d2823-108">该`RenewSubscription`方法将续订订阅, 并且仅在以下两分钟内订阅即将过期时才会调用该方法。</span><span class="sxs-lookup"><span data-stu-id="d2823-108">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="d2823-109">选择 "**调试" > "启动调试**" 以运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="d2823-109">Select **Debug > Start debugging** to run the application.</span></span> <span data-ttu-id="d2823-110">导航到以下 url `*http://localhost:5000/api/notifications` , 以注册新的订阅。</span><span class="sxs-lookup"><span data-stu-id="d2823-110">Navigate to the following url `*http://localhost:5000/api/notifications` to register a new subscription.</span></span>

<span data-ttu-id="d2823-111">每15秒大约在 Visual Studio Code `DEBUG OUTPUT`窗口中显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="d2823-111">You will see the following output in the `DEBUG OUTPUT` window of Visual Studio Code approximately every 15 seconds.</span></span>  <span data-ttu-id="d2823-112">这是检查订阅是否过期的计时器。</span><span class="sxs-lookup"><span data-stu-id="d2823-112">This is the timer checking the subscription for expiry.</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="d2823-113">等待几分钟, 当订阅需要续订时, 您将看到以下内容:</span><span class="sxs-lookup"><span data-stu-id="d2823-113">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="d2823-114">这表示订阅已续订并显示新的过期时间。</span><span class="sxs-lookup"><span data-stu-id="d2823-114">This indicates that the subscription was renewed and shows the new expiry time.</span></span>
