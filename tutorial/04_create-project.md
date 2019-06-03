<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="02c64-101">打开命令提示符, 导航到您有权在其中创建文件的目录, 并运行以下命令以创建新的 .NET Core Microsoft.aspnet.webapi.tracing 应用程序。</span><span class="sxs-lookup"><span data-stu-id="02c64-101">Open your command prompt, navigate to a directory where you have rights to create files, and run the following commands to create a new .NET Core WebApi app.</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="02c64-102">命令完成后, 运行以下命令以确保新项目正常运行。</span><span class="sxs-lookup"><span data-stu-id="02c64-102">Once the command finishes, run the following commands to ensure your new project runs correctly.</span></span>

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

<span data-ttu-id="02c64-103">应用程序将启动并输出:</span><span class="sxs-lookup"><span data-stu-id="02c64-103">The application will start and output:</span></span>

```shell
Now listening on: http://localhost:5000
```

<span data-ttu-id="02c64-104">如果您看不到此输出, 或者看到错误消息, 则可能是开发计算机上安装了需要修复的[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)存在问题, 然后才能继续操作。</span><span class="sxs-lookup"><span data-stu-id="02c64-104">If you don't see this output, or you see error messages, there is likely a problem with the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) installed on your development machine that needs to be fixed before continuing.</span></span>

<span data-ttu-id="02c64-105">通过按<kbd>CTRL</kbd>+<kbd>C</kbd>停止正在运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="02c64-105">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="02c64-106">使用以下命令在 Visual Studio Code 中打开应用程序:</span><span class="sxs-lookup"><span data-stu-id="02c64-106">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="02c64-107">当对话框询问您是否要向项目添加所需的资产时, 请选择 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="02c64-107">When a dialog box asks if you want to add required assets to the project, select **Yes**.</span></span>
