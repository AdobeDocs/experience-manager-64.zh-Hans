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


# 问题与答案论坛功能{#q-a-forum-feature}

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
* `QnA`组件的配置设置

## 将问题与答案论坛添加到页面{#adding-a-q-a-forum-to-a-page}

要在创作模式下将`QnA`组件添加到页面，请使用组件浏览器找到`Communities / QnA`并将它拖动到应显示QnA论坛的页面上。

有关必要的信息，请访问[社区组件基础知识](basics.md)。

当包含[必需的客户端库](qna-essentials.md#essentials-for-client-side)时，`QnA`组件的显示方式如下：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置QnA {#configuring-qna}

选择要访问的已放置`QnA`组件，然后选择打开编辑对话框的`Configure`图标。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### 设置选项卡{#settings-tab}

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，指定主题（问题）和答复（答案）的设置：

* **[!UICONTROL 每页主]**
题定义每页显示的问题／帖子数。默认值为10。

* **[!UICONTROL 审核]**
如果选中，则发布主题和评论必须获得批准，然后才能在发布站点上显示它们。默认为未选中。

* **[!UICONTROL 关闭]**
如果选中，则论坛将不会显示新问题和评论。默认为未选中。

* **[!UICONTROL 富文本编]**
辑器如果选中，则主题和注释可以输入标记。默认为未选中。

* **[!UICONTROL 允许]**
标记如果选中，允许成员向其帖子中添加标记标签(请参 **[!UICONTROL 阅标]** 记字段选项卡)。默认为未选中。

* **[!UICONTROL 允许文]**
件上传如果选中，允许将文件附件添加到问题或评论。默认为未选中。

* **[!UICONTROL 最大文件大]**
小仅在 
`Allow File Uploads` 的双曲余切值。此字段将限制已上载文件的大小（以字节为单位）。 默认值为104857600(10 Mb)。

* **[!UICONTROL 允许的文件]**
类型仅在 
`Allow File Uploads` 的双曲余切值。以逗号分隔的文件扩展名列表，以“点”分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 最大附加图像文]**
件大小仅在选中“允许文件上传”时相关。上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许]**
遵循如果选中，则为论坛帖子提供以下功能，允许成员 [](notifications.md) 通知新帖子。默认为未选中。

* **[!UICONTROL 允]**
许固定如果选中，论坛主题可能被固定到主题列表的顶部。默认为未选中。

* **[!UICONTROL 允许电]**
子邮件订阅如果选中，允许成员通过电子邮件(订阅)通知[新帖子](subscriptions.md)。需要检查`Allow Following`并配置[电子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 允]**
许回复如果选中，允许回复发布到问题的评论。默认为未选中。

* **[!UICONTROL 允许用户删除评论和主]**
题如果选中，允许成员删除他们发布的评论和问题。默认为未选中。

* **[!UICONTROL 允许]**
投票如果选中，则在问题中包含投票功能。默认为未选中。

* **[!UICONTROL 将选定答案移至顶]**
部如果选中，显示的第一个答案为选定答案。选中默认值。

* **[!UICONTROL 显示]**
标记如果选中，则使用成员的博 [](implementing-scoring.md) 客条目显示已获得和已分配的标记。默认为未选中。

* **[!UICONTROL 如果选]**
中“允许使用特色内容”，则可以将该想法标识为 [特色内容](featured.md)。默认为未选中。

#### “用户协调”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户协调]**&#x200B;选项卡下，指定如何管理已发布的主题（问题）和答案（用户生成的内容）。 有关详细信息，请参阅[协调用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝]**
答案如果选中，信任的成员审核者将可以拒绝发布的答案，并阻止答案显示在公共问答论坛中。默认为未选中。

* **[!UICONTROL 关闭／重新打]**
开主题如果选中，受信任的成员审核者可以关闭问题（主题）以进一步编辑和回答，也可以重新打开问题。默认为未选中。

* **[!UICONTROL 移动]**
主题如果选中，允许发布端版主移动问题。默认为未选中。

* **[!UICONTROL 标记]**
帖子如果选中，允许成员将其他人的问题或答案标记为不合适。默认为未选中。

* **[!UICONTROL 标记原]**
因列表如果选中，允许成员从下拉列表中选择其标记问题或答案为不适当的原因。默认为未选中。

* **[!UICONTROL 自定义标]**
志原因如果选中，允许成员输入自己将问题或答案标记为不合适的原因。默认为未选中。

* **[!UICONTROL 审核]**
阈值输入在通知审核者之前，成员必须标记问题或答案的次数。默认值为1（一次）。

* **[!UICONTROL 标记]**
限制输入在对公共视图隐藏问题或答案之前必须标记的次数。如果设置为-1，则标记的问题或答案永远不会隐藏在公共视图中。 否则，此数字必须大于或等于仲裁阈值。 默认值为5。

#### 标记字段选项卡{#tag-field-tab}

在&#x200B;**[!UICONTROL 标记字段]**&#x200B;选项卡下，如果允许在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下应用的标记会根据所选命名空间进行限制。

* **[!UICONTROL 允许的命]**
名空间相关(如果 
`Allow Tagging` 在“设置”选项卡 **** 下检查。可应用的标记仅限于所选命名空间类别内的标记。 命名空间的列表包括“标准标记”(默认命名空间)和“包括所有标记”。 默认值为“无”(none checked)，这意味着允许所有命名空间。

* **[!UICONTROL 建议]**
限制输入要作为建议显示给论坛的成员发布的标记数。值 
`-1` 意味着没有限制。默认值为0。

#### 排序设置选项卡{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序设置]**&#x200B;选项卡下，指定显示已发布注释时的排序方式。

* **[!UICONTROL 排序依]**
据检查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 默认值为`Newest, Oldest, Last Updated`。

* **[!UICONTROL 设置为]**
DefaultPulldown以选择一个选中的排序选项作为默认值显示。默认为 
`Newest`。

* **[!UICONTROL 选择分析排序的时间]**
选项下拉以选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.默认值为`All`。

## 站点访客体验{#site-visitor-experience}

### 确定答案{#identifying-answers}

使用`Select Answer`按钮可以将一个答案标记为正确或有用的答案。 将问题标为“已回答”后，直到使用`Unmark Chosen Answer`按钮取消选择第一个答案，才能选择其他答案。

一旦选择为可行答案，则可使用`Unmark Chosen Answer`按钮取消选择该答案。

选择答案作为可行答案后，问题解答主页上的问题主题旁边将显示问题`Answered`的指示。

### 版主和管理员{#moderators-and-administrators}

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

有关开发人员的详细信息，请参阅[ QnA Essentials](qna-essentials.md)页面。

有关已发布主题和注释的审核，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。
