# <a name="microsoft-graph-training-module---using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="2ead5-101">Microsoft Graph 培训模块-在 Microsoft Graph 中使用更改通知和跟踪更改</span><span class="sxs-lookup"><span data-stu-id="2ead5-101">Microsoft Graph Training Module - Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="2ead5-102">本模块将介绍如何使用更改通知 (webhook) & 跟踪 Microsoft Graph 中的更改 (delta 查询)。</span><span class="sxs-lookup"><span data-stu-id="2ead5-102">This module will introduce you to working with change notifications (webhooks) & track changes (delta query) in the Microsoft Graph.</span></span>

## <a name="lab---change-notifications-and-track-changes-with-the-microsoft-graph"></a><span data-ttu-id="2ead5-103">在 Microsoft Graph 中进行实验室更改通知和跟踪更改</span><span class="sxs-lookup"><span data-stu-id="2ead5-103">Lab - Change Notifications and Track Changes with the Microsoft Graph</span></span>

<span data-ttu-id="2ead5-104">在此实验室中, 将创建一个 .NET Core 控制台应用程序, 该应用程序在对 Azure Active Directory (Azure AD) 中的用户帐户进行更新时接收来自 Microsoft Graph 的更改通知。</span><span class="sxs-lookup"><span data-stu-id="2ead5-104">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="2ead5-105">应用程序将管理更改通知订阅并使用 Microsoft Graph 中的跟踪更改, 以确保不会丢失任何更改。</span><span class="sxs-lookup"><span data-stu-id="2ead5-105">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

- [<span data-ttu-id="2ead5-106">实验室手册</span><span class="sxs-lookup"><span data-stu-id="2ead5-106">Lab Manual</span></span>](./Lab.md)

## <a name="demos"></a><span data-ttu-id="2ead5-107">演示</span><span class="sxs-lookup"><span data-stu-id="2ead5-107">Demos</span></span>

- [<span data-ttu-id="2ead5-108">创建 .NET Core 应用程序</span><span class="sxs-lookup"><span data-stu-id="2ead5-108">Create a .NET Core app</span></span>](./demos/01-create-application)
- [<span data-ttu-id="2ead5-109">添加订阅生命周期</span><span class="sxs-lookup"><span data-stu-id="2ead5-109">Add Subscription Lifecycle</span></span>](./demos/02-subscription-management)
- [<span data-ttu-id="2ead5-110">添加修订</span><span class="sxs-lookup"><span data-stu-id="2ead5-110">Add Track Changes</span></span>](./demos/03-track-changes)

## <a name="watch-the-module"></a><span data-ttu-id="2ead5-111">观看模块</span><span class="sxs-lookup"><span data-stu-id="2ead5-111">Watch the module</span></span>

