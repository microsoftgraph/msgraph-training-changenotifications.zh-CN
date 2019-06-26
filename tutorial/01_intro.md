<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="135d5-101">本教程介绍了如何构建一个 .NET Core 应用程序, 该应用程序使用 Microsoft Graph API 在 Azure Active Directory (Azure AD) 中更改用户帐户并使用增量查询 API 执行查询以接收对用户的所有更改, 以接收通知 (webhook)。自上次进行查询以来的帐户。</span><span class="sxs-lookup"><span data-stu-id="135d5-101">This tutorial teaches you how to build a .NET Core app that uses the Microsoft Graph API to receive notifications (webhooks) when a user account changes in Azure Active Directory (Azure AD) and perform queries using the delta query API to receive all changes to user accounts since the last query was made.</span></span>

> [!TIP]
> <span data-ttu-id="135d5-102">如果您只想下载已完成的教程, 可以下载或克隆[GitHub 存储库](https://github.com/microsoftgraph/msgraph-training-changenotifications)。</span><span class="sxs-lookup"><span data-stu-id="135d5-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="135d5-103">先决条件</span><span class="sxs-lookup"><span data-stu-id="135d5-103">Prerequisites</span></span>

<span data-ttu-id="135d5-104">在开始本教程之前, 您应在开发计算机上安装[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)和[Visual Studio 代码](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="135d5-104">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span>

> [!NOTE]
> <span data-ttu-id="135d5-105">本教程是使用 .NET Core 版本2.2 编写的。</span><span class="sxs-lookup"><span data-stu-id="135d5-105">This tutorial was written with .NET Core version 2.2.</span></span> <span data-ttu-id="135d5-106">本指南中的步骤可能适用于其他版本, 但尚未经过测试。</span><span class="sxs-lookup"><span data-stu-id="135d5-106">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="watch-the-tutorial"></a><span data-ttu-id="135d5-107">观看教程</span><span class="sxs-lookup"><span data-stu-id="135d5-107">Watch the tutorial</span></span>

<span data-ttu-id="135d5-108">此模块已记录, 在 Office 开发 YouTube 频道中可用。</span><span class="sxs-lookup"><span data-stu-id="135d5-108">This module has been recorded and is available in the Office Development YouTube channel.</span></span>

<!-- markdownlint-disable MD033 MD034 -->
<br/>

> [!VIDEO https://www.youtube-nocookie.com/embed/fThiCZmIcMQ]
<!-- markdownlint-enable MD033 MD034 -->

## <a name="feedback"></a><span data-ttu-id="135d5-109">反馈</span><span class="sxs-lookup"><span data-stu-id="135d5-109">Feedback</span></span>

<span data-ttu-id="135d5-110">请在[GitHub 存储库](https://github.com/microsoftgraph/msgraph-training-changenotifications)中提供有关本教程的任何反馈。</span><span class="sxs-lookup"><span data-stu-id="135d5-110">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>
