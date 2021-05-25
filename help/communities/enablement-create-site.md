---
title: 创作新的社区网站以启用
seo-title: 创作新的社区网站以启用
description: 创建社区站点以启用
seo-description: 创建社区站点以启用
uuid: 6822cc99-e272-4661-bddf-aa0800b88c41
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: aff8b79f-dd4e-486e-9d59-5d09dfe34f27
exl-id: 5b16c775-3bd0-4a55-ba9e-f326224e8bae
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1744'
ht-degree: 1%

---

# 为启用{#author-a-new-community-site-for-enablement}创作新社区站点

## 创建社区站点 {#create-community-site}

[社区站](sites-console.md) 点创建采用向导，可指导您完成创建社区站点的步骤。在最后一步中提交站点之前，可以前进到`Next`步骤或`Back`步骤。

要开始创建新的社区站点，请执行以下操作：

使用[author实例](http://localhost:4502/)

* 使用管理员权限登录
* 导航到&#x200B;**[!UICONTROL Communities > Sites]**

* 选择&#x200B;**[!UICONTROL 创建]**

### 步骤1:网站模板{#step-site-template}

![enablementsitetemplate](assets/enablementsitetemplate.png)

在&#x200B;**网站模板**&#x200B;步骤中，输入标题、描述、URL的名称，然后选择社区网站模板，例如：

* **社区站点标题**: `Enablement Tutorial`

* **社区站点描述**: `A site for enabling the community to learn.`

* **社区站点根目录**:(默认根留空 `/content/sites`)

* **云配置**:（如果未指定云配置，则留空）提供指定云配置的路径。
* **社区站点基本语言**:（单语言保持不变）英语)使用下拉菜单从可用 *语* 言(德语、意大利语、法语、日语、西班牙语、葡萄牙语（巴西）、中文（繁体）和中文（简体）中选择一种或多种基本语言。将为添加的每种语言创建一个社区站点，并按照[多语言站点翻译内容](../../help/sites-administering/translation.md)中描述的最佳实践，将位于同一站点文件夹中。 每个站点的根页面将包含一个子页面，该子页面由所选语言之一的语言代码命名，如“en”表示英语，“fr”表示法语。

* **[!UICONTROL 社区站点名称]**: `enable`

   * 初始URL将显示在“社区网站名称”下方
   * 对于有效的URL，附加基本语言代码+ &quot;。html&quot;

      *例如*, http://localhost:4502/content/sites/  `enable/en.html`

* **[!UICONTROL 引用网站模板]**:下拉选择  `Reference Structured Learning Site Template`

选择&#x200B;**[!UICONTROL Next]**

### 步骤2:设计{#step-design}

设计步骤分为两个部分，用于选择主题和品牌横幅：

#### 社区站点主题{#community-site-theme}

选择要应用于模板的所需样式。 选择后，将使用复选标记覆盖主题。

![enablementsitetheme](assets/enablementsitetheme.png)

#### 社区网站品牌{#community-site-branding}

（可选）上传要在网站页面中显示的横幅图像。 横幅被固定到浏览器的左边缘，在社区站点标题和菜单（导航链接）之间。 横幅高度会被裁剪为120像素。 无法调整横幅大小以适合浏览器的宽度和120像素高度。

![chlimage_1-284](assets/chlimage_1-284.png) ![chlimage_1](assets/chlimage_1.jpeg)

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤3:设置{#step-settings}

在“设置”步骤中，在选择`Next`之前，请注意有七个部分提供了对涉及用户管理、标记、角色、审核、分析、翻译和启用的配置的访问权限。

#### 用户管理{#user-management}

建议将[启用社区](overview.md#enablement-community)设为私有。

当匿名网站访客被拒绝访问、不能自行注册，以及不能使用社交登录时，社区网站是私有的。

确保未选中[用户管理](sites-console.md#user-management)的大多数复选框：

* 不允许站点访客自行注册
* 不允许匿名网站访客查看网站
* 是否允许在社区成员之间发送消息是可选的
* 不允许使用Facebook登录
* 不允许使用Twitter登录

![chlimage_1-285](assets/chlimage_1-285.png)

#### 标记 {#tagging}

可以应用于社区内容的标记可通过选择之前通过[Tagging Console](../../help/sites-administering/tags.md#tagging-console)定义的AEM命名空间（例如[Tutorial命名空间](enablement-setup.md#create-tutorial-tags)）来控制。

此外，为社区站点选择标记命名空间会限制在定义目录和启用资源时显示的选择。 请参阅[标记支持资源](tag-resources.md) ，以了解重要信息。

使用提前键入搜索，可轻松查找命名空间。 例如，

* 键入“tut”
* 选择 `Tutorial`

![chlimage_1-286](assets/chlimage_1-286.png)

### 角色 {#roles}

[社区成](users.md) 员角色通过角色部分中的设置进行分配。

要让社区成员（或成员组）以社区经理的身份体验站点，请使用提前键入搜索并从下拉列表的选项中选择成员或组名称。

例如，

* 类型“q”
* 选择[Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[隧道](deploy-communities.md#tunnel-service-on-author) 服务允许选择仅在发布环境中存在的成员和组。

![community_roles](assets/community_roles.png)

#### 审核 {#moderation}

接受[审核](sites-console.md#moderation)用户生成内容(UGC)的默认全局设置。

![chlimage_1-287](assets/chlimage_1-287.png)

#### ANALYTICS {#analytics}

从下拉菜单中，选择为此社区站点配置的Analytics云服务框架。

屏幕截图中显示的选择`Communities`是[配置文档中的框架示例。](analytics.md#aem-analytics-framework-configuration)

![chlimage_1-288](assets/chlimage_1-288.png)

#### 翻译 {#translation}

[翻译设置](sites-console.md#translation)指定UGC是否可以被翻译以及翻译到哪种语言（如果可以）。

* 检查&#x200B;**[!UICONTROL 允许机器翻译]**
* 使用默认设置

![chlimage_1-289](assets/chlimage_1-289.png)

#### 启用 {#enablement}

对于支持社区，需要确定一个或多个社区支持管理器。

* **[!UICONTROL 启用管理器]**
（必需） 
`Community Enablement Managers` 可选择群组以管理此社区站点。

   * 类型“s”
   * 选择 `Sirius Nilson`

* **[!UICONTROL Marketing Cloud组织ID]**
（可选）Adobe Analytics帐户的ID，在启用报表中包含视频心率分 [析](analytics.md#video-heartbeat-analytics) 时，需要此ID。

![chlimage_1-290](assets/chlimage_1-290.png)

选择&#x200B;**[!UICONTROL 下一步]**。

### 步骤4:创建社区站点{#step-create-community-site}

选择&#x200B;**[!UICONTROL 创建]**。

![chlimage_1-291](assets/chlimage_1-291.png)

完成该过程后，新站点的文件夹会显示在“社区 — 站点”控制台中。

![enablementsitecreated](assets/enablementsitecreated.png)

### 发布新社区站点{#publish-the-new-community-site}

创建的站点应从社区 — 站点控制台进行管理，该控制台与可从中创建新站点的控制台相同。

选择社区站点的文件夹后，将鼠标悬停在站点图标上，可显示四个操作图标：

![站点操作图标](assets/siteactionicons.png)

在选择省略号图标（更多操作图标）时，将显示导出网站和删除网站选项。

![站点操作新](assets/siteactionsnew.png)

从左到右为：

* **打开**
网站选择铅笔图标以在创作编辑模式下打开社区网站，以添加和/或配置页面组件

* **编辑**
站点选择属性图标以打开社区站点以修改属性，如标题或更改主题

* **发**
布站点选择世界图标以发布社区站点（默认情况下为localhost:4503）

* **导出**
站点选择导出图标可创建社区站点的包，该包既存储在包管理器中，又 [已](../../help/sites-administering/package-manager.md) 下载。

   请注意，网站包中未包含UGC。

* **删**
除站点要删除社区站点，请在社区站点控制台中选择将鼠标悬停在站点上时显示的删除站点图标。此操作会删除与网站关联的所有项目，如UGC、用户组、资产和数据库记录。

![启用站点操作](assets/enablesiteactions.png)

#### 选择发布{#select-publish}

选择用于发布社区站点的世界图标。

![chlimage_1-292](assets/chlimage_1-292.png)

将显示网站已发布的迹象。

![chlimage_1-293](assets/chlimage_1-293.png)

## 社区用户和用户组{#community-users-user-groups}

### 注意新社区用户组{#notice-new-community-user-groups}

除了新的社区站点之外，还会创建新用户组，其中为各种管理功能设置了适当的权限。 有关详细信息，请访问[社区站点的用户组](users.md#usergroupsforcommunitysites)。

对于此新社区站点，如果在步骤1中为站点名称“enable”，则可以从[社区成员和组控制台](members.md#groups-console)中查看发布环境中存在的新用户组：

![chlimage_1-294](assets/chlimage_1-294.png)

### 为社区分配成员启用成员组{#assign-members-to-community-enable-members-group}

在创作时，启用隧道服务后，可以将在初始设置期间创建的[用户分配给新创建的社区站点的社区成员组。](enablement-setup.md#publishcreateenablementmembers)

使用社区组控制台，可以单独添加成员，也可以通过组中的成员资格添加成员。

在本例中，组`Community Ski Class`被添加为组`Community Enable Members`的成员以及成员`Quinn Harper`。

* 导航到&#x200B;**[!UICONTROL Communities > Groups]**&#x200B;控制台
* 选择&#x200B;**[!UICONTROL 社区启用成员]**&#x200B;组
* 在&#x200B;**[!UICONTROL Add Members To Group]**&#x200B;搜索框中输入`ski`
* 选择&#x200B;**[!UICONTROL 社区滑雪课]**（学习者组）
* 在搜索框中输入`quinn`
* 选择&#x200B;**[!UICONTROL Quinn Harper]**（启用资源联系人）

* 选择&#x200B;**[!UICONTROL Save]**

![chlimage_1-295](assets/chlimage_1-295.png)

## 发布{#configurations-on-publish}时的配置

### http://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}

![chlimage_1-296](assets/chlimage_1-296.png)

### 验证错误{#configure-for-authentication-error}的配置

配置并推送站点以发布后，在发布实例上配置登录映射](sites-console.md#configure-for-authentication-error)(`Adobe Granite Login Selector Authentication Handler`)。 [好处是当登录凭据输入不正确时，身份验证错误将在错误消息中重新显示社区站点的登录页面。

将`Login Page Mapping`添加为

* /content/sites/enable/en/signin:/content/sites/enable/en

### （可选）更改默认主页{#optional-change-the-default-home-page}

使用发布站点进行演示时，将默认主页更改为新站点可能会非常有用。

为此，需要使用[CRX|DE](http://localhost:4503/crx/de) Lite在发布时编辑[资源映射](../../help/sites-deploying/resource-mapping.md)表。

开始使用

1. 在发布时，访问CRXDE并使用管理员权限登录

   * 例如，浏览到[http://localhost:4503/crx/de](http://localhost:4503/crx/de)，然后使用`admin/admin`登录

1. 在项目浏览器中，展开`/etc/map`
1. 选择`http`节点

   * 选择&#x200B;**[!UICONTROL 创建节点]**

      * **** Namelocalhost.4503

         （*不*&#x200B;使用`:`）

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
      * **值** /content/sites/enable/en.html


1. 选择&#x200B;**[!UICONTROL Save All]**
1. （可选）删除浏览历史记录
1. 浏览到http://localhost:4503/

   * 访问http://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>要禁用，只需在`sling:match`属性值前面添加“x” - `xlocalhost.4503/$` — 和&#x200B;**[!UICONTROL Save All]**。

![chlimage_1-297](assets/chlimage_1-297.png)

#### 疑难解答：保存映射{#troubleshooting-error-saving-map}时出错

如果无法保存更改，请确保节点名称为`localhost.4503`（带有“dot”分隔符），而不是`localhost:4503`（带有“冒号”分隔符），因为`localhost`不是有效的命名空间前缀。

![chlimage_1-298](assets/chlimage_1-298.png)

#### 疑难解答：无法重定向{#troubleshooting-fail-to-redirect}

正则表达式`sling:match`字符串末尾的“**$**”至关重要，因此只能精确映射`http://localhost:4503/`，否则，重定向值会附加到URL中server:port之后可能存在的任何路径的前面。 因此，当AEM尝试重定向到登录页面时，重定向会失败。

## 修改社区站点{#modifying-the-community-site}

最初创建网站后，作者可以使用[打开网站图标](sites-console.md#authoring-site-content)来执行标准的AEM创作活动。

此外，管理员还可以使用[编辑站点图标](sites-console.md#modifying-site-properties)来修改站点的属性，如标题。

在进行任何修改后，请记住&#x200B;**Save**&#x200B;并重新&#x200B;**Publish**&#x200B;站点。

>[!NOTE]
>
>如果不熟悉AEM，请查看有关[基本操作](../../help/sites-authoring/basic-handling.md)和[页面创作快速指南的文档](../../help/sites-authoring/qg-page-authoring.md)。

### 添加目录{#add-a-catalog}

为此社区站点选择的社区站点模板应包含目录功能。

如果没有，则可以轻松添加目录函数。 这将允许未分配到支持资源或学习路径的社区其他成员从目录中选择支持资源。

如果站点结构已包含目录功能，则可以更改其标题。

要修改站点的结构，请导航到&#x200B;**[!UICONTROL Communities、Sites]**&#x200B;控制台，打开`enable`文件夹，然后选择&#x200B;**编辑站点**&#x200B;图标以访问`Enablement Tutorial`的属性。

选择“结构”面板可添加目录或修改现有目录：

* **标题**: `Ski Catalog`

* **URL**: `catalog`

* **选择所有命名空间**:保留为默认。
* 选择&#x200B;**[!UICONTROL Save]**

![chlimage_1-299](assets/chlimage_1-299.png)

使用“位置”图标将“目录”函数移动到“分配”后的第二个位置。

![chlimage_1-300](assets/chlimage_1-300.png)

选择右上角的&#x200B;**[!UICONTROL Save]**&#x200B;以将更改保存到社区站点。

然后，重新 — **发布**&#x200B;站点。
