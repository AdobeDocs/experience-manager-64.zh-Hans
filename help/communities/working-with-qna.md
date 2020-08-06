---
title: 问题与答案论坛功能
seo-title: 问题与答案论坛功能
description: 将QnA论坛功能添加到页面
seo-description: 将QnA论坛功能添加到页面
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# 问题与答案论坛功能 {#q-a-forum-feature}

## 简介 {#introduction}

问题与答案(QnA)论坛功能为社区成员提供了一个可提问和回答问题的区域：

* 创建新问题
* 内联图像（支持拖放）
* 视图和回答问题
* 搜索问题
* 帮助审核QnA内容
* 确定最佳答案
* 将QnA问题从一页移到另一页

文档的本节介绍

* 将QnA论坛功能添加到AEM站点
* 组件的配置设 `QnA`置

## 将问题与答案论坛添加到页面 {#adding-a-q-a-forum-to-a-page}

要在创作 `QnA` 模式下将组件添加到页面，请使用组件浏览器 `Communities / QnA` 在应显示问题与答案论坛的页面上查找并将其拖动到相应位置。

有关必要的信息，请访 [问社区组件基础](basics.md)。

当包 [含所需的客户端库](qna-essentials.md#essentials-for-client-side) ，组件的显示 `QnA` 方式如下：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置问题与答案 {#configuring-qna}

选择要访问的 `QnA` 已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### “设置”选项卡 {#settings-tab}

在“设 **[!UICONTROL 置]** ”选项卡下，指定主题（问题）和答复（答案）的设置：

* **[!UICONTROL 每页主题]**&#x200B;定义每页显示的问题／帖子数。 默认值为10。

* **[!UICONTROL 已审核]**&#x200B;如果选中，则发布主题和评论之前必须获得批准，然后才能在发布站点上显示这些主题和评论。 默认为未选中。

* **[!UICONTROL 关闭]**&#x200B;如果选中，则论坛将不会显示新问题和评论。 默认为未选中。

* **[!UICONTROL 富文本编]**&#x200B;辑器如果选中，则主题和注释可以输入标记。 默认为未选中。

* **[!UICONTROL 允许标记]**&#x200B;如果选中，允许成员向其帖子中添加标记标签(请参 **[!UICONTROL 阅标记字段]** 选项卡)。 默认为未选中。

* **[!UICONTROL 允许文件上]**&#x200B;载如果选中，允许将文件附件添加到问题或评论中。 默认为未选中。

* **[!UICONTROL 最大文件大小]**&#x200B;仅在 
`Allow File Uploads` 的双曲余切值。 此字段将限制已上载文件的大小（以字节为单位）。 默认值为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**&#x200B;仅在 
`Allow File Uploads` 的双曲余切值。 以逗号分隔的文件扩展名列表，以“点”分隔。 例如： .jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 仅当选中“允许文件]**&#x200B;上传”时，最大附加图像文件大小才相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许以]**&#x200B;下如果选中，则为论坛帖子提供以下功能，允许成员 [收到](notifications.md) 新帖子的通知。 默认为未选中。

* **[!UICONTROL 允许固]**&#x200B;定如果选中，论坛主题可能被固定到主题列表的顶部。 默认为未选中。

* **[!UICONTROL 允许电子邮件订阅]**&#x200B;如果选中此选项，则允许成员通过电子邮件(订阅)通知[新帖子](subscriptions.md)。 需要 `Allow Following` 检查并配置电 [子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 允许回复]**&#x200B;如果选中，则允许回复发布到问题的评论。 默认为未选中。

* **[!UICONTROL 允许用户删除评论和主题]**&#x200B;如果选中，允许成员删除他们发布的评论和问题。 默认为未选中。

* **[!UICONTROL 允许投票]**&#x200B;如果选中，则在问题中包含投票功能。 默认为未选中。

* **[!UICONTROL 将选定答案移至顶部]**&#x200B;如果选中，则显示的第一个答案为选定答案。 选中默认值。

* **[!UICONTROL 显示标记]**&#x200B;如果选中，则使用会员的博 [客条目](implementing-scoring.md) ，显示已获得和已分配的标记。 默认为未选中。

* **[!UICONTROL 如果选中]**“允许特色内容”，则可以将该想法标识为特 [色内容](featured.md)。 默认为未选中。

#### “用户审核”选项卡 {#user-moderation-tab}

