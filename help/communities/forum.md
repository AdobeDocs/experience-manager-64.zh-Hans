---
title: 论坛功能
seo-title: 论坛功能
description: 如何添加和配置论坛功能
seo-description: 如何添加和配置论坛功能
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# 论坛功能{#forum-feature}

## 简介 {#introduction}

“论坛”功能为发布环境中的登录站点访客（社区成员）提供了一个区域，用于：

* 创建新主题
* 查看和回复主题
* 关注主题
* 搜索论坛
* 帮助审核论坛内容
* 将论坛主题从一个页面移动到另一个页面

此文档部分描述

* 将论坛功能添加到AEM网站
* `Forum`组件的配置设置

## 将论坛添加到页面{#adding-a-forum-to-a-page}

要在创作模式下向页面添加`Forum`组件，请使用组件浏览器找到

* `Communities / Forum`

然后将其拖动到应显示论坛的页面上。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](essentials-forum.md#essentials-for-client-side)时，将显示`Forum`组件的方式：

![chlimage_1-60](assets/chlimage_1-60.png)

## 配置论坛{#configuring-a-forum}

选择要访问的已放置的`Forum`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### “设置”选项卡{#settings-tab}

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，指定主题和回复的设置：

* **[!UICONTROL 每页主]**
题定义每页显示的主题/帖子数。默认值为10。

* ****
已审核如果选中此选项，则必须批准发布主题和评论，然后才能在发布网站上显示这些主题和评论。默认为未选中。

* ****
关闭如果选中此选项，则论坛将不会显示新主题和评论。默认为未选中。

* **[!UICONTROL 富文本编]**
辑器如果选中此选项，则可以输入带有标记的主题和注释。默认为未选中。

* **[!UICONTROL 允许]**
标记如果选中此选项，允许成员向其帖子中添加标记标签(请参阅 **[!UICONTROL 标记]** 字段选项卡)。默认为未选中。

* **[!UICONTROL 允许文]**
件上载如果选中此选项，则允许将文件附件添加到主题或评论。默认为未选中。

* **[!UICONTROL 允许]**
关注如果选中此项，则为论坛帖子提供以下功能，以允许成员 [](notifications.md) 获得新帖子。默认为未选中。

* **[!UICONTROL 允许]**
固定如果选中此选项，则论坛主题可能会固定到主题列表的顶部。默认为未选中。

* **[!UICONTROL 允许显]**
示特色内容，如果选中此选项，则该创意能够被识别为特 [色内容](featured.md)。默认为未选中。

* **[!UICONTROL 允许电子]**
邮件订阅如果选中此选项，则允许会员通过电子邮件([订阅](subscriptions.md))接收新帖子的通知。需要检查`Allow Following`并[电子邮件配置](email.md)。 默认为未选中。

* **[!UICONTROL 最大文件大]**
小仅在 
`Allow File Uploads` 复选框。此字段将限制已上传文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件]**
类型仅在 
`Allow File Uploads` 复选框。以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许上载未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 最大附加图像文件大]**
小仅在选中允许文件上传时相关。上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许线程]**
化回复如果选中此选项，则允许对发布到该主题的评论做出回复。默认为未选中。

* **[!UICONTROL 允许用户删除评论和主]**
题如果选中此选项，允许成员删除他们发布的评论和主题。默认为未选中。

* **[!UICONTROL 允许]**
投票如果选中，则包含带有主题的投票功能。默认为未选中。

* **[!UICONTROL 显示痕迹]**
导航如果选中此选项，则在主题页面上显示导航痕迹导航。默认选中。

* **[!UICONTROL 显示]**
徽章如果选中此项，则使用会员的博 [](implementing-scoring.md) 客条目显示已获得和已分配的徽章。默认为未选中。

>[!NOTE]
>
>可能需要同时检查`AllowThreaded Replies`和`Allow users to Delete Comments and Topics`以启用对主题的注释。

### “用户审核”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户审核]**&#x200B;选项卡下，指定如何管理已发布的主题和回复（用户生成的内容）。 有关更多信息，请参阅[审核用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝]**
帖子如果选中此选项，则允许受信任的成员审核者拒绝帖子并阻止帖子出现在公共论坛中。默认为未选中。

* **[!UICONTROL 关闭/重新打]**
开主题如果选中此选项，受信任的成员审核者可以关闭主题以进一步编辑和评论，并且还可以重新打开主题。默认为未选中。

* **[!UICONTROL 移动]**
主题如果选中此选项，则允许发布端审核者移动主题。默认选中。

* **[!UICONTROL 标记]**
帖子如果选中，允许成员将他人的主题或评论标记为不适当。默认为未选中。

* **[!UICONTROL 标记原]**
因列表如果选中，允许成员从下拉列表中选择标记主题或评论为不适当的原因。默认为未选中。

* **[!UICONTROL 自定义标]**
记原因如果选中此选项，则允许成员输入自己将主题或评论标记为不适当的原因。默认为未选中。

* **[!UICONTROL 审核]**
阈值输入在通知审核者之前，主题或评论必须由成员进行标记的次数。默认值为1（一次）。

* **[!UICONTROL 标记]**
限制输入在主题或评论在公共视图中隐藏之前必须标记的次数。如果设置为–1，则标记的主题或评论永远不会在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认值为5。

### 标记字段选项卡{#tag-field-tab}

在&#x200B;**[!UICONTROL 标记字段]**&#x200B;选项卡下，可能应用的标记（如果允许）位于&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，将根据所选的命名空间而受到限制。

* **[!UICONTROL 允许的]**
命名空间如果 `Allow Tagging` 在“设置”选项卡下选中，则 **** 相关。可应用的标记仅限于所选命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）以及“包括所有标记”。 默认为“未选中”，这表示允许使用所有命名空间。

* **[!UICONTROL 建议]**
限制输入要作为建议显示给论坛成员的标记数。默认为 
**-** 1（无限制）。

### 翻译选项卡{#translation-tab}

在&#x200B;**[!UICONTROL 翻译]**&#x200B;选项卡下，如果为社区站点启用了翻译，则可以设置翻译以翻译整个主题或选定的帖子。

* **[!UICONTROL Translate]**
All如果选中此选项，则论坛线程将被翻译成用户的首选语言。默认为未选中。

### 排序设置选项卡{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序设置]**&#x200B;选项卡下，指定在显示时对发布的评论进行排序的方式。

* **[!UICONTROL 按检]**
查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 默认值为`Newest, Oldest, Last Updated`。

* **[!UICONTROL 设置为]**
DefaultDull（下拉）以选择要显示为默认值的选中排序选项之一。默认为 
`Newest`。

* **[!UICONTROL 选择Analytics排序的时间选]**
项下拉选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.默认值为`All`。

## 附加信息 {#additional-information}

有关更多信息，请参阅[Forum Essentials](essentials-forum.md)页面，供开发人员使用。

有关审核已发布的主题和评论，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。

有关已发布主题和评论的翻译，请参阅[翻译用户生成的内容](translate-ugc.md)。
