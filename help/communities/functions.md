---
title: 社区功能
seo-title: Community Functions
description: 了解如何访问社区功能控制台
seo-description: Learn how to access the Community Functions console
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 2%

---

# 社区功能 {#community-functions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

社区体验预期的功能类型已广为人知。 社区功能可作为社区功能提供。 本质上说，它们是预先布线的一个或多个页面，用于实施社区功能，该功能不仅需要在创作模式下向页面添加组件，还需要其他功能。 它们是用于定义 [社区站点模板](sites.md) 社区站点所在的位置 [已创建](sites-console.md).

创建社区站点后，可以使用标准 [AEM创作模式](../../help/sites-authoring/editing-content.md).

许多社区功能可立即使用，如社区功能控制台中所示。 未来版本中将提供更多社区功能，并可能创建自定义功能。

>[!NOTE]
>
>用于创建 [社区站点](sites-console.md), [社区网站模板](sites.md), [社区组模板](tools-groups.md) 和 [社区功能](functions.md) 只能在创作环境中使用。

## 社区功能控制台 {#community-functions-console}

在创作环境中，访问社区功能控制台

* 从全局导航： **[!UICONTROL 工具>社区>社区功能]**

![chlimage_1-379](assets/chlimage_1-379.png)

## 预建函数 {#pre-built-functions}

以下是随AEM Communities一起提供的功能的简要描述。 每个函数都由一个或多个AEM页面组成，这些页面包含连接在一起的功能中的“社区”组件，该功能可轻松整合到 [社区站点模板](sites.md).

社区站点模板为社区站点提供了结构，包括登录、用户配置文件、通知、消息、站点菜单、搜索、主题和品牌功能。

### 标题和URL设置 {#title-and-url-settings}

**标题** 和 **URL** 是所有社区功能的通用属性。

将社区功能添加到社区站点模板或在 [修改](sites-console.md#modifying-site-properties) 社区站点的结构中，将打开函数对话框，以便可以配置标题和URL。

#### 配置功能详细信息 {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL 标题]**
(
*必需*)网站功能菜单中显示的文本

* **[!UICONTROL URL]**
(*必需*)用于生成URI的名称。 名称必须符合 [命名约定](../../help/sites-developing/naming-conventions.md) 由AEM和JCR强加。

例如，使用通过以下内容创建的网站： [快速入门](getting-started.md) 教程，如果

* 标题=网页
* URL = page

然后，指向该页面的URL是http://local_host:4503/content/sites/engage/en/page.html，并且该页面的菜单链接显示为：

![chlimage_1-381](assets/chlimage_1-381.png)

### 活动流功能 {#activity-stream-function}

活动流函数是一个 [活动流组件](activities.md) 选定所有视图（所有活动、用户活动及后续活动）。 另请参阅 [活动流要点](essentials-activities.md) 适用于开发人员。

添加到模板后，将打开以下对话框：

#### 配置功能详细信息 {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 显示“我的活动”视图]**
如果选中此项，“活动”页面将包含一个选项卡，该选项卡会根据当前成员在社区中生成的活动筛选活动。 默认选中。

* **[!UICONTROL 显示“所有活动”视图]**
如果选中此项，“活动”页面将包含一个选项卡，其中包含在当前成员有权访问的社区中生成的所有活动。 默认选中。

* **[!UICONTROL 显示“新闻源”视图]**
如果选中此项，“活动”页面将包含一个选项卡，该选项卡会根据当前成员关注的活动筛选活动。 默认选中。

### 指定任务功能 {#assignments-function}

工作分配函数是定义 [社区网站以启用](overview.md#enablement-community). 它允许向社区成员分配支持资源。 另请参阅 [工作总揽](essentials-assignments.md) 适用于开发人员。

此函数可作为 [启用附加组件](enablement.md). 启用附加组件需要额外的许可才能在生产环境中使用。

添加到模板后，唯一的配置是 [标题和URL设置](#title-and-url-settings).

### 博客功能 {#blog-function}

博客函数是 [博客组件](blog-feature.md) 配置了标记、文件上传、后续、成员自行编辑、投票和审核功能。 另请参阅 [博客要点](blog-developer-basics.md) 适用于开发人员。

添加到模板后，将打开以下对话框：

![chlimage_1-383](assets/chlimage_1-383.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 允许特权成员]**
如果选中，博客将仅允许特权成员通过允许选择 [特权成员组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员创建。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中，则博客将包含成员上传文件的功能。 默认选中。

* **[!UICONTROL 允许线程化回复]**
如果未选中，博客将允许对文章进行回复（评论），但不允许对评论进行回复。 默认选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则该构思可被识别为 [特色内容](featured.md). 默认选中。

### 日历功能 {#calendar-function}

日历函数是 [日历组件](calendar.md) 配置为允许标记。 另请参阅 [日历要点](calendar-basics-for-developers.md) 适用于开发人员。

添加到模板后，将打开以下对话框：

![chlimage_1-384](assets/chlimage_1-384.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 允许固定]**
如果选中，论坛将允许将主题回复固定到评论列表的开头。 默认选中。

* **[!UICONTROL 允许特权成员]**
如果选中，博客将仅允许特权成员通过允许选择 [特权成员组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员创建。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中，则博客将包含成员上传文件的功能。 默认选中。

* **[!UICONTROL 允许线程化回复]**
如果未选中，博客将允许对文章进行回复（评论），但不允许对评论进行回复。 默认选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则该构思可被识别为 [特色内容](featured.md). 默认选中。

### 目录功能 {#catalog-function}

目录函数提供了 [启用社区](overview.md#enablement-community) 成员以浏览未分配给他们的启用资源。 请参阅 [标记支持资源](tag-resources.md) 和 [目录要点](catalog-developer-essentials.md) 适用于开发人员。

社区站点的所有支持资源和学习路径如果属性为，则将显示在所有目录中。 ` [Show in Catalog](resources.md)`，则设置为true。 要明确包含资源和学习路径，必须应用 [预过滤](catalog-developer-essentials.md#pre-filters) 目录。

添加到模板后，配置允许指定标记命名空间，用于配置呈现给网站访客的标记过滤器：

![目录函数](assets/catalogfunc.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 选择所有命名空间]**

   * 选定的标记命名空间定义了哪些标记可供访客选择，以过滤目录中列出的支持资源列表。
   * 如果选中此项，则社区站点允许的所有标记命名空间都将可用。
   * 如果未选中，则可以选择社区站点允许的一个或多个命名空间。
   * 默认选中。

### 特色内容功能 {#featured-content-function}

特色内容功能是一个 [特色内容组件](featured.md) 配置为允许添加和删除注释。

每个组件可能允许或禁止功能显示内容(请参阅 [博客功能](#blog-function), [日历函数](#calendar-function), [论坛功能](#forum-function), [构思函数](#ideation-function)和 [问题解答函数](#qna-function))。

添加到模板后，唯一的配置是 [标题和URL设置](#title-and-url-settings).

### 文件库功能 {#file-library-function}

文件库函数是 [文件库组件](file-library.md) 配置为允许添加和删除注释。

添加到模板后，唯一的配置是 [标题和URL设置](#title-and-url-settings).

### 论坛功能 {#forum-function}

论坛函数是一个 [论坛组件](forum.md) 配置了标记、文件上传、后续、成员自行编辑、投票和审核功能。

添加到模板后，将打开以下对话框：

#### 配置功能详细信息 {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 允许固定]**
如果选中，论坛将允许将主题回复固定到评论列表的开头。 默认选中。

* **[!UICONTROL 允许特权成员]**
如果选中，论坛将仅允许特权成员通过选择 [特权成员组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员发布内容。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中，论坛将包括成员上传文件的功能。 默认选中。

* **[!UICONTROL 允许线程化回复]**
如果未选中，论坛将允许对主题进行评论，但不允许对这些评论进行回复。 默认选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则该构思可被识别为 [特色内容](featured.md). 默认选中。

### 组函数 {#groups-function}

>[!CAUTION]
>
>组函数必须 *not* be *第一，也是唯一* 功能。
>
>任何其他函数，例如 [页面函数](#page-function)，必须先包含并列出。

群组功能允许社区成员在发布环境中的社区站点内创建子社区。

取决于 [设置](sites-console.md#groupmanagement) 组函数包含在 [社区站点模板](sites.md)，则这些组可以是公共的或私有的，并且一个或多个社区组模板可配置为在实际创建社区组时（例如从发布环境）提供模板选项。 A [社区组模板](tools-groups.md) 指定为群组页面创建的社区功能，如论坛和日历。

创建社区组后，会为新组动态创建成员组，可以将成员分配或加入到新组中。 有关更多信息，请参阅 [管理用户和用户组](users.md).

截至社区 [功能包1](deploy-communities.md#latestfeaturepack)，则可使用 [“社区站点”的“组”控制台](groups.md)，且可以在启用后在发布环境中创建。

添加到模板后，将打开以下对话框：

![chlimage_1-386](assets/chlimage_1-386.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 选择组模板]**
一个下拉菜单，用于选择一个或多个已启用的组模板，新社区组（在发布环境中）的未来创建者可以从中选择一个或多个已启用的组模板。

* **[!UICONTROL 允许特权成员]**
如果选中，论坛将仅允许特权成员通过选择 [特权成员安全组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员发布内容。 默认为未选中。

* **[!UICONTROL 允许创建发布]**
如果选中此选项，则授权社区成员可以在发布环境中创建组。 如果未选中此选项，则只能在创作环境中通过“社区站点”的“组”控制台创建新组（子社区）。

   默认为 `checked`.

### 构思功能 {#ideation-function}

构思函数是一个包含 [构思组件](ideation-feature.md).

添加到模板后，将打开以下对话框，其中指定了模板的默认标题和URL名称以及默认的显示设置：

![chlimage_1-387](assets/chlimage_1-387.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 允许特权成员]**
如果选中，论坛将仅允许特权成员通过选择 [特权成员安全组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员发布内容。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中此选项，则构思将包括让成员上传文件的功能。 默认选中。

* **[!UICONTROL 允许线程化回复]**
如果未选中，则该构思将允许对主题进行回复（评论），但不允许对评论进行回复。 默认选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则该构思可被识别为 [特色内容](featured.md). 默认选中。

### 排行榜功能 {#leaderboard-function}

排行榜功能是一个包含 [排行榜部分](enabling-leaderboard.md).

**注意**:领导板组件需要进一步配置 *after* 社区站点是从包含领导板功能的社区模板创建的。 排行榜部分的 [规则](enabling-leaderboard.md#rules-tab) 将需要指定，具体取决于 [评分和徽章](implementing-scoring.md) （用于社区站点）。

添加到模板后，将打开以下对话框，其中指定了模板的默认标题和URL名称以及默认的显示设置：

![chlimage_1-388](assets/chlimage_1-388.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 显示徽章]**
如果选中此选项，则标记图标的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 显示标记名称]**
如果选中此项，则标志名称的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 显示头像]**
如果选中此项，则会将成员的头像图像包含在排行榜中，旁边是其名称链接到其成员配置文件的位置。

   默认为未选中。

### 页面功能 {#page-function}

页面功能可向社区站点添加一个与社区站点功能连接的空白页面：登录、菜单、通知、消息、主题和品牌策略。 可以使用 [标准AEM创作模式](../../help/sites-authoring/editing-content.md).

添加到模板后，唯一的配置是 [标题和URL设置](#title-and-url-settings).

### 问题与解答功能 {#qna-function}

问题解答函数是一个 [问题解答组件](working-with-qna.md) 配置了标记、文件上传、后续、成员自行编辑、投票和审核功能。

添加到模板后，配置允许对特权成员进行限制：

![chlimage_1-389](assets/chlimage_1-389.png)

* 请参阅 [标题和URL设置](#title-and-url-settings)
* **[!UICONTROL 允许固定]**
如果选中，论坛将允许将主题回复固定到评论列表的开头。 默认选中。

* **[!UICONTROL 允许特权成员]**
如果选中，则QnA论坛将仅允许特权成员通过选择 [特权成员组](users.md#privileged-members-group). 如果未选中，则允许所有社区成员发布内容。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中此选项，则问题解答论坛将包含成员上传文件的功能。 默认选中。

* **[!UICONTROL 允许线程化回复]**
如果未选中，问题与解答论坛将允许对已发布的问题进行评论（回答），但不允许对答案进行回复。 默认选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则该构思可被识别为 [特色内容](featured.md). 默认选中。

## 创建社区功能 {#create-community-function}

通过选择 `Create Community Function` 图标。 可以创建基于同一AEM Blueprint的多个函数，然后通过在创作编辑模式下打开来进行唯一自定义。

![chlimage_1-390](assets/chlimage_1-390.png)

### 社区功能名称 {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

在“社区函数名称”面板上，配置了函数的名称、说明以及是启用还是禁用该函数：

* **[!UICONTROL 社区功能名称]**
用于显示和存储的函数名称

* **[!UICONTROL 社区功能描述]**
显示的函数描述

* **[!UICONTROL 已禁用/已启用]**
控制函数是否可引用的切换开关

### AEM Blueprint {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

在 `AEM Blueprint` ，则可以选择作为社区功能底层实现的Blueprint。

社区功能是一个由一个或多个页面组成的迷你网站，预先连接成网页以包含到社区网站中，包括登录、用户配置文件、通知、消息、网站菜单、搜索、主题和品牌策略功能。 创建函数后，可以 [打开函数](#open-community-function) 在创作编辑模式下，自定义页面和/或组件设置。

由于社区功能是作为 [live copy](../../help/sites-administering/msm.md#live-copies) a [Blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint)，则可以转出对函数所做的更改，该函数会影响从中创建的所有社区网站页面 [社区站点模板](sites.md) 或 [社区组模板](tools-groups.md) 包含函数。 还可以将页面与其父Blueprint取消关联，以便进行页面级别的修改。

另请参阅 [多站点管理器](../../help/sites-administering/msm.md).

### 缩略图 {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

在“缩略图”面板上，可以上传图像以在 [社区功能控制台](#community-functions-console).

## 打开社区功能 {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

选择 `Open Community Function` 图标，以进入创作编辑模式以创作页面内容和修改功能组件的配置。

### 配置组件 {#configuring-components}

社区功能作为AEM Blueprint的Live Copy实施，其详细信息记录在 [多站点管理器](../../help/sites-administering/msm.md).

不仅可以创作页面内容，还可以配置组件。

如果在已创建社区站点的页面上配置组件，则可能需要取消 [继承](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) 以配置组件。 配置完成后，应重新建立继承。

有关配置详细信息，请访问 [社区组件](author-communities.md) 作者。

## 编辑社区功能 {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

选择 `Edit Community Function` 图标，以使用与 [创建社区功能](#create-community-function)，包括启用或禁用函数。