<span data-ttu-id="2ead5-112">此模块已记录并在 Office 开发 YouTube 频道中可用:[更改通知并使用 Microsoft Graph 跟踪更改](https://youtu.be/fThiCZmIcMQ)</span><span class="sxs-lookup"><span data-stu-id="2ead5-112">This module has been recorded and is available in the Office Development YouTube channel: [Change Notifications and Track Changes with the Microsoft Graph](https://youtu.be/fThiCZmIcMQ)</span></span>

## <a name="contributors"></a><span data-ttu-id="2ead5-113">参与者</span><span class="sxs-lookup"><span data-stu-id="2ead5-113">Contributors</span></span>

|        <span data-ttu-id="2ead5-114">角色</span><span class="sxs-lookup"><span data-stu-id="2ead5-114">Roles</span></span>         |                                       <span data-ttu-id="2ead5-115">作者 (s)</span><span class="sxs-lookup"><span data-stu-id="2ead5-115">Author(s)</span></span>                                       |
| -------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="2ead5-116">实验室手册/幻灯片</span><span class="sxs-lookup"><span data-stu-id="2ead5-116">Lab Manuals / Slides</span></span> | <span data-ttu-id="2ead5-117">Andrew Connell (Microsoft MVP, Voitanos) [@andrewconnell](//github.com/andrewconnell)</span><span class="sxs-lookup"><span data-stu-id="2ead5-117">Andrew Connell (Microsoft MVP, Voitanos) [@andrewconnell](//github.com/andrewconnell)</span></span> |
| <span data-ttu-id="2ead5-118">承办人/支持</span><span class="sxs-lookup"><span data-stu-id="2ead5-118">Sponsor / Support</span></span>    | <span data-ttu-id="2ead5-119">Jeremy Thake (Microsoft) [@jthake](//github.com/jthake)</span><span class="sxs-lookup"><span data-stu-id="2ead5-119">Jeremy Thake (Microsoft) [@jthake](//github.com/jthake)</span></span>                               |

## <a name="version-history"></a><span data-ttu-id="2ead5-120">版本历史记录</span><span class="sxs-lookup"><span data-stu-id="2ead5-120">Version history</span></span>

| <span data-ttu-id="2ead5-121">版本</span><span class="sxs-lookup"><span data-stu-id="2ead5-121">Version</span></span> |      <span data-ttu-id="2ead5-122">日期</span><span class="sxs-lookup"><span data-stu-id="2ead5-122">Date</span></span>      |                     <span data-ttu-id="2ead5-123">注释</span><span class="sxs-lookup"><span data-stu-id="2ead5-123">Comments</span></span>                     |
| ------- | -------------- | ------------------------------------------------ |
| <span data-ttu-id="2ead5-124">1.3</span><span class="sxs-lookup"><span data-stu-id="2ead5-124">1.3</span></span>     | <span data-ttu-id="2ead5-125">2019年6月18日</span><span class="sxs-lookup"><span data-stu-id="2ead5-125">June 18, 2019</span></span>  | <span data-ttu-id="2ead5-126">更新了用于刷新截屏视频录制的自述文件</span><span class="sxs-lookup"><span data-stu-id="2ead5-126">Updated readme to refreshed screencast recording</span></span> |
| <span data-ttu-id="2ead5-127">1.2</span><span class="sxs-lookup"><span data-stu-id="2ead5-127">1.2</span></span>     | <span data-ttu-id="2ead5-128">5月30日, 2019</span><span class="sxs-lookup"><span data-stu-id="2ead5-128">May 30, 2019</span></span>   | <span data-ttu-id="2ead5-129">Fy2019Q4 内容刷新</span><span class="sxs-lookup"><span data-stu-id="2ead5-129">Fy2019Q4 content refresh</span></span>                         |
| <span data-ttu-id="2ead5-130">1.1</span><span class="sxs-lookup"><span data-stu-id="2ead5-130">1.1</span></span>     | <span data-ttu-id="2ead5-131">2019 年 4 月 9 日</span><span class="sxs-lookup"><span data-stu-id="2ead5-131">April 9, 2019</span></span>  | <span data-ttu-id="2ead5-132">添加了截屏视频链接</span><span class="sxs-lookup"><span data-stu-id="2ead5-132">Added screencast link</span></span>                            |
| <span data-ttu-id="2ead5-133">1.0</span><span class="sxs-lookup"><span data-stu-id="2ead5-133">1.0</span></span>     | <span data-ttu-id="2ead5-134">2019 年 3 月 14 日</span><span class="sxs-lookup"><span data-stu-id="2ead5-134">March 14, 2019</span></span> | <span data-ttu-id="2ead5-135">新模块已提交</span><span class="sxs-lookup"><span data-stu-id="2ead5-135">New module submitted</span></span>                             |

## <a name="disclaimer"></a><span data-ttu-id="2ead5-136">免责声明</span><span class="sxs-lookup"><span data-stu-id="2ead5-136">Disclaimer</span></span>

<span data-ttu-id="2ead5-137">**此代码_按_原样提供, 无需任何明示或暗示的担保, 包括对特定目的适用性、适销性或不侵权的任何暗示担保。**</span><span class="sxs-lookup"><span data-stu-id="2ead5-137">**THIS CODE IS PROVIDED _AS IS_ WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>

<img src="https://telemetry.sharepointpnp.com/msgraph-training-changenotifications" />
