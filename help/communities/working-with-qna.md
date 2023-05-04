---
title: 问答论坛功能
seo-title: Q&A Forum Feature
description: 将QnA论坛功能添加到页面
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---

# 问答论坛功能 {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

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
* 的配置设置 `QnA`组件

## 向页面添加问题与解答论坛 {#adding-a-q-a-forum-to-a-page}

添加 `QnA` 组件添加到创作模式下的页面，可使用组件浏览器找到 `Communities / QnA` 并将其拖动到应显示QnA论坛的页面上。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](qna-essentials.md#essentials-for-client-side) 包含，这是 `QnA` 组件将显示：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置QnA {#configuring-qna}

选择已放置的 `QnA` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### “设置”选项卡 {#settings-tab}

在 **[!UICONTROL 设置]** 选项卡，指定主题（问题）和回复（答案）的设置：

* **[!UICONTROL 每页主题数]**
定义每页显示的问题/帖子数。 默认值为10。

* **[!UICONTROL 已审核]**
如果选中此项，则必须批准发布主题和评论，然后主题和评论才会显示在发布网站上。 默认为未选中。

* **[!UICONTROL 已关闭]**
如果选中，则论坛将不会出现新问题和评论。 默认为未选中。

* **[!UICONTROL 富文本编辑器]**
如果选中，则可以输入带有标记的主题和注释。 默认为未选中。

* **[!UICONTROL 允许标记]**
如果选中此项，则允许成员向其帖子添加标签(请参阅 **[!UICONTROL 标记字段]** 选项卡。 默认为未选中。

* **[!UICONTROL 允许文件上传]**
如果选中，则允许将文件附件添加到问题或评论中。 默认为未选中。

* **[!UICONTROL 最大文件大小]**
仅在 
`Allow File Uploads` 复选框。 此字段将限制已上传文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**
仅在 
`Allow File Uploads` 复选框。 以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许上载未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 最大附加图像文件大小]**
仅当选中允许文件上传时相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许跟踪]**
如果选中此项，则为论坛帖子包含以下功能，以允许成员 [通知](notifications.md) 新职位数量。 默认为未选中。

* **[!UICONTROL 允许固定]**
如果选中，则论坛主题可被固定到主题列表的顶部。 默认为未选中。

* **[!UICONTROL 允许电子邮件订阅]**
如果选中此项，则允许成员通过电子邮件接收新帖子的通知([订阅](subscriptions.md))。 需要 `Allow Following` 要检查和 [已配置电子邮件](email.md). 默认为未选中。

* **[!UICONTROL 允许回复]**
如果选中此项，则允许对发布到问题的评论进行回复。 默认为未选中。

* **[!UICONTROL 允许用户删除评论和主题]**
如果选中，则允许成员删除他们发布的评论和问题。 默认为未选中。

* **[!UICONTROL 允许投票]**
如果选中此项，则包含带有问题的投票功能。 默认为未选中。

* **[!UICONTROL 将选定答案移至顶部]**
如果选中，则显示的第一个答案为选定的答案。 默认选中。

* **[!UICONTROL 显示徽章]**
如果选中，则显示已获取和已分配的 [徽章](implementing-scoring.md) 的博客条目。 默认为未选中。

* **[!UICONTROL 允许特色内容]**
如果选中，则能将构思识别为 [特色内容](featured.md). 默认为未选中。

#### “用户审核”选项卡 {#user-moderation-tab}

在 **[!UICONTROL 用户审核]** 选项卡，指定如何管理已发布的主题（问题）和答案（用户生成的内容）。 有关更多信息，请参阅 [审核用户生成的内容](moderate-ugc.md).

* **[!UICONTROL 拒绝回答]**
如果选中此项，则允许受信任的成员审核者拒绝发布的答案，并阻止该答案出现在公共问答论坛上。 默认为未选中。

* **[!UICONTROL 关闭/重新打开主题]**
如果选中，受信任的成员审核者可以关闭问题（主题）以进一步编辑和回答，也可以重新打开问题。 默认为未选中。

* **[!UICONTROL 移动主题]**
如果选中此项，则允许发布端审核者移动问题。 默认为未选中。

* **[!UICONTROL 标记帖子]**
如果选中，则允许成员将他人的问题或答案标记为不适当。 默认为未选中。

* **[!UICONTROL 标记原因列表]**
如果选中，则允许成员从下拉列表中选择标记问题或答案为不恰当的原因。 默认为未选中。

* **[!UICONTROL 自定义标记原因]**
如果选中，则允许成员输入自己的原因，以标记问题或答案为不适当。 默认为未选中。

* **[!UICONTROL 审核阈值]**
输入在通知审核者之前必须由成员标记问题或答案的次数。 默认值为1（一次）。

* **[!UICONTROL 标记限制]**
输入在将问题或答案隐藏在公共视图中之前必须标记的次数。 如果设置为–1，则标记的问题或答案永远不会在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认值为5。

#### 标记字段选项卡 {#tag-field-tab}

在 **[!UICONTROL 标记字段]** 选项卡，可应用的标记（如果允许） **[!UICONTROL 设置]** 选项卡，具体受到的限制，具体取决于所选的命名空间。

* **[!UICONTROL 允许的命名空间]**
相关条件 
`Allow Tagging` 在 **设置** 选项卡。 可应用的标记仅限于所选命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）以及“包括所有标记”。 默认为“未选中”，这表示允许使用所有命名空间。

* **[!UICONTROL 建议限制]**
输入要作为建议显示给论坛成员的标记数。 值 
`-1` 意味着没有限制。 默认值为0。

#### 排序设置选项卡 {#sort-settings-tab}

在 **[!UICONTROL 排序设置]** 选项卡，指定在显示已发布评论时的排序方式。

* **[!UICONTROL 排序依据]**
检查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 默认为 `Newest, Oldest, Last Updated`.

* **[!UICONTROL 设置为默认值]**
下拉以选择要显示为默认的选中排序选项之一。 默认为 
`Newest`。

* **[!UICONTROL 选择Analytics排序的时间选项]**
下拉以选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. 默认为 `All`.

## 网站访客体验 {#site-visitor-experience}

### 确定答案 {#identifying-answers}

可使用 `Select Answer` 按钮。 将问题标记为已回答后，只有在使用取消选择第一个答案之前，才能选择另一个答案 `Unmark Chosen Answer`按钮。

选择作为可行答案后，可使用 `Unmark Chosen Answer` 按钮。

选择某个答案作为可行的答案后，即表示问题已 `Answered`显示在主QnA页面上问题主题的旁边。

### 审核者和管理员 {#moderators-and-administrators}

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

有关 [问题解答要点](qna-essentials.md) 页面。

有关审核已发布的主题和评论，请参阅 [审核用户生成的内容](moderate-ugc.md).

有关标记已发布的主题和评论，请参阅 [标记用户生成的内容](tag-ugc.md).
