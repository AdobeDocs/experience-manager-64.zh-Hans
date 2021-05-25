---
title: 社区通知
seo-title: 社区通知
description: AEM Communities有显示已登录社区成员感兴趣事件的通知
seo-description: AEM Communities有显示已登录社区成员感兴趣事件的通知
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Administrator
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 社区通知{#communities-notifications}

## 概述 {#overview}

AEM Communities提供了通知部分，其中显示已登录社区成员感兴趣的事件。

通知与[活动](essentials-activities.md)和[订阅](subscriptions.md)类似，因为它们可能来自

* 成员发布内容
* 选择跟随另一成员的成员
* 成员选择遵循特定主题、文章和其他内容线程

通知与活动和订阅的区别在于

* 指向通知部分的链接始终显示在社区站点的标题中
   * 活动要求将[活动流函数](functions.md#activity-stream-function)包含在社区站点的结构中
   * 订阅需要[配置电子邮件](email.md)
* 通知的实施是通过可扩展的可插拔渠道
   * 活动仅在Web上可用
   * 订阅仅通过电子邮件提供

从社区[FP1](deploy-communities.md#latestfeaturepack)开始，可用的通知渠道有

* 使用`Notifications`链接访问的Web渠道
* 电子邮件渠道，在正确配置电子邮件时可用

未来的渠道包括移动设备和台式机。

### 要求 {#requirements}

**配置电子邮件**

必须配置电子邮件，才能使电子邮件渠道正常运行通知。

有关设置电子邮件的说明，请参阅[配置电子邮件](analytics.md)。

**启用关注**

必须配置组件才能启用以下功能。 允许以下功能： [blog](blog-feature.md)、[论坛](forum.md)、[QnA](working-with-qna.md)、[日历](calendar.md)、[filelibrary](file-library.md)和[评论](comments.md)。

请注意

* 社区[站点模板](sites.md)和[组模板](tools-groups.md)中使用的组件可能已配置为允许以下

* 成员配置文件已配置为允许其他成员跟踪

## 以下{#notifications-from-following}的通知

![chlimage_1-254](assets/chlimage_1-254.png)

**Follow**&#x200B;按钮提供了作为活动、订阅和/或通知跟踪条目的方法。 每次选择&#x200B;**Follow**&#x200B;按钮时，都可以打开或关闭选定内容。 `Email Subscriptions`选项仅在配置后才存在。

如果选择了以下任何方法，则按钮的文本将变为&#x200B;**Following**。 为方便起见，可以选择`Unfollow All`以关闭所有方法。

将显示&#x200B;**Follow**&#x200B;按钮

* 查看其他成员的配置文件时
* 在主功能页面上，如论坛、QnA和博客
   * 遵循该常规功能的所有活动
* 对于特定条目，如论坛主题、问题解答问题或博客文章
   * 跟踪该特定条目的所有活动

## 管理通知设置{#managing-notification-settings}

通过从“通知”页面中选择“通知设置”链接，每个成员都可以管理通知的接收方式。

始终启用Web渠道。

![chlimage_1-255](assets/chlimage_1-255.png)

电子邮件渠道依赖于电子邮件](email.md)的正确[配置，它提供的设置与Web渠道的设置相同。

默认情况下，电子邮件渠道处于关闭状态。

![chlimage_1-256](assets/chlimage_1-256.png)

它可能由成员打开，但仍取决于是否配置了电子邮件。

![chlimage_1-257](assets/chlimage_1-257.png)

## 查看通知 {#viewing-notifications}

### Web通知{#web-notifications}

现在，创建的[向导社区站点](sites-console.md)包含一个指向横幅上方站点标题栏中`Notifications`功能的链接。 与消息不同，会为每个社区站点创建通知，而在站点创建过程中必须启用消息。

访问已发布的站点时，选择`Notifications`链接将显示该成员的所有通知。

![chlimage_1-258](assets/chlimage_1-258.png)

### 电子邮件通知{#email-notifications}

启用电子邮件渠道后，成员会收到一封电子邮件，其中包含指向Web上内容的链接。

![chlimage_1-259](assets/chlimage_1-259.png)
