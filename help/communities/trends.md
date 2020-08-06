---
title: 活动趋势
seo-title: 活动趋势
description: 将社区活动列表组件添加到页面
seo-description: 将社区活动列表组件添加到页面
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 4%

---


# 活动趋势 {#activity-trends}

## 简介 {#introduction}

该 `Community Activity List` 组件能够按成员以及帖子和视图内容添加有关帖子和视图的趋势信息。

文档的本节介绍

* 将组件 `Community Activity List` 添加到社 [区站点](overview.md#community-sites)

* 组件的配置设 `Community Activity List` 置

## 要求 {#requirement}

只有在Adobe Analytics `Community Activity List` 获得社区站点的许可和配置后，才能获得社区站点的数据。

请参 [阅社区分析配置功能](analytics.md)。

## 将社区活动列表添加到页面 {#adding-a-community-activity-list-to-a-page}

要在创作 `Community Activity List` 模式下将组件添加到页面，请找到该组 `Communities / Community Activity List` 件，然后将其拖动到页面上的相应位置。

有关必要的信息，请访 [问社区组件基础](basics.md)。

首次放置到社区站点的页面时，组件的显示方式如下：

![chlimage_1-227](assets/chlimage_1-227.png)

## 配置社区活动列表  {#configuring-community-activity-list}

选择要访问的 `Community Activity List` 已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-228](assets/chlimage_1-228.png)

在“注 **[!UICONTROL 释]** ”选项卡下，指定是否显示已上载文件的注释以及如何显示：

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 类型]**

   指定是显示有关社区成员还是用户生成的内容(UGC)的数据。

   从
   * `Members`
   * `Content`

   Default is `Members`.

* **[!UICONTROL 显示标题]**

   要在数据上方显示的描述性标题，如 `Trending Content`。

   默认为无标题。

* **[!UICONTROL 显示数量]**

   要列表的项目数。

   默认值为10。

* **[!UICONTROL 活动类型]**

   选择其中一个
   * `Views`（页面访问）
   * `Posts`（创建UGC）
   * `Follows`
   * `Likes`

   默认为视图。

* **[!UICONTROL 时间段]**

   选择其中一个
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   Default is `Total`.

* **[!UICONTROL 上下文路径]**

   提供将活动范围限定到站点的子集（如特定博客）的功能。

   默认为整个社区站点。

* **[!UICONTROL 成员数量整合]**

   取消选中（关闭）时，只计数顶级帖子。 例如，如果上下文是根页面（默认），则 `Activity Type`其 `Posts`中的活动将不显示任何，因为无法将内容发布到根页面。 选中后，将包括所有子页面上的计数。

   选中默认值。

## 包含4个组件的示例页面 {#example-page-with-components}

**顶级访客** 配置： 类型=成员，活动类型=视图

**顶级参与者** 配置： 类型=成员，活动类型=帖子

**主要内容** 配置： 类型=内容，活动类型=视图,

**趋势内容** 配置： 类型=内容，活动类型=帖子

![chlimage_1-230](assets/chlimage_1-230.png)
