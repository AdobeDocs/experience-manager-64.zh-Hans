---
title: 内容分析
seo-title: Content Insight
description: 内容分析使用Web分析和SEO推荐提供有关页面性能的信息
seo-description: Content Insight provides information about page performance using web analytics and SEO recommendation
uuid: 32f5b37c-2a82-462a-9f0a-c19bed46e198
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 60f980fd-049e-43c1-8b5d-60a8279b357a
exl-id: 54ec1b84-bee2-4c1f-acbc-8e6bd0d76c87
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%

---

# 内容分析{#content-insight}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

内容分析使用Web分析和SEO推荐提供有关页面性能的信息。 使用内容分析可决定如何修改页面，或了解以前的更改对性能有何影响。 对于您创作的每个页面，都可以打开内容分析来分析该页面。

![chlimage_1-311](assets/chlimage_1-311.png)

“内容分析”页面的布局会根据您所使用的设备的屏幕尺寸和方向而发生更改。

## 报表数据

“内容分析”页面包含使用Adobe SiteCatalyst、Adobe Target、Adobe Social和BrightEdge数据的报表：

* SiteCatalyst:以下量度的报表可用：

   * 页面查看次数
   * 页面平均逗留时间
   * 源

* 目标：您的页面包含选件的营销活动报表。
* BrightEdge:报告可提高页面对搜索引擎的可见性的页面功能，并推荐应该实施的功能。

请参阅 [为页面打开Analytics和Recommendations](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## 报告期

报表显示您控制的一段时间的数据。 在调整报表时段时，报表会自动刷新该时段的数据。 可视提示指示页面版本发生更改的时间，以便您可以比较每个版本的性能。

您还可以指定报告数据的粒度，例如，您可以查看每日、每周、每月或每年的数据。

请参阅 [更改报告期](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>内容分析报表要求您的管理员将AEM与SiteCatalyst、Target和BrightEdge集成。 请参阅 [与SightCatalyst集成](/help/sites-administering/adobeanalytics.md), [与Adobe Target集成](/help/sites-administering/target.md)和 [与BrightEdge集成](/help/sites-administering/brightedge.md).

## 查看次数报表 {#the-views-report}

查看次数报表包含以下用于评估页面流量的功能：

* 报告时段内某个页面的查看总数。
* 报告时段内查看次数的图表：

   * 查看总数。
   * 独特访客。

![chlimage_1-312](assets/chlimage_1-312.png)

## 页面平均参与量报表 {#the-page-average-engaged-report}

“页面平均参与”报表包含以下用于评估页面有效性的功能：

* 整个报表时段内页面保持打开状态的平均时间。
* 报表时段内页面查看平均长度的图表。

![chlimage_1-313](assets/chlimage_1-313.png)

## 源报表 {#the-sources-report}

“源”报表指示用户如何从搜索引擎结果或使用已知URL导航到页面。

![chlimage_1-314](assets/chlimage_1-314.png)

## 跳出次数报表 {#the-bounces-report}

“跳出次数”报表包含一个图表，其中显示了在选定报告时段内某个页面发生的跳出次数。

![chlimage_1-315](assets/chlimage_1-315.png)

## 促销活动报表 {#the-campaign-activity-report}

对于页面处于活动状态的每个营销活动，都会显示一个名为 *营销活动名称* 活动。 报表显示每个提供了选件的区段的页面展示次数和转化次数。

![chlimage_1-316](assets/chlimage_1-316.png)

## SEO Recommendations报表 {#the-seo-recommendations-report}

SEO Recommendations报表包含页面的BrightEdge分析结果。 报表是页面功能的核对清单，用于指示页面包含和不包含哪些功能，以便使用搜索引擎最大限度地提高可查找性。

利用报表，可创建任务，以便进行改进以提高页面可查找性。 Recommendations表示已为实施建议创建任务。 请参阅 [为SEO Recommendations分配任务](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![chlimage_1-317](assets/chlimage_1-317.png)
