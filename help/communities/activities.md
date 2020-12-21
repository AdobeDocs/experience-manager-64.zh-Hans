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
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# 活动流功能{#activity-streams-feature}

## 简介 {#introduction}

已登录社区成员的活动，如发布到论坛或博客，被收集到流中，流可以通过配置`Activity Streams`组件以各种方式过滤和显示。

跟踪功能可在社区成员关注感兴趣的帖子或关注其他社区成员的活动时添加另一视图活动。

文档的本节介绍

* 将活动流组件添加到AEM站点
* 活动流组件的配置设置

## 向页面{#adding-activity-streams-to-a-page}添加活动流

如果希望在创作模式下向页面添加`Activity Streams`组件，请使用组件浏览器查找

* `Communities / Activity Streams`

并将其拖动到应显示活动流的页面上。

有关必要的信息，请访问[社区组件基础知识](basics.md)。

当包含[必需的客户端库](essentials-activities.md#essentials-for-client-side)时，`Activity Streams`组件的显示方式如下：

![chlimage_1-195](assets/chlimage_1-195.png)

## 配置活动流{#configuring-activity-streams}

选择要访问的已放置`Activity Streams`组件，然后选择打开编辑对话框的`Configure`图标。

![chlimage_1-196](assets/chlimage_1-196.png)

在&#x200B;**[!UICONTROL 用户活动]**&#x200B;选项卡下，指定要显示的活动:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 活动的最]**
大数量要显示的活动数
* **[!UICONTROL 流资源]**
路径保留为空将默认为社区站点或社区组。流资源路径标识活动源。 默认值为空。
* **[!UICONTROL 显示用户活动]**
视图选中后，活动页面将包含一个选项卡，该选项卡基于当前成员在社区中生成的过滤器活动。选中默认值。
* **[!UICONTROL 显示所有活动]**
视图如果选中，活动页面将包含一个选项卡，其中包含当前成员有权访问的社区中生成的所有活动。选中默认值。
* **[!UICONTROL 显示以]**
下视图如果选中，活动页面将包含一个选项卡，根据当前成员所遵循的过滤器活动显示这些选项卡。选中默认值。

## 以下视图{#following-view}

必须配置组件以启用以下功能。 允许以下功能：[blog](blog-feature.md)、[论坛](forum.md)、[QnA](working-with-qna.md)、[日历](calendar.md)、[文件库](file-library.md)和[注释](comments.md)。

![chlimage_1-198](assets/chlimage_1-198.png)

**“跟进”按钮提供了一种方法，用于跟踪作为活动、[通知](notifications.md)和／或[订阅](subscriptions.md)的条目。**&#x200B;每次选择&#x200B;**“跟随”按钮时，都可以打开或关闭选择。**`Email Subscriptions`选择仅在配置后出现。

如果选择了以下任何方法，则按钮的文本将变为&#x200B;**Following**。 为方便起见，可以选择`Unfollow All`以关闭所有方法。

将显示&#x200B;**Follow**&#x200B;按钮：

* 查看其他成员的用户档案
* 在主功能页面上，如论坛、问题与解答和博客
   * 遵循该一般功能的所有活动

* 对于特定条目，如论坛主题、问题与答案问题或博客文章
   * 遵循该特定条目的所有活动

## 附加信息 {#additional-information}

有关开发人员的详细信息，请参阅[活动流基础工具](essentials-activities.md)页。
