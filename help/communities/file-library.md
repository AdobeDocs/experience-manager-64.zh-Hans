---
title: 文件库功能
seo-title: File Library Feature
description: “文件库”功能允许登录站点的访客上传、管理和下载文件
seo-description: The File Library feature lets signed-in site visitors upload, manage, and download files
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# 文件库功能 {#file-library-feature}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

文件库功能为已登录的站点访客（社区成员）上传、管理和下载社区站点中的文件提供了一个位置。

此文档部分描述

* 将文件库功能添加到AEM站点
* 的配置设置 `File Library` 组件

## 将文件库添加到页面 {#adding-a-file-library-to-a-page}

添加 `File Library` 组件到创作模式下的页面，找到组件

* `Communities / File Library`

并将其拖动到页面上的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](essentials-file-library.md#essentials-for-client-side) 包含，这是 `File Library` 组件将显示：

![chlimage_1-430](assets/chlimage_1-430.png)

## 配置文件库 {#configuring-file-library}

选择已放置的 `File Library` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### “注释”选项卡 {#comments-tab}

在 **[!UICONTROL 评论]** 选项卡，指定上传文件的注释的显示方式和方式：

* **[!UICONTROL 允许对文件进行注释]**
如果选中此项，则允许对已上传的文件进行注释。 默认为未选中。

* **[!UICONTROL 每页注释数]**
限制每页显示的评论数以及显示的回复数。 默认为 
**10**.

* **[!UICONTROL 最大文件大小]**
此值将限制上传的文件大小。 默认限制为104857600(10 Mb)。

* **[!UICONTROL 最大消息长度]**
可在文本框中输入的最大字符数。 默认为4096个字符。

* **[!UICONTROL 允许的文件类型]**
以逗号分隔的文件扩展名列表，其中带有“圆点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许指定未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 富文本编辑器]**
如果选中，则可以输入带有标记的注释。 默认为未选中。

* **[!UICONTROL 删除注释]**
如果选中，则允许用户删除其自己的评论。 默认选中。

* **[!UICONTROL 允许标记]**
如果选中此项，则将启用向文件添加标记的功能。 默认为未选中。

* **[!UICONTROL 允许的命名空间]**
如果选中允许标记，则可用的标记将限制为选中的命名空间。 如果未选中“无”，则允许使用所有选项。 默认值是所有命名空间。

* **[!UICONTROL 建议限制]**
如果选中允许标记，则此设置将限制要显示的建议标记数。 如果设置为–1，则没有限制。 默认值为–1。

* **[!UICONTROL 允许投票]**
如果选中，则将启用选民文件的功能。 默认为未选中。

* **[!UICONTROL 允许跟踪]**
如果选中此项，请为博客文章包含以下功能，该功能允许成员 [通知](notifications.md) 新职位数量。 默认为未选中。

* **[!UICONTROL 允许线程化回复]**
如果选中此项，则允许对已发布的评论进行回复。 默认为未选中。

### “用户审核”选项卡 {#user-moderation-tab}

在 **[!UICONTROL 用户审核]** 选项卡，配置评论审核（如果允许评论）：

* **[!UICONTROL 审核前]**
如果选中此项，则必须批准注释，然后注释才会显示在发布网站上。 默认为未选中。

* **[!UICONTROL 删除注释]**
如果选中，则发布评论的访客将能够删除该评论。 默认选中。

* **[!UICONTROL 拒绝评论]**
如果选中，则允许受信任的成员审核者拒绝评论。 默认为未选中。

* **[!UICONTROL 关闭/重新打开评论]**
如果选中，则允许受信任的成员审核者关闭并重新打开注释。 默认为未选中。

* **[!UICONTROL 标记评论]**
如果选中此选项，则允许访客将评论标记为不适当。 默认为未选中。

* **[!UICONTROL 标记原因列表]**
如果选中，则允许访客从下拉列表中选择将评论标记为不适当的原因。 默认为未选中。

* **[!UICONTROL 自定义标记原因]**
如果选中，则允许访客输入自己将评论标记为不适当的原因。 默认为未选中。

* **[!UICONTROL 审核阈值]**
输入在通知审核者之前，访客必须标记评论的次数。 默认为一次(
**1**).

* **[!UICONTROL 标记限制]**
输入在注释在公共视图中隐藏之前必须标记的次数。 此数字必须大于或等于 
**审核阈值**. 默认值为5。

## 附加信息 {#additional-information}

有关 [文件库要点](essentials-file-library.md) 页面。

有关审核已发布的主题和评论，请参阅 [审核用户生成的内容](moderate-ugc.md).

有关标记已发布的主题和评论，请参阅 [标记用户生成的内容](tag-ugc.md).