在“用 **[!UICONTROL 户审核]** ”选项卡下，指定如何管理已发布的主题（问题）和答案（用户生成的内容）。 有关详细信息，请参 [阅调节用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝答]**&#x200B;案如果选中，则允许受信任的成员审核者拒绝发布的答案，并阻止答案显示在公共问答论坛中。 默认为未选中。

* **[!UICONTROL 关闭／重新打开主]**&#x200B;题如果选中，受信任的成员审核者可以关闭问题（主题）以进一步编辑和回答，也可以重新打开问题。 默认为未选中。

* **[!UICONTROL 移动主题]**&#x200B;如果选中，允许发布端版主移动问题。 默认为未选中。

* **[!UICONTROL 标记帖子]**&#x200B;如果选中，允许成员将其他人的问题或答案标记为不恰当。 默认为未选中。

* **[!UICONTROL 标记原因列表]**&#x200B;如果选中，允许成员从下拉式列表中选择其标记问题或答案为不适当的理由。 默认为未选中。

* **[!UICONTROL 自定义标志原]**&#x200B;因如果选中，允许成员输入自己将问题或答案标记为不合适的原因。 默认为未选中。

* **[!UICONTROL 审核阈]**&#x200B;值输入在通知审核者之前，成员必须标记问题或答案的次数。 默认值为1（一次）。

* **[!UICONTROL 标记]**&#x200B;限制输入在对公共视图隐藏问题或答案之前必须标记的次数。 如果设置为-1，则标记的问题或答案永远不会隐藏在公共视图中。 否则，此数字必须大于或等于仲裁阈值。 默认值为5。

#### 标记字段选项卡 {#tag-field-tab}

在“标 **[!UICONTROL 记”字段]** (Tag field)选项卡下 **[!UICONTROL ，根据所选的命名空间，在“设置”(Settings)选项卡下允许的情况下，]** 可以应用的标记会受到限制。

* **[!UICONTROL 允许的命名空间]**&#x200B;相关(如果 
`Allow Tagging` 选项卡 **中** 。 可应用的标记仅限于所选命名空间类别内的标记。 命名空间的列表包括“标准标记”(默认命名空间)和“包括所有标记”。 默认值为“无”(none checked)，这意味着允许所有命名空间。

* **[!UICONTROL 建议限]**&#x200B;制输入要作为建议显示给论坛的成员发布的标记数。 值 
`-1` 意味着没有限制。 默认值为0。

#### “排序设置”选项卡 {#sort-settings-tab}

在“排 **[!UICONTROL 序设置]** ”选项卡下，指定显示已发布注释时的排序方式。

* **[!UICONTROL 排序依据]**&#x200B;检查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Default is `Newest, Oldest, Last Updated`.

* **[!UICONTROL 设置为默]**&#x200B;认下拉选项，选择一个选中的排序选项作为默认选项显示。 默认为 
`Newest`。

* **[!UICONTROL 选择分析排序的时间]**&#x200B;选项下拉以选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Default is `All`.

## 站点访客体验 {#site-visitor-experience}

### 确定答案 {#identifying-answers}

一个答案可以使用按钮标记为正确或有用的 `Select Answer` 答案。 将某个问题标记为“已回答”后，直到使用按钮取消选择第一个答案，才能选择其他 `Unmark Chosen Answer`答案。

一旦选择为可行答案，就可能使用按钮取消选 `Unmark Chosen Answer` 择它。

一旦将某个答案选为可行的答案，问题解答主页 `Answered`上的问题主题旁边将显示问题的指示。

### 版主和管理员 {#moderators-and-administrators}

当登录用户具有版主或管理员权限时，他们可以执行组件配置所允许的审核任务，而不管问题或答案的作者是谁。

他们还能够识别答案。

### 成员 {#members}

站点访客登录后，根据配置，可能会

* 发布新问题
* 编辑或删除他们创作的问题
* 还可以标记其他人的问题或答案
* 可能确定他们创作的问题的答案

### 匿名 {#anonymous}

未登录的网站访客只能阅读已发布的问题和答案，如果支持，可翻译这些问题和答案，但不得添加问题和答案，也不得标记其他人的帖子。

## 附加信息 {#additional-information}

有关更多信息，请参 [阅适用于开发](qna-essentials.md) 人员的QnA Essentials页。

有关审核已发布的主题和评论，请参 [阅审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参 [阅标记用户生成的内容](tag-ugc.md)。
