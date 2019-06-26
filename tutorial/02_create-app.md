<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="fc7a2-101">在本练习中, 你将使用 Azure Active Directory 管理中心创建新的 Azure AD web 应用程序注册, 并向管理员授予所需权限范围的许可。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="fc7a2-102">打开浏览器并导航到[Azure Active Directory 管理中心 (https://aad.portal.azure.com)](https://aad.portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-102">Open a browser and navigate to the [Azure Active Directory admin center (https://aad.portal.azure.com)](https://aad.portal.azure.com).</span></span> <span data-ttu-id="fc7a2-103">使用**工作或学校帐户**登录。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="fc7a2-104">在左侧导航栏中选择 " **Azure Active Directory** ", 然后选择 "**管理**" 下的 "**应用程序注册**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![应用注册的屏幕截图](./images/aad-portal-home.png)

1. <span data-ttu-id="fc7a2-106">选择“新注册”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-106">Select **New registration**.</span></span> <span data-ttu-id="fc7a2-107">在 "**注册应用程序**" 页上</span><span class="sxs-lookup"><span data-stu-id="fc7a2-107">On the **Register an application** page</span></span>

    !["应用注册" 页的屏幕截图](./images/aad-portal-newapp.png)

    <span data-ttu-id="fc7a2-109">设置值, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="fc7a2-109">Set the values as follows:</span></span>

    - <span data-ttu-id="fc7a2-110">**名称**: GraphNotificationTutorial</span><span class="sxs-lookup"><span data-stu-id="fc7a2-110">**Name**: GraphNotificationTutorial</span></span>
    - <span data-ttu-id="fc7a2-111">**受支持的帐户类型**: 任何组织目录和个人 Microsoft 帐户中的帐户</span><span class="sxs-lookup"><span data-stu-id="fc7a2-111">**Supported account types**: Accounts in any organizational directory and personal Microsoft accounts</span></span>
    - <span data-ttu-id="fc7a2-112">**重定向 URI**: Web >http://localhost</span><span class="sxs-lookup"><span data-stu-id="fc7a2-112">**Redirect URI**: Web > http://localhost</span></span>

    !["注册应用程序" 页的屏幕截图](./images/aad-portal-newapp-01.png)

    <span data-ttu-id="fc7a2-114">选择 "**注册**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-114">Select **Register**.</span></span>

1. <span data-ttu-id="fc7a2-115">在 " **GraphNotificationTutorial** " 页上, 复制**应用程序 (客户端) id**和**目录 (租户) id**的值保存它, 在下一步中将需要它们。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-115">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![新应用注册的应用程序 ID 的屏幕截图](./images/aad-portal-newapp-details.png)

1. <span data-ttu-id="fc7a2-117">选择 "**管理 > 证书 & 密码**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-117">Select **Manage > Certificates & secrets**.</span></span> 

    <span data-ttu-id="fc7a2-118">选择 "**新建客户端密码**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-118">Select **New client secret**.</span></span>

    <span data-ttu-id="fc7a2-119">在 "**说明**" 中输入一个值, 然后选择 "**过期**" 选项之一, 然后选择 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-119">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    !["添加客户端密码" 对话框的屏幕截图](./images/aad-portal-newapp-secret.png)

    !["添加客户端密码" 对话框的屏幕截图](./images/aad-portal-newapp-secret-02.png)

1. <span data-ttu-id="fc7a2-122">离开此页前，先复制客户端密码值。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-122">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="fc7a2-123">将在下一步中用到它。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-123">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fc7a2-124">此客户端密码不会再次显示，所以请务必现在就复制它。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-124">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![新添加的客户端密码的屏幕截图](./images/aad-portal-newapp-secret-03.png)

1. <span data-ttu-id="fc7a2-126">选择 "**管理 > API 权限**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-126">Select **Manage > API Permissions**.</span></span>

    <span data-ttu-id="fc7a2-127">选择 "**添加权限**", 然后选择 " **Microsoft Graph**"。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-127">Select **Add a permission** and select **Microsoft Graph**.</span></span>

    ![选择 Microsoft Graph 服务的屏幕截图](./images/aad-portal-newapp-graphscope.png)

    <span data-ttu-id="fc7a2-129">选择 "**应用程序权限**", 展开**用户**组, 然后选择 "**用户" 所有**作用域。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-129">Select **Application Permission**, expand the **User** group and select **User.ReadWrite.All** scope.</span></span>

    <span data-ttu-id="fc7a2-130">选择 "**添加权限**" 以保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-130">Select **Add permissions** to save your changes.</span></span>

    ![选择 Microsoft Graph 范围的屏幕截图](./images/aad-portal-newapp-graphscope-02.png)

    ![新添加的客户端密码的屏幕截图](./images/aad-portal-newapp-graphscope-03.png)

<span data-ttu-id="fc7a2-133">应用程序请求用户的应用程序权限。 **ReadWrite。所有**作用域。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-133">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="fc7a2-134">此权限要求具有管理许可。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-134">This permission requires administrative consent.</span></span>

<span data-ttu-id="fc7a2-135">选择 "**授予对 Contoso 的管理员同意**", 然后选择 **"是"** 以同意此应用程序, 并使用指定的范围授予应用程序对租户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="fc7a2-135">Select **Grant admin consent for Contoso**, then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![屏幕截图批准的管理员同意](./images/aad-portal-newapp-graphscope-04.png)
