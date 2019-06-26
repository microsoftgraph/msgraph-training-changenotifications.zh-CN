<!-- markdownlint-disable MD002 MD041 -->

创建用于在 Visual Studio Code 中调试应用程序的启动配置。

在 Visual Studio Code 中, 选择 "**调试" > "打开配置**"。

  ![截屏视频的 VS 代码打开启动配置](./images/vscode-debugapp-01.png)

当系统提示选择环境时, 选择 " **.Net Core**"。

  ![截屏视频 of VS 代码创建 .NET Core 的启动配置](./images/vscode-debugapp-02.png)

> [!NOTE]
> 默认情况下, .NET Core 启动配置将在启动调试器时打开浏览器并导航到应用程序的默认 URL。 对于此应用程序, 我们要转到 NGrok URL。 如果将启动配置保留为原样, 则每次调试应用程序时, 它将显示一个已损坏的页面。 您只需更改 URL, 或将启动配置更改为不启动浏览器:

更新 Visual Studio 调试器启动配置:

  1. 在 Visual Studio Code 中, 打开**vscode/启动**文件。
  1. 在默认配置中找到以下部分:

      ```json
      "launchBrowser": {
        "enabled": true
      },
      ```

  1. 将`enabled`属性设置为`false`。
  1. 保存所做的更改。

### <a name="test-the-application"></a>测试应用程序:

在 Visual Studio Code 中, 选择 "**调试" > 启动调试**以运行应用程序。 VS 代码将生成和星型应用程序。

在**调试控制台**窗口中看到以下各项后 .。。

![VS 代码调试控制台的屏幕截图](./images/vscode-debugapp-03.png)

...打开浏览器并导航到**http://localhost:5000/api/notifications**以订阅更改通知。 如果成功, 你将看到包含如下所示的订阅 id 的输出:

![成功订阅的屏幕截图](./images/vscode-debugapp-04.png)

现在, 在 Office 365 租户中的任何用户进行更新时, 您的应用程序将订阅从 Microsoft Graph 接收通知。

触发通知:

1. 打开浏览器并导航到[Microsoft 365 管理中心 (https://admin.microsoft.com/AdminPortal)](https://admin.microsoft.com/AdminPortal)。
1. 如果系统提示您登录, 请使用管理员帐户登录。
1. 选择 "**用户 > 活动用户**"。

    ![Microsoft 365 管理中心的屏幕截图](./images/vscode-debugapp-05.png)

1. 选择一个活动用户并为其**联系人信息**选择 "**编辑**"。

    ![用户详细信息的屏幕截图](./images/vscode-debugapp-06.png)

1. 使用新号码更新**电话号码**值, 然后选择 "**保存**"。

    在 Visual Studio Code**调试控制台**中, 您将看到已收到通知。 有时, 这可能需要几分钟的时间才能到达。 输出的示例如下:

    ```shell
    Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
    ```

这表示应用程序成功接收到在输出中指定的用户的来自 Microsoft Graph 的通知。 如果要将用户的详细信息同步到您的应用程序中, 则可以使用此信息查询 Microsoft Graph 以了解用户的详细信息。