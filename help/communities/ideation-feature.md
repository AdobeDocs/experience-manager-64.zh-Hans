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

---


# 构思功能 {#ideation-feature}

## 简介 {#introduction}

构思功能为发布环境中的登录站点访问者（社区成员）提供了一个区域，用于：

* 创建想法并与社区共享
* 观看和评论想法
* 遵循想法
* 就一个想法投票

文档的此部分描述了

* 将构思功能添加到AEM站点
* 构思组件的配置设置

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

要在创作模 `Ideation` 式下将组件添加到页面，请使用组件浏览器在应显示构思的页面上查找 `Communities / Ideation` 并将其拖动到相应位置。

有关必要的信息，请访 [问社区组件基础](basics.md)。

包括所 [需的客户端库](ideation.md#essentials-for-client-side) ，组件的显示 `Ideation`方式如下：

![chlimage_1-29](assets/chlimage_1-29.png)

## 配置构思 {#configuring-an-ideation}

选择要访问 `Ideation` 的已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 设置选项卡 {#settings-tab}

在“设 **[!UICONTROL 置]** ”选项卡下，指定构思和注释的设置：

* **[!UICONTROL 构思标]**&#x200B;题构思的显示标题。 Default is `Ideation`.

* **[!UICONTROL 构思描]**&#x200B;述要显示为构思子标题的说明。 默认为无说明。

* **[!UICONTROL 每页主题]**&#x200B;定义每页显示的构思／帖子数。 默认值为10。

* **[!UICONTROL 已审核]**&#x200B;如果选中此项，则发布构思和评论必须获得批准，然后才能在发布站点上显示。 默认为未选中。

* **[!UICONTROL 关闭]**&#x200B;如果选中此选项，则构思论坛将关闭以查看新构思和评论。 默认为未选中。

* **[!UICONTROL 富文本编辑器]**&#x200B;如果选中此选项，则可以使用标记输入构思和注释。 默认为未选中。

* **[!UICONTROL 允许标记]**&#x200B;如果选中此项，允许成员向其帖子中添加标记标签(请参 **[!UICONTROL 阅标记字段]** 选项卡)。 默认为未选中。

* **[!UICONTROL 允许文件上]**&#x200B;传如果选中此项，则允许将文件附件添加到构思或注释中。 默认为未选中。

* **[!UICONTROL 最大文件大小]**&#x200B;仅在选中时 `Allow File Uploads` 相关。 此字段将限制已上载文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**&#x200B;仅在选中时 `Allow File Uploads` 相关。 以逗号分隔的文件扩展名列表，带有“点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 仅当选中“允许文件上]**&#x200B;传”时，附加图像文件的最大大小相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许回复]**&#x200B;如果选中此项，则允许回复发布到构思的评论。 默认为未选中。

* **[!UICONTROL 允许用户删除注释和主题]**&#x200B;如果选中此项，允许成员删除他们发布的注释和想法。 默认为未选中。

* **[!UICONTROL 允许以]**&#x200B;下操作如果选中此项，则为创意帖子提供以下功能，允许成员 [收到](notifications.md) 新帖子的通知。 默认为未选中。

* **[!UICONTROL 允许电子邮]**&#x200B;件订阅如果选中此项，则允许会员通过电子邮件(订阅[](subscriptions.md))通知新帖子。 需要 `Allow Following` 选中并配置电 [子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 允许投票]**&#x200B;如果选中，允许对某个想法的评论进行投票。 默认为未选中。

* **[!UICONTROL 显示徽章]**&#x200B;如果选中此项，则使用会员的 [想法显示已获得](implementing-scoring.md) 和已分配的徽章。 默认为未选中。

* **[!UICONTROL 如果选中]**“允许特色内容”，则可以将该创意标识为特色 [内容](featured.md)。 默认为未选中。

### “用户审核”选项卡 {#user-moderation-tab}

在“用户 **[!UICONTROL 协调]** ”选项卡下，指定如何管理已发布的构思和评论（用户生成的内容）。 有关详细信息，请参阅 [审核用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝帖子]**&#x200B;如果选中此项，则允许受信任的成员审核者拒绝帖子并阻止帖子显示在公共论坛中。 默认为未选中。

* **[!UICONTROL 关闭／重新打开主]**&#x200B;题如果选中，受信任的成员审核者可以关闭主题以进一步编辑和评论，也可以重新打开主题。 默认为未选中。

* **[!UICONTROL 标记帖子]**&#x200B;如果选中此项，则允许成员将他人的主题或评论标记为不合适。 默认为未选中。

* **[!UICONTROL 标记原因列]**&#x200B;表如果选中此项，则允许成员从下拉列表中选择其标记主题或评论为不适当的原因。 默认为未选中。

* **[!UICONTROL 自定义标记原]**&#x200B;因如果选中此项，则允许成员输入自己将主题或评论标记为不适当的原因。 默认为未选中。

* **[!UICONTROL 审核阈]**&#x200B;值输入在通知审核者之前，主题或评论必须由成员标出的次数。 默认值为1（一次）。

* **[!UICONTROL 标记限]**&#x200B;制输入主题或评论在公共视图中隐藏之前必须标记的次数。 如果设置为-1，则标记的主题或评论从不在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认为5。

### 标记字段选项卡 {#tag-field-tab}

在“标 **[!UICONTROL 记字段]** ”选项卡下，可能应用的标记（如果允许）会根据所选的命名空间 **[!UICONTROL 来限制]** 。

* **[!UICONTROL 允许的命]**&#x200B;名空间如果 `Allow Tagging` 在“设置”选项卡下选 **中** ，则“相关”。 可应用的标记仅限于选定的命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）和“包括所有标记”。 默认值为“无”选中，这意味着允许所有命名空间。

* **[!UICONTROL 建议限]**&#x200B;制输入要作为建议显示给发布到论坛的成员的标记数。 值- **** 1表示无限制。 默认值为0。

### “排序设置”选项卡 {#sort-settings-tab}

在“排序 **[!UICONTROL 设置”选项卡下]** ，指定显示已发布注释时的排序方式。

* **[!UICONTROL 排序依据]**&#x200B;检查所有允许的排序选择： `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Default is `Newest, Oldest, Last Updated`.

* **[!UICONTROL 设置为默认]**&#x200B;下拉选项，以选择一个选中的排序选项作为默认值显示。 Default is `Newest`.

* **[!UICONTROL 选择Analytics Sorting Down的时间选项]**，选择其中一个 `All, Last 24 Hours, Last 7 Days, Last 30 Days`。 Default is `All`.

## 网站访客体验 {#site-visitor-experience}

### 创建构思 {#creating-idea}

与所有社区功能一样，如果未登录，站点访问者只能阅读想法和查看其他意见（通过评论和投票／喜欢）。

登录后，会员可能会创建新想法。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交构思之前，成员可以保存草稿。

通过选择按 `Save as Draft` 钮，将保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在选项卡中查看保存的草 `My Drafts` 稿时，选择 `Read More` 以重新进入编辑模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供反馈 {#providing-feedback}

构思发布后，其他成员可以登录，打开构思( `Read More`)并像其他想法一样，从而增加投票数并发表评论。

![chlimage_1-35](assets/chlimage_1-35.png)

### 附加信息 {#additional-information}

有关详细信息，请参阅面向开发 [人员的Idemation Essentials](ideation.md) （构思基本工具）页面。

有关审核已发布的主题和评论，请参阅审核 [用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅 [标记用户生成的内容](tag-ugc.md)。
