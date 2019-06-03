# <a name="microsoft-graph-training-module---using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="5bd8b-101">Microsoft Graph 培训模块-在 Microsoft Graph 中使用更改通知和跟踪更改</span><span class="sxs-lookup"><span data-stu-id="5bd8b-101">Microsoft Graph Training Module - Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="5bd8b-102">本模块将介绍如何使用更改通知 (webhook) & 跟踪 Microsoft Graph 中的更改 (delta 查询)。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-102">This module will introduce you to working with change notifications (webhooks) & track changes (delta query) in the Microsoft Graph.</span></span>

## <a name="lab---change-notifications-and-track-changes-with-the-microsoft-graph"></a><span data-ttu-id="5bd8b-103">在 Microsoft Graph 中进行实验室更改通知和跟踪更改</span><span class="sxs-lookup"><span data-stu-id="5bd8b-103">Lab - Change Notifications and Track Changes with the Microsoft Graph</span></span>

<span data-ttu-id="5bd8b-104">在此实验室中, 将创建一个 .NET Core 控制台应用程序, 该应用程序在对 Azure Active Directory (Azure AD) 中的用户帐户进行更新时接收来自 Microsoft Graph 的更改通知。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-104">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="5bd8b-105">应用程序将管理更改通知订阅并使用 Microsoft Graph 中的跟踪更改, 以确保不会丢失任何更改。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-105">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

- [<span data-ttu-id="5bd8b-106">实验室手册</span><span class="sxs-lookup"><span data-stu-id="5bd8b-106">Lab Manual</span></span>](./Lab.md)

## <a name="demos"></a><span data-ttu-id="5bd8b-107">演示</span><span class="sxs-lookup"><span data-stu-id="5bd8b-107">Demos</span></span>

- [<span data-ttu-id="5bd8b-108">创建 .NET Core 应用程序</span><span class="sxs-lookup"><span data-stu-id="5bd8b-108">Create a .NET Core app</span></span>](./demos/01-create-application)
- [<span data-ttu-id="5bd8b-109">添加订阅生命周期</span><span class="sxs-lookup"><span data-stu-id="5bd8b-109">Add Subscription Lifecycle</span></span>](./demos/02-subscription-management)
- [<span data-ttu-id="5bd8b-110">添加修订</span><span class="sxs-lookup"><span data-stu-id="5bd8b-110">Add Track Changes</span></span>](./demos/03-track-changes)

## <a name="watch-the-module"></a><span data-ttu-id="5bd8b-111">观看模块</span><span class="sxs-lookup"><span data-stu-id="5bd8b-111">Watch the module</span></span>

<span data-ttu-id="5bd8b-112">此模块已记录并在 Office 开发 YouTube 频道中可用:[更改通知并使用 Microsoft Graph 跟踪更改](https://youtu.be/MvJ15BHTdHA)</span><span class="sxs-lookup"><span data-stu-id="5bd8b-112">This module has been recorded and is available in the Office Development YouTube channel: [Change Notifications and Track Changes with the Microsoft Graph](https://youtu.be/MvJ15BHTdHA)</span></span>

## <a name="contributors"></a><span data-ttu-id="5bd8b-113">参与者</span><span class="sxs-lookup"><span data-stu-id="5bd8b-113">Contributors</span></span>

| <span data-ttu-id="5bd8b-114">角色</span><span class="sxs-lookup"><span data-stu-id="5bd8b-114">Roles</span></span>                | <span data-ttu-id="5bd8b-115">作者 (s)</span><span class="sxs-lookup"><span data-stu-id="5bd8b-115">Author(s)</span></span>                                               |
| -------------------- | ------------------------------------------------------- |
| <span data-ttu-id="5bd8b-116">实验室手册/幻灯片</span><span class="sxs-lookup"><span data-stu-id="5bd8b-116">Lab Manuals / Slides</span></span> | <span data-ttu-id="5bd8b-117">Andrew Connell (Microsoft MVP, Voitanos) @andrewconnell</span><span class="sxs-lookup"><span data-stu-id="5bd8b-117">Andrew Connell (Microsoft MVP, Voitanos) @andrewconnell</span></span> |
| <span data-ttu-id="5bd8b-118">承办人/支持</span><span class="sxs-lookup"><span data-stu-id="5bd8b-118">Sponsor / Support</span></span>    | <span data-ttu-id="5bd8b-119">Jeremy Thake (Microsoft) @jthake</span><span class="sxs-lookup"><span data-stu-id="5bd8b-119">Jeremy Thake (Microsoft) @jthake</span></span>                        |

## <a name="version-history"></a><span data-ttu-id="5bd8b-120">版本历史记录</span><span class="sxs-lookup"><span data-stu-id="5bd8b-120">Version history</span></span>

| <span data-ttu-id="5bd8b-121">版本</span><span class="sxs-lookup"><span data-stu-id="5bd8b-121">Version</span></span> | <span data-ttu-id="5bd8b-122">日期</span><span class="sxs-lookup"><span data-stu-id="5bd8b-122">Date</span></span>           | <span data-ttu-id="5bd8b-123">注释</span><span class="sxs-lookup"><span data-stu-id="5bd8b-123">Comments</span></span>             |
| ------- | -------------- | -------------------- |
| <span data-ttu-id="5bd8b-124">1.1</span><span class="sxs-lookup"><span data-stu-id="5bd8b-124">1.1</span></span>     | <span data-ttu-id="5bd8b-125">2019 年 4 月 9 日</span><span class="sxs-lookup"><span data-stu-id="5bd8b-125">April 9, 2019</span></span> | <span data-ttu-id="5bd8b-126">添加了截屏视频链接</span><span class="sxs-lookup"><span data-stu-id="5bd8b-126">Added screencast link</span></span> |
| <span data-ttu-id="5bd8b-127">1.0</span><span class="sxs-lookup"><span data-stu-id="5bd8b-127">1.0</span></span>     | <span data-ttu-id="5bd8b-128">2019 年 3 月 14 日</span><span class="sxs-lookup"><span data-stu-id="5bd8b-128">March 14, 2019</span></span> | <span data-ttu-id="5bd8b-129">新模块已提交</span><span class="sxs-lookup"><span data-stu-id="5bd8b-129">New module submitted</span></span> |

## <a name="disclaimer"></a><span data-ttu-id="5bd8b-130">免责声明</span><span class="sxs-lookup"><span data-stu-id="5bd8b-130">Disclaimer</span></span>

<span data-ttu-id="5bd8b-131">**此代码_按_原样提供, 无需任何明示或暗示的担保, 包括对特定目的适用性、适销性或不侵权的任何暗示担保。**</span><span class="sxs-lookup"><span data-stu-id="5bd8b-131">**THIS CODE IS PROVIDED _AS IS_ WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>

<img src="https://telemetry.sharepointpnp.com/msgraph-training-changenotifications" />
