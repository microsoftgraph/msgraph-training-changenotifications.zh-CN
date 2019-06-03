# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a>在 Microsoft Graph 中使用更改通知和跟踪更改

在此实验室中, 将创建一个 .NET Core 控制台应用程序, 该应用程序在对 Azure Active Directory (Azure AD) 中的用户帐户进行更新时接收来自 Microsoft Graph 的更改通知。 应用程序将管理更改通知订阅并使用 Microsoft Graph 中的跟踪更改, 以确保不会丢失任何更改。

## <a name="in-this-lab"></a>在此实验室中

1. [实验室简介](./tutorial/01_intro.md)
1. [在 Microsoft Graph 中注册并授予应用程序许可](./tutorial/02_create-app.md)
1. [安装 ngrok](./tutorial/03_ngrok.md)
1. [创建 .NET Core 项目](./tutorial/04_create-project.md)
1. [对 HTTP API 进行编码](./tutorial/05_add-code.md)
1. [运行应用程序](./tutorial/06_run.md)
1. [管理通知订阅](./tutorial/07_subbscription-management.md)
1. [查询更改](./tutorial/08_deltaquery.md)
1. [已完成实验室](./tutorial/09_completed.md)

## <a name="prerequisites"></a>先决条件

在开始本教程之前, 您应在开发计算机上安装[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)和[Visual Studio 代码](https://code.visualstudio.com/)。 如果没有安装它们, 请访问以前的链接获取下载选项。

## <a name="completed-exercises"></a>完成练习

如果您遇到卡, 则在 "[演示](./Demos)" 文件夹中提供已完成的解决方案。