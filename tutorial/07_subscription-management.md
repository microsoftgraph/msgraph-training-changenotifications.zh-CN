<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="cd5fe-101">通知的订阅过期, 需要定期续订。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span> <span data-ttu-id="cd5fe-102">以下步骤将演示如何续订通知</span><span class="sxs-lookup"><span data-stu-id="cd5fe-102">The following steps will demonstrate how to renew notifications</span></span>

<span data-ttu-id="cd5fe-103">打开 **> NotificationsController.cs**文件的控制器</span><span class="sxs-lookup"><span data-stu-id="cd5fe-103">Open **Controllers > NotificationsController.cs** file</span></span>

<span data-ttu-id="cd5fe-104">向`NotificationsController`类中添加以下两个成员声明:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-104">Add the following two member declarations to the `NotificationsController` class:</span></span>

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

<span data-ttu-id="cd5fe-105">添加以下新方法。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-105">Add the following new methods.</span></span> <span data-ttu-id="cd5fe-106">这些将实现将每15秒运行一次的后台计时器, 以检查订阅是否已过期。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-106">These will implement a background timer that will run every 15 seconds to check if subscriptions have expired.</span></span> <span data-ttu-id="cd5fe-107">如果有, 则将续订它们。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-107">If they have, they will be renewed.</span></span>

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

<span data-ttu-id="cd5fe-108">计时器`CheckSubscriptions`每15秒调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-108">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="cd5fe-109">对于生产用途, 应将此设置为更合理的值, 以减少对 Microsoft Graph 不必要的调用次数。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-109">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Microsoft Graph.</span></span>

<span data-ttu-id="cd5fe-110">该`RenewSubscription`方法将续订订阅, 并且仅在以下两分钟内订阅即将过期时才会调用该方法。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-110">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="cd5fe-111">找到该方法`Get()` , 并将其替换为以下代码:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-111">Locate the method `Get()` and replace it with the following code:</span></span>

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

<span data-ttu-id="cd5fe-112">将以下语句添加到文件顶部`using`的现有语句之后:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-112">Add the following statement after the existing `using` statements at the top of the file:</span></span>

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a><span data-ttu-id="cd5fe-113">测试更改:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-113">Test the changes:</span></span>

<span data-ttu-id="cd5fe-114">在 Visual Studio Code 中, 选择 "**调试" > 启动调试**以运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-114">Within Visual Studio Code, select **Debug > Start debugging** to run the application.</span></span>
<span data-ttu-id="cd5fe-115">导航到以下 url: **http://localhost:5000/api/notifications**。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-115">Navigate to the following url: **http://localhost:5000/api/notifications**.</span></span> <span data-ttu-id="cd5fe-116">这将注册新的订阅。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-116">This will register a new subscription.</span></span>

<span data-ttu-id="cd5fe-117">在 Visual Studio Code**调试控制台**窗口中, 大约每隔15秒, 请注意计时器检查订阅是否过期:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-117">In the Visual Studio Code **Debug Console** window, approximately every 15 seconds, notice the timer checking the subscription for expiration:</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="cd5fe-118">等待几分钟, 当订阅需要续订时, 您将看到以下内容:</span><span class="sxs-lookup"><span data-stu-id="cd5fe-118">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="cd5fe-119">这表示订阅已续订并显示新的过期时间。</span><span class="sxs-lookup"><span data-stu-id="cd5fe-119">This indicates that the subscription was renewed and shows the new expiry time.</span></span>