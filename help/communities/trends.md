---
title: 活动趋势
seo-title: Activity Trends
description: 向页面添加社区活动列表组件
seo-description: Adding a Community Activity List component to a page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 5%

---

# 活动趋势 {#activity-trends}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

的 `Community Activity List` 组件提供添加与成员发布的帖子和查看次数以及帖子和内容查看次数有关的趋势信息的功能。

此文档部分描述

* 添加 `Community Activity List` 组件 [社区网站](overview.md#community-sites)

* 的配置设置 `Community Activity List` 组件

## 要求 {#requirement}

的数据 `Community Activity List` 仅当Adobe Analytics获得社区站点的许可和配置时，才可用。

请参阅 [社区功能的Analytics配置](analytics.md).

## 向页面添加社区活动列表 {#adding-a-community-activity-list-to-a-page}

添加 `Community Activity List` 组件到创作模式下的页面，找到组件 `Communities / Community Activity List` 并将其拖动到页面上的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

首次将组件放置在社区站点的页面上时，组件的显示方式如下：

![chlimage_1-227](assets/chlimage_1-227.png)

## 配置社区活动列表  {#configuring-community-activity-list}

选择已放置的 `Community Activity List` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-228](assets/chlimage_1-228.png)

在 **[!UICONTROL 评论]** 选项卡，指定上传文件的注释的显示方式和方式：

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 类型]**

   指定是显示社区成员或用户生成内容(UGC)的数据。

   从
   * `Members`
   * `Content`

   默认为 `Members`.

* **[!UICONTROL 显示标题]**

   要在数据上方显示的描述性标题，如 `Trending Content`.

   默认为无标题。

* **[!UICONTROL 显示数量]**

   要列出的项目数。

   默认值为10。

* **[!UICONTROL 活动类型]**

   选择其中一个
   * `Views`（页面访问量）
   * `Posts`（创建UGC）
   * `Follows`
   * `Likes`

   默认为“视图”。

* **[!UICONTROL 时间段]**

   选择其中一个
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   默认为 `Total`.

* **[!UICONTROL 上下文路径]**

   提供将活动范围限定在网站子集（如特定博客）的功能。

   默认为整个社区站点。

* **[!UICONTROL 成员数量整合]**

   如果未选中（关闭），则只计为顶级帖子。 例如，如果上下文是根页面（默认），则 `Activity Type`of `Posts`将不会显示任何活动，因为无法将内容发布到根页面。 选中此选项后，将包含所有子页面上的计数。

   默认选中。

## 包含4个组件的示例页面 {#example-page-with-components}

**热门访客** 配置：类型=成员，活动类型=视图

**热门参与者** 配置：类型=成员，活动类型=帖子

**热门内容** 配置：类型=内容，活动类型=视图，

**趋势内容** 配置：类型=内容，活动类型=帖子

![chlimage_1-230](assets/chlimage_1-230.png)
