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
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1643'
ht-degree: 1%

---


# 社区组控制台 {#community-groups-console}

当社区站点的[模板结构](sites-console.md#step1)包含[组函数](functions.md#groups-function)时，“组”控制台提供创建社区组的访问权限。

* 组可以嵌套在其他组中。 当新组](tools-groups.md)的[结构包含组函数时，会发生这种情况。
* 仅对于作者环境，存在与站点创建向导类似的组创建向导。
* 在向社区站点结构或社区组结构添加“组”功能时，可以配置成员是否可以通过发布环境创建组。

在包含的三个组模板中，只有`Reference Group`模板在其结构中包含组函数。

社区组的几个方面包括：

* 创建：可以在创作时或在发布时（可选）创建新组
* 控制：组可能是开放的或秘密的
* 嵌套：组可能包含零个或多个组

>[!NOTE]
>
>在[存在“社区组”控制台](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1)之前在发布环境中创建的社区组将不会列在“社区组”控制台中，因此，无法使用控制台进行修改。

>[!NOTE]
>
>此“组”控制台仅可从“社区站点”控制台访问，不要与成员[“组”控制台](members.md)混淆，以管理成员组。
>
>成员组是在发布环境中注册的用户组，使用[隧道服务](deploy-communities.md#tunnel-service-on-author)从作者环境访问。

## 组创建 {#group-creation}

要访问“组”控制台，请执行以下操作：

* 在创作时，使用管理员权限登录
* 从全局导航：**[!UICONTROL 社区>站点]**
* 选择现有社区站点文件夹以将其打开
* 在文件夹中选择社区站点的实例

   * 社区站点的结构必须包括组功能
   * 这些屏幕快照来自[在发布](published-site.md)上创建组之后的“入门”教程

![chlimage_1-135](assets/chlimage_1-133.png)

选择&#x200B;**[!UICONTROL Groups文件夹]**&#x200B;以将其打开。

打开后，将显示所有现有用户组（无论是在作者创建还是发布创建）。

通过此“组”控制台，可以创作新组。

![chlimage_1-134](assets/chlimage_1-134.png)

* 选择&#x200B;**[!UICONTROL 创建组]**&#x200B;按钮

### 第1步：社区组模板{#step-community-group-template}

![多语言组](assets/multilingualgroup.png)

* **[!UICONTROL 社区组标题]**:组的显示标题。

   标题将显示在组的已发布站点上。

* **[!UICONTROL 社区组描述]**:组的描述。
* **[!UICONTROL 社区组根]**:组的根路径。

   默认的根是父站点，但根可能被移动到网站中的任何位置。 不建议更改它。

* **[!UICONTROL 其他可用的社区组语言]** 菜单：使用下拉菜单选择可用的社区组语言。该菜单显示创建父社区站点时使用的所有语言。 用户可以在这些语言中进行选择，以便通过这一步骤在多个区域设置中创建组。 在相应社区站点的“组”控制台中，以多种指定语言创建同一组。

* **[!UICONTROL 社区组名称]**:URL中显示的组根页面的名称

   * 多次 — 检查名称，因为创建组后，该名称不易更改
   * 基本URL将显示在`Community Group Name`
   * 对于有效的URL，请附加“.html”

      *例如*,  `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL 社区组模]** 板菜单：使用下拉菜单选择可用的 [社区组模板](tools.md)。

### 第2步：设计{#step-design}

#### 社区组主题{#community-group-theme}

![社区组主题](assets/communitygrouptheme.png)

该框架使用[TwitterBootstrap](https://twitterbootstrap.org/)为站点引入响应式灵活设计。 可以选择多个预加载的Bootstrap主题之一来设置所选社区组模板的样式，或者可以上传Bootstrap主题。

选择后，主题将用不透明的蓝色复选标记覆盖。

可以选择与父站点主题不同的主题。

发布社区站点后，可以[编辑属性](#modifying-group-properties)并选择其他主题。

#### 社区组品牌{#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

社区站点品牌是每个页面顶部显示为标题的图像。 可以显示与其他网站页面不同的群组横幅。

图像的大小应与浏览器中页面的预期显示大小相同，高度应为120像素。

创建或选择图像时，请牢记：

* 图像高度将从图像的上边缘裁剪为120像素
* 图像被固定到浏览器窗口的左边缘
* 图像不会调整大小，因此当图像宽度为……

   * 小于浏览器的宽度，图像将水平重复
   * 图像的宽度大于浏览器的宽度，将显示为被裁剪

### 第3步：设置{#step-settings}

#### 审核{#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

默认情况下，父社区站点的版主列表是继承的。

可以添加特定于组的版主：

* 搜索成员(从发布环境)以将其添加为版主

#### 成员资格{#membership}

通过成员资格设置，可以选择三种保护社区组的方式之一。

![chlimage_1-137](assets/chlimage_1-137.png)

* 可选成员资格

   如果选择，则社区组为公共组。 站点成员可以加入组并发布信息，而无需明确加入组。 已选择默认值。
* 必需成员资格

   如果选择，则社区组为打开的组。 社区站点成员可以视图组的内容，但必须加入组才能发布内容。 通过选择发布环境中的`Join`按钮加入成员。 未选择默认值。

* 受限制的成员资格

   如果选中，则社区组为机密组。 必须明确邀请社区成员。 邀请的成员将输入搜索框中。 以后可以使用作者环境[成员和组控制台](members.md)添加成员。 未选择默认值。

#### 缩略图 {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

缩略图是创作和发布时要为组显示的图像。

组图像的最佳大小是170 x 90像素，采用支持的图像格式（如JPG或PNG）。

如果未添加图像，则显示默认图像。

![chlimage_1-139](assets/chlimage_1-139.png)

### 第4步：创建组{#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

如果需要进行任何调整，请使用&#x200B;**返回**&#x200B;按钮进行调整。

选择并启动&#x200B;**创建**&#x200B;后，创建组的过程便无法中断。

完成该过程后，新子社区站点（组）的卡片将显示在“社区站点组”控制台中，作者可以从中添加页面内容，或管理员可以修改站点的属性。

![createcommunitygroup-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>按照[步骤1中的指定，组将以所有语言创建：在相应社区站点的“社区组”控制台中，使用“其他可用社区组语言”中的社区组模板](groups.md#step1communitygrouptemplate)。

## 创作组内容{#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

可以使用与任何其他AEM页面相同的工具创作组的页面内容。 要打开组进行创作，请选择将鼠标悬停在组卡上时显示的“打开站点”图标。

## 修改组属性{#modifying-group-properties}

在社区组创建过程中指定的现有子社区站点的属性可以通过选择将鼠标悬停在组卡上时显示的“编辑站点”图标进行修改：

![chlimage_1-142](assets/chlimage_1-142.png)

以下属性的详细信息与[组创建](#group-creation)部分中提供的说明相符。 无论是在发布环境还是作者环境中创建，都可以修改任何嵌套组。

![chlimage_1-143](assets/chlimage_1-143.png)

### 修改基本{#modify-basic}

BASIC面板允许修改

* 社区组标题
* 社区组描述

不能修改社区组名称。

选择其他社区组模板不会影响现有社区组站点，因为模板和站点之间没有任何连接。

相反，可以修改子社区的[STRUCTURE](#modify-structure)。

### 修改结构{#modify-structure}

通过“结构”面板，可修改最初根据从作者或发布环境创建子社区站点时选择的社区组模板创建的结构。 从面板中，

* 将其他[社区函数](functions.md)拖放到站点结构中
* 在站点结构中社区功能的实例中：

   * **`gear icon`**

      编辑设置，包括显示标题和URL名称以及[特权成员组](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      从站点结构中删除（删除）函数

   * **`grid icon`**

      修改在站点的顶级导航栏中显示的功能顺序

>[!CAUTION]
>
>虽然可以在不产生副作用的情况下更改显示标题，但不建议编辑属于社区站点的社区功能的URL名称。
>
>例如，重命名URL不会移动现有UGC，因此会产生“losing”UGC的效果。

>[!CAUTION]
>
>组函数必须&#x200B;*不*&#x200B;是站点结构中的&#x200B;*或唯一*&#x200B;函数。
>
>必须首先包含并列出任何其他函数，如[页函数](functions.md#page-function)。

#### 示例：将日历函数添加到子社区（组）结构{#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### 修改设计{#modify-design}

“设计”面板允许修改主题：

* [社区组主题](#community-group-theme)
* [社区组品牌](#community-group-branding)

   * 滚动到面板底部以更改品牌图像

### 修改设置{#modify-settings}

“设置”面板允许添加社区[版主](#moderation)。

### 修改成员资格{#modify-membership}

[MEMBERSHIP](#membership)面板仅供参考。 无论是可选的、必需的还是受限的，都无法更改已建立的组成员关系类型。

### 修改缩略图{#modify-thumbnail}

通过[THUMBNAIL](#thumbnail)面板，可上传图像以将社区组表示到发布环境以及创作环境中社区站点的“组”控制台中的站点访客。

## 发布组{#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

新建或修改社区组后，可以通过选择`Publish Site`图标来发布（激活）该组。

成功发布组后，将显示一条消息：

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>父社区站点和父组应已发布。
>
>社区站点和嵌套用户组应以自上而下的方式发布。

## 删除组{#deleting-the-group}

![删除图标](assets/deleteicon.png)

通过选择删除组图标（将鼠标悬停在组上方时显示），从社区组控制台中删除组。

这将删除与组关联的所有项目，例如，将永久删除组的所有内容，并从系统中删除用户成员资格。
