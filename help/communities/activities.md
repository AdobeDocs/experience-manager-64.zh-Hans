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


# 活动流功能 {#activity-streams-feature}

## 简介 {#introduction}

已登录社区成员的活动，例如发布到论坛或博客，被收集到流中，流可以通过组件的配置以各种方式过滤和显 `Activity Streams` 示。

跟踪功能可在社区成员关注感兴趣的帖子或关注其他社区成员的活动时添加另一视图活动。

文档的本节介绍

* 将活动流组件添加到AEM站点
* 活动流组件的配置设置

## 向页面添加活动流 {#adding-activity-streams-to-a-page}

如果希望在创作模式 `Activity Streams` 下将组件添加到页面，请使用组件浏览器查找

* `Communities / Activity Streams`

并将其拖动到应显示活动流的页面上。

有关必要的信息，请访 [问社区组件基础](basics.md)。

当包 [含所需的客户端库](essentials-activities.md#essentials-for-client-side) ，组件的显示 `Activity Streams` 方式如下：

![chlimage_1-195](assets/chlimage_1-195.png)

## 配置活动流 {#configuring-activity-streams}

选择要访问的 `Activity Streams` 已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-196](assets/chlimage_1-196.png)

在“用 **[!UICONTROL 户活动]** ”选项卡下，指定要显示的活动:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 最大活动数]**&#x200B;要显示的活动数
* **[!UICONTROL 流资源路径]**&#x200B;保留为空将默认为社区站点或社区组。 流资源路径标识活动源。 默认值为空。
* **[!UICONTROL 显示用户活动]**&#x200B;视图过滤器符（如果选中）,活动页面将包含一个选项卡，该选项卡基于当前成员在社区中生成的活动符。 选中默认值。
* **[!UICONTROL 显示所有活动]**&#x200B;视图如果选中，活动页面将包含一个选项卡，其中包含当前成员有权访问的社区中生成的所有活动。 选中默认值。
* **[!UICONTROL 显示以下视图]**&#x200B;如果选中，则活动页面将包含一个选项卡，其中基于当前成员所遵循的过滤器活动。 选中默认值。

## 跟踪视图 {#following-view}

必须配置组件以启用以下功能。 支持以下功能：博 [客](blog-feature.md)、论 [坛](forum.md)、QnA [、](working-with-qna.md)日历 [、、](calendar.md)、、 [](file-library.md)[](comments.md)、、和标。

![chlimage_1-198](assets/chlimage_1-198.png)

“跟 **踪** ”按钮提供了以活动、通 [知和/](notifications.md)或订阅形式跟 [踪条目](subscriptions.md)。 每次选 **择** “跟随”按钮时，都可以打开或关闭选择。 仅 `Email Subscriptions` 在配置后才显示选择。

如果选择了以下任何方法，则按钮的文本将变为“以 **下”**。 为方便起见，可以选择 `Unfollow All` 关闭所有方法。

将显 **示** “关注”按钮：

* 查看其他成员的用户档案
* 在主功能页面上，如论坛、问题与解答和博客
   * 遵循该一般功能的所有活动

* 对于特定条目，如论坛主题、问题与答案问题或博客文章
   * 遵循该特定条目的所有活动

## 附加信息 {#additional-information}

有关更多信息，请参阅开发 [人员的“活动流](essentials-activities.md) Essentials”页。
