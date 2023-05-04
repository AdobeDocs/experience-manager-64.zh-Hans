---
title: 报表控制台
seo-title: Reports Console
description: 了解如何访问报告
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 6%

---

# 报表控制台 {#reports-console}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

对于AEM Communities，可以通过多种方式从创作环境访问各种报表。

通常，各种报告包括：

* [分配报表](#assignments-report)  — 对于 [启用社区](overview.md#enablement-community)，提供学习者分配进度的概述，包括实施SCORM标准时的关联分数
* [查看报表](#views-report)  — 提供任何社区站点的社区成员和站点访客查看内容的图表
* [帖子报表](#posts-report)  — 提供社区成员向任何社区站点发布的各种类型帖子的图表

When [Adobe Analytics已启用](sites-console.md#analytics)，报表将包括一段时间内每个启用资源的查看次数、播放次数、评论次数和评级

表格报表可以导出为.csv格式，以供后续处理。

## 报表控制台 {#reporting-consoles}

### 社区站点报告 {#reports-for-community-sites}

* 从全局导航： **[!UICONTROL 导航>社区>报表]**
* 选择
   * **[!UICONTROL 指定报表]**
      * 为选定的社区站点、用户或组和分配生成报告
   * **[!UICONTROL 发布报表]**
      * 为选定的社区站点、内容类型和时间段生成报表
   * **[!UICONTROL 查看次数报表]**
      * 为选定的社区站点、内容类型和时间段生成报表
         ![chlimage_1-156](assets/chlimage_1-156.png)

### 有关启用资源和学习路径的报表 {#reports-for-enablement-resources-and-learning-paths}

* 从全局导航： **[!UICONTROL 导航>社区>资源]**
* 选择现有的启用社区站点
   * 选择 **[!UICONTROL 报表]** 图标以生成涵盖所有启用资源的报表
   * 选择启用学习路径
   * 选择 **[!UICONTROL 报表]** 图标为生成报表
      * 包含的支持资源
      * 分配到学习路径的学习者
* 这些报表提供：
   * 表格数据，可下载为CSV格式
      * 识别学习者
      * 他们的状态
      * 通过目录分配或访问
      * 评论次数
      * 给定星级

有关更多详细信息，请参阅 [报表部分](resources.md#report) 的子菜单。

## 指定报表 {#assignments-report}

“工作总揽”控制台允许按启用社区网站、用户或组以及工作总揽过滤报表。

报告提供了有关其进展情况以及提供的任何评论或评级的信息。

![chlimage_1-157](assets/chlimage_1-157.png)

为报表选择标准：

* **[!UICONTROL 网站]**
选择启用社区网站
* **[!UICONTROL 用户或组]**
   * 选择用户以为一个学习者生成报告
   * 选择“组”以为学习者组生成报告隧道服务将从发布环境访问成员和成员组
* **[!UICONTROL 分配]**
从分配给选定学习者的支持资源中进行选择

选择 **[!UICONTROL 生成]** 要创建报表，请执行以下操作：

![chlimage_1-158](assets/chlimage_1-158.png)

## 查看次数报表 {#views-report}

查看次数控制台允许在给定时间段内按社区功能在页面查看次数中生成报表。

![chlimage_1-159](assets/chlimage_1-159.png)

为报表选择标准：

* **[!UICONTROL 网站]**
选择社区站点
* **[!UICONTROL 内容类型]**
可以选择“所有内容”或选择网站上存在的功能之一
* 时间范围选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择 **[!UICONTROL 生成]** 要创建报表，请执行以下操作：

![chlimage_1-160](assets/chlimage_1-160.png)

## 发布报表 {#posts-report}

“帖子”控制台允许在给定时间段内生成有关社区功能的帖子数量的报表。

![chlimage_1-161](assets/chlimage_1-161.png)

为报表选择标准：

* **[!UICONTROL 网站]**
选择社区站点
* **[!UICONTROL 内容类型]**
可以选择“所有内容”或选择网站上存在的功能之一
* 时间范围选择以下选项之一：
   * 过去 7 天
   * 过去 30 天
   * 过去 90 天
   * 去年

选择 **[!UICONTROL 生成]** 要创建报表，请执行以下操作：

![chlimage_1-162](assets/chlimage_1-162.png)

## 疑难解答 {#troubleshooting}

### 未列出社区站点 {#no-community-sites-listed}

如果未列出社区站点，请确保已为站点启用Adobe Analytics。 如果选择分配报告，请确保分配功能在社区站点的结构中。
