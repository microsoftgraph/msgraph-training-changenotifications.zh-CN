<!-- markdownlint-disable MD002 MD041 -->

打开命令提示符, 导航到您有权在其中创建文件的目录, 并运行以下命令以创建新的 .NET Core Microsoft.aspnet.webapi.tracing 应用程序。

```shell
dotnet new webapi -o msgraphapp
```

命令完成后, 运行以下命令以确保新项目正常运行。

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

应用程序将启动并输出:

```shell
Now listening on: http://localhost:5000
```

如果您看不到此输出, 或者看到错误消息, 则可能是开发计算机上安装了需要修复的[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)存在问题, 然后才能继续操作。

通过按<kbd>CTRL</kbd>+<kbd>C</kbd>停止正在运行的应用程序。

使用以下命令在 Visual Studio Code 中打开应用程序:

```shell
code .
```

当对话框询问您是否要向项目添加所需的资产时, 请选择 **"是"**。
