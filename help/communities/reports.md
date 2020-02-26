---
title: 报告控制台
seo-title: 报告控制台
description: 了解如何访问报告
seo-description: 了解如何访问报告
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# 报告控制台 {#reports-console}

## 概述 {#overview}

对于AEM Communities，可以通过多种方式从创作环境访问各种报告。

一般而言，各种报告包括：

* [任务报告](#assignments-report) -对于启用 [社区](overview.md#enablement-community)，提供学员分配进度的概述，包括在实施SCORM标准时的关联得分
* [查看报告](#views-report) -提供按社区成员和任何社区站点的站点访客查看内容的图表
* [帖子报告](#posts-report) -提供社区成员向任何社区站点发布的各种类型帖子的图表

启用 [Adobe Analytics后](sites-console.md#analytics)，报告将包括一段时间内每个支持资源的查看次数、播放次数、评论数和评级数

表格式报告可以以。csv格式导出，以便后续处理。

## 报告控制台 {#reporting-consoles}

### 社区站点报告 {#reports-for-community-sites}

* 从全局导航：“导 **[!UICONTROL 航”>“社区”>“报告”]**
* 从
   * **[!UICONTROL 指定报表]**
      * 为选定的社区站点、用户或用户组以及分配生成报告
   * **[!UICONTROL 发布报表]**
      * 为选定的社区站点、内容类型和时间段生成报告
   * **[!UICONTROL 查看次数报表]**
      * 为选定的社区站点、内容类型和时间段生成报告
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Enablement Resources和学习路径报告 {#reports-for-enablement-resources-and-learning-paths}

* 从全局导航：“导 **[!UICONTROL 航”>“社区”>“资源”]**
* 选择现有的支持社区站点
   * 选择“ **[!UICONTROL 报告]** ”图标以生成涵盖所有启用资源的报告
   * 选择支持学习路径
   * 选择“ **[!UICONTROL 报告]** ”图标以生成
      * 包含的支持资源
      * 分配给学习路径的学员数
* 这些报告提供：
   * 表数据，可下载为CSV
      * 识别学员
      * 他们的状态
      * 是分配还是通过目录访问
      * 评论数
      * 给定星级

有关详细信息，请参 [阅资源控制台](resources.md#report) 的“报告”部分。

## 指定报表 {#assignments-report}

“任务”控制台允许按启用社区站点、用户或用户组以及任务分配筛选报告。

该报告提供了有关其进度的信息以及提供的任何评论或评级。

![chlimage_1-157](assets/chlimage_1-157.png)

选择报表的条件：

* **[!UICONTROL 站点]**&#x200B;选择一个支持社区站点
* **[!UICONTROL 用户或组]**
   * 选择“用户”以为一个学员生成报告
   * 选择“组”以为一组学员生成报告通道服务将从发布环境访问成员和成员组
* **[!UICONTROL 分配]**&#x200B;从分配给选定学员的启用资源中进行选择

选择 **[!UICONTROL 生成]** ，以创建报表：

![chlimage_1-158](assets/chlimage_1-158.png)

## 查看次数报表 {#views-report}

“查看”控制台允许在给定时间段内按社区功能在页面查看时生成报告。

![chlimage_1-159](assets/chlimage_1-159.png)

选择报表的条件：

* **[!UICONTROL 站点]**&#x200B;选择社区站点
* **[!UICONTROL 内容类]**&#x200B;型可以选择所有内容或选择站点上存在的功能之一
* 时间范围选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择 **[!UICONTROL 生成]** ，以创建报表：

![chlimage_1-160](assets/chlimage_1-160.png)

## 发布报表 {#posts-report}

“帖子”控制台允许在指定时间段内生成有关社区功能的帖子数的报告。

![chlimage_1-161](assets/chlimage_1-161.png)

选择报表的条件：

* **[!UICONTROL 站点]**&#x200B;选择社区站点
* **[!UICONTROL 内容类]**&#x200B;型可以选择所有内容或选择站点上存在的功能之一
* 时间范围选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择 **[!UICONTROL 生成]** ，以创建报表：

![chlimage_1-162](assets/chlimage_1-162.png)

## 疑难解答 {#troubleshooting}

### 未列出社区站点 {#no-community-sites-listed}

如果未列出社区站点，请确保已为站点启用Adobe Analytics。 如果选择任务报告，请确保任务功能位于社区站点的结构中。
