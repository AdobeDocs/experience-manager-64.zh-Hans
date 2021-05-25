---
title: 创作新社区站点
seo-title: 创作新社区站点
description: 如何创作新的AEM Communities网站
seo-description: 如何创作新的AEM Communities网站
uuid: b8557416-cae4-489e-ab3b-e94d56686b7a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: bf182bb7-e305-45be-aadb-d71efd70f8cb
exl-id: 5d58f9c5-3210-48ef-94a3-805a1a57e3af
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1649'
ht-degree: 1%

---

# 创作新社区站点{#author-a-new-community-site}

## 创建新社区站点{#create-a-new-community-site}

使用创作实例创建新的社区站点

* 使用管理员权限登录
* 从全局导航：**[!UICONTROL 导航>社区>站点]**

社区站点控制台提供了一个向导，可指导用户完成创建社区站点的步骤。 在最后一步中提交站点之前，可以前进到`Next`步骤或`Back`步骤。

要开始创建新的社区站点，请执行以下操作：

* 选择`Create`按钮

![createcommunitysite](assets/createcommunitysite.png)

### 步骤1:网站模板{#step-site-template}

![createsitetemplate63](assets/createsitetemplate63.png)

在[网站模板步骤](sites-console.md#step2013asitetemplate)中，输入标题、描述、URL的名称，然后选择社区网站模板，例如：

* **[!UICONTROL 社区站点标题]**: `Getting Started Tutorial`

* **[!UICONTROL 社区站点描述]**: `A site for engaging with the community.`

* **[!UICONTROL 社区站点根目录]**:(默认根留空 `/content/sites`)

* **[!UICONTROL 云配置]**:（如果未指定云配置，则留空）提供指定云配置的路径。
* **[!UICONTROL 社区站点基本语言]**:（单语言保持不变）英语)使用下拉菜单从可用 *语* 言(德语、意大利语、法语、日语、西班牙语、葡萄牙语（巴西）、中文（繁体）和中文（简体）中选择一种或多种基本语言。将为添加的每种语言创建一个社区站点，并按照[多语言站点翻译内容](../../help/sites-administering/translation.md)中描述的最佳实践，将位于同一站点文件夹中。 每个站点的根页面将包含一个子页面，该子页面由所选语言之一的语言代码命名，如“en”表示英语，“fr”表示法语。

* **[!UICONTROL 社区站点名称]**:参与

   * 请仔细检查名称，因为创建网站后，该名称不容易更改
   * 初始URL将显示在“社区网站名称”下方
   * 对于有效的URL，请附加基本语言代码+ &quot;。html&quot;
   * *例如*, http://localhost:4502/content/sites/  `engage/en.html`

* **[!UICONTROL 模板]**:下拉选择  `Reference Site`

选择&#x200B;**[!UICONTROL Next]**

### 步骤2:设计{#step-design}

设计步骤分为两个部分，用于选择主题和品牌横幅：

#### 社区站点主题{#community-site-theme}

选择要应用于模板的所需样式。 选择后，将使用复选标记覆盖主题。

![sitetheme](assets/sitetheme.png)

#### 社区网站品牌{#community-site-branding}

（可选）上传要在网站页面中显示的横幅图像。 横幅被固定到浏览器的左边缘，在社区站点标题和菜单（导航链接）之间。 横幅高度会被裁剪为120像素。 无法调整横幅大小以适合浏览器的宽度和120像素高度。

![chlimage_1-353](assets/chlimage_1-353.png) ![chlimage_1-354](assets/chlimage_1-354.png)

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤3:设置{#step-settings}

在“设置”步骤中，在选择`Next`之前，请注意有七个部分提供了对涉及用户管理、标记、审核、群组管理、分析、翻译和启用的配置的访问权限。

请访问[AEM Communities启用入门](getting-started-enablement.md)教程，以体验如何使用启用功能。

#### 用户管理{#user-management}

选中[User Management](sites-console.md#user-management)的所有复选框

* 允许站点访客自行注册
* 允许网站访客在不登录的情况下查看网站
* 允许成员发送和接收来自其他社区成员的消息
* 允许使用Facebook登录，而不是注册和创建用户档案
* 允许使用Twitter登录，而不是注册和创建用户档案

>[!NOTE]
>
>对于生产环境，需要创建自定义Facebook和Twitter应用程序。 请参阅[使用Facebook和Twitter进行社交登录](social-login.md)。

![创建站点设置](assets/createsitesettings.png)

#### 标记 {#tagging}

可以应用于社区内容的标记可通过选择之前通过[Tagging Console](../../help/sites-administering/tags.md#tagging-console)定义的AEM命名空间（例如[Tutorial命名空间](setup.md#create-tutorial-tags)）来控制。

使用提前键入搜索，可轻松查找命名空间。 例如，

* 键入“tut”
* 选择 `Tutorial`

![chlimage_1-355](assets/chlimage_1-355.png)

#### 角色 {#roles}

[社区成](users.md) 员角色通过角色部分中的设置进行分配。

要让社区成员（或成员组）以社区经理的身份体验站点，请使用提前键入搜索并从下拉列表的选项中选择成员或组名称。

例如，

* 类型“q”
* 选择[Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[隧道](https://helpx.adobe.com/experience-manager/6-3/communities/using/deploy-communities.html#tunnel-service-on-author) 服务允许选择仅在发布环境中存在的成员和组。

![community_roles-1](assets/community_roles-1.png)

#### 审核 {#moderation}

接受[审核](sites-console.md#moderation)用户生成内容(UGC)的默认全局设置。

![chlimage_1-356](assets/chlimage_1-356.png)

#### ANALYTICS {#analytics}

如果Adobe Analytics获得许可并配置了Analytics云服务和框架，则可以启用Analytics并选择框架。

请参阅[社区功能的Analytics配置](analytics.md)。

![chlimage_1-357](assets/chlimage_1-357.png)

#### 翻译 {#translation}

[翻译设置](sites-console.md#translation)指定站点的基本语言，以及UGC是否可以被翻译以及翻译到哪种语言（如果可以）。

* 检查&#x200B;**[!UICONTROL 允许机器翻译]**
* 在默认的机器翻译服务中保留为翻译选择的默认语言
* 保留默认翻译提供程序和配置
* 由于没有语言副本，因此不需要全局存储
* 选择&#x200B;**[!UICONTROL 翻译整个页面]**
* 保留默认持久性选项

![chlimage_1-358](assets/chlimage_1-358.png)

#### 启用 {#enablement}

创建参与社区时留空。

有关快速创建[启用社区](overview.md#enablement-community)的类似教程，请参阅[AEM Communities支持入门](getting-started-enablement.md)。

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤4:创建社区站点{#step-create-communities-site}

选择&#x200B;**[!UICONTROL 创建]**。

![chlimage_1-359](assets/chlimage_1-359.png)

完成该过程后，新站点的文件夹会显示在“社区 — 站点”控制台中。

![通信站点控制台](assets/communitiessitesconsole.png)

## 发布新社区站点{#publish-the-new-community-site}

创建的站点应从社区 — 站点控制台进行管理，该控制台与可从中创建新站点的控制台相同。

选择社区站点的文件夹以将其打开后，将鼠标悬停在站点图标上，可显示四个操作图标：

![siteactionicons-1](assets/siteactionicons-1.png)

在选择第四个省略号图标（更多操作）时，将显示导出网站和删除网站选项。

![siteactionsnew-1](assets/siteactionsnew-1.png)

从左到右为：

* **打开**
网站选择铅笔图标以在创作编辑模式下打开社区网站，以添加和/或配置页面组件

* **编辑**
站点选择属性图标以打开社区站点以修改属性，如标题或更改主题

* **发布**
站点选择用于发布社区站点的世界图标（例如，如果发布服务器在本地计算机上运行，则默认情况下会运行到localhost:4503）

* **导出**
站点选择导出图标可创建社区站点的包，该包既存储在包管理器中，又 [已](../../help/sites-administering/package-manager.md) 下载。

   请注意，网站包中未包含UGC。

* **删除站点**

   选择删除图标，以从&#x200B;**[!UICONTROL 社区>站点控制台]**&#x200B;中删除社区站点。 此操作会删除与网站关联的所有项目，如UGC、用户组、资产和数据库记录。

![siteactions-1](assets/siteactions-1.png)

>[!NOTE]
>
>如果未对发布实例使用默认端口4503，请编辑默认复制代理，将端口号设置为正确的值。
>
>在创作实例上，从主菜单
>
>1. 导航到&#x200B;**[!UICONTROL 工具>操作>复制]**&#x200B;菜单
>1. 选择&#x200B;**[!UICONTROL 创作代理]**
>1. 选择&#x200B;**[!UICONTROL 默认代理（发布）]**
>1. 在&#x200B;**[!UICONTROL 设置]**&#x200B;旁边，选择&#x200B;**[!UICONTROL 编辑]**
>1. 在“代理设置”的弹出对话框中，选择“传输”选项卡
>1. 在URI中，将端口号4503更改为所需的端口号

>
>
例如，要使用端口6103:`http://localhost:6103/bin/receive?sling:authRequestLogin=1`
>
>1. 选择&#x200B;**[!UICONTROL OK]**
>1. （可选）选择`Clear`或`Force Retry`以重置复制队列


### 选择发布{#select-publish}

确保发布服务器运行后，选择世界图标以发布社区站点。

![chlimage_1-360](assets/chlimage_1-360.png)

成功发布社区网站后，会短暂显示一条消息：

![chlimage_1-361](assets/chlimage_1-361.png)

### 注意新社区用户组{#notice-new-community-user-groups}

除了新的社区站点之外，还会创建新用户组，其中为各种管理功能设置了适当的权限。 有关详细信息，请访问[社区站点的用户组](users.md#usergroupsforcommunitysites)。

对于此新社区站点，如果在步骤1中为站点名称“engage”，则可以从[组控制台](members.md)(全局导航：社区、组):

* 社区参与社区经理
* 社区参与组管理员
* 社区参与成员
* 社区参与审核者
* 社区参与特权成员
* 社区参与Sitecontentmanager

请注意，[Aaron McDonald](tutorials.md#demo-users)是

* 社区参与社区经理
* 社区参与审核者
* 社区参与成员（间接作为审核者组的成员）

![chlimage_1-362](assets/chlimage_1-362.png)

#### http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-363](assets/chlimage_1-363.png)

## 验证错误{#configure-for-authentication-error}的配置

配置并推送站点以发布后，在发布实例上配置登录映射](sites-console.md#configure-for-authentication-error)(`Adobe Granite Login Selector Authentication Handler`)。 [好处是当登录凭据输入不正确时，身份验证错误将在错误消息中重新显示社区站点的登录页面。

将`Login Page Mapping`添加为

* /content/sites/engage/en/signin:/content/sites/engage/en

## 可选步骤{#optional-steps}

### 更改默认主页{#change-the-default-home-page}

使用发布站点进行演示时，将默认主页更改为新站点可能会非常有用。

为此，需要使用[CRXDE](http://localhost:4503/crx/de) Lite在发布时编辑[资源映射](../../help/sites-deploying/resource-mapping.md)表。

要开始操作，请执行以下操作：

1. 在发布时，使用管理员权限登录
1. 浏览到[http://localhost:4503/crx/de](http://localhost:4503/crx/de)
1. 在项目浏览器中，展开`/etc/map`
1. 选择`http`节点

   * 选择&#x200B;**[!UICONTROL 创建节点]**

      * **** Namelocalhost.4503

         (do *not* use `:`)

      * **** [键入：映射](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. 选择新创建的`localhost.4503`节点

   * 添加属性

      * **** 名称：匹配
      * **** TypeString
      * **** Valuelocalhost.4503/\$

         （必须以“$”字符结尾）
   * 添加属性

      * **** 名称：internalRedirect
      * **** TypeString
      * **值** /content/sites/engage/en.html


1. 选择&#x200B;**[!UICONTROL Save All]**
1. （可选）删除浏览历史记录
1. 浏览到http://localhost:4503/

   * 访问http://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>要禁用，只需在`sling:match`属性值前面添加“x” - `xlocalhost.4503/$` — 和&#x200B;**[!UICONTROL Save All]**。

![chlimage_1-364](assets/chlimage_1-364.png)

#### 疑难解答：保存映射{#troubleshooting-error-saving-map}时出错

如果无法保存更改，请确保节点名称为`localhost.4503`（带有“dot”分隔符），而不是`localhost:4503`（带有“冒号”分隔符），因为`localhost`不是有效的命名空间前缀。

![chlimage_1-365](assets/chlimage_1-365.png)

#### 疑难解答：无法重定向{#troubleshooting-fail-to-redirect}

正则表达式`sling:match`字符串末尾的“**$**”至关重要，因此只能精确映射`http://localhost:4503/`，否则，重定向值会附加到URL中server:port之后可能存在的任何路径的前面。 因此，当AEM尝试重定向到登录页面时，重定向会失败。

### 修改站点{#modify-the-site}

最初创建网站后，作者可以使用[打开网站图标](sites-console.md#authoring-site-content)来执行标准的AEM创作活动。

此外，管理员还可以使用[编辑站点图标](sites-console.md#modifying-site-properties)来修改站点的属性，如标题。

在进行任何修改后，请记住&#x200B;**save**&#x200B;和&#x200B;**重新发布**&#x200B;站点。

>[!NOTE]
>
>如果不熟悉AEM，请查看有关[基本操作](../../help/sites-authoring/basic-handling.md)和[页面创作快速指南的文档](../../help/sites-authoring/qg-page-authoring.md)。
