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
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# 构思功能{#ideation-feature}

## 简介 {#introduction}

构思功能为发布环境中的登录站点访客（社区成员）提供了一个区域，用于：

* 创建想法并与社区分享
* 视图与思想评论
* 遵循想法
* 就一个想法投票

文档的本节介绍

* 将构思功能添加到AEM站点
* 标识组件的配置设置

## 将构思添加到页面{#adding-a-ideation-to-a-page}

要在创作模式下将`Ideation`组件添加到页面，请使用组件浏览器找到`Communities / Ideation`并将其拖动到应显示构思的页面上。

有关必要的信息，请访问[社区组件基础知识](basics.md)。

当包含[必需的客户端库](ideation.md#essentials-for-client-side)时，`Ideation`组件的显示方式如下：

![chlimage_1-21](assets/chlimage_1-29.png)

## 配置构思{#configuring-an-ideation}

选择要访问的已放置`Ideation`组件，然后选择打开编辑对话框的`Configure`图标。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 设置选项卡{#settings-tab}

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，指定构思和注释的设置：

* **[!UICONTROL 构思]**
标题构思的显示标题。默认为 
`Ideation`。

* **[!UICONTROL 构思]**
描述要作为构思的子标题显示的描述。默认为无说明。

* **[!UICONTROL 每页主]**
题定义每页显示的想法／帖子数。默认值为10。

* **[!UICONTROL 审核]**
如果选中，则发布创意和评论必须获得批准，然后才能在发布站点上显示。默认为未选中。

* **[!UICONTROL 已]**
关闭如果选中，则构思论坛将关闭，供新想法和评论使用。默认为未选中。

* **[!UICONTROL 富文本编]**
辑器如果选中，则可以使用标记输入构思和注释。默认为未选中。

* **[!UICONTROL 允许]**
标记如果选中，允许成员向其帖子中添加标记标签(请参 **[!UICONTROL 阅标]** 记字段选项卡)。默认为未选中。

* **[!UICONTROL 允许文]**
件上传如果选中，允许将文件附件添加到构思或注释中。默认为未选中。

* **[!UICONTROL 最大文件大]**
小仅在 
`Allow File Uploads` 的双曲余切值。此字段将限制已上载文件的大小（以字节为单位）。 默认值为104857600(10 Mb)。

* **[!UICONTROL 允许的文件]**
类型仅在 
`Allow File Uploads` 的双曲余切值。以逗号分隔的文件扩展名列表，以“点”分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 最大附加图像文]**
件大小仅在选中“允许文件上传”时相关。上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许]**
回复如果选中，允许回复发布到构思的评论。默认为未选中。

* **[!UICONTROL 允许用户删除注释和主]**
题如果选中，允许成员删除他们发布的注释和想法。默认为未选中。

* **[!UICONTROL 允许]**
遵循如果选中此项，则为创意帖子加入以下功能，允许成员通 [](notifications.md) 知新帖子。默认为未选中。

* **[!UICONTROL 允许电]**
子邮件订阅如果选中，允许成员通过电子邮件(订阅)通知[新帖子](subscriptions.md)。需要检查`Allow Following`并配置[电子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 允许]**
投票如果选中，允许对某个想法的评论进行投票。默认为未选中。

* **[!UICONTROL 显示]**
徽章如果选中，则使用会员的 [](implementing-scoring.md) 想法显示已获得和已分配徽章。默认为未选中。

* **[!UICONTROL 如果选]**
中“允许使用特色内容”，则可以将该想法标识为 [特色内容](featured.md)。默认为未选中。

### “用户协调”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户协调]**&#x200B;选项卡下，指定如何管理已发布的构思和评论（用户生成的内容）。 有关详细信息，请参阅[协调用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝]**
帖子如果选中，则允许受信任的成员审核者拒绝帖子并阻止帖子显示在公共论坛中。默认为未选中。

* **[!UICONTROL 关闭／重新打]**
开主题如果选中，受信任的成员审核者可以关闭主题以进一步编辑和评论，还可以重新打开主题。默认为未选中。

* **[!UICONTROL 标记]**
帖子如果选中，允许成员将其他主题或评论标记为不合适。默认为未选中。

* **[!UICONTROL 标记原]**
因列表如果选中，允许成员从下拉列表中选择标记主题或评论为不合适的原因。默认为未选中。

* **[!UICONTROL 自定义标]**
志原因如果选中，允许成员输入自己将主题或评论标记为不合适的原因。默认为未选中。

* **[!UICONTROL 审核]**
阈值输入在通知审核者之前，成员必须标记主题或评论的次数。默认值为1（一次）。

* **[!UICONTROL 标记]**
限制输入主题或评论在隐藏到公共视图之前必须标记的次数。如果设置为-1，则标记的主题或评论从不隐藏于公共视图。 否则，此数字必须大于或等于仲裁阈值。 默认值为5。

### 标记字段选项卡{#tag-field-tab}

在&#x200B;**[!UICONTROL 标记字段]**&#x200B;选项卡下，如果允许在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下应用的标记会根据所选命名空间进行限制。

* **[!UICONTROL 允许的命]**
名空间相关(如果 
`Allow Tagging` 在“设置”选项卡 **** 下检查。可应用的标记仅限于所选命名空间类别内的标记。 命名空间的列表包括“标准标记”(默认命名空间)和“包括所有标记”。 默认值为“无”(none checked)，这意味着允许所有命名空间。

* **[!UICONTROL 建议]**
限制输入要作为建议显示给论坛的成员发布的标记数。值 
**-** 1表示无限制。默认值为0。

### 排序设置选项卡{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序设置]**&#x200B;选项卡下，指定显示已发布注释时的排序方式。

* **[!UICONTROL 排序依]**
据检查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`.默认值为`Newest, Oldest, Last Updated`。

* **[!UICONTROL 设置为]**
DefaultPulldown以选择一个选中的排序选项作为默认值显示。默认为 
`Newest`。

* **[!UICONTROL 选择分析排序的时间]**
选项下拉以选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.默认值为`All`。

## 站点访客体验{#site-visitor-experience}

### 创建构思{#creating-idea}

与所有社区功能一样，如果未登录，站点访客只能阅读想法并视图他人的意见（通过评论和投票／喜欢）。

登录后，会员可能会创建新想法。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交构思之前，成员可以保存草稿。

通过选择`Save as Draft`按钮，将保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在`My Drafts`选项卡中查看保存的草稿时，选择`Read More`以重新进入编辑模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供反馈{#providing-feedback}

构思发布后，其他成员可以登录，打开构思(`Read More`)并喜欢该构思，从而增加投票数并发表评论。

![chlimage_1-35](assets/chlimage_1-35.png)

### 附加信息 {#additional-information}

有关开发人员的详细信息，请参阅[Ideation Essentials](ideation.md)页面。

有关已发布主题和注释的审核，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。
