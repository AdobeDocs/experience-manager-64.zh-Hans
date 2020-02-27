---
title: 社区组控制台
seo-title: 社区组控制台
description: “组”控制台允许您创建社区组
seo-description: “组”控制台允许您创建社区组
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2

---


# 社区组控制台 {#community-groups-console}

当社区站点的模板结构包括组功能时，“组”控制台 [提供了创建社](sites-console.md#step1) 区 [组的权限](functions.md#groups-function)。

* 组可以嵌套在其他组中。 当新组的结 [构包含组函数时](tools-groups.md) ，会发生这种情况。
* 仅对于创作环境，存在一个与站点创建向导类似的组创建向导。
* 在向社区站点结构或社区组结构添加“组”功能时，成员是否可以从发布环境创建组是可配置的。

在包含的三个用户组模板中，只有该模 `Reference Group` 板在其结构中包含用户组功能。

社区组的几个方面包括：

* 创建：可以在创作时或在发布时（可选）创建新组
* 控制：组可能是开放的或秘密的
* 嵌套：组可能包含零个或多个组

>[!NOTE]
>
>在“社区组”控制台存在之前在发布环境中创建的 [社区组](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1)，将不会在“社区组”控制台中列出，因此，无法使用控制台进行修改。

>[!NOTE]
>
>此“组”控制台仅可从“社区站点”控制台访问，不要与用于管理成员组的“成 [员组”控制台相混淆](members.md) 。
>
>成员组是在发布环境中注册的用户组，使用隧道服务从创作环境 [访问](deploy-communities.md#tunnel-service-on-author)。

## 组创建 {#group-creation}

要访问“组”控制台，请执行以下操作：

* 在创作时，使用管理员权限登录
* 从全局导航：“社 **[!UICONTROL 区”>“站点”]**
* 选择现有社区站点文件夹以将其打开
* 在文件夹中选择社区站点的实例

   * 社区站点的结构必须包括组功能
   * 这些屏幕快照来自发布时创建组 [后的入门教程](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

选择“ **[!UICONTROL 组”文件夹]** ，以将其打开。

打开后，将显示所有现有用户组（无论是在创作时创建还是发布时创建）。

通过此“组”控制台，可以创作新组。

![chlimage_1-134](assets/chlimage_1-134.png)

* 选择“ **[!UICONTROL 创建组]** ”按钮

### 第1步：社区组模板 {#step-community-group-template}

![多语言组](assets/multilingualgroup.png)

* **[!UICONTROL 社区组标题]**:组的显示标题。

   标题显示在组的已发布站点上。

* **[!UICONTROL 社区组描述]**:用户组的说明。
* **[!UICONTROL 社区组根]**:组的根路径。

   默认的根是父站点，但根可能被移到网站中的任意位置。 建议不要更改它。

* **[!UICONTROL 其他可用的“社区组语言”菜单]** :使用下拉菜单选择可用的社区组语言。 该菜单显示创建父社区站点时所用的所有语言。 用户可以在这些语言中进行选择，以在此单步中创建多个区域设置的用户组。 在相应社区站点的“组”控制台中，以多种指定语言创建同一组。

* **[!UICONTROL 社区组名称]**:URL中显示的组根页面的名称

   * 请仔细检查名称，因为创建组后该名称不易更改
   * 基本URL将显示在 `Community Group Name`
   * 对于有效的URL，请附加“.html”

      *例如*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL “社区组模板]** ”菜单：使用下拉菜单选择可用的社 [区组模板](tools.md)。

### 第2步：设计 {#step-design}

#### COMMUNITY GROUP THEME {#community-group-theme}

![社区组主题](assets/communitygrouptheme.png)

该框架使 [用Twitter Bootstrap](https://twitterbootstrap.org/) ，为网站提供响应迅速、灵活的设计。 可以选择多个预加载的Bootstrap主题之一来设置所选社区组模板的样式，或者可以上传Bootstrap主题。

选择后，主题将用不透明的蓝色复选标记覆盖。

可以选择与父站点的主题不同的主题。

发布社区站点后，可以编辑属性 [并选择其](#modifying-group-properties) 他主题。

#### COMMUNITY GROUP BRANDING {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

社区站点品牌是显示为每个页面顶部标题的图像。 可以显示与其他站点页面不同的组的横幅。

图像的大小应与浏览器中页面的预期显示大小相同，高度应为120像素。

创建或选择图像时，请牢记：

* 图像高度将从图像的上边缘裁切为120像素
* 图像被固定到浏览器窗口的左边缘
* 图像不会调整大小，因此当图像宽度为……

   * 小于浏览器的宽度，图像将水平重复
   * 大于浏览器的宽度后，图像将看起来会被裁掉

### 第3步：设置 {#step-settings}

#### MODERATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

默认情况下，将继承父社区站点的审核者列表。

可以添加特定于用户组的审核者：

* 搜索成员（从发布环境中）以将其添加为版主

#### MEMBERSHIP {#membership}

通过会员资格设置，可以选择三种方式之一来保护社区组。

![chlimage_1-137](assets/chlimage_1-137.png)

* 可选成员资格

   如果选择此选项，则社区组为公共组。 站点成员可以加入组并发布内容，而无需明确加入组。 默认为选中状态。
* 必需成员资格

   如果选择此选项，则社区组为打开的组。 社区站点成员可以查看组的内容，但必须加入组才能发布内容。 通过在发布环境中选 `Join` 择按钮，成员加入。 未选择默认值。

* 受限制的成员资格

   如果选择此选项，则社区组为机密组。 必须明确邀请社区成员。 已邀请的成员将在搜索框中输入。 以后可以使用创作环境的“成 [员”和“组”控制台](members.md) ，添加成员。 未选择默认值。

#### 缩略图 {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

缩略图是创作和发布时要为组显示的图像。

组图像的最佳大小是支持的图像格式（如JPG或PNG）的170 x 90像素。

如果未添加图像，则显示默认图像。

![chlimage_1-139](assets/chlimage_1-139.png)

### 第4步：创建组 {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

如果需要进行任何调整，请使 **用** “返回”按钮进行调整。

选 **择并启动** “创建”后，创建组的过程将无法中断。

完成该过程后，新的子社区站点（组）的卡片将显示在“社区站点组”控制台中，作者可以从中添加页面内容，或管理员可以修改站点的属性。

![createcommunitygroup-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>按照第1步中的指定，用户组将以所有语言 [创建：社区组模板](groups.md#step1communitygrouptemplate) ，位于各个社区站点的“社区组”控制台中，使用其他可用的社区组语言。

## 创作组内容 {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

可以使用与任何其他AEM页面相同的工具创作组的页面内容。 要打开创作组，请选择将鼠标悬停在组卡上时显示的“打开站点”图标。

## 修改组属性 {#modifying-group-properties}

在社区组创建过程中指定的现有子社区站点的属性可以通过选择将鼠标悬停在组卡上时显示的编辑站点图标进行修改：

![chlimage_1-142](assets/chlimage_1-142.png)

以下属性的详细信息与“组创建”部分中提供 [的说明相符](#group-creation) 。 无论是在发布环境还是创作环境中创建的，都可以修改任何嵌套组。

![chlimage_1-143](assets/chlimage_1-143.png)

### 修改基本 {#modify-basic}

BASIC面板允许修改

* 社区组标题
* 社区组描述

不能修改社区组名称。

选择其他社区组模板不会影响现有的社区组站点，因为模板和站点之间没有连接。

相反，可 [以修改](#modify-structure) 子社区的STRUCTURE。

### 修改结构 {#modify-structure}

通过“结构”面板，可以修改最初从创作或发布环境创建子社区站点时选定的社区组模板创建的结构。 从面板中，

* 将其他社区功能拖 [放到站点结](functions.md) 构中
* 在站点结构中社区功能的实例上：

   * **`gear icon`**

      编辑设置，包括显示标题、URL名称以及特权成 [员组](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      从站点结构中删除（删除）功能

   * **`grid icon`**

      修改站点顶级导航栏中显示的功能顺序

>[!CAUTION]
>
>虽然显示标题可以在不产生副作用的情况下进行更改，但不建议编辑属于社区站点的社区功能的URL名称。
>
>例如，重命名URL不会移动现有UGC，因此具有“丢失”UGC的效果。

>[!CAUTION]
>
>组函数不能 *是**站点结构中的第一个* ，也不能是唯一的函数。
>
>必须首先包含并列出任何其 [他函数](functions.md#page-function)，如页面函数。

#### 示例：向子社区（组）结构添加日历功能 {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### 修改设计 {#modify-design}

“设计”面板允许修改主题：

* [社区组主题](#community-group-theme)
* [社区组品牌](#community-group-branding)

   * 滚动到面板底部以更改品牌图像

### 修改设置 {#modify-settings}

通过“设置”面板，可以添加社区版主 [者](#moderation)。

### 修改会员资格 {#modify-membership}

MEMBERSHIP [面板](#membership) (MEMBERSHIP panel)仅供参考。 无论是可选的、必需的还是受限的，都无法更改已建立的组成员关系类型。

### 修改缩略图 {#modify-thumbnail}

通过 [THUMBNAIL](#thumbnail) 面板，可以上传图像，以将社区组表示给发布环境中以及创作环境中社区站点的“组”控制台中的站点访客。

## 发布组 {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

在新创建或修改社区组后，可以通过选择图标发布（激活）该 `Publish Site` 组。

成功发布组后，将显示一条消息：

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>父社区站点和父组应已发布。
>
>社区站点和嵌套组应以自上而下的方式发布。

## 删除组 {#deleting-the-group}

![删除图标](assets/deleteicon.png)

通过选择“删除组”图标，从社区组控制台中删除组，该图标将鼠标悬停在组上时显示。

这将删除与组关联的所有项目，例如，将永久删除组的所有内容，并从系统中删除用户成员关系。
