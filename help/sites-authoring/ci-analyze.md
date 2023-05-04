---
title: 分析页面性能
seo-title: Analyzing Page Performance
description: 使用“内容分析”页面可分析您正在创作的页面的性能
seo-description: Use the Content Insight page to analyze the performance of the page that you are authoring
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
exl-id: dc24edaf-ca1d-4a6b-a2dc-86677267e18d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# 分析页面性能{#analyzing-page-performance}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

打开 [内容分析](/help/sites-authoring/content-insights.md) 页面来分析您正在创作的页面的性能。 配置报告期以集中分析。

## 为页面打开Analytics和Recommendations {#opening-analytics-and-recommendations-for-a-page}

请按照以下步骤查看页面的Analytics和Recommendations:

1. 导航到要分析的页面。
1. 在工具栏中，单击或点按 **Analytics和Recommendations**.

   >[!NOTE]
   >
   >仅当您将AEM配置为 [与Adobe Analytics集成](/help/sites-administering/adobeanalytics-connect.md).

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## 更改报告期 {#changing-the-reporting-period}

更改分析报表的以下与时间相关的方面：

* 要报告的时间段。
* 数据的粒度。

用于更改报表中与时间相关的方面的工具显示在“内容分析”页面的顶部。 ![chlimage_1-249](assets/chlimage_1-249.png)

### 更改报告期 {#changing-the-reporting-period-1}

更改“内容分析”页面的报告时段，以便将对页面活动的分析集中到特定时间段。 在更改报表时间段时，报表会自动刷新。 时间范围上的阴影区域表示报告时段。 时间范围中的日期从左到右递增。

![chlimage_1-250](assets/chlimage_1-250.png)

要更改“内容分析”页面的报告期，请执行以下操作：

1. 如果时间范围未显示在页面顶部，请单击或点按切换时间范围图标。

   ![](do-not-localize/chlimage_1-22.png)

1. 要更改报告时段的开始日期，请将显示在阴影区域左侧的圆圈拖动到所需的开始日期。

   如果看不到阴影区域的左侧，请使用滚动条将其显示到视图中。

1. 要更改报告时段的结束日期，请将显示在阴影区域右侧的圆圈拖动到所需的结束日期。

### 更改报告时段的粒度 {#changing-the-granularity-of-the-reporting-period}

更改报表中每个数据点跨越的时间量。 例如，选择“周”粒度后，“查看次数”报表上的每个数据点都表示一周的查看次数。

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

粒度会影响根据时间绘制数据的报表，例如“查看次数”和“页面平均参与分钟数”报表。 粒度还会影响时间范围的规模。

1. 如果未显示粒度控件，请单击或点按“切换粒度”图标。

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. 单击或点按所需的粒度。 选择后，报表会自动更新以反映粒度。

## 为SEO Recommendations分配任务 {#assigning-tasks-for-seo-recommendations}

使用SEO Recommendations报表创建任务，以提高页面对搜索引擎的可见性。 对于报表中没有复选标记的每个推荐，您可以创建一个任务，将其分配给用户以执行所需的工作。

![chlimage_1-252](assets/chlimage_1-252.png)

SEO推荐的状态指示何时创建了任务但尚未完成。

![chlimage_1-253](assets/chlimage_1-253.png)

创建任务后，该任务会显示在用户的任务列表中。 有关任务的信息，请参阅 [使用任务](/help/sites-authoring/task-content.md).

请按照以下过程为SEO推荐创建任务。

1. 单击或点按SEO推荐的信息图标。

   ![](do-not-localize/chlimage_1-23.png)

1. 单击信息图标旁边显示的带圆圈三角形图标。

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. 填写显示的表单字段，然后点按创建：

   * 项目：选择要在其中创建任务的项目。
   * 名称：用于标识任务的名称。 默认名称是SEO推荐的标题。
   * 分配给：选择要分配任务的用户。 开始键入用户的名称以过滤列表。
   * 描述：完成任务所需的活动描述。 默认描述是SEO推荐附带的信息。
   * 任务优先级：任务的优先级。
   * 到期日期：应完成任务的日期。

1. 单击或点按完成，以关闭“已创建任务”消息。

>[!NOTE]
>
>创建的任务还包括应用SEO推荐的页面路径。
