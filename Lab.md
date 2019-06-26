# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="9f9dd-101">在 Microsoft Graph 中使用更改通知和跟踪更改</span><span class="sxs-lookup"><span data-stu-id="9f9dd-101">Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="9f9dd-102">在此实验室中, 将创建一个 .NET Core 控制台应用程序, 该应用程序在对 Azure Active Directory (Azure AD) 中的用户帐户进行更新时接收来自 Microsoft Graph 的更改通知。</span><span class="sxs-lookup"><span data-stu-id="9f9dd-102">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="9f9dd-103">应用程序将管理更改通知订阅并使用 Microsoft Graph 中的跟踪更改, 以确保不会丢失任何更改。</span><span class="sxs-lookup"><span data-stu-id="9f9dd-103">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

## <a name="in-this-lab"></a><span data-ttu-id="9f9dd-104">在此实验室中</span><span class="sxs-lookup"><span data-stu-id="9f9dd-104">In this lab</span></span>

1. [<span data-ttu-id="9f9dd-105">实验室简介</span><span class="sxs-lookup"><span data-stu-id="9f9dd-105">Introduction to the lab</span></span>](./tutorial/01_intro.md)
1. [<span data-ttu-id="9f9dd-106">在 Microsoft Graph 中注册并授予应用程序许可</span><span class="sxs-lookup"><span data-stu-id="9f9dd-106">Register and grant consent to the application in Microsoft Graph</span></span>](./tutorial/02_create-app.md)
1. [<span data-ttu-id="9f9dd-107">安装 ngrok</span><span class="sxs-lookup"><span data-stu-id="9f9dd-107">Install ngrok</span></span>](./tutorial/03_ngrok.md)
1. [<span data-ttu-id="9f9dd-108">创建 .NET Core 项目</span><span class="sxs-lookup"><span data-stu-id="9f9dd-108">Create the .NET Core project</span></span>](./tutorial/04_create-project.md)
1. [<span data-ttu-id="9f9dd-109">对 HTTP API 进行编码</span><span class="sxs-lookup"><span data-stu-id="9f9dd-109">Code the HTTP API</span></span>](./tutorial/05_add-code.md)
1. [<span data-ttu-id="9f9dd-110">运行应用程序</span><span class="sxs-lookup"><span data-stu-id="9f9dd-110">Run the application</span></span>](./tutorial/06_run.md)
1. [<span data-ttu-id="9f9dd-111">管理通知订阅</span><span class="sxs-lookup"><span data-stu-id="9f9dd-111">Manage notification subscriptions</span></span>](./tutorial/07_subbscription-management.md)
1. [<span data-ttu-id="9f9dd-112">查询更改</span><span class="sxs-lookup"><span data-stu-id="9f9dd-112">Query for changes</span></span>](./tutorial/08_deltaquery.md)
1. [<span data-ttu-id="9f9dd-113">已完成实验室</span><span class="sxs-lookup"><span data-stu-id="9f9dd-113">Completed Lab</span></span>](./tutorial/09_completed.md)

## <a name="prerequisites"></a><span data-ttu-id="9f9dd-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="9f9dd-114">Prerequisites</span></span>

<span data-ttu-id="9f9dd-115">在开始本教程之前, 您应在开发计算机上安装[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)和[Visual Studio 代码](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="9f9dd-115">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span> 

## <a name="completed-exercises"></a><span data-ttu-id="9f9dd-116">完成练习</span><span class="sxs-lookup"><span data-stu-id="9f9dd-116">Completed Exercises</span></span>

<span data-ttu-id="9f9dd-117">如果您遇到卡, 则在 "[演示](./Demos)" 文件夹中提供已完成的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9f9dd-117">Finished solutions are provided in the [Demos](./Demos) folder if you get stuck.</span></span>