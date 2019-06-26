<!-- markdownlint-disable MD002 MD041 -->

### <a name="query-for-changes"></a><span data-ttu-id="251a7-101">查询更改</span><span class="sxs-lookup"><span data-stu-id="251a7-101">Query for changes</span></span>

<span data-ttu-id="251a7-102">Microsoft Graph 提供了在您上次调用后查询对特定资源的更改的功能。</span><span class="sxs-lookup"><span data-stu-id="251a7-102">Microsoft Graph offers the ability to query for changes to a particular resource since you last called it.</span></span> <span data-ttu-id="251a7-103">使用此选项和更改通知结合使用, 可启用强大的模式, 以确保您不会错过对资源的任何更改。</span><span class="sxs-lookup"><span data-stu-id="251a7-103">Using this option, combined with Change Notifications, enables a robust pattern for ensuring you don't miss any changes to the resources.</span></span>

<span data-ttu-id="251a7-104">找到并打开以下控制器:**控制器 > NotificationsController.cs**。</span><span class="sxs-lookup"><span data-stu-id="251a7-104">Locate and open the following controller: **Controllers > NotificationsController.cs**.</span></span>
<span data-ttu-id="251a7-105">将以下代码添加到现有`NotificationsController`类中。</span><span class="sxs-lookup"><span data-stu-id="251a7-105">Add the following code to the existing `NotificationsController` class.</span></span>

<span data-ttu-id="251a7-106">此代码包含一个新方法, `CheckForUpdates()`该方法将使用增量 Url 调用 Microsoft Graph, 然后在结果页面上查看结果, 直到它在最后`deltalink`一页上找到新结果。</span><span class="sxs-lookup"><span data-stu-id="251a7-106">This code includes a new method, `CheckForUpdates()`, that will call the Microsoft Graph using the delta url and then pages through the results until it finds a new `deltalink` on the final page of results.</span></span> <span data-ttu-id="251a7-107">它将 url 存储在内存中, 直到触发另一个通知时再次通知代码。</span><span class="sxs-lookup"><span data-stu-id="251a7-107">It stores the url in memory until the code is notified again when another notification is triggered.</span></span>

```csharp
private static object DeltaLink = null;

private static IUserDeltaCollectionPage lastPage = null;

private void CheckForUpdates()
{
  var graphClient = GetGraphClient();

  // get a page of users
  var users = GetUsers(graphClient, DeltaLink);

  OutputUsers(users);

  // go through all of the pages so that we can get the delta link on the last page.
  while (users.NextPageRequest != null)
  {
    users = users.NextPageRequest.GetAsync().Result;
    OutputUsers(users);
  }

  object deltaLink;

  if (users.AdditionalData.TryGetValue("@odata.deltaLink", out deltaLink))
  {
    DeltaLink = deltaLink;
  }
}

private void OutputUsers(IUserDeltaCollectionPage users)
{
  foreach(var user in users)
    {
      var message = $"User: {user.Id}, {user.GivenName} {user.Surname}";
      Console.WriteLine(message);
    }
}

private IUserDeltaCollectionPage GetUsers(GraphServiceClient graphClient, object deltaLink)
{
  IUserDeltaCollectionPage page;

  if(lastPage == null)
  {
    page = graphClient
      .Users
      .Delta()
      .Request()
      .GetAsync()
      .Result;

  }
  else
  {
    lastPage.InitializeNextPageRequest(graphClient, deltaLink.ToString());
    page = lastPage.NextPageRequest.GetAsync().Result;
  }

  lastPage = page;
  return page;
}
```

<span data-ttu-id="251a7-108">找到现有`Post()`方法, 并将其替换为以下代码:</span><span class="sxs-lookup"><span data-stu-id="251a7-108">Locate the existing `Post()` method and replace it with the following code:</span></span>

