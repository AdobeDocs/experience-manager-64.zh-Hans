---
title: 文件库功能
seo-title: 文件库功能
description: “文件库”功能允许登录站点的访客上传、管理和下载文件
seo-description: “文件库”功能允许登录站点的访客上传、管理和下载文件
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---

# 文件库功能{#file-library-feature}

## 简介 {#introduction}

文件库功能为已登录的站点访客（社区成员）上传、管理和下载社区站点中的文件提供了一个位置。

此文档部分描述

* 将文件库功能添加到AEM站点
* `File Library`组件的配置设置

## 将文件库添加到页面{#adding-a-file-library-to-a-page}

要在创作模式下向页面添加`File Library`组件，请找到该组件

* `Communities / File Library`

并将其拖动到页面上的位置。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](essentials-file-library.md#essentials-for-client-side)时，将显示`File Library`组件：

![chlimage_1-430](assets/chlimage_1-430.png)

## 配置文件库{#configuring-file-library}

选择要访问的已放置的`File Library`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### “注释”选项卡{#comments-tab}

在&#x200B;**[!UICONTROL 注释]**&#x200B;选项卡下，指定上载文件的注释是否以及显示方式：

* **[!UICONTROL 允许对文件进行注]**
释如果选中此选项，则允许对已上传的文件进行注释。默认为未选中。

* **[!UICONTROL 每页评]**
论数限制每页显示的评论数以及显示的回复数。默认为 
**10**.

* **[!UICONTROL 最大文]**
件大小此值将限制上载的文件大小。默认限制为104857600(10 Mb)。

* **[!UICONTROL 最大消]**
息长度可输入到文本框中的最大字符数。默认为4096个字符。

* **[!UICONTROL 允许的文]**
件类型以逗号分隔的文件扩展名列表，其中“点”分隔符以逗号分隔。例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则将不允许指定未指定的文件类型。 默认值未指定，以便允许使用所有文件类型。

* **[!UICONTROL 富文本编]**
辑器如果选中此选项，则可以输入带有标记的注释。默认为未选中。

* **[!UICONTROL 删除]**
注释如果选中，则允许用户删除其自己的注释。默认选中。

* **[!UICONTROL 允许]**
标记如果选中此选项，则将启用向文件添加标记的功能。默认为未选中。

* **[!UICONTROL 允许]**
的命名空间如果选中允许标记，则可用的标记将限制为选中的命名空间。如果未选中“无”，则允许使用所有选项。 默认值是所有命名空间。

* **[!UICONTROL 建议]**
限制如果选中允许标记，则此设置会限制要显示的建议标记数。如果设置为–1，则没有限制。 默认值为–1。

* **[!UICONTROL 允许]**
投票如果选中此选项，则将启用文件的投票能力。默认为未选中。

* **[!UICONTROL 允许]**
关注如果选中此项，请为博客文章包含以下功能，以便向成员通 [](notifications.md) 知新帖子。默认为未选中。

* **[!UICONTROL 允许线程]**
化回复如果选中，则允许回复已发布的评论。默认为未选中。

### “用户审核”选项卡{#user-moderation-tab}

在&#x200B;**[!UICONTROL 用户审核]**&#x200B;选项卡下，配置评论的审核（如果允许评论）：

* **[!UICONTROL 预审核]**
如果选中此选项，则必须批准评论，然后才能在发布网站上显示评论。默认为未选中。

* **[!UICONTROL 删]**
除评论如果选中此项，则发布评论的访客将能够删除评论。默认选中。

* **[!UICONTROL 拒绝]**
评论如果选中，则允许受信任的成员审核者拒绝评论。默认为未选中。

* **[!UICONTROL 关闭/重新打开]**
评论如果选中此选项，则允许受信任的成员审核者关闭并重新打开评论。默认为未选中。

* **[!UICONTROL 标记]**
评论如果选中，允许访客将评论标记为不适当。默认为未选中。

* **[!UICONTROL 标记原]**
因列表如果选中，允许访客从下拉列表中选择标记评论不恰当的原因。默认为未选中。

* **[!UICONTROL 自定义标]**
记原因如果选中此选项，则允许访客输入自己将评论标记为不适当的原因。默认为未选中。

* **[!UICONTROL 审核]**
阈值输入在通知审核者之前访客必须标记评论的次数。默认为一次(
**1**)。

* **[!UICONTROL 标记]**
限制输入在注释在公共视图中隐藏之前必须标记的次数。此数字必须大于或等于 
**审核阈值**。默认值为5。

## 附加信息 {#additional-information}

有关更多信息，请参阅面向开发人员的[File Library Essentials](essentials-file-library.md)页面。

有关审核已发布的主题和评论，请参阅[审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参阅[标记用户生成的内容](tag-ugc.md)。
