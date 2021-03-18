---
title: 报表控制台
seo-title: 报表控制台
description: 了解如何访问报告
seo-description: 了解如何访问报告
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: 管理员
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 报表控制台{#reports-console}

## 概述 {#overview}

对于AEM Communities，有各种报表可以通过多种方式从作者环境访问。

一般而言，各种报告包括：

* [任务报](#assignments-report) 告 — 针对支 [持社区](overview.md#enablement-community)，提供学员分配进度的概览，包括在实施SCORM标准时的关联得分
* [视图报](#views-report) 告 — 提供按社区成员和任何社区站点站点访客的视图图表
* [帖子报告](#posts-report)  — 提供按社区成员到任何社区站点的各种类型帖子的图表

启用[Adobe Analytics](sites-console.md#analytics)时，报告将包括一段时间内每个启用资源的视图、播放、评论和评级数

表格报表可以以.csv格式导出，以便后续处理。

## 报告控制台{#reporting-consoles}

### 社区站点{#reports-for-community-sites}的报告

* 从全局导航：**[!UICONTROL 导航>社区>报告]**
* 从
   * **[!UICONTROL 指定报表]**
      * 为选定的社区站点、用户或组以及分配生成报告
   * **[!UICONTROL 发布报表]**
      * 为所选社区站点、内容类型和时间段生成报告
   * **[!UICONTROL 查看次数报表]**
      * 为所选社区站点、内容类型和时间段生成报告
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Enablement Resources和学习路径报告{#reports-for-enablement-resources-and-learning-paths}

* 从全局导航：**[!UICONTROL 导航>社区>资源]**
* 选择现有的教育社区站点
   * 选择&#x200B;**[!UICONTROL 报表]**&#x200B;图标以生成涵盖所有启用资源的报表
   * 选择支持学习路径
   * 选择&#x200B;**[!UICONTROL 报表]**&#x200B;图标以生成报表
      * 包含的支持资源
      * 分配给学习路径的学员
* 这些报告提供：
   * 表数据，可下载为CSV
      * 识别学员
      * 他们的地位
      * 是指派还是通过目录访问
      * 所作评论的数量
      * 给定星级

有关详细信息，请参阅“资源”控制台的[报告部分](resources.md#report)。

## 指定报表 {#assignments-report}

“任务”控制台允许按Enablement Community站点、用户或用户组以及任务分配筛选报表。

报告提供了有关其进展情况的信息以及提供的任何评论或评级。

![chlimage_1-157](assets/chlimage_1-157.png)

选择报表的条件：

* **[!UICONTROL 站]**
点选择教育社区站点
* **[!UICONTROL 用户或组]**
   * 选择“用户”为一个学员生成报告
   * 选择“组”以为一组学员生成报告
隧道服务将从发布环境访问成员和成员组
* **[!UICONTROL 分]**
配从分配给选定学员的教育资源中进行选择

选择&#x200B;**[!UICONTROL 生成]**&#x200B;以创建报表：

![chlimage_1-158](assets/chlimage_1-158.png)

## 查看次数报表 {#views-report}

“视图”控制台允许在指定时间段内按社区功能在页面视图上生成报表。

![chlimage_1-159](assets/chlimage_1-159.png)

选择报表的条件：

* **[!UICONTROL 站]**
点选择社区站点
* **[!UICONTROL 内容]**
类型可以选择所有内容或选择站点上存在的功能之一
* 时间范围
选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择&#x200B;**[!UICONTROL 生成]**&#x200B;以创建报表：

![chlimage_1-160](assets/chlimage_1-160.png)

## 发布报表 {#posts-report}

帖子控制台允许在指定时间段内生成针对社区功能的帖子数的报告。

![chlimage_1-161](assets/chlimage_1-161.png)

选择报表的条件：

* **[!UICONTROL 站]**
点选择社区站点
* **[!UICONTROL 内容]**
类型可以选择所有内容或选择站点上存在的功能之一
* 时间范围
选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择&#x200B;**[!UICONTROL 生成]**&#x200B;以创建报表：

![chlimage_1-162](assets/chlimage_1-162.png)

## 疑难解答 {#troubleshooting}

### 未列出社区站点{#no-community-sites-listed}

如果未列出社区站点，请确保已为站点启用Adobe Analytics。 如果选择分配报告，请确保分配功能位于社区站点的结构中。