```csharp
public ActionResult<string> Post([FromQuery]string validationToken = null)
{
  // handle validation
  if(!string.IsNullOrEmpty(validationToken))
  {
    Console.WriteLine($"Received Token: '{validationToken}'");
    return Ok(validationToken);
  }

  // handle notifications
  using (StreamReader reader = new StreamReader(Request.Body))
  {
    string content = reader.ReadToEnd();

    Console.WriteLine(content);

    var notifications = JsonConvert.DeserializeObject<Notifications>(content);

    foreach(var notification in notifications.Items)
    {
      Console.WriteLine($"Received notification: '{notification.Resource}', {notification.ResourceData?.Id}");
    }
  }

  // use deltaquery to query for all updates
  CheckForUpdates();

  return Ok();
}
```

<span data-ttu-id="251a7-109">此`Post`方法现在将在`CheckForUpdates`收到通知时调用。</span><span class="sxs-lookup"><span data-stu-id="251a7-109">The `Post` method will now call `CheckForUpdates` when a notification is received.</span></span> <span data-ttu-id="251a7-110">在方法`Post`下方, 添加以下两个新方法:</span><span class="sxs-lookup"><span data-stu-id="251a7-110">Below the `Post` method add the following two new methods:</span></span>

<span data-ttu-id="251a7-111">**保存**所有文件。</span><span class="sxs-lookup"><span data-stu-id="251a7-111">**Save** all files.</span></span>

### <a name="test-your-changes"></a><span data-ttu-id="251a7-112">测试更改:</span><span class="sxs-lookup"><span data-stu-id="251a7-112">Test your changes:</span></span>

<span data-ttu-id="251a7-113">在 Visual Studio Code 中, 选择 "**调试" > 启动调试**以运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="251a7-113">Within Visual Studio Code, select **Debug > Start debugging** to run the application.</span></span>
<span data-ttu-id="251a7-114">导航到以下 url: **http://localhost:5000/api/notifications**。</span><span class="sxs-lookup"><span data-stu-id="251a7-114">Navigate to the following url: **http://localhost:5000/api/notifications**.</span></span> <span data-ttu-id="251a7-115">这将注册新的订阅。</span><span class="sxs-lookup"><span data-stu-id="251a7-115">This will register a new subscription.</span></span>

