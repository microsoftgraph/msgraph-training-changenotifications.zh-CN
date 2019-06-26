<!-- markdownlint-disable MD002 MD041 -->

打开命令提示符, 导航到您有权在其中创建项目的目录, 并运行以下命令以创建新的 .NET Core Microsoft.aspnet.webapi.tracing 应用程序:

```shell
dotnet new webapi -o msgraphapp
```

创建应用程序后, 运行以下命令以确保新项目正常运行。

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  应用程序将启动并输出以下内容:

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

通过按<kbd>CTRL</kbd>+<kbd>C</kbd>停止正在运行的应用程序。

使用以下命令在 Visual Studio Code 中打开应用程序:

```shell
code .
```

如果 Visual Studio code 显示一个对话框, 询问您是否要将所需的资产添加到项目中, 请选择 **"是"**。
