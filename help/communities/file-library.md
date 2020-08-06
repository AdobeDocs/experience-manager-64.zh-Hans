---
title: 文件库功能
seo-title: 文件库功能
description: “文件库”功能允许登录站点访客上传、管理和下载文件
seo-description: “文件库”功能允许登录站点访客上传、管理和下载文件
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---


# 文件库功能 {#file-library-feature}

## 简介 {#introduction}

文件库功能为登录站点访客（社区成员）提供了一个位置，供他们上传、管理和下载社区站点内的文件。

文档的本节介绍

* 将文件库功能添加到AEM站点
* 组件的配置设 `File Library` 置

## 将文件库添加到页面 {#adding-a-file-library-to-a-page}

要在创作模 `File Library` 式下将组件添加到页面，请找到该组件

* `Communities / File Library`

并将其拖动到页面上的位置。

有关必要的信息，请访 [问社区组件基础](basics.md)。

当包 [含所需的客户端库](essentials-file-library.md#essentials-for-client-side) ，组件的显示 `File Library` 方式如下：

![chlimage_1-430](assets/chlimage_1-430.png)

## 配置文件库 {#configuring-file-library}

选择要访问的 `File Library` 已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### “注释”选项卡 {#comments-tab}

在“注 **[!UICONTROL 释]** ”选项卡下，指定是否显示已上载文件的注释以及如何显示：

* **[!UICONTROL 允许对文件进行注]**&#x200B;释如果选中，则允许对已上载的文件进行注释。 默认为未选中。

* **[!UICONTROL 每页注释]**&#x200B;限制每页显示的注释数以及显示的回复数。 默认为 
**10**.

* **[!UICONTROL 最大文件大]**&#x200B;小此值将限制上传的文件大小。 默认限制为104857600(10 Mb)。

* **[!UICONTROL 最大消息]**&#x200B;长度可输入到文本框中的最大字符数。 默认为4096个字符。

* **[!UICONTROL 允许的文件]**&#x200B;类型以逗号分隔的文件扩展名列表，以“点”分隔。 例如： .jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许指定那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 富文本编辑器]**&#x200B;如果选中此选项，则可以使用标记输入注释。 默认为未选中。

* **[!UICONTROL 删除注]**&#x200B;释如果选中，则允许用户删除自己的注释。 选中默认值。

* **[!UICONTROL 允许标记]**&#x200B;如果选中，则将启用向文件添加标记的功能。 默认为未选中。

* **[!UICONTROL 允许的命名空间]**&#x200B;如果选中“允许标记”，则可用的标记将限于选中的命名空间。 如果未选中任何项，则允许全部选中。 默认为所有命名空间。

* **[!UICONTROL 建议限制]**&#x200B;如果选中“允许标记”，则此设置将限制要显示的建议标记数。 如果设置为-1，则没有限制。 默认值为-1。

* **[!UICONTROL 允许投]**&#x200B;票如果选中，将启用文件的投票功能。 默认为未选中。

* **[!UICONTROL 允许以]**&#x200B;下如果选中此项，请为博客文章加入以下功能，允许成员 [收到](notifications.md) 新帖子的通知。 默认为未选中。

* **[!UICONTROL 允许线程化]**&#x200B;回复如果选中，允许回复已发布的注释。 默认为未选中。

### “用户审核”选项卡 {#user-moderation-tab}

在“用户 **[!UICONTROL 审核]** ”选项卡下，配置审核评论（如果允许进行评论）:

* **[!UICONTROL 预审核如果]**&#x200B;选中此项，则注释必须经过批准，才能显示在发布站点上。 默认为未选中。

* **[!UICONTROL 删除注]**&#x200B;释如果选中，则向发布注释的访客提供删除注释的功能。 选中默认值。

* **[!UICONTROL 拒绝注释]**&#x200B;如果选中，则允许受信任的成员审核者拒绝注释。 默认为未选中。

* **[!UICONTROL 关闭／重新打开注]**&#x200B;释如果选中，允许受信任的成员审核者关闭并重新打开注释。 默认为未选中。

* **[!UICONTROL 标记注]**&#x200B;释如果选中，允许访客将注释标记为不合适。 默认为未选中。

* **[!UICONTROL 标记原因列表]**&#x200B;如果选中，允许访客从下拉式列表中选择其标记评论为不合适的原因。 默认为未选中。

* **[!UICONTROL 自定义标志]**&#x200B;原因如果选中，允许访客输入自己将评论标记为不合适的原因。 默认为未选中。

* **[!UICONTROL 审核阈]**&#x200B;值输入通知审核者之前访客必须标记评论的次数。 默认值为一次(
**1**).

* **[!UICONTROL 标记]**&#x200B;限制输入评论在隐藏到公共视图之前必须标记的次数。 此数字必须大于或等于 
**审核阈值**。 默认值为5。

## 附加信息 {#additional-information}

有关开发人员的详细信息， [请参阅“文件库](essentials-file-library.md) Essentials”页。

有关审核已发布的主题和评论，请参 [阅审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参 [阅标记用户生成的内容](tag-ugc.md)。
