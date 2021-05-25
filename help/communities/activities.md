---
title: 活动流功能
seo-title: 活动流功能
description: 已登录社区成员的活动
seo-description: 已登录社区成员的活动
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# 活动流功能{#activity-streams-feature}

## 简介 {#introduction}

已登录社区成员的活动（如向论坛或博客发布）被收集到流中，该流可通过配置`Activity Streams`组件以各种方式过滤和显示。

跟踪功能为社区成员关注感兴趣的帖子或关注其他社区成员的活动添加了另一种活动视图。

此文档部分描述

* 将活动流组件添加到AEM站点
* 活动流组件的配置设置

## 向页面{#adding-activity-streams-to-a-page}添加活动流

如果需要在创作模式下向页面添加`Activity Streams`组件，请使用组件浏览器找到

* `Communities / Activity Streams`

并将其拖动到应显示活动流的页面上的位置。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](essentials-activities.md#essentials-for-client-side)时，将显示`Activity Streams`组件：

![chlimage_1-195](assets/chlimage_1-195.png)

## 配置活动流{#configuring-activity-streams}

选择要访问的已放置的`Activity Streams`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-196](assets/chlimage_1-196.png)

在&#x200B;**[!UICONTROL 用户活动]**&#x200B;选项卡下，指定要显示的活动：

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 最大活]**
动数要显示的活动数
* **[!UICONTROL 流资源]**
路径将留空默认为社区站点或社区组。流资源路径可标识活动源。 默认值为空。
* **[!UICONTROL 显示用户活]**
动选中“查看”，“活动”页面将包含一个选项卡，其中根据当前成员在社区中生成的活动筛选活动。默认选中。
* **[!UICONTROL 显示所有活]**
动视图如果选中此选项，则活动页面将包含一个选项卡，其中包含在社区中生成且当前成员有权访问的所有活动。默认选中。
* **[!UICONTROL 显示在]**
后视图如果选中此选项，活动页面将包含一个选项卡，根据当前成员正在跟踪的活动筛选活动。默认选中。

## 查看{#following-view}之后

必须配置组件才能启用以下功能。 允许以下功能： [blog](blog-feature.md)、[论坛](forum.md)、[QnA](working-with-qna.md)、[日历](calendar.md)、[filelibrary](file-library.md)和[评论](comments.md)。

![chlimage_1-198](assets/chlimage_1-198.png)

**Follow**&#x200B;按钮提供了一种方法，可以跟踪作为活动、[通知](notifications.md)和/或[订阅](subscriptions.md)的条目。 每次选择&#x200B;**Follow**&#x200B;按钮时，都可以打开或关闭选定内容。 `Email Subscriptions`选项仅在配置后才存在。

如果选择了以下任何方法，则按钮的文本将变为&#x200B;**Following**。 为方便起见，可以选择`Unfollow All`以关闭所有方法。

将显示&#x200B;**Follow**&#x200B;按钮：

* 查看其他成员的配置文件时
* 在主功能页面上，如论坛、QnA和博客
   * 遵循该常规功能的所有活动

* 对于特定条目，如论坛主题、问题解答问题或博客文章
   * 跟踪该特定条目的所有活动

## 附加信息 {#additional-information}

有关更多信息，请参阅面向开发人员的[Activity Streams Essentials](essentials-activities.md)页面。
