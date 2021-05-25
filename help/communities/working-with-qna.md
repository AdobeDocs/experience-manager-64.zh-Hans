---
title: 问答论坛功能
seo-title: 问答论坛功能
description: 将QnA论坛功能添加到页面
seo-description: 将QnA论坛功能添加到页面
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---

# 问答论坛功能{#q-a-forum-feature}

## 简介 {#introduction}

问题与解答(QnA)论坛功能为社区成员提供了一个可提问或回答问题的区域：

* 创建新问题
* 内联图像（支持拖放）
* 查看和回答问题
* 搜索问题
* 帮助审核QnA内容
* 确定最佳答案
* 将问题解答问题从一个页面移动到另一个页面

此文档部分描述

* 将QnA论坛功能添加到AEM网站
* `QnA`组件的配置设置

## 向页面{#adding-a-q-a-forum-to-a-page}添加问题与解答论坛

要在创作模式下将`QnA`组件添加到页面，请使用组件浏览器找到`Communities / QnA`并将其拖动到应显示QnA论坛的页面上。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](qna-essentials.md#essentials-for-client-side)时，将显示`QnA`组件：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置QnA {#configuring-qna}

选择要访问的已放置的`QnA`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### “设置”选项卡{#settings-tab}

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，指定主题（问题）和回复（答案）的设置：

* **[!UICONTROL 每页主]**
题定义每页显示的问题/帖子数。默认值为10。

* ****
已审核如果选中此选项，则必须批准发布主题和评论，然后才能在发布网站上显示这些主题和评论。默认为未选中。

* ****
关闭如果选中此选项，则论坛将不会显示新问题和评论。默认为未选中。

* **[!UICONTROL 富文本编]**
辑器如果选中此选项，则可以输入带有标记的主题和注释。默认为未选中。

* **[!UICONTROL 允许]**
标记如果选中此选项，允许成员向其帖子中添加标记标签(请参阅 **[!UICONTROL 标记]** 字段选项卡)。默认为未选中。

* **[!UICONTROL 允许文]**
件上载如果选中，则允许将文件附件添加到问题或评论中。默认为未选中。

* **[!UICONTROL 最大文件大]**
小仅在 
`Allow File Uploads` 复选框。此字段将限制已上传文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件]**
类型仅在 
`Allow File Uploads` 复选框。以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许上载未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 最大附加图像文件大]**
小仅在选中允许文件上传时相关。上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许]**
关注如果选中此项，则为论坛帖子提供以下功能，以允许成员 [](notifications.md) 获得新帖子。默认为未选中。

* **[!UICONTROL 允许]**
固定如果选中此选项，则论坛主题可能会固定到主题列表的顶部。默认为未选中。

* **[!UICONTROL 允许电子]**
邮件订阅如果选中此选项，则允许会员通过电子邮件([订阅](subscriptions.md))接收新帖子的通知。需要检查`Allow Following`并[电子邮件配置](email.md)。 默认为未选中。

* **[!UICONTROL 允许]**
回复如果选中此选项，则允许回复发布到问题的评论。默认为未选中。

* **[!UICONTROL 允许用户删除评论和主]**
题如果选中此选项，允许成员删除他们发布的评论和问题。默认为未选中。

* **[!UICONTROL 允许]**
投票如果选中，则包含带有问题的投票功能。默认为未选中。

* **[!UICONTROL 将选定答案移至顶]**
部如果选中，则显示的第一个答案为选定答案。默认选中。

* **[!UICONTROL 显示]**
徽章如果选中此项，则使用会员的博 [](implementing-scoring.md) 客条目显示已获得和已分配的徽章。默认为未选中。

* **[!UICONTROL 允许显]**
示特色内容，如果选中此选项，则该创意能够被识别为特 [色内容](featured.md)。默认为未选中。

#### “用户审核”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户审核]**&#x200B;选项卡下，指定如何管理已发布的主题（问题）和答案（用户生成的内容）。 有关更多信息，请参阅[审核用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝]**
答案如果选中此选项，则允许受信任的成员审核者拒绝发布的答案，并阻止该答案出现在公共问答论坛上。默认为未选中。

* **[!UICONTROL 关闭/重新打]**
开主题如果选中此选项，受信任的成员审核者可以关闭问题（主题）以进一步编辑和回答，并可以重新打开问题。默认为未选中。

* **[!UICONTROL 移动]**
主题如果选中此选项，则允许发布端审核者移动问题。默认为未选中。

* **[!UICONTROL 标记]**
帖子如果选中，允许成员将他人的问题或答案标记为不适当。默认为未选中。

* **[!UICONTROL 标记原]**
因列表如果选中，允许成员从下拉列表中选择标记问题或答案为不适当的原因。默认为未选中。

* **[!UICONTROL 自定义标]**
记原因如果选中此选项，则允许成员输入自己将问题或答案标记为不适当的原因。默认为未选中。

* **[!UICONTROL 审核]**
阈值输入在通知审核者之前，必须由成员标记问题或答案的次数。默认值为1（一次）。

* **[!UICONTROL 标记]**
限制输入在将问题或答案隐藏在公共视图中之前必须标记的次数。如果设置为–1，则标记的问题或答案永远不会在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认值为5。

#### 标记字段选项卡{#tag-field-tab}

在&#x200B;**[!UICONTROL 标记字段]**&#x200B;选项卡下，可能应用的标记（如果允许）位于&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，将根据所选的命名空间而受到限制。

* **[!UICONTROL 允许的命]**
名空间相关(如果 
`Allow Tagging` 已在设置选项卡下 **** 选中。可应用的标记仅限于所选命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）以及“包括所有标记”。 默认为“未选中”，这表示允许使用所有命名空间。

* **[!UICONTROL 建议]**
限制输入要作为建议显示给论坛成员的标记数。值 
`-1` 意味着没有限制。默认值为0。

#### 排序设置选项卡{#sort-settings-tab}

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

## 网站访客体验{#site-visitor-experience}

### 确定答案{#identifying-answers}

使用`Select Answer`按钮可将一个答案标记为正确或有用的答案。 将问题标记为已回答后，只有在使用`Unmark Chosen Answer`按钮取消选择第一个答案之前，才能选择另一个答案。

选择某个可行答案后，可使用`Unmark Chosen Answer`按钮取消选择该答案。

选择某个答案作为可行答案后，问题解答主页上的问题主题旁边会显示一个指示，表示问题已`Answered`。

### 审核者和管理员{#moderators-and-administrators}

当登录用户具有审核者或管理员权限时，他们便能够执行组件配置所允许的审核任务，而不管是谁创作了问题或答案。

他们还有能力识别答案。

### 成员 {#members}

网站访客登录后，根据配置，他们可能会

* 发布新问题
* 编辑或删除他们创作的问题
* 还可以标记他人的问题或答案
* 可以确定他们创作的问题的答案

### 匿名 {#anonymous}

未登录的网站访客只能阅读发布的问题和答案，如果受支持，可以翻译，但不得添加问题和答案，也不得标记他人的帖子。

## 附加信息 {#additional-information}

有关更多信息，请参阅面向开发人员的[QnA Essentials](qna-essentials.md)页面。

有关审核已发布的主题和评论，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。
