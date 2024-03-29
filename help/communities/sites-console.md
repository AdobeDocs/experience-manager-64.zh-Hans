---
title: 社区站点控制台
seo-title: Communities Sites Console
description: 如何访问社区站点控制台
seo-description: How to access the Communities Sites console
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
role: Admin
exl-id: f1408709-5402-4f55-bd37-9943fe828af0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3263'
ht-degree: 3%

---

# 社区站点控制台 {#communities-sites-console}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

社区站点控制台提供对以下项的访问：

* 网站创建
* 网站编辑
* 站点管理
* [创建和编辑嵌套群组](groups.md) （子社区）

请参阅 [开始使用AEM Communities](getting-started.md) 了解如何在创作环境中快速创建社区站点，以及如何从创作和发布环境创建社区组。

>[!NOTE]
>
>用于创建 [社区站点](sites-console.md), [社区网站模板](sites.md), [社区组模板](tools-groups.md) 和 [社区功能](functions.md) 只能在创作环境中使用。

## 前提条件 {#prerequisites}

在创建社区站点之前，它是 *必需* 至：

* 确保一个或多个发布实例正在运行
* 启用 [隧道服务](deploy-communities.md#tunnel-service-on-author) 管理成员和成员组
* 识别 [主发布者](deploy-communities.md#primary-publisher)
* [配置复制](deploy-communities.md#replication-agents-on-author) 当主发布者端口不是默认端口时(4503)

为确保站点准备好支持许多功能，最佳做法是采取以下步骤：

* 安装 [最新功能包](deploy-communities.md#latestfeaturepack)
* 启用 [Adobe Analytics](analytics.md) 对于AEM Communities
* 配置 [电子邮件](email.md)
* 识别 [社区管理员](users.md#creating-community-members)
* [启用OAuth处理程序](social-login.md#adobe-granite-oauth-authentication-handler) 用于社交登录

## 访问社区站点控制台 {#accessing-communities-sites-console}

在创作环境中，要访问社区站点控制台，请执行以下操作：

* 从全局导航： **[!UICONTROL 社区>站点]**

“社区站点”控制台会显示任何现有的社区站点。 在此控制台中，可以创建、编辑、管理和删除社区站点。

要创建新的社区站点，请选择 **创建** 图标。

要访问现有的社区网站，为了创作、修改、发布、导出或添加嵌套群组，请选择站点的文件夹图标。

例如，下图显示了主社区站点控制台，其中显示了两个社区站点的文件夹： [启用](getting-started-enablement.md) 和 [参与](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## 站点创建 {#site-creation}

站点创建控制台提供了一种根据所选内容来组合站点功能的分步方法 [社区站点模板](sites.md) 和设置。

创建的每个网站都包含登录功能，因为网站访客在发布内容、发送消息或参与群组之前，必须先登录。 其他包含的功能包括用户配置文件、消息、通知、网站菜单、搜索、主题和品牌。

通过选择 `Create` 按钮。

创建过程是一系列步骤，这些步骤以面板的形式呈现，其中包含要配置的一组特征（以子面板的形式呈现）。 可以向 **下一个** 步骤或 **返回** 到上一步，然后再在最后一步中提交网站。

### 步骤1:网站模板 {#step-site-template}

![新站点模板](assets/newsitetemplate.png)

在“站点模板”面板中，指定了“标题”、“描述”、“站点根”、“基本语言”、“名称”和“站点模板”：

* **[!UICONTROL 社区站点标题]**:网站的显示标题。

   标题会显示在已发布的网站以及网站管理员UI中。

* **[!UICONTROL 社区站点描述]**:网站的描述。

   该描述不会显示在已发布的网站上。

* **[!UICONTROL 社区站点根目录]**:站点的根路径。

   默认根为 `/content/sites`，但可以将根移动到网站中的任何位置。

* **[!UICONTROL 社区站点基本语言]**:（单语言保持不变）英语)使用下拉菜单选择一个 *或更多* 基本语言 — 德语、意大利语、法语、日语、西班牙语、葡萄牙语（巴西）、中文（繁体）和简体中文。 将为添加的每种语言创建一个社区站点，并按照 [翻译多语言站点的内容](../../help/sites-administering/translation.md). 每个站点的根页面将包含一个子页面，该子页面由所选语言之一的语言代码命名，如“en”表示英语，“fr”表示法语。

* **[!UICONTROL 社区站点名称]**:站点根页面在URL中显示的名称

   * 请仔细检查名称，因为创建网站后，该名称不容易更改
   * 基本URL( `https://*server:port/site root/site name*)` 将显示在 `Community Site Name`
   * 对于有效的URL，请附加基本语言代码+ &quot;。html&quot;

      *例如*, `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL 社区站点模板]** 菜单：使用下拉菜单选择可用的 [社区站点模板](tools.md).

选择 **[!UICONTROL 下一个]**

### 步骤2:设计 {#step-design}

“设计”面板包含2个用于选择主题和品牌横幅的子面板：

#### 社区站点主题 {#community-site-theme}

![sitetheme-1](assets/sitetheme-1.png)

框架使用 `Twitter Bootstrap` 为网站引入响应式灵活设计。 可以选择多个预加载的Bootstrap主题之一来设置所选社区站点模板的样式，或者可以上传Bootstrap主题。

选择后，将使用不透明的蓝色复选标记覆盖主题。

发布社区网站后，可以 [编辑属性](#modifying-site-properties) 并选择其他主题。

#### 社区网站品牌化 {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

社区网站品牌化是在每个页面顶部显示为标题的图像。

图像的大小应与浏览器中页面的预期显示一样宽，高度应为120像素。

在创建或选择图像时，请记住：

* 图像高度将从图像的上边缘裁剪为120像素
* 图像已固定到浏览器窗口的左边缘
* 图像没有调整大小，因此当图像宽度为……

   * 小于浏览器的宽度，图像将水平重复
   * 大于浏览器的宽度，图像将被裁剪

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤3:设置 {#step-settings}

“设置”面板包含多个子面板，这些子面板显示要在移至创建站点的最后一步之前配置的功能。

* [用户管理](#user-management)
* [标记](#tagging)
* [角色](#roles)
* [审核](#moderation)
* [ANALYTICS](#analytics)
* [翻译](#translation)
* [启用](#enablement)

>[!NOTE]
>
>**启用隧道服务**
>
>几个“设置”子面板允许分配受信任成员以审核UGC、管理组或作为联系人，以在发布环境中获取启用资源。
>
>约定适用于发布端 [用户和用户组](users.md) （成员和成员组）。
>
>因此，在创作环境中创建社区站点并将可信成员分配给各种角色时，需要从发布环境中检索成员数据。
>
>这是通过启用 ` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`（在创作环境中）。

#### 用户管理 {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>建议 [启用社区站点](overview.md#enablement-community) 私有（有关更多信息，请联系您的客户代表）。
>
>当匿名网站访客被拒绝访问、不能自行注册，以及不能使用社交登录时，社区网站是私有的。

* **[!UICONTROL 允许用户注册]**

   如果选中此选项，则网站访客可以通过自行注册成为社区成员。

   如果未选中，则社区站点将 *受限* 和网站访客必须被分配到社区网站的成员组、提出请求或通过电子邮件发送邀请。 如果未选中，则不应允许匿名访问。

   取消选中 *私人* 社区站点。 默认选中。

* **[!UICONTROL 允许匿名访问]**

   如果选中，则社区站点为 *open* 和任何网站访客都可以访问该网站。

   如果未选中，则只有已登录的成员才能访问该站点。

   取消选中 *私人* 社区站点。 默认选中。

* **[!UICONTROL 允许发送消息]**

   如果选中，则成员可以向彼此发送消息，并向社区站点内的组发送消息。

   如果未选中此选项，则不会为社区设置消息传送。

   默认为未选中。

* **[!UICONTROL 允许社交登录: Facebook]**

   如果选中此项，则允许网站访客使用其Facebook帐户凭据登录。 选定的 [Facebook云配置](social-login.md#create-a-facebook-connect-cloud-service) 应配置为在创建社区站点后将用户添加到社区站点的成员组。

   如果未选中，则不会显示Facebook登录。

   取消选中 *私人* 社区站点。 默认为未选中。

* **[!UICONTROL 允许社交登录: Twitter]**

   如果选中此项，则允许网站访客使用其Twitter帐户凭据登录。 选定的 [Twitter云配置](social-login.md#create-a-twitter-connect-cloud-service) 应配置为在创建社区站点后将用户添加到社区站点的成员组。

   如果未选中，则不会显示Twitter登录。

   取消选中 *私人* 社区站点。 默认为未选中。

>[!NOTE]
>
>**[!UICONTROL 允许社交登录]**
>
>虽然Facebook和Twitter配置示例可能存在，并且可供选择，但是 [生产环境](../../help/sites-administering/production-ready.md)，则需要创建自定义Facebook和Twitter应用程序。 请参阅 [使用Facebook和Twitter进行社交登录](social-login.md).

#### 标记 {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

可应用于社区内容的标记可通过选择之前通过 [标记控制台](../../help/sites-administering/tags.md#tagging-console).

此外，为社区站点选择标记命名空间会限制在定义目录和资源时显示的选择。 请参阅 [标记支持资源](tag-resources.md) 以了解重要信息。

* 文本搜索框：开始键入以识别允许在网站上使用的标记

#### 角色 {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

的 [社区成员的角色](users.md) 会随这些设置一起分配。

使用提前键入搜索，可轻松查找社区成员。

* **[!UICONTROL 社区管理员]**

   开始键入内容以选择一个或多个社区成员或可管理社区成员和成员组的成员组。

* **[!UICONTROL 社区审查方]**

   开始键入内容以选择一个或多个社区成员或成员组，这些成员或成员组将作为用户生成内容的审核者受信任。

* **[!UICONTROL 拥有权限的社区成员]**

   开始键入内容以选择一个或多个社区成员或成员组，以便在 `Allow Privileged Member` 已为 [社区功能](functions.md).

#### 审核 {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

审核用户生成内容(UGC)的全局设置由这些设置控制。 单个组件具有用于控制审核的其他设置。

* **[!UICONTROL 内容已通过预审]**

   如果选中此项，则在审核者批准后才会显示已发布的社区内容。 默认为未选中。 有关更多信息，请参阅 [审核社区内容](moderate-ugc.md#premoderation).

* **[!UICONTROL 标记阈值，达到此值后隐藏内容]**

   如果大于0，则在将主题或帖子隐藏到公共视图中之前必须标记其次数。 如果设置为–1，则标记的主题或帖子永远不会在公共视图中隐藏。 默认值为5。

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL 启用 Analytics]**

   仅在Adobe Analytics [已配置](analytics.md) （针对社区功能）。

   默认为未选中。 选中此选项后，将显示额外的选择菜单：

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL 云配置框架引用]**

   从下拉菜单中，选择为此社区站点配置的Analytics云服务框架。

   `Communities`是 [社区功能的Analytics配置](analytics.md#aem-analytics-framework-configuration) 文档。

#### 翻译 {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL 允许机器翻译]**
选中此选项（默认选项未选中）后，将为网站中的UGC启用机器翻译。 这不会影响任何其他内容，例如页面内容，即使该网站设置为多语言网站也是如此。 请参阅 [翻译用户生成的内容](translate-ugc.md) 有关为AEM Communities配置授权翻译服务的信息。 请参阅 [翻译多语言站点的内容](../../help/sites-administering/translation.md) 以获取完整概述。

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL 为选定的语言启用机器翻译]**

   为机器翻译启用的语言默认为 [翻译集成配置](translate-ugc.md#translation-integration-configuration). 通过删除默认设置和/或从下拉菜单中选择其他语言，可能会覆盖此网站的这些默认设置。

* **[!UICONTROL 选择翻译提供商]**

   默认情况下，服务提供商是使用 `microsoft`仅供演示。 如果没有翻译服务提供商获得许可， **允许机器翻译** 应该不加限制。

* **[!UICONTROL 选择全球共享商店]**

   对于具有多个语言副本的网站，全局共享存储会提供单个会话线程，从每个语言副本中可见。 这可以通过选择其中一种语言作为语言副本来实现。 默认为 *无全局共享存储*.

* **[!UICONTROL 选择翻译提供商配置]**

   选择 [翻译集成框架](../../help/sites-administering/tc-tic.md) 为授权翻译提供程序创建。

* **为您的社区站点选择翻译选项**

   * **[!UICONTROL 翻译整个页面]**

      如果选择，则页面上的所有UGC都将转换为页面的基本语言。

      默认为 *未选定*.

   * **[!UICONTROL 仅翻译选定内容]**

      如果选中，则每个帖子旁边都会显示一个翻译选项，允许将各个帖子翻译成该页面的基本语言。

      默认为 *已选*.

* **选择持久性选项**

   * **[!UICONTROL 依据用户的请求翻译贡献的文稿，并在此后持续]**

      如果选中此选项，则在发出请求之前不会翻译内容。 翻译后，翻译会存储在存储库中。

      默认为 *未选定*.

   * **[!UICONTROL 不保留翻译]**

      如果选中，则转换不会存储在存储库中。

      如果未选择，则保留翻译。

      默认为 *未选定*.

* **[!UICONTROL 智能渲染]**
选择其中一个

   * `Always show contributions in the original language`（默认）
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### 启用 {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

的 `ENABLEMENT`当所选社区站点模板包含 [赋值函数](functions.md#assignments-function)，当启用功能获得许可并且 [已配置](enablement.md). 包括分配函数的参考站点模板是 `Reference Structured Learning Site Template.`

* **[!UICONTROL 启用管理者]**

   （必需）仅 `Community Enablementmanagers` 可选择群组以管理此启用社区。 支持经理负责将成员分配给资源。 另请参阅 [管理用户和用户组](users.md).

* **[!UICONTROL Marketing Cloud 组织 ID]**

   （可选） [视频心率分析](analytics.md#video-heartbeat-analytics) 许可证。

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤4:创建社区站点 {#step-create-communities-site}

如果需要进行任何调整，请使用 **返回** 按钮来制作它们。

一次 **创建** 选择并启动后，创建站点的过程将无法中断。

创建网站后：

* 不支持更改URL（节点名称）
* 将来对社区站点模板所做的更改将不会影响已创建的社区站点
* 禁用社区站点模板不会影响已创建的社区站点
* 可以编辑 [结构](#modify-structure) 通过修改其属性

![chlimage_1-458](assets/chlimage_1-458.png)

完成该过程后，新站点的文件夹将显示在社区站点控制台中，作者可以在此控制台中添加页面内容，或者管理员可以修改站点的属性。

![chlimage_1-459](assets/chlimage_1-459.png)

要修改社区站点，请选择其项目文件夹以将其打开：

![siteactions-2](assets/siteactions-2.png)

将鼠标悬停在网站上或触摸网站卡时，会显示图标，允许 [在创作模式下编辑网站](#authoring-site-content), [打开网站属性进行修改](#modifying-site-properties), [发布网站](#publishing-the-site), [导出网站](#exporting-the-site)和 [删除网站](#deleting-the-site).

## 创作网站内容 {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

网站内容的创作工具可能与任何其他AEM网站相同。 要打开要创作的站点，请选择 `Open Site` 鼠标悬停在网站上时显示的图标。 该站点将在新选项卡中打开，以便仍然可以访问社区站点控制台。

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
>
>如果不熟悉AEM，请查看 [基本操作](../../help/sites-authoring/basic-handling.md) 和 [页面创作快速指南](../../help/sites-authoring/qg-page-authoring.md).

## 修改网站属性 {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

通过选择 `Edit Site`图标。

`Details of the following properties match the descriptions provided in the` [网站创建](#site-creation) 中。

![chlimage_1-463](assets/chlimage_1-463.png)

### 修改基本 {#modify-basic}

基本面板允许修改

* 社区站点标题
* 社区站点描述

不能修改社区站点名称。

选择其他社区站点模板对现有社区站点不会产生任何影响，因为模板和站点之间没有任何连接。

相反， [结构](#modify-structure) 可以修改社区站点。

### 修改结构 {#modify-structure}

“结构”面板允许修改最初从所选社区站点模板创建的结构。 从面板，可以

* 拖放其他 [社区功能](functions.md) 进入网站结构
* 在站点结构中社区功能的实例上：

   * **`gear icon`**

      编辑设置，包括显示标题和URL名称&amp;ast;

      以及 [特权成员组](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      从站点结构中删除（删除）函数

   * **`grid icon`**

      修改在网站顶级导航栏中显示的函数顺序

>[!NOTE]
>
>除了顶部的函数外，您可以更改“网站结构”中所有函数的顺序。 因此，无法更改社区站点的主页。

>[!CAUTION]
>
>虽然显示标题可能会发生更改而不会产生副作用，但不建议编辑属于社区站点的社区函数的URL名称。
>
>例如，重命名URL不会移动现有UGC，因此会产生“丢失”UGC的效果。

>[!CAUTION]
>
>组函数必须 *not* be *第一，也是唯一* 函数。
>
>任何其他函数，例如 [页面函数](functions.md#page-function)，必须先包含并列出。

#### 示例：向社区站点结构添加目录函数 {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### 修改设计 {#modify-design}

“设计”面板允许应用新主题：

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

缩略图面板允许上传图像以在社区站点控制台中表示站点。

### 修改启用 {#modify-enablement}

启用面板允许访问在社区站点创建期间提供的设置。

请参阅 [启用](#enablement) 描述。

## 发布网站 {#publishing-the-site}

在社区网站新创建或修改后，可以通过选择 `Publish Site` 图标，该图标会在将鼠标悬停在网站上时显示。

![chlimage_1-465](assets/chlimage_1-465.png)

网站成功发布后，将显示一个指示。

![chlimage_1-466](assets/chlimage_1-466.png)

### 使用嵌套群组发布 {#publishing-with-nested-groups}

发布社区站点后，必须单独发布使用 [“组”控制台](groups.md).

## 导出网站 {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

选择将鼠标悬停在网站上的导出图标，以创建同时存储在 [包管理器](../../help/sites-administering/package-manager.md) 和下载。\
请注意，网站包中未包含UGC。

## 删除网站 {#deleting-the-site}

![deleteicon-1](assets/deleteicon-1.png)

要删除社区站点，请选择删除站点图标，该图标将鼠标悬停在社区站点控制台中的站点上。 此操作会删除与网站关联的所有项目，如UGC、用户组、资产和数据库记录。

## 创建的社区用户组 {#created-community-user-groups}

发布新社区站点后，新的成员组（在发布环境中创建用户组）将拥有为各种管理角色和成员角色设置的适当权限。

为成员组创建的名称包括 *site-name* 在 [步骤1](#step13asitetemplate) （在URL中显示的名称）以及唯一ID，以避免与不同社区站点根目录具有相同站点名称的社区站点和组发生冲突。

例如，如果标题为“Getting Started Tutorial”的网站的名称为“engage”，则审核者的用户组将为：

* 标题：社区参与审核者
* 名称：社区 — *engage-uid* — 审核者

请注意，在创建站点时，任何以审核者或组管理员身份分配角色的成员都将被分配给相应的组，并被分配给成员组。 发布新站点时，将在发布时创建这些组和成员分配。

有关详细信息，请参阅 [管理用户和用户组](users.md).

>[!NOTE]
>
>如果 [允许社交登录：Facebook](#user-management) 启用后，用户群组
>
>* 社区 — *&lt;site-name>*-*&lt;uid>* — 成员
>
创建后，应用的 [Facebook云服务](social-login.md#createafacebookcloudservice) 应配置为将用户添加到此组。

## 验证错误配置 {#configure-for-authentication-error}

默认情况下，当用户输入错误的凭据且无法登录时，社区站点将重定向到示例登录页面。 此登录示例将不存在于 [生产服务器](../../help/sites-administering/production-ready.md).

要正确重定向，请在配置了网站并将其推送到发布后，完成以下步骤以获取无法重定向到社区站点的身份验证：

* 在每个AEM发布实例上
* 首次登录时具有管理员权限
* 访问 [Web控制台](../../help/sites-deploying/configuring-osgi.md)
   * 例如， [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* 定位 `Adobe Granite Login Selector Authentication Handler`
* 选择 `pencil`图标以打开要编辑的配置
* 输入 **[!UICONTROL 登录页面映射]** 如下所示：

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   例如：

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* 选择 **[!UICONTROL 保存]**

![chlimage_1-468](assets/chlimage_1-468.png)

### 测试身份验证重定向 {#test-authentication-redirection}

在使用社区站点的登录页面映射配置的同一AEM发布实例上：

* 浏览社区站点主页
   * 例如， [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* 选择注销
* 选择登录
* 输入明显不正确的凭据，如用户名“x”和密码“x”
* 登录页面应显示“登录无效”错误

![chlimage_1-469](assets/chlimage_1-469.png)

## 从主站点控制台访问社区站点 {#accessing-community-sites-from-main-sites-console}

从全局导航站点控制台中，社区站点位于 `Community Sites` 文件夹。

虽然可以通过这种方式访问社区站点，但是对于管理任务，应从社区站点控制台访问社区站点。

![chlimage_1-470](assets/chlimage_1-470.png)
