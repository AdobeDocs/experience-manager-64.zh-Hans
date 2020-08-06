---
title: 为Enablement创作新社区站点
seo-title: 为Enablement创作新社区站点
description: 创建社区站点以进行启用
seo-description: 创建社区站点以进行启用
uuid: 6822cc99-e272-4661-bddf-aa0800b88c41
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: aff8b79f-dd4e-486e-9d59-5d09dfe34f27
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '1744'
ht-degree: 1%

---


# 为Enablement创作新社区站点 {#author-a-new-community-site-for-enablement}

## 创建社区站点 {#create-community-site}

[“社区站点](sites-console.md) ”创建采用向导，向导将指导您完成创建社区站点的各个步骤。 在最后一步中提交站 `Next`点 `Back`之前，可以前进到步骤或上一步。

要开始创建新社区站点，请执行以下操作：

使用作 [者实例](http://localhost:4502/)

* 以管理员权限登录
* 导航到“ **[!UICONTROL 社区”>“站点”]**

* Select **[!UICONTROL Create]**

### 第1步： 站点模板 {#step-site-template}

![enablesitetemplate](assets/enablementsitetemplate.png)

在“站 **点模板** ”步骤中，输入标题、说明和URL的名称，然后选择社区站点模板，例如：

* **社区站点标题**: `Enablement Tutorial`

* **社区站点描述**: `A site for enabling the community to learn.`

* **社区站点根目录**: (默认根留空 `/content/sites`)

* **云配置**: （如果未指定云配置，则留空）提供指定云配置的路径。
* **社区站点基础语言**: (对于单种语言，请保持不变： 英语)使用下拉菜单从可用 *语言* (德语、意大利语、法语、日语、西班牙语、葡萄牙语（巴西）、繁体中文和简体中文)中选择一种或多种基本语言。 将根据多语言站点的翻译内容中介绍的最佳实践，为添加的每种语言创建一个社区站点，并且该站点将 [存在于同一站点文件夹中](../../help/sites-administering/translation.md)。 每个站点的根页面将包含一个由所选语言之一的语言代码命名的子页面，如英语为“en”或法语为“fr”。

* **[!UICONTROL 社区站点名称]**: `enable`

   * 初始URL将显示在社区站点名称下方
   * 对于有效的URL，请附加基本语言代码+ &quot;。html&quot;

      *例如*,http://localhost:4502/content/sites/ `enable/en.html`

* **[!UICONTROL 引用站点模板]**: 下拉选择 `Reference Structured Learning Site Template`

Select **[!UICONTROL Next]**

### 第2步： 设计 {#step-design}

设计步骤分为两个部分，用于选择主题和品牌横幅：

#### COMMUNITY SITE THEME {#community-site-theme}

选择要应用于模板的所需样式。 选中后，主题将用复选标记覆盖。

![启用站点主题](assets/enablementsitetheme.png)

#### COMMUNITY SITE BRANDING {#community-site-branding}

（可选）上传要在网站页面上显示的横幅图像。 横幅被固定到浏览器的左边缘，位于社区站点标题和菜单（导航链接）之间。 横幅高度会被裁剪为120像素。 横幅的大小不会调整为适合浏览器的宽度和120像素高。

![chlimage_1-284](assets/chlimage_1-284.png) ![chlimage_1](assets/chlimage_1.jpeg)

选择&#x200B;**[!UICONTROL 下一步]**。

### 第3步： 设置 {#step-settings}

在设置步骤中，在选择之 `Next`前，请注意有七个部分提供了对涉及用户管理、标记、角色、协调、分析、翻译和启用的配置的访问权限。

#### USER MANAGEMENT {#user-management}

建议将教育 [社区](overview.md#enablement-community) 设为私有。

当拒绝匿名站点访客访问、不能自行注册或不能使用社交登录时，社区站点是私有的。

确保在用户管理中未选中大 [多数复选框](sites-console.md#user-management):

* 不允许站点访客自行注册
* 不允许匿名网站访客视图网站
* 是否允许社区成员之间进行消息传递的可选
* 不允许使用Facebook登录
* 不允许使用Twitter登录

![chlimage_1-285](assets/chlimage_1-285.png)

#### TAGGING {#tagging}

可应用于社区内容的标记通过选择先前通过标记控制台定义的AEM命名空间( [如教程命名空间](../../help/sites-administering/tags.md#tagging-console) )来 [进行控制](enablement-setup.md#create-tutorial-tags)。

此外，为社区站点选择标记命名空间会限制在定义目录和启用资源时显示的选择。 有关重 [要信息，请参阅](tag-resources.md) “标记启用资源”。

使用预先键入搜索可轻松查找命名空间。 例如，

* 键入“tut”
* 选择 `Tutorial`

![chlimage_1-286](assets/chlimage_1-286.png)

### ROLES {#roles}

[社区成员角色](users.md) ，通过“角色”部分中的设置进行分配。

要让社区成员（或成员组）以社区管理者身份体验站点，请使用“预先键入”搜索并从下拉列表的选项中选择成员或组名称。

例如，

* 键入“q”
* 选择 [奎恩·哈珀](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[隧道服务](deploy-communities.md#tunnel-service-on-author) 允许选择仅在发布环境中存在的成员和组。

![community_roles](assets/community_roles.png)

#### MODERATION {#moderation}

接受审核用户生成的 [内容](sites-console.md#moderation) (UGC)的默认全局设置。

![chlimage_1-287](assets/chlimage_1-287.png)

#### ANALYTICS {#analytics}

从下拉菜单中，选择为此社区站点配置的Analytics云服务框架。

屏幕截图中显示的选 `Communities`择是配置文档中的框架 [示例。](analytics.md#aem-analytics-framework-configuration)

![chlimage_1-288](assets/chlimage_1-288.png)

#### TRANSLATION {#translation}

“ [翻译](sites-console.md#translation) ”设置指定UGC是否可以翻译，如果可以，则可以翻译到哪种语言。

* 检查允 **[!UICONTROL 许机器翻译]**
* 使用默认设置

![chlimage_1-289](assets/chlimage_1-289.png)

#### ENABLEMENT {#enablement}

对于支持社区，必须确定一个或多个社区支持管理者。

* **[!UICONTROL Enablement Managers]**（必需） 
`Community Enablement Managers` 可选择组来管理此社区站点。

   * 类型“s”
   * 选择 `Sirius Nilson`

* **[!UICONTROL Marketing Cloud组织]** Id（可选）在启用报告中包含视频心跳分析时，必 [需的Adobe Analytics帐户](analytics.md#video-heartbeat-analytics) ID。

![chlimage_1-290](assets/chlimage_1-290.png)

选择&#x200B;**[!UICONTROL 下一步]**。

### 第4步： 创建社区站点 {#step-create-community-site}

选择&#x200B;**[!UICONTROL 创建]**。

![chlimage_1-291](assets/chlimage_1-291.png)

完成该过程后，新站点的文件夹会显示在“社区——站点”控制台中。

![enablesitecreated](assets/enablementsitecreated.png)

### 发布新社区站点 {#publish-the-new-community-site}

创建的站点应从社区——站点控制台进行管理，该控制台与创建新站点的控制台相同。

选择社区站点的文件夹后，将指针悬停在站点图标上，以显示四个操作图标：

![站点操作图标](assets/siteactionicons.png)

选择省略号图标（更多操作图标）时，将显示“导出站点”和“删除站点”选项。

![站点操作新](assets/siteactionsnew.png)

从左至右为：

* **打开站点**&#x200B;选择铅笔图标以在作者编辑模式下打开社区站点，以添加和／或配置页面组件

* **编辑站**&#x200B;点选择属性图标以打开社区站点以修改属性，如标题或更改主题

* **发布站**&#x200B;点选择“全球”图标以发布社区站点（默认为localhost:4503）

* **导出站**&#x200B;点选择导出图标以创建同时存储在包管理器中和已下载的 [社区站点](../../help/sites-administering/package-manager.md) 的包。

   请注意，UGC未包含在站点包中。

* **删除站**&#x200B;点要删除社区站点，请选择将鼠标悬停在“社区站点”控制台中站点上时显示的“删除站点”图标。 此操作将删除与站点关联的所有项目，如UGC、用户组、资产和数据库记录。

![启用站点操作](assets/enablesiteactions.png)

#### Select Publish {#select-publish}

选择“全球”图标以发布社区站点。

![chlimage_1-292](assets/chlimage_1-292.png)

将显示该网站已发布。

![chlimage_1-293](assets/chlimage_1-293.png)

## 社区用户和用户组 {#community-users-user-groups}

### 注意新社区用户组 {#notice-new-community-user-groups}

与新社区站点一起，还会创建新用户组，这些用户组具有为各种管理功能设置的适当权限。 有关详细信息，请 [访问社区站点的用户组](users.md#usergroupsforcommunitysites)。

对于此新社区站点，如果在步骤1中为站点名称“enable”，则可以从“社区成员和组”控制台中查看发布环境中存 [在的新用户组](members.md#groups-console):

![chlimage_1-294](assets/chlimage_1-294.png)

### 将成员分配到社区启用成员组 {#assign-members-to-community-enable-members-group}

在创作时，启用隧道服务后，可以将初始设置期间 [创建的用户分配给新创建的社](enablement-setup.md#publishcreateenablementmembers) 区站点的“社区成员”组。

使用“社区组”控制台，可以单独添加成员，也可以通过组中的成员关系添加成员。

在此示例中， `Community Ski Class` 将组添加为组的成员 `Community Enable Members` 和成员 `Quinn Harper`。

* 导航到“社 **[!UICONTROL 区”>“组”控制台]** 。
* 选择 **[!UICONTROL 社区启用成员]** 组
* 在“ `ski` 将成员 **[!UICONTROL 添加到组”搜索框]** 中输入
* 选 **[!UICONTROL 择社区滑雪课]** （学员组）
* 进入 `quinn` 搜索框
* 选择 **[!UICONTROL Quinn Harper]** （启用资源联系人）

* Select **[!UICONTROL Save]**

![chlimage_1-295](assets/chlimage_1-295.png)

## 发布时的配置 {#configurations-on-publish}

### http://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}

![chlimage_1-296](assets/chlimage_1-296.png)

### 配置身份验证错误 {#configure-for-authentication-error}

在将站点配置并推送到发布后， [在发布实例](sites-console.md#configure-for-authentication-error)`Adobe Granite Login Selector Authentication Handler`上配置登录映射()。 优点是，当登录信用输入不正确时，身份验证错误将重新显示社区站点的登录页面并显示错误消息。

添加作 `Login Page Mapping` 为

* /content/sites/enable/cn/signin:/content/sites/enable/cn

### （可选）更改默认主页 {#optional-change-the-default-home-page}

当为演示目的使用发布站点时，将默认主页更改为新站点可能会很有用。

为此，需要在发 [布时使用CRX](http://localhost:4503/crx/de) |DE Lite [编辑资](../../help/sites-deploying/resource-mapping.md) 源映射表。

开始

1. 在发布时，访问CRXDE并使用管理员权限登录

   * 例如，浏览至http://localhost:4503/crx/de [并](http://localhost:4503/crx/de) 登录到 `admin/admin`

1. 在项目浏览器中，展开 `/etc/map`
1. 选择节 `http` 点

   * 选择 **[!UICONTROL 创建节点]**

      * **名称** localhost.4503

         (不 *使用*`:`)

      * **Type** [sling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. 选择新创建 `localhost.4503` 的节点

   * 添加属性

      * **姓名** sling:match
      * **类型字符** 串
      * **值** localhost.4503/\$

         （必须以“$”字符结尾）
   * 添加属性

      * **名称** sling:internalRedirect
      * **类型字符** 串
      * **值** /content/sites/enable/en.html


1. 选择 **[!UICONTROL 全部保存]**
1. （可选）删除浏览历史记录
1. 浏览到http://localhost:4503/

   * 请访问http://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>要禁用，只需在属性 `sling:match` 值前面添加“x” - —— 和 `xlocalhost.4503/$` “全 **[!UICONTROL 部保存”]**。

![chlimage_1-297](assets/chlimage_1-297.png)

#### 疑难解答： 保存映射时出错 {#troubleshooting-error-saving-map}

如果无法保存更改，请确保节点名称为 `localhost.4503`“点”分隔符，而不 `localhost:4503` 是“冒号”分隔符，因 `localhost`为它不是有效的命名空间前缀。

![chlimage_1-298](assets/chlimage_1-298.png)

#### 疑难解答： 无法重定向 {#troubleshooting-fail-to-redirect}

常规表达式&#x200B;**字符串**`sling:match``http://localhost:4503/` 末尾的“$”很重要，因此只能完全映射，否则重定向值会优先于URL中的server:port之后可能存在的任何路径。 因此，当AEM尝试重定向到登录页面时，将失败。

## 修改社区站点 {#modifying-the-community-site}

最初创建站点后，作者可以使用“打开 [站点”图标](sites-console.md#authoring-site-content) ，执行标准AEM创作活动。

此外，管理员可以使 [用“编辑站点](sites-console.md#modifying-site-properties) ”图标来修改站点的属性，如标题。

进行任何修改后，请记 **住保** 存并重&#x200B;**新发** 布站点。

>[!NOTE]
>
>如果不熟悉AEM，请视图有关基本 [操作的文档](../../help/sites-authoring/basic-handling.md) ，并 [阅读页面创作快速指南](../../help/sites-authoring/qg-page-authoring.md)。

### 添加目录 {#add-a-catalog}

为此社区站点选择的社区站点模板应包含目录功能。

否则，可轻松添加目录功能。 这将允许未分配给启用资源或学习路径的社区的其他成员从目录中选择启用资源。

如果站点结构已包含目录功能，则其标题可以更改。

要修改站点的结构，请导航到社 **[!UICONTROL 区、站点]** 控制台，打开文 `enable` 件夹，然后选择编 **辑站点图标以访问其属性**`Enablement Tutorial`。

选择“结构”面板以添加目录或修改现有目录：

* **标题**: `Ski Catalog`

* **URL**: `catalog`

* **选择所有命名空间**: 保留为默认值。
* Select **[!UICONTROL Save]**

![chlimage_1-299](assets/chlimage_1-299.png)

使用“职位”图标将“目录”功能移动到“工作总揽”之后的第二个职位。

![chlimage_1-300](assets/chlimage_1-300.png)

选 **[!UICONTROL 择右]** 上角的“保存”，将更改保存到社区站点。

然后重新&#x200B;**发布** 该站点。