---
title: 社区通知
seo-title: Communities Notifications
description: AEM Communities有显示已登录社区成员感兴趣事件的通知
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%

---

# 社区通知 {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Communities提供了通知部分，其中显示已登录社区成员感兴趣的事件。

通知类似于 [活动](essentials-activities.md) 和 [订阅](subscriptions.md) 因为

* 成员发布内容
* 选择跟随另一成员的成员
* 成员选择遵循特定主题、文章和其他内容线程

通知与活动和订阅的区别在于

* 指向通知部分的链接始终显示在社区站点的标题中
   * 活动需要 [活动流函数](functions.md#activity-stream-function) 包含在社区站点的结构中
   * 订阅需要 [电子邮件的配置](email.md)
* 通知的实施是通过可扩展的可插拔渠道
   * 活动仅在Web上可用
   * 订阅仅使用电子邮件提供

截至社区 [FP1](deploy-communities.md#latestfeaturepack)，则可用的通知渠道为

* 使用 `Notifications` 链接
* 电子邮件渠道，在正确配置电子邮件时可用

未来的渠道包括移动设备和台式机。

### 要求 {#requirements}

**配置电子邮件**

必须配置电子邮件，才能使电子邮件渠道正常运行通知。

有关设置电子邮件的说明，请参阅 [配置电子邮件](analytics.md).

**启用关注**

必须配置组件才能启用以下功能。 允许遵循的功能包括 [博客](blog-feature.md), [论坛](forum.md), [问题解答](working-with-qna.md), [日历](calendar.md), [文件库](file-library.md)和 [评论](comments.md).

请注意

* 社区中使用的组件 [网站模板](sites.md) 和 [组模板](tools-groups.md) 可能已配置为允许执行以下操作

* 成员配置文件已配置为允许其他成员跟踪

## 以下通知 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

的 **关注** 按钮提供了跟踪活动、订阅和/或通知条目的方法。 每次 **关注** 按钮时，可以打开或关闭选定内容。 的 `Email Subscriptions` 仅在配置后才存在选择。

如果选择了以下任何方法，则按钮的文本将更改为 **关注**. 为方便起见，可以选择 `Unfollow All` 以关闭所有方法。

的 **关注** 按钮

* 查看其他成员的配置文件时
* 在主功能页面上，如论坛、QnA和博客
   * 遵循该常规功能的所有活动
* 对于特定条目，如论坛主题、问题解答问题或博客文章
   * 跟踪该特定条目的所有活动

## 管理通知设置 {#managing-notification-settings}

通过从“通知”页面中选择“通知设置”链接，每个成员都可以管理通知的接收方式。

始终启用Web渠道。

![chlimage_1-255](assets/chlimage_1-255.png)

电子邮件渠道，依赖于正确 [电子邮件的配置](email.md)，提供与Web渠道相同的设置。

默认情况下，电子邮件渠道处于关闭状态。

![chlimage_1-256](assets/chlimage_1-256.png)

它可能由成员打开，但仍取决于是否配置了电子邮件。

![chlimage_1-257](assets/chlimage_1-257.png)

## 查看通知 {#viewing-notifications}

### Web通知 {#web-notifications}

A [向导创建的社区站点](sites-console.md) 现在包含指向的链接 `Notifications` 功能。 与消息不同，会为每个社区站点创建通知，而在站点创建过程中必须启用消息。

访问已发布的网站时，选择 `Notifications` 链接将显示该成员的所有通知。

![chlimage_1-258](assets/chlimage_1-258.png)

### 电子邮件通知 {#email-notifications}

启用电子邮件渠道后，成员会收到一封电子邮件，其中包含指向Web上内容的链接。

![chlimage_1-259](assets/chlimage_1-259.png)
