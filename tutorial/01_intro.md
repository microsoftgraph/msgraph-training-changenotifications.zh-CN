<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="dd68a-101">本教程介绍了如何构建一个 .NET Core 应用程序, 该应用程序使用 Microsoft Graph API 在 Azure Active Directory (Azure AD) 中更改用户帐户并使用增量查询 API 执行查询以接收对用户的所有更改, 以接收通知 (webhook)。自上次进行查询以来的帐户。</span><span class="sxs-lookup"><span data-stu-id="dd68a-101">This tutorial teaches you how to build a .NET Core app that uses the Microsoft Graph API to receive notifications (webhooks) when a user account changes in Azure Active Directory (Azure AD) and perform queries using the delta query API to receive all changes to user accounts since the last query was made.</span></span>

> [!TIP]
> <span data-ttu-id="dd68a-102">如果您只想下载已完成的教程, 可以下载或克隆[GitHub 存储库](https://github.com/microsoftgraph/msgraph-training-changenotifications)。</span><span class="sxs-lookup"><span data-stu-id="dd68a-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd68a-103">先决条件</span><span class="sxs-lookup"><span data-stu-id="dd68a-103">Prerequisites</span></span>

<span data-ttu-id="dd68a-104">在开始本教程之前, 您应在开发计算机上安装[.Net Core 2.2 SDK](https://dotnet.microsoft.com/download)和[Visual Studio 代码](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="dd68a-104">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span> <span data-ttu-id="dd68a-105">如果没有安装它们, 请访问以前的链接获取下载选项。</span><span class="sxs-lookup"><span data-stu-id="dd68a-105">If you do not have them installed, visit the previous links for download options.</span></span>

> [!NOTE]
> <span data-ttu-id="dd68a-106">本教程是使用 .NET Core 版本2.2 编写的。</span><span class="sxs-lookup"><span data-stu-id="dd68a-106">This tutorial was written with .NET Core version 2.2.</span></span> <span data-ttu-id="dd68a-107">本指南中的步骤可能适用于其他版本, 但尚未经过测试。</span><span class="sxs-lookup"><span data-stu-id="dd68a-107">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="feedback"></a><span data-ttu-id="dd68a-108">反馈</span><span class="sxs-lookup"><span data-stu-id="dd68a-108">Feedback</span></span>

<span data-ttu-id="dd68a-109">请在[GitHub 存储库](https://github.com/microsoftgraph/msgraph-training-changenotifications)中提供有关本教程的任何反馈。</span><span class="sxs-lookup"><span data-stu-id="dd68a-109">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>