<span data-ttu-id="251a7-116">打开浏览器并导航到[Microsoft 365 管理中心 (https://admin.microsoft.com/AdminPortal)](https://admin.microsoft.com/AdminPortal)。</span><span class="sxs-lookup"><span data-stu-id="251a7-116">Open a browser and navigate to the [Microsoft 365 admin center (https://admin.microsoft.com/AdminPortal)](https://admin.microsoft.com/AdminPortal).</span></span>

1. <span data-ttu-id="251a7-117">如果系统提示您登录, 请使用管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="251a7-117">If prompted to login, sign-in using an admin account.</span></span>
1. <span data-ttu-id="251a7-118">选择 "**用户 > 活动用户**"。</span><span class="sxs-lookup"><span data-stu-id="251a7-118">Select **Users > Active users**.</span></span> 
1. <span data-ttu-id="251a7-119">选择一个活动用户并为其**联系人信息**选择 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="251a7-119">Select an active user and select **Edit** for their **Contact information**.</span></span> 
1. <span data-ttu-id="251a7-120">使用新号码更新**移动电话**值, 然后选择 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="251a7-120">Update the **Mobile phone** value with a new number and Select **Save**.</span></span>

<span data-ttu-id="251a7-121">等待接收通知, 如 Visual Studio Code**调试控制台**中所示:</span><span class="sxs-lookup"><span data-stu-id="251a7-121">Wait for the notification to be received as indicated in the Visual Studio Code **Debug Console**:</span></span>

```shell
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

<span data-ttu-id="251a7-122">应用程序现在将启动增量查询和 graph, 以获取所有用户并将这些详细信息的一些详细信息记录到控制台输出。</span><span class="sxs-lookup"><span data-stu-id="251a7-122">The application will now initiate a delta query with the graph to get all the users and log out some of their details to the console output.</span></span>

```shell
User: 19e429d2-541a-4e0b-9873-6dff9f48fabe, Allan Deyoung
User: 05501e79-f527-4913-aabf-e535646d7ffa, Christie Cline
User: fecac4be-76e7-48ec-99df-df745854aa9c, Debra Berger
User: 4095c5c4-b960-43b9-ba53-ef806d169f3e, Diego Siciliani
User: b1246157-482f-420c-992c-fc26cbff74a5, Emily Braun
User: c2b510b7-1f76-4f75-a9c1-b3176b68d7ca, Enrico Cattaneo
User: 6ec9bd4b-fc6a-4653-a291-70d3809f2610, Grady Archie
User: b6924afe-cb7f-45a3-a904-c9d5d56e06ea, Henrietta Mueller
User: 0ee8d076-4f13-4e1a-a961-eac2b29c0ef6, Irvin Sayers
User: 31f66f05-ac9b-4723-9b5d-8f381f5a6e25, Isaiah Langer
User: 7ee95e20-247d-43ef-b368-d19d96550c81, Johanna Lorenz
User: b2fa93ac-19a0-499b-b1b6-afa76c44a301, Joni Sherman
User: 01db13c5-74fc-470a-8e45-d6d736f8a35b, Jordan Miller
User: fb0b8363-4126-4c34-8185-c998ff697a60, Lee Gu
User: ee75e249-a4c1-487b-a03a-5a170c2aa33f, Lidia Holloway
User: 5449bd61-cc63-40b9-b0a8-e83720eeefba, Lynne Robbins
User: 7ce295c3-25fa-4d79-8122-9a87d15e2438, Miriam Graham
User: 737fe0a7-0b67-47dc-b7a6-9cfc07870705, Nestor Wilke
User: a1572b58-35cd-41a0-804a-732bd978df3e, Patti Fernandez
User: 7275e1c4-5698-446c-8d1d-fa8b0503c78a, Pradeep Gupta
User: 96ab25eb-6b69-4481-9d28-7b01cf367170, Megan Bowen
User: 846327fa-e6d6-4a82-89ad-5fd313bff0cc, Alex Wilber
User: 200e4c7a-b778-436c-8690-7a6398e5fe6e, MOD Administrator
User: 7a7fded6-0269-42c2-a0be-512d58da4463, Adele Vance
User: 752f0102-90f2-4b8d-ae98-79dee995e35e,   Removed?:deleted
User: 4887248a-6b48-4ba5-bdd5-fed89d8ea6a0,   Removed?:deleted
User: e538b2d5-6481-4a90-a20a-21ad55ce4c1d,   Removed?:deleted
User: bc5994d9-4404-4a14-8fb0-46b8dccca0ad,   Removed?:deleted
User: d4e3a3e0-72e9-41a6-9538-c23e10a16122,   Removed?:deleted
Got deltalink
```

<span data-ttu-id="251a7-123">在 Microsoft 365 管理门户中, 重复编辑用户并再次**保存**的过程。</span><span class="sxs-lookup"><span data-stu-id="251a7-123">In the Microsoft 365 Admin Portal, repeat the process of editing a user and **Save** again.</span></span>

<span data-ttu-id="251a7-124">应用程序将接收到另一条通知, 并将使用收到的最后一个增量链接再次查询关系图。</span><span class="sxs-lookup"><span data-stu-id="251a7-124">The application will receive another notification and will query the graph again using the last delta link it received.</span></span> <span data-ttu-id="251a7-125">但是, 这次您会注意到, 结果中只返回已修改的用户。</span><span class="sxs-lookup"><span data-stu-id="251a7-125">However, this time you will notice that only the modified user was returned in the results.</span></span>

```shell
User: 7a7fded6-0269-42c2-a0be-512d58da4463, Adele Vance
```

<span data-ttu-id="251a7-126">将此通知组合用于增量查询, 可以确保您不会错过对某个资源的任何更新。</span><span class="sxs-lookup"><span data-stu-id="251a7-126">Using this combination of notifications with delta query you can be assured you wont miss any updates to a resource.</span></span> <span data-ttu-id="251a7-127">通知可能因暂时性的连接问题而丢失, 但下次应用程序收到通知时, 它将从上次成功的查询中选取所有更改。</span><span class="sxs-lookup"><span data-stu-id="251a7-127">Notifications may be missed due to transient connection issues, however the next time your application gets a notification it will pick up all the changes since the last successful query.</span></span>
