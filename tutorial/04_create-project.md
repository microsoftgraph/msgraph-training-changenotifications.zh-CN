<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="d82f0-101">打开命令提示符, 导航到您有权在其中创建项目的目录, 并运行以下命令以创建新的 .NET Core Microsoft.aspnet.webapi.tracing 应用程序:</span><span class="sxs-lookup"><span data-stu-id="d82f0-101">Open your command prompt, navigate to a directory where you have rights to create your project, and run the following command to create a new .NET Core WebApi app:</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="d82f0-102">创建应用程序后, 运行以下命令以确保新项目正常运行。</span><span class="sxs-lookup"><span data-stu-id="d82f0-102">After creating the application, run the following commands to ensure your new project runs correctly.</span></span>

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  <span data-ttu-id="d82f0-103">应用程序将启动并输出以下内容:</span><span class="sxs-lookup"><span data-stu-id="d82f0-103">The application will start and output the following:</span></span>

  ```shell
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[0] ...
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[58] ...
  warn: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[35] ...
  info: Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository[39] ...
  Hosting environment: Development
  Content root path: /Users/ac/_play/graphchangenotifications/msgraphapp
  Now listening on: https://localhost:5001
  Now listening on: http://localhost:5000
  Application started. Press Ctrl+C to shut down.
  ```

<span data-ttu-id="d82f0-104">通过按<kbd>CTRL</kbd>+<kbd>C</kbd>停止正在运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d82f0-104">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="d82f0-105">使用以下命令在 Visual Studio Code 中打开应用程序:</span><span class="sxs-lookup"><span data-stu-id="d82f0-105">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="d82f0-106">如果 Visual Studio code 显示一个对话框, 询问您是否要将所需的资产添加到项目中, 请选择 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="d82f0-106">If Visual Studio code displays a dialog box asking if you want to add required assets to the project, select **Yes**.</span></span>
