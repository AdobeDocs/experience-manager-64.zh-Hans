---
title: 社区通知
seo-title: 社区通知
description: AEM Communities有通知，显示已登录社区成员感兴趣的事件
seo-description: AEM Communities有通知，显示已登录社区成员感兴趣的事件
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# 社区通知 {#communities-notifications}

## 概述 {#overview}

AEM Communities提供通知部分，其中显示已登录社区成员感兴趣的事件。

通知与活动 [和](essentials-activities.md)[订阅](subscriptions.md) 类似，因为它们可能来自

* 成员发布内容
* 选择跟随另一个成员的成员
* 成员选择遵循特定主题、文章和其他内容线程

通知与活动和订阅的区别在于

* 指向通知部分的链接始终显示在社区站点的标题中
   * 活动需要 [将活动流函](functions.md#activity-stream-function) 数包含在社区站点的结构中
   * 订阅需 [要配置电子邮件](email.md)
* 通知的实现是通过可扩展的可插拔渠道
   * 活动仅在Web上可用
   * 订阅仅可使用电子邮件

从Communities [FP1开始](deploy-communities.md#latestfeaturepack)，可用的通知渠道

* Web渠道，使用链接访 `Notifications` 问
* 电子邮件渠道，在正确配置电子邮件时可用

未来的渠道是移动和桌面。

### 要求 {#requirements}

**配置电子邮件**

必须配置电子邮件，以便电子邮件渠道通知正常工作。

有关设置电子邮件的说明，请参阅 [配置电子邮件](analytics.md)。

**启用跟踪**

必须配置组件以启用以下功能。 支持以下功能：博 [客](blog-feature.md)、论 [坛](forum.md)、QnA [、](working-with-qna.md)日历 [、、](calendar.md)、、 [](file-library.md)[](comments.md)、、和标。

请注意，

* 在社区站点模 [板和组](sites.md)[模板中使用](tools-groups.md) 的组件，可能已配置为允许以下

* 成员用户档案已配置为允许其他成员遵循

## 来自以下的通知 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

“跟 **踪** ”按钮提供了以活动、订阅和／或通知形式跟踪条目的方法。 每次选 **择** “跟随”按钮时，都可以打开或关闭选择。 仅 `Email Subscriptions` 在配置后才显示选择。

如果选择了以下任何方法，则按钮的文本将变为“以 **下”**。 为方便起见，可以选择 `Unfollow All` 关闭所有方法。

将显 **示** “跟随”按钮

* 查看其他成员的用户档案
* 在主功能页面上，如论坛、问题与解答和博客
   * 遵循该一般功能的所有活动
* 对于特定条目，如论坛主题、问题与答案问题或博客文章
   * 遵循该特定条目的所有活动

## 管理通知设置 {#managing-notification-settings}

通过从“通知”页面选择“通知设置”链接，每个成员都可以管理接收通知的方式。

始终启用Web渠道。

![chlimage_1-255](assets/chlimage_1-255.png)

电子邮件渠道依赖于电 [子邮件的正确配](email.md)置，它提供的设置与Web渠道的设置相同。

电子邮件渠道默认为关闭状态。

![chlimage_1-256](assets/chlimage_1-256.png)

成员可以打开它，但仍取决于配置电子邮件。

![chlimage_1-257](assets/chlimage_1-257.png)

## 查看通知 {#viewing-notifications}

### Web通知 {#web-notifications}

向导 [创建的社区站点](sites-console.md) ，现在在横幅上 `Notifications` 方的站点标题栏中包含指向该功能的链接。 与消息不同，每个社区站点都会创建通知，而站点创建过程中必须启用消息。

访问已发布的站点时，选择链 `Notifications` 接将显示该成员的所有通知。

![chlimage_1-258](assets/chlimage_1-258.png)

### 电子邮件通知 {#email-notifications}

启用电子邮件渠道后，成员会收到一封电子邮件，其中包含指向Web上内容的链接。

![chlimage_1-259](assets/chlimage_1-259.png)

