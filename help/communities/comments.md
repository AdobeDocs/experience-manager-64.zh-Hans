---
title: 使用注释
seo-title: Using Comments
description: “评论”功能允许登录网站的访客分享其意见和知识
seo-description: Comments feature lets signed-in site visitors share their opinions and knowledge
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
exl-id: 8ad5ce3e-c5dd-48d7-8812-43172eda36cc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 5%

---

# 使用注释 {#using-comments}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

评论功能用于允许已登录的网站访客（成员）分享他们对网站内容的意见和知识。 此功能通常已在其他功能中提供，但可以添加到任何网站。

此文档部分描述

* 添加 `Comments`到页面
* 的配置设置 `Comments`组件

>[!NOTE]
>
>不支持匿名发布评论。 网站访客必须注册（成为会员）并登录以参与。

## 向页面添加注释 {#adding-comments-to-a-page}

添加 `Comments`组件添加到创作模式下的页面，可使用组件浏览器找到

* `Communities / Comments`

并将其拖动到页面上的适当位置，例如相对于用户可评论的功能的位置，或者只是位于页面底部的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](essentials-comments.md#essentials-for-client-side) 包含，这是 `Comments`组件。

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>只有一个 `Comments`组件可能存在于页面上。 请注意，一些社区功能已经包含评论，例如博客、日历、论坛、QnA和评论。

## 配置注释 {#configuring-comments}

选择已放置的 `Comments` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![配置](assets/configure.png) ![评论设置](assets/commentssettings.png)

### “注释”选项卡 {#comments-tab}

在 **[!UICONTROL 评论]** 选项卡，指定访客如何输入评论。

* **[!UICONTROL 允许回复]**

   如果选中，则允许成员回复现有评论。 默认为未选中。

* **[!UICONTROL 每页的评论数]**

   限制每页显示的评论数以及显示的回复数。 默认值为10。

* **[!UICONTROL 允许文件上传]**

   如果选中，则将显示用于上传文件的选项，其中包含文本输入框。 默认为未选中。

* **[!UICONTROL 最大文件大小]**

   仅当选中允许文件上传时相关。 此值将限制上传的文件大小。 默认限制为10 MB。

* **[!UICONTROL 最大消息长度]**

   可在文本框中输入的最大字符数。 默认为4096个字符。

* **[!UICONTROL 允许的文件类型]**

   仅当选中允许文件上传时相关。 带“圆点”分隔符的文件扩展名列表（以逗号分隔）。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许指定未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 富文本编辑器]**

   如果选中，则可以输入带有标记的注释。 默认为未选中。

* **[!UICONTROL 允许投票]**

   如果选中，则将显示上下投票选项和文本输入框。 默认为未选中。

* **[!UICONTROL 允许关注]**

   如果选中此项，则允许成员关注评论。 默认为未选中。

* **[!UICONTROL 显示徽章]**

   如果选中，则允许显示已获奖和已授予的徽章。 默认为未选中。

### “用户审核”选项卡 {#user-moderation-tab}

在 **[!UICONTROL 用户审核]** 选项卡，指定如何管理已发布的评论。 有关更多信息，请参阅 [审核用户生成的内容](moderate-ugc.md).

* **[!UICONTROL 预审]**

   如果选中此项，则必须批准注释，然后注释才会显示在发布网站上。 默认为未选中。

* **[!UICONTROL 删除评论]**

   如果选中，则发布评论的成员将能够删除评论。 默认为未选中。

* **[!UICONTROL 拒绝评论]**

   如果选中，则允许审核者拒绝评论。 默认为未选中。

* **[!UICONTROL 关闭/重新打开注释]**

   如果选中，则允许审核者关闭并重新打开评论。 默认为未选中。

* **[!UICONTROL 标记评论]**

   如果选中，则允许成员将评论标记为不适当。 默认为未选中。

* **[!UICONTROL 标记原因列表]**

   如果选中，允许成员从下拉列表中选择其标记评论不恰当的原因。 默认为未选中。

* **[!UICONTROL 自定义标记原因]**

   如果选中，则允许成员输入自己将评论标记为不适当的原因。 默认为未选中。

* **[!UICONTROL 审核阈值]**

   输入在通知审核者之前必须由成员标记评论的次数。 默认值为一次(1)。

* **[!UICONTROL 标记限制]**

   输入在注释在公共视图中隐藏之前必须标记的次数。 此数字必须大于或等于 **[!UICONTROL 审核阈值]**. 默认值为5。

### 排序设置选项卡 {#sort-settings-tab}

在 **[!UICONTROL 排序设置]** 选项卡，指定在显示已发布评论时的排序方式。

* **[!UICONTROL 排序字段]**

   下拉以选择其中一个 `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`或 `Most Liked`.

* **[!UICONTROL 排序顺序]**

   下拉以选择其中一个 `Ascending` 或 `Descending`.

### 更改为自定义注释类型 {#changing-to-a-custom-comment-type}

通过更改注释资源类型，注释系统将不再使用默认值生成注释的实例，而是使用开发人员自定义（扩展）的实例。

在自定义资源类型已知后，输入 [设计模式](../../help/sites-authoring/default-components-designmode.md) 并双击已放置的 `Comments` 组件来打开一个包含其他选项卡的对话框。

在 **[!UICONTROL 资源类型]** 选项卡，为的新实例指定自定义resourceType `Comments or Voting`组件：

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL 评论资源类型]**

   导航到扩展的resourceType `comment`组件（单个注释）。 例如，`/apps/social/commons/components/hbs/comments/comment`

   此资源将识别访客发布评论时创建的UGC的resourceType。

* **[!UICONTROL 投票资源类型]**

   导航到扩展的resourceType `voting`组件。 例如，`/apps/social/components/hbs/voting`

   此资源将确定访客发布投票时创建的UGC的资源类型。

* **[!UICONTROL 注释系统资源类型]**

   导航到扩展的resourceType `comments`组件（注释系统）。 留空，除非页面模板 [动态包含](scf.md#add-or-include-a-communities-component) 注释系统，而不是作为资源（注释节点）添加到页面中。 阅读 [{{include}} 助手](handlebars-helpers.md#include).

## 网站访客体验 {#site-visitor-experience}

### 审核者和管理员 {#moderators-and-administrators}

当登录用户具有审核者或管理员权限时，他们便能够执行组件配置所允许的审核任务，而无论评论的创作者是谁。

### 成员 {#members}

网站访客登录后，根据配置，他们可能会

* 发布新评论
* 编辑其自己的评论
* 删除其自己的评论
* 标记他人的评论

### 匿名 {#anonymous}

未登录的网站访客只能阅读已发布的评论，如果支持，可翻译这些评论，但不得添加评论或标记其他人的评论。

## 附加信息 {#additional-information}

有关 [评论要点](essentials-comments.md) 页面。

有关审核已发布的评论，请参阅 [审核用户生成的内容](moderate-ugc.md).

有关已发布评论的翻译，请参阅 [翻译用户生成的内容](translate-ugc.md).
