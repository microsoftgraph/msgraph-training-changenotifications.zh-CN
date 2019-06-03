<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="3d23e-101">在本练习中, 你将使用 Azure Active Directory 管理中心创建新的 Azure AD web 应用程序注册, 并向管理员授予所需权限范围的许可。</span><span class="sxs-lookup"><span data-stu-id="3d23e-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="3d23e-102">打开浏览器，并转到 [Azure Active Directory 管理中心](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="3d23e-102">Open a browser and navigate to the [Azure Active Directory admin center](https://portal.azure.com).</span></span> <span data-ttu-id="3d23e-103">使用**工作或学校帐户**登录。</span><span class="sxs-lookup"><span data-stu-id="3d23e-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="3d23e-104">选择左侧导航栏中的“Azure Active Directory”\*\*\*\*，再选择“管理”\*\*\*\* 下的“应用注册(预览版)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d23e-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations (Preview)** under **Manage**.</span></span>

    ![<span data-ttu-id="3d23e-105">应用注册的屏幕截图</span><span class="sxs-lookup"><span data-stu-id="3d23e-105">A screenshot of the App registrations</span></span> ](./images/01.png)

1. <span data-ttu-id="3d23e-106">选择“新注册”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d23e-106">Select **New registration**.</span></span> <span data-ttu-id="3d23e-107">在“注册应用”\*\*\*\* 页上，按如下方式设置值。</span><span class="sxs-lookup"><span data-stu-id="3d23e-107">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="3d23e-108">将“名称”\*\*\*\* 设置为“`GraphNotificationTutorial`”。</span><span class="sxs-lookup"><span data-stu-id="3d23e-108">Set **Name** to `GraphNotificationTutorial`.</span></span>
    - <span data-ttu-id="3d23e-109">将“受支持的帐户类型”\*\*\*\* 设置为“任何组织目录中的帐户和个人 Microsoft 帐户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d23e-109">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="3d23e-110">在“重定向 URI”\*\*\*\* 下，将第一个下拉列表设置为“`Web`”，并将值设置为“`http://localhost`”。</span><span class="sxs-lookup"><span data-stu-id="3d23e-110">Under **Redirect URI**, set the first drop-down to `Web` and set the value to `http://localhost`.</span></span>

    !["注册应用程序" 页的屏幕截图](./images/02.png)

1. <span data-ttu-id="3d23e-112">选择 "**注册**"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-112">Select **Register**.</span></span> <span data-ttu-id="3d23e-113">在 " **GraphNotificationTutorial** " 页上, 复制**应用程序 (客户端) id**和**目录 (租户) id**的值保存它, 在下一步中将需要它们。</span><span class="sxs-lookup"><span data-stu-id="3d23e-113">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![新应用注册的应用程序 ID 的屏幕截图](./images/03.png)

1. <span data-ttu-id="3d23e-115">选择“管理”\*\*\*\* 下的“证书和密码”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d23e-115">Select **Certificates & secrets** under **Manage**.</span></span> <span data-ttu-id="3d23e-116">选择 "**新建客户端密码**"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-116">Select **New client secret**.</span></span> <span data-ttu-id="3d23e-117">在 "**说明**" 中输入一个值, 然后选择 "**过期**" 选项之一, 然后选择 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-117">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    !["添加客户端密码" 对话框的屏幕截图](./images/04.png)

1. <span data-ttu-id="3d23e-119">离开此页前，先复制客户端密码值。</span><span class="sxs-lookup"><span data-stu-id="3d23e-119">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="3d23e-120">将在下一步中用到它。</span><span class="sxs-lookup"><span data-stu-id="3d23e-120">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3d23e-121">此客户端密码不会再次显示，所以请务必现在就复制它。</span><span class="sxs-lookup"><span data-stu-id="3d23e-121">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![新添加的客户端密码的屏幕截图](./images/05.png)

1. <span data-ttu-id="3d23e-123">选择 "**管理**" 下的 " **API 权限**"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-123">Select **API Permissions** under **Manage**.</span></span> <span data-ttu-id="3d23e-124">**添加权限**并选择 " **Microsoft Graph**"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-124">**Add a permission** and select **Microsoft Graph**.</span></span> <span data-ttu-id="3d23e-125">选择 "**应用程序权限**" 并展开 "**用户**", 然后选择 "**所有**作用域"。</span><span class="sxs-lookup"><span data-stu-id="3d23e-125">Select **Application Permission** and expand **User** and select the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="3d23e-126">选择 "**添加权限**" 以保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="3d23e-126">Select **Add permissions** to save your changes.</span></span>

    ![新添加的客户端密码的屏幕截图](./images/06.png)

<span data-ttu-id="3d23e-128">应用程序请求用户的应用程序权限。 **ReadWrite。所有**作用域。</span><span class="sxs-lookup"><span data-stu-id="3d23e-128">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="3d23e-129">此权限要求具有管理许可。</span><span class="sxs-lookup"><span data-stu-id="3d23e-129">This permission requires administrative consent.</span></span>

<span data-ttu-id="3d23e-130">选择 "**授予对 Contoso 的管理员同意**", 然后选择 **"是"** 以同意此应用程序, 并使用指定的范围授予应用程序对租户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3d23e-130">Select **Grant admin consent for Contoso** and then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![登录屏幕截图](./images/07.png)
