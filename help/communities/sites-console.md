---
title: 社区站点控制台
seo-title: 社区站点控制台
description: 如何访问“社区站点”控制台
seo-description: 如何访问“社区站点”控制台
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
translation-type: tm+mt
source-git-commit: f4cdd3d5020b917676fe8715d4e21e98f3a096b4
workflow-type: tm+mt
source-wordcount: '3241'
ht-degree: 3%

---


# 社区站点控制台 {#communities-sites-console}

通过“社区站点”控制台，可以访问：

* 站点创建
* 站点编辑
* 站点管理
* [创建和编辑嵌套组](groups.md) （子社区）

请参 [阅AEM Communities入门](getting-started.md) ，体验在创作环境下创建社区站点的速度，以及如何从创作者和发布环境创建社区组。

>[!NOTE]
>
>用于创建社区站点的主“社 [区”菜单](sites-console.md)、社 [区站点模板](sites.md)、社 [区组模板](tools-groups.md) 和社区功 [能的主“社区”菜单仅供作](functions.md) 者环境使用。

## 前提条件 {#prerequisites}

在创建社区站点之前，需 *要* :

* 确保一个或多个发布实例正在运行
* 启用隧 [道服务](deploy-communities.md#tunnel-service-on-author) ，以管理成员和成员组
* 识别主发 [布者](deploy-communities.md#primary-publisher)
* [在主发布者端口不是](deploy-communities.md#replication-agents-on-author) 默认端口时配置复制(4503)

最佳实践是，为确保站点能够支持许多功能，请采取以下步骤：

* 安装最 [新功能包](deploy-communities.md#latestfeaturepack)
* 让Adobe Analytics [成为](analytics.md) AEM Communities
* 配置电子 [邮件](email.md)
* 识别社 [区管理员](users.md#creating-community-members)
* [为社交登录启用](social-login.md#adobe-granite-oauth-authentication-handler) OAuth处理程序

## 访问社区站点控制台 {#accessing-communities-sites-console}

在创作环境中，要访问“社区站点”控制台：

* 从全局导航： **[!UICONTROL “社区”>“站点”]**

“社区站点”控制台显示任何现有社区站点。 在此控制台中，可以创建、编辑、管理和删除社区站点。

要创建新社区站点，请选择“创 **建** ”图标。

要访问现有社区站点，为创作、修改、发布、导出或添加嵌套组，请选择站点的文件夹图标。

例如，下图显示了主“社区站点”控制台，其中显示了两个社区站点的文件夹： [启用](getting-started-enablement.md) 和 [吸引](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## 站点创建 {#site-creation}

站点创建控制台提供了一种分步方法，根据选定的社区站点模板和设置来 [组合站点](sites.md) 的功能。

创建的每个站点都包含登录功能，因为站点访客必须先登录才能发布内容、发送消息或加入组。 其他功能包括用户用户档案、消息、通知、站点菜单、搜索、主题和品牌。

通过选择“社区站点” `Create` 控制台顶部的按钮启动该过程。

创建过程是一系列步骤，这些步骤以面板的形式呈现，其中包含要配置的一组特征（以子面板的形式呈现）。 在最后一步中提交站点 **之前** ，可 **以前** 进到下一步，也可以后退到上一步。

### 第1步：站点模板 {#step-site-template}

![新站点模板](assets/newsitetemplate.png)

在“站点模板”面板中，将指定标题、说明、站点根、基本语言、名称和站点模板：

* **[!UICONTROL 社区站点标题]**:站点的显示标题。

   标题将显示在已发布的站点上以及站点管理员UI中。

* **[!UICONTROL 社区站点描述]**:站点的描述。

   该说明不显示在已发布的站点上。

* **[!UICONTROL 社区站点根目录]**:站点的根路径。

   默认根目录 `/content/sites`为，但根目录可以移动到网站中的任何位置。

* **[!UICONTROL 社区站点基础语言]**:(对于单种语言，请保持不变：英语)使用下拉菜单从可用 *语言* (德语、意大利语、法语、日语、西班牙语、葡萄牙语（巴西）、繁体中文和简体中文)中选择一种或多种基本语言。 将根据多语言站点的翻译内容中介绍的最佳实践，为添加的每种语言创建一个社区站点，并且该站点将 [存在于同一站点文件夹中](../../help/sites-administering/translation.md)。 每个站点的根页面将包含一个由所选语言之一的语言代码命名的子页面，如英语为“en”或法语为“fr”。

* **[!UICONTROL 社区站点名称]**:站点的根页面的名称，显示在URL中

   * 多次-检查名称，因为创建站点后该名称不易更改
   * 基本URL( `https://*server:port/site root/site name*)` 将显示在 `Community Site Name`
   * 对于有效的URL，请附加基本语言代码+ &quot;。html&quot;

      *例如*, `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL “社区站点模板]** ”菜单：使用下拉菜单选择可用的社 [区站点模板](tools.md)。

Select **[!UICONTROL Next]**

### 第2步：设计 {#step-design}

“设计”面板包含两个用于选择主题和品牌横幅的子面板：

#### COMMUNITY SITE THEME {#community-site-theme}

![sitetheme-1](assets/sitetheme-1.png)

该框架使 [用TwitterBootstrap](https://twitterbootstrap.org/) ，为网站提供响应迅速、灵活的设计。 可以选择多个预先加载的Bootstrap主题之一来设置所选社区站点模板的样式，或者可以上传Bootstrap主题。

选中后，主题将用不透明的蓝色复选标记覆盖。

发布社区站点后，可以编辑属 [性并选择](#modifying-site-properties) 其他主题。

#### COMMUNITY SITE BRANDING {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

社区站点品牌是显示为每个页面顶部标题的图像。

图像的大小应与浏览器中页面的预期显示大小相同，高度应为120像素。

创建或选择图像时，请牢记：

* 图像高度将从图像的上边缘裁剪为120像素
* 图像已固定到浏览器窗口的左边缘
* 图像不会调整大小，因此当图像宽度为……

   * 小于浏览器的宽度，图像将水平重复
   * 图像宽度大于浏览器的宽度后，图像会被裁切

选择&#x200B;**[!UICONTROL 下一步]**。

### 第3步：设置 {#step-settings}

“设置”面板包含几个子面板，这些子面板显示要配置的功能，然后转到创建站点的最后一步。

* [用户管理](#user-management)
* [标记](#tagging)
* [角色](#roles)
* [协调](#moderation)
* [分析](#analytics)
* [翻译](#translation)
* [支持](#enablement)

>[!NOTE]
>
>**启用隧道服务**
>
>几个“设置”子面板允许指定受信任成员以审核UGC、管理组或成为发布环境中的启用资源联系人。
>
>约定发布端用户 [和用户组](users.md) （成员和成员组）在创作环境中不重复。
>
>因此，在创作环境中创建社区站点并将受信任成员分配给各种角色时，必须从发布环境检索成员数据。
>
>这是通过为作者 ` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`环境启用而实现的。

#### USER MANAGEMENT {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>建议将教育社 [区站点](overview.md#enablement-community) （有关详细信息，请与客户代表联系）。
>
>当拒绝匿名站点访客访问、不能自行注册或不能使用社交登录时，社区站点是私有的。

* **[!UICONTROL 允许用户注册]**

   如果选中此项，站点访客可以通过自助注册成为社区成员。

   如果未选中，则会限 *制社区* 站点，并且必须将站点访客分配给社区站点的成员组、发出请求或通过电子邮件发送邀请。 如果未选中，则不允许匿名访问。

   取消选中私 *人社* 区站点。 选中默认值。

* **[!UICONTROL 允许匿名访问]**

   如果选中，则社区站点将 *打开* ，任何站点访客都可以访问该站点。

   如果未选中，则只有登录成员才能访问该站点。

   取消选中私 *人社* 区站点。 选中默认值。

* **[!UICONTROL 允许发送消息]**

   如果选中，成员可以向彼此发送消息，并向社区站点内的组发送消息。

   如果未选中，则不会为社区设置消息。

   默认为未选中。

* **[!UICONTROL 允许社交登录: Facebook]**

   如果选中，则允许网站访客使用其Facebook帐户凭据登录。 在创建 [社区站点后](social-login.md#create-a-facebook-connect-cloud-service) ，应将选定的Facebook云配置配置为将用户添加到社区站点的成员组。

   如果不选中，则不显示Facebook登录名。

   对私人社区站点 *取消选* 中选项。 默认为未选中。

* **[!UICONTROL 允许社交登录: Twitter]**

   如果选中，允许站点访客使用其Twitter帐户凭据登录。 应将选 [定的Twitter](social-login.md#create-a-twitter-connect-cloud-service) 云配置配置为在创建社区站点后将用户添加到社区站点的成员组。

   如果不选中，则不显示Twitter登录名。

   对私人社区站点 *取消选* 中选项。 默认为未选中。

>[!NOTE]
>
>**[!UICONTROL 允许社交登录]**
>
>尽管Facebook和Twitter配置示例可能存在并可供选择，但对于 [生产环境](../../help/sites-administering/production-ready.md)，有必要创建自定义Facebook和Twitter应用程序。 请参 [阅使用Facebook和Twitter进行社交登录](social-login.md)。

#### TAGGING {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

可应用于社区内容的标记通过选择之前通过标记控制台定义的标记命名空间来 [进行控制](../../help/sites-administering/tags.md#tagging-console)。

此外，为社区站点选择标记命名空间会限制在定义目录和资源时显示的选择。 有关重 [要信息，请参阅](tag-resources.md) “标记启用资源”。

* 文本搜索框：开始键入以标识允许在站点上使用的标记

#### ROLES {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

社 [区成员的角色](users.md) ，会通过这些设置进行分配。

使用预先键入搜索，可轻松查找社区成员。

* **[!UICONTROL 社区管理员]**

   开始键入以选择一个或多个社区成员或成员组，这些成员组可以管理社区成员和成员组。

* **[!UICONTROL 社区审查方]**

   开始键入以选择一个或多个社区成员或成员组，这些成员组将作为用户生成内容的版主者受信任。

* **[!UICONTROL 拥有权限的社区成员]**

   开始键入以选择一个或多个社区成员或要赋予其在为社区功能选择后创建新内 `Allow Privileged Member` 容的能力的成 [员组](functions.md)。

#### MODERATION {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

用于调节用户生成的内容(UGC)的全局设置由这些设置控制。 单个组件具有其他设置来控制仲裁。

* **[!UICONTROL 内容已通过预审]**

   如果选中此项，则发布的社区内容只有在审查方批准后才会显示。 默认为未选中。 有关详细信息，请参 [阅协调社区内容](moderate-ugc.md#premoderation)。

* **[!UICONTROL 标记阈值，达到此值后隐藏内容]**

   如果大于0，则主题或帖子在隐藏到公共视图之前必须标出的次数。 如果设置为-1，则标记的主题或帖子从不隐藏于公开视图。 默认值为5。

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL 启用 Analytics]**

   仅当Adobe Analytics已配置 [Communities功](analytics.md) 能时可用。

   默认为未选中。 选中后，将显示其他选择菜单：

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL 云配置框架引用]**

   从下拉菜单中，选择为此社区站点配置的Analytics云服务框架。

   `Communities`是Analytics Configuration for Communities Features文 [档中的框架示例](analytics.md#aem-analytics-framework-configuration) 。

#### TRANSLATION {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL 允许机器翻]**&#x200B;译选中（默认为未选中）后，站点内的UGC将启用机器翻译。 这不会影响任何其他内容，如页面内容，即使该站点设置为多语言站点也是如此。 有关 [为AEM Communities配置授权翻译服务](translate-ugc.md) ，请参阅翻译用户生成的内容。 有关 [完整概述，请参阅](../../help/sites-administering/translation.md) “多语言站点翻译内容”。

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL 为选定的语言启用机器翻译]**

   启用机器翻译的语言默认为翻译集成配置指定的 [系统设置](translate-ugc.md#translation-integration-configuration)。 通过删除默认值和／或从下拉菜单中选择其他语言，可能会覆盖此站点的这些默认设置。

* **[!UICONTROL 选择翻译提供商]**

   默认情况下，服务提供商是仅用于演示的 `microsoft`试用服务。 如果未授权翻译服务提供商, **应取消选中** “允许机器翻译”。

* **[!UICONTROL 选择全球共享商店]**

   对于包含多个语言副本的网站，全局共享商店提供单一的对话线程，每个语言副本中均可见。 这是通过选择作为语言副本包含的语言之一来实现的。 默认为 *无全局共享存储*。

* **[!UICONTROL 选择翻译提供商配置]**

   选择为 [授权翻译提供者](../../help/sites-administering/tc-tic.md) 创建的翻译集成框架。

* **为您的社区站点选择翻译选项**

   * **[!UICONTROL 翻译整个页面]**

      如果选中此选项，则页面上的所有UGC都将转换为页面的基本语言。

      未选 *择默认值*。

   * **[!UICONTROL 仅翻译选定内容]**

      如果选中此项，则每个帖子旁边会显示一个翻译选项，允许将各个帖子翻译为页面的基本语言。

      选中默认 *值*。

* **选择持久性选项**

   * **[!UICONTROL 依据用户的请求翻译贡献的文稿，并在此后持续]**

      如果选中此选项，则直到发出请求后，内容才会进行翻译。 翻译完成后，翻译会存储在存储库中。

      未选 *择默认值*。

   * **[!UICONTROL 不保留翻译]**

      如果选择此项，则转换不会存储在存储库中。

      如果未选择，则保留翻译。

      未选 *择默认值*。

* **[!UICONTROL 智能渲染]**&#x200B;选择其中一项

   * `Always show contributions in the original language` (默认)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### ENABLEMENT {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

当选 `ENABLEMENT`定的社区站点模板包含分配功能时，这些设 [置将适用](functions.md#assignments-function)，在授权功能获得许可和配置时，这 [些功能可用](enablement.md)。 包含分配功能的参考站点模板是 `Reference Structured Learning Site Template.`

* **[!UICONTROL 启用管理者]**

   （必需）只有组成员 `Community Enablementmanagers` 可以被选择来管理此启用社区。 Enablement Manager负责将成员分配给资源。 另请参阅 [管理用户和用户组](users.md)。

* **[!UICONTROL Marketing Cloud 组织 ID]**

   （可选）视频心跳分析 [许可证的ID](analytics.md#video-heartbeat-analytics) 。

选择&#x200B;**[!UICONTROL 下一步]**。

### 第4步：创建社区站点 {#step-create-communities-site}

如果需要调整，请使 **用** “返回”按钮。

选择 **并启** 动“创建”后，创建站点的过程将无法中断。

创建站点后：

* 不支持更改url（节点名称）
* 将来更改社区站点模板不会影响创建的社区站点
* 禁用社区站点模板不会影响创建的社区站点
* 可通过修改社区 [站点](#modify-structure) 的属性来编辑其STRUCTURE

![chlimage_1-458](assets/chlimage_1-458.png)

完成该过程后，新站点的文件夹会显示在“社区站点”控制台中，作者可以从该控制台添加页面内容，或管理员可以修改站点的属性。

![chlimage_1-459](assets/chlimage_1-459.png)

要修改社区站点，请选择其项目文件夹以将其打开：

![siteactions-2](assets/siteactions-2.png)

当用鼠标悬停在站点上或触摸站点卡时，会出现以作者 [模式编辑站点](#authoring-site-content)、打开站点属性进行 [修改、](#modifying-site-properties)发布站点 [、导](#publishing-the-site)[](#exporting-the-site)[](#deleting-the-site)出站点、删除站点图标。

## 创作站点内容 {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

站点的内容可以与任何其他AEM网站使用相同的工具进行创作。 要打开站点进行创作，请选 `Open Site` 择鼠标悬停站点时显示的图标。 站点将在新选项卡中打开，以便“社区站点”控制台仍可访问。

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
>
>如果不熟悉AEM，请视图有关基本 [操作的文档](../../help/sites-authoring/basic-handling.md) ，并 [阅读页面创作快速指南](../../help/sites-authoring/qg-page-authoring.md)。

## 修改站点属性 {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

通过选择鼠标悬停站点时显示的图标，可以修改在站点创建过程中 `Edit Site`指定的现有站点的属性。

`Details of the following properties match the descriptions provided in the` [“站点创建](#site-creation) ”部分。

![chlimage_1-463](assets/chlimage_1-463.png)

### 修改基本 {#modify-basic}

BASIC面板允许修改

* 社区站点标题
* 社区站点描述

不能修改社区站点名称。

选择其他社区站点模板不会影响现有社区站点，因为模板和站点之间没有任何连接。

相反，可 [以修](#modify-structure) 改社区站点的STRUCTURE。

### 修改结构 {#modify-structure}

STRUCTURE面板允许修改最初从所选社区站点模板创建的结构。 从面板中，

* 将其他社区功 [能拖放到](functions.md) 站点结构中
* 在站点结构中社区功能的实例上：

   * **`gear icon`**

      编辑设置，包括显示标题和URL name&amp;ast;

      以及特权 [成员组](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      从站点结构中删除（删除）函数

   * **`grid icon`**

      修改站点顶级导航栏中显示的功能顺序

>[!NOTE]
>
>除了顶部的函数外，您可以更改“站点结构”中所有函数的顺序。 因此，不能更改社区站点的主页。

>[!CAUTION]
>
>虽然显示标题可以在不产生副作用的情况下进行更改，但不建议编辑属于社区站点的社区功能的URL名称。
>
>例如，重命名URL不会移动现有UGC，因此具有“丢失”UGC的效果。

>[!CAUTION]
>
>组函数不 *能是* 站 *点结构中* 的第一个，也不能是唯一的函数。
>
>任何其他函数(如页 [面函数](functions.md#page-function))必须首先包含并列出。

#### 示例：将目录功能添加到社区站点结构 {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### 修改设计 {#modify-design}

DESIGN面板允许应用新主题：

* [社区站点主题](#community-site-theme)
* [社区站点品牌化](#community-site-branding)
   * 滚动到面板底部以更改品牌图像

### 修改设置 {#modify-settings}

“设置”面板允许访问社区站点创建步骤3的子面板下的大多数设置：

* [用户管理](#user-management)
* [标记](#tagging)
* [审核](#moderation)
* [成员角色](#roles)
* [分析](#analytics)
* [翻译](#translation)

### 修改缩略图 {#modify-thumbnail}

通过THUMBNAIL面板，可以上传图像以在“社区站点”控制台中代表站点。

### 修改启用 {#modify-enablement}

ENABLEMENT面板允许访问在社区站点创建过程中提供的设置。

请参阅 [ENABLEMENT](#enablement) description。

## 发布站点 {#publishing-the-site}

新建或修改社区站点后，可以选择鼠标悬停在站点上时显示的图标 `Publish Site` 来发布（激活）站点。

![chlimage_1-465](assets/chlimage_1-465.png)

网站成功发布后将显示一个指示。

![chlimage_1-466](assets/chlimage_1-466.png)

### 使用嵌套组发布 {#publishing-with-nested-groups}

发布社区站点后，必须单独发布使用“组”控制台创建的每个子社区(嵌套 [组)](groups.md)。

## 导出站点 {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

选择导出图标（鼠标悬停在站点上）以创建同时存储在包管理器中和已下载的 [社区站](../../help/sites-administering/package-manager.md) 点包。\
请注意，UGC未包含在站点包中。

## 删除站点 {#deleting-the-site}

![deleteicon-1](assets/deleteicon-1.png)

要删除社区站点，请选择将鼠标悬停在“社区站点”控制台中该站点上时显示的“删除站点”图标。 此操作将删除与站点关联的所有项目，如UGC、用户组、资产和数据库记录。

## 创建的社区用户组 {#created-community-user-groups}

发布新社区站点后，新成员组(在发布环境创建用户组)将具有为各种管理和成员角色设置的相应权限。

为成员组创建的名称 *包括步骤1* （URL中显示的名称）中给定 [](#step13asitetemplate) 站点的站点名，以及一个唯一ID，以避免与社区站点以及具有不同社区站点根目录的具有相同站点名的组发生冲突。

例如，如果标题为“入门教程”的站点的名称为“参与”，则版主的用户组将为：

* 标题：社区参与版主
* 名称：community-*engage-uid*-moderators

请注意，在创建站点时，任何分配了主持人角色或组管理员角色的成员都将分配到相应的组，并分配到成员组。 发布新站点时，将在发布时创建这些组和成员分配。

有关详细信息，请 [参阅管理用户和用户组](users.md)。

>[!NOTE]
>
>如果允 [许社交登录：在用户](#user-management) 组启用后，Facebook即处于启用状态
>
>* community-*&lt;site-name>*-*&lt;uid>*-members

已创建，应将已 [应用的Facebook](social-login.md#createafacebookcloudservice) 云服务配置为将用户添加到此组。

## 配置身份验证错误 {#configure-for-authentication-error}

默认情况下，当用户输入错误凭据且无法登录时，社区站点将重定向到示例登录页。 此示例登录在生产服务器上不 [存在](../../help/sites-administering/production-ready.md)。

要正确重定向，在将站点配置并推送到发布后，请完成以下步骤，以获取身份验证失败，将其重定向到社区站点：

* 在每个AEM发布实例上
* 首次以管理员权限登录
* 访问 [Web控制台](../../help/sites-deploying/configuring-osgi.md)
   * 例如， [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* 定位 `Adobe Granite Login Selector Authentication Handler`
* 选择图 `pencil`标以打开要编辑的配置
* 按如下 **[!UICONTROL 输入登录页]** 面映射：

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   例如：

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Select **[!UICONTROL Save]**

![chlimage_1-468](assets/chlimage_1-468.png)

### 测试身份验证重定向 {#test-authentication-redirection}

在为社区站点配置登录页面映射的同一AEM发布实例上：

* 浏览社区站点主页
   * 例如， [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* 选择注销
* 选择登录
* 输入明显不正确的凭据，如用户名“x”和密码“x”
* 登录页面应显示“登录无效”错误

![chlimage_1-469](assets/chlimage_1-469.png)

## 从主站点控制台访问社区站点 {#accessing-community-sites-from-main-sites-console}

在全局导航站点控制台中，社区站点位于文件夹 `Community Sites` 中。

虽然可以通过这种方式访问社区站点，但对于管理任务，应从“社区站点”控制台访问社区站点。

![chlimage_1-470](assets/chlimage_1-470.png)

