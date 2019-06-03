<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="ab2fe-101">选择 "**调试" > "启动调试**" 以运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-101">Select **Debug > Start debugging** to run the application.</span></span> <span data-ttu-id="ab2fe-102">生成应用程序后, 浏览器窗口将打开一个404页面。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-102">After building the application a browser window will open to a 404 page.</span></span> <span data-ttu-id="ab2fe-103">这是正常的, 因为我们的应用程序是 API, 而不是网页。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-103">This is ok since our application is an API and not a webpage.</span></span>

<span data-ttu-id="ab2fe-104">若要为用户订阅更改通知, 请导航到以下`http://localhost:5000/api/notifications`url。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-104">To subscribe for change notifications for users navigate to the following url `http://localhost:5000/api/notifications`.</span></span> <span data-ttu-id="ab2fe-105">如果成功, 你将看到包含如下所示的订阅 id 的输出:</span><span class="sxs-lookup"><span data-stu-id="ab2fe-105">If successful you will see output that includes a subscription id like the one below:</span></span>

```shell
Subscribed. Id: e2dbfbe1-160b-42b0-9b9f-8ab79bf8dfed
```

<span data-ttu-id="ab2fe-106">现在, 在 Office 365 租户中的任何用户进行更新时, 您的应用程序将订阅从 Microsoft Graph 接收通知。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-106">Your application is now subscribed to receive notifications from the Microsoft Graph when an update is made on any users in the Office 365 tenant.</span></span>

<span data-ttu-id="ab2fe-107">打开浏览器并访问[Microsoft 365 管理中心](https://admin.microsoft.com/AdminPortal)。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-107">Open a browser and visit the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal).</span></span> <span data-ttu-id="ab2fe-108">使用管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-108">Sign-in using an administrator account.</span></span> <span data-ttu-id="ab2fe-109">选择 "**用户 > 活动用户**"。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-109">Select **Users > Active users**.</span></span> <span data-ttu-id="ab2fe-110">选择一个活动用户并为其**联系人信息**选择 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-110">Select an active user and select **Edit** for their **Contact information**.</span></span> <span data-ttu-id="ab2fe-111">使用新号码更新**移动电话**值, 然后选择 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-111">Update the **Mobile phone** value with a new number and Select **Save**.</span></span>

![用户详细信息的屏幕截图](./images/03.png)

<span data-ttu-id="ab2fe-113">在 Visual Studio 的**调试控制台**中, 你将看到 "已收到通知"。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-113">In the **DEBUG CONSOLE** of Visual Studio you will see a notification has been received.</span></span> <span data-ttu-id="ab2fe-114">有时, 这可能需要几分钟的时间才能到达。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-114">Sometimes this may take a few minutes to arrive.</span></span> <span data-ttu-id="ab2fe-115">输出的示例如下:</span><span class="sxs-lookup"><span data-stu-id="ab2fe-115">An example of the output is below:</span></span>

```shell
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

<span data-ttu-id="ab2fe-116">这表示应用程序成功接收到在输出中指定的用户的来自 Microsoft Graph 的通知。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-116">This indicates the application successfully received the notification from the Microsoft Graph for the user specified in the output.</span></span> <span data-ttu-id="ab2fe-117">如果要将用户的详细信息同步到您的应用程序中, 则可以使用此信息来查询有关用户的完整详细信息的图。</span><span class="sxs-lookup"><span data-stu-id="ab2fe-117">You can then use this information to query the graph for the users full details if you want to synchronize their details into your application.</span></span>