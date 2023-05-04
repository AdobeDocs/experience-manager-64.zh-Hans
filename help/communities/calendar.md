---
title: 日历功能
seo-title: Calendar Feature
description: 以日历格式提供社区活动信息
seo-description: Provides community event information in a calendar format
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
exl-id: f95d1471-82a1-4c37-ac5b-0eb861c823a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 6%

---

# 日历功能 {#calendar-feature}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

日历功能支持以日历格式向所有站点访客或仅登录站点访客（社区成员）提供社区活动信息，而只有授权成员才能添加活动。

文档的此部分描述：

* 向AEM网站添加日历功能
* 的配置设置 `Calendar`组件

## 向页面添加日历 {#adding-a-calendar-to-a-page}

添加 `Calendar` 组件添加到创作模式下的页面，可使用组件浏览器找到

* `Communities / Calendar`

并将其拖动到页面上的适当位置，如相对于要供用户查看的功能的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](calendar-basics-for-developers.md#essentials-for-client-side) 包含，这是 `Calendar` 组件。

![chlimage_1-112](assets/chlimage_1-112.png)

### 配置日历 {#configuring-calendar}

选择已放置的 `Calendar`要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### “设置”选项卡 {#settings-tab}

在 **[!UICONTROL 设置]** 选项卡，指定是否允许将标记应用于日历条目。

* **[!UICONTROL 每页的事件数]**

   定义每页显示的事件数。 默认值为10。

* **[!UICONTROL 已审核]**

   如果选中此项，则必须批准发布日历事件和评论，然后才能在发布网站上显示这些事件和评论。 默认为未选中。

* **[!UICONTROL 已关闭]**

   如果选中，则日历将关闭为新事件条目和注释。 默认为未选中。

* **[!UICONTROL 富文本编辑器]**

   如果选中，则可以输入带有标记的日历事件和注释。 默认选中。

* **[!UICONTROL 允许标记]**

   如果选中此选项，则允许成员向他们发布的事件添加标签(请参阅 **标记字段** 选项卡。 默认选中。

* **[!UICONTROL 允许文件上传]**

   如果选中此项，则允许将文件附件添加到日历事件或评论。 默认选中。

* **[!UICONTROL 允许关注]**

   如果选中，则允许成员关注发布到日历的事件。 默认选中。

* **[!UICONTROL 最大文件大小]**

   仅在 `Allow File Uploads` 复选框。 此字段将限制已上传文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**

   仅在 `Allow File Uploads` 复选框。 以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许上载未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 附加图像文件最大大小]**

   仅当选中允许文件上传时相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许的封面图像类型]**

   以逗号分隔的图像文件扩展名列表，其中带有“点”分隔符。 默认为 `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL 允许主题回复]**

   如果选中此项，则允许对发布到日历事件的评论做出回复。 默认选中。

* **[!UICONTROL 允许用户删除评论和事件]**

   如果选中此项，则允许成员删除他们发布的评论和日历事件。 默认选中。

* **[!UICONTROL 允许投票]**

   如果选中此项，则包含包含日历事件的投票功能。 默认选中。

* **[!UICONTROL 显示痕迹导航]**

   在事件页面上显示痕迹导航. 默认选中。

* **[!UICONTROL 日期范围筛选器]**

   定义添加到当前日期的天数，以计算日历事件列表页面过滤器的“至”值。 默认数字为30。

* **[!UICONTROL 允许专题内容]**

   如果选中，则该构思可被识别为 [特色内容](featured.md). 默认为未选中。

在 **[!UICONTROL 用户审核]** 选项卡，指定如何管理已发布的主题和回复（用户生成的内容）。 有关更多信息，请参阅 [审核用户生成的内容](moderate-ugc.md).

#### “用户审核”选项卡 {#user-moderation-tab}

* **[!UICONTROL 拒绝帖子]**

   如果选中，则允许受信任的成员审核者拒绝帖子并阻止帖子出现在公共论坛中。 默认选中。

* **[!UICONTROL 关闭/重新打开事件]**

   如果选中，受信任的成员审核者可以关闭事件以进一步进行编辑和评论，也可以重新打开事件。 默认选中。

* **[!UICONTROL 标记帖子]**

   如果选中此选项，则允许成员将他人的事件或评论标记为不适当。 默认选中。

* **[!UICONTROL 标记原因列表]**

   如果选中，允许成员从下拉列表中选择其标记事件或评论为不适当的原因。 默认为未选中。

* **[!UICONTROL 自定义标记原因]**

   如果选中，则允许成员输入自己将事件或评论标记为不适当的原因。 默认为未选中。

* **[!UICONTROL 审核阈值]**

   输入在通知审核者之前，必须由成员标记事件或评论的次数。 默认值为1（一次）。

* **[!UICONTROL 标记限制]**

   输入在事件或评论在公共视图中隐藏之前必须进行标记的次数。 如果设置为–1，则标记的主题或评论永远不会在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认值为5。

#### 标记字段选项卡 {#tag-field-tab}

在 **[!UICONTROL 标记字段]** 选项卡，可应用的标记（如果允许） **[!UICONTROL 设置]** 选项卡，具体受到的限制，具体取决于所选的命名空间。

* **[!UICONTROL 允许的命名空间]**

   相关条件 `Allow Tagging` 在 **[!UICONTROL 设置]** 选项卡。 可应用的标记仅限于所选命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）以及“包括所有标记”。 默认为“未选中”，这表示允许使用所有命名空间。

* **[!UICONTROL 建议限制]**

   输入要作为建议显示给论坛成员的标记数。 默认为 `-1` （无限制）。

>[!NOTE]
>
>访问 [管理标记](../../help/sites-administering/tags.md) 了解如何添加新标记命名空间（分类）。

#### “翻译”选项卡 {#translation-tab}

在 **[!UICONTROL 翻译]** 选项卡，如果为社区站点启用了翻译，则可以设置翻译来翻译整个主题（事件和评论），而不是翻译特定帖子。

* **[!UICONTROL 全部翻译]**

   如果选中此选项，则事件和注释将翻译为用户的首选语言。 默认选中。

## 网站访客体验 {#site-visitor-experience}

在发布环境中，日历功能将显示具有默认日期范围的搜索字段以及该范围内的任何日历事件。

选择日历事件后，将显示日历事件详细信息、说明和注释。

其他功能取决于网站访客是审核者、管理员、社区成员、特权成员还是匿名。

### 审核者和管理员 {#moderators-and-administrators}

当登录用户具有审核者或管理员权限时，他们能够执行 [审核任务](moderate-ugc.md) （组件配置允许）。

![chlimage_1-115](assets/chlimage_1-115.png)

### 成员 {#members}

当登录用户是社区成员或 [特权成员](users.md#privileged-members-group) （具体取决于配置），用户可以选择 `New Event` 创建和发布新日历事件。

具体而言，他们可能

* 创建新日历事件
* 将评论发布到日历事件
* 编辑自己的日历事件或评论
* 删除自己的日历事件或评论
* 标记他人的日历事件或评论

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### 匿名 {#anonymous}

未登录的网站访客只能阅读发布的日历事件，翻译这些事件（如果受支持），但不得添加事件或评论，也不得标记他人的事件或评论。

![chlimage_1-118](assets/chlimage_1-118.png)

## 附加信息 {#additional-information}

有关 [日历要点](calendar-basics-for-developers.md) 页面。

有关审核日历事件和评论，请参阅 [审核用户生成的内容](moderate-ugc.md).

有关标记日历事件和注释，请参阅 [标记用户生成的内容](tag-ugc.md).

有关日历事件和注释的翻译，请参阅 [翻译用户生成的内容](translate-ugc.md).
