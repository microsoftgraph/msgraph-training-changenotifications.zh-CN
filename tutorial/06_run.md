<!-- markdownlint-disable MD002 MD041 -->

选择 "**调试" > "启动调试**" 以运行应用程序。 生成应用程序后, 浏览器窗口将打开一个404页面。 这是正常的, 因为我们的应用程序是 API, 而不是网页。

若要为用户订阅更改通知, 请导航到以下`http://localhost:5000/api/notifications`url。 如果成功, 你将看到包含如下所示的订阅 id 的输出:

```shell
Subscribed. Id: e2dbfbe1-160b-42b0-9b9f-8ab79bf8dfed
```

现在, 在 Office 365 租户中的任何用户进行更新时, 您的应用程序将订阅从 Microsoft Graph 接收通知。

打开浏览器并访问[Microsoft 365 管理中心](https://admin.microsoft.com/AdminPortal)。 使用管理员帐户登录。 选择 "**用户 > 活动用户**"。 选择一个活动用户并为其**联系人信息**选择 "**编辑**"。 使用新号码更新**移动电话**值, 然后选择 "**保存**"。

![用户详细信息的屏幕截图](./images/03.png)

在 Visual Studio 的**调试控制台**中, 你将看到 "已收到通知"。 有时, 这可能需要几分钟的时间才能到达。 输出的示例如下:

```shell
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

这表示应用程序成功接收到在输出中指定的用户的来自 Microsoft Graph 的通知。 如果要将用户的详细信息同步到您的应用程序中, 则可以使用此信息来查询有关用户的完整详细信息的图。