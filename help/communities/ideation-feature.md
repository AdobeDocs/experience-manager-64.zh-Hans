---
title: 构思功能
seo-title: 构思功能
description: 添加和配置构思功能
seo-description: 添加和配置构思功能
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# 构思功能{#ideation-feature}

## 简介 {#introduction}

“构思”功能为发布环境中的登录站点访客（社区成员）提供了一个区域，用于：

* 创建想法以与社区共享
* 观看和评论意见
* 遵循一个想法
* 就一个想法投票

此文档部分描述

* 将构思功能添加到AEM网站
* 构思组件的配置设置

## 向页面{#adding-a-ideation-to-a-page}添加构思

要在创作模式下将`Ideation`组件添加到页面，请使用组件浏览器找到`Communities / Ideation`并将其拖动到应显示构思的页面上。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](ideation.md#essentials-for-client-side)时，将显示`Ideation`组件的方式：

![chlimage_1-21](assets/chlimage_1-29.png)

## 配置构思{#configuring-an-ideation}

选择要访问的已放置的`Ideation`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### “设置”选项卡{#settings-tab}

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，指定构思和注释的设置：

* **[!UICONTROL 构思]**
标题构思的显示标题。默认为 
`Ideation`。

* **[!UICONTROL 构思]**
描述要作为构思的子标题显示的描述。默认为无描述。

* **[!UICONTROL 每页主]**
题定义每页显示的构思/帖子数。默认值为10。

* ****
已审核如果选中此选项，则必须先批准发布意见和评论，然后才能在发布网站上显示这些意见和评论。默认为未选中。

* ****
关闭如果选中此选项，则构思论坛将不会显示新想法和评论。默认为未选中。

* **[!UICONTROL 富文本编]**
辑器如果选中此选项，则可以输入带有标记的构思和注释。默认为未选中。

* **[!UICONTROL 允许]**
标记如果选中此选项，允许成员向其帖子中添加标记标签(请参阅 **[!UICONTROL 标记]** 字段选项卡)。默认为未选中。

* **[!UICONTROL 允许文]**
件上传如果选中此选项，则允许将文件附件添加到构思或注释中。默认为未选中。

* **[!UICONTROL 最大文件大]**
小仅在 
`Allow File Uploads` 复选框。此字段将限制已上传文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件]**
类型仅在 
`Allow File Uploads` 复选框。以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许上载未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 最大附加图像文件大]**
小仅在选中允许文件上传时相关。上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许]**
回复如果选中此选项，则允许对发布到构思的评论做出回复。默认为未选中。

* **[!UICONTROL 允许用户删除评论和主]**
题如果选中此选项，则允许成员删除他们发布的评论和意见。默认为未选中。

* **[!UICONTROL 允许]**
关注如果选中此项，则为创意帖子提供以下功能，以便向成员通 [](notifications.md) 知新帖子。默认为未选中。

* **[!UICONTROL 允许电子]**
邮件订阅如果选中此选项，则允许会员通过电子邮件([订阅](subscriptions.md))接收新帖子的通知。需要检查`Allow Following`并[电子邮件配置](email.md)。 默认为未选中。

* **[!UICONTROL 允许]**
投票如果选中，则允许对构思的评论进行投票。默认为未选中。

* **[!UICONTROL 显示]**
徽章如果选中此选项，则用会员的 [](implementing-scoring.md) 想法显示已获得和已分配的徽章。默认为未选中。

* **[!UICONTROL 允许显]**
示特色内容，如果选中此选项，则该创意能够被识别为特 [色内容](featured.md)。默认为未选中。

### “用户审核”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户审核]**&#x200B;选项卡下，指定如何管理已发布的想法和评论（用户生成的内容）。 有关更多信息，请参阅[审核用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝]**
帖子如果选中此选项，则允许受信任的成员审核者拒绝帖子并阻止帖子出现在公共论坛中。默认为未选中。

* **[!UICONTROL 关闭/重新打]**
开主题如果选中此选项，受信任的成员审核者可以关闭主题以进一步编辑和评论，并且还可以重新打开主题。默认为未选中。

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

* **[!UICONTROL 允许的命]**
名空间相关(如果 
`Allow Tagging` 已在设置选项卡下 **** 选中。可应用的标记仅限于所选命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）以及“包括所有标记”。 默认为“未选中”，这表示允许使用所有命名空间。

* **[!UICONTROL 建议]**
限制输入要作为建议显示给论坛成员的标记数。值 
**-** 1表示无限制。默认值为0。

### 排序设置选项卡{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序设置]**&#x200B;选项卡下，指定在显示时对发布的评论进行排序的方式。

* **[!UICONTROL 按检]**
查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`.默认值为`Newest, Oldest, Last Updated`。

* **[!UICONTROL 设置为]**
DefaultDull（下拉）以选择要显示为默认值的选中排序选项之一。默认为 
`Newest`。

* **[!UICONTROL 选择Analytics排序的时间选]**
项下拉选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.默认值为`All`。

## 网站访客体验{#site-visitor-experience}

### 创建构思{#creating-idea}

与所有“社区”功能一样，如果未登录，网站访客只能阅读意见和查看他人的意见（通过评论和投票/称赞）。

登录后，会员可以创建新想法。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交构思之前，成员可以保存草稿。

选择`Save as Draft`按钮，将保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在`My Drafts`选项卡中查看保存的草稿时，选择`Read More`以重新进入编辑模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供反馈{#providing-feedback}

构思发布后，其他成员可以登录，打开构思(`Read More`)，并像构思一样，从而将其添加到投票计数中，并发表评论。

![chlimage_1-35](assets/chlimage_1-35.png)

### 附加信息 {#additional-information}

有关更多信息，请参阅[Ideation Essentials](ideation.md)页面，供开发人员使用。

有关审核已发布的主题和评论，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。
