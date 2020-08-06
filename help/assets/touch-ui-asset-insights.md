---
title: 使用资产分析功能跟踪图像的使用情况
description: 通过资产分析功能，您可以跟踪第三方网站、营销活动和Adobe的创意解决方案中使用的图像的用户评级和使用情况统计。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 9%

---


# 资产分析 {#asset-insights}

了解资产分析功能如何让您跟踪第三方网站、营销活动和Adobe的创意解决方案中使用的资产的用户评级和使用情况统计。

通过资产分析功能，您可以跟踪第三方网站、营销活动和Adobe的创意解决方案中使用的资产的用户评级和使用情况统计信息，从而获得有关其性能和受欢迎程度的洞察。

资产分析可捕获用户活动详细信息，如资产的评级、点击次数和展示次数（资产在网站上加载的次数）。 它会根据这些统计信息为资产分配分数。 您可以使用分数和绩效统计信息来选择热门资产，以纳入目录、营销活动等。 您甚至可以根据这些统计信息为资产制定存档和许可续订策略。

要使用资产分析从网站捕获资产的使用情况统计信息，您必须在网站代码中包含资产的嵌入代码。

要让资产分析显示资产的使用情况统计信息，请首先配置该功能以从中提取报告 [!DNL Adobe Analytics]数据。 有关详细信息，请 [参阅配置资产分析](touch-ui-configuring-asset-insights.md)。

>[!NOTE]
>
>支持并仅为图像提供洞察。

## 视图资产统计 {#viewing-statistics-for-an-asset}

您可以从元数据页面视图资产分析得分。

1. 从资产用户界面(UI)中，选择资产，然后点按／单击工 **[!UICONTROL 具栏]** 中的属性图标。
1. 在属性页面中，点按／单击 **[!UICONTROL 分析]** 选项卡。
1. 在“洞察”选项卡中查看资产的使用 **[!UICONTROL 情况]** 详细信息。 “分 **[!UICONTROL 数]** ”部分描述资产的资产使用总数和性能存储。

   使用情况分数描述资产在各种解决方案中的使用次数。

   展示 **[!UICONTROL 次数]** (Impessions)得分是资产在网站上加载的次数。 单击次数 **[!UICONTROL 下显]** 示的数量是单击资产的次数。

1. 查看“ **[!UICONTROL 使用统计]** ”部分，了解资产所属的实体以及最近使用的创意解决方案。 使用率越高，资产在用户中受欢迎的可能性就越大。 使用情况数据显示在以下标题下：

   * **[!UICONTROL 资产]**: 资产加入集合或复合资产的次数
   * **[!UICONTROL Web和移动]**: 资产加入网站和应用程序的次数
   * **[!UICONTROL 社交]**: 资产在解决方案中的使用次数，如Adobe Social和Adobe Campaign
   * **[!UICONTROL 电子邮件]**: 资产在电子邮件活动中的使用次数

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >由于资产分析功能通常会定期从Adobe Analytics获取解决方案数据，因此解决方案部分可能不会显示最新数据。 显示数据的时间段取决于资产分析运行以检索Analytics数据的提取操作的计划。

1. 要以图形方式查看一段时间内资产的性能统计信息，请在&#x200B;**[!UICONTROL 性能统计信息]**&#x200B;部分中选择时间段。包括点击次数和印象在内的详细信息将显示为图形的趋势线。

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >与“解决方案”部分中的数据不同，“性能统计”部分显示最新数据。

1. 要获取包含在网站中的资产的嵌入代码以获取性能数据，请点按／单击资产 **[!UICONTROL 缩略图下方的获]** 取嵌入代码。 有关如何将嵌入代码包含在第三方网页中的更多信息，请参 [阅使用页面跟踪器和网页中嵌入代码](touch-ui-using-page-tracker.md)。

   ![chlimage_1-303](assets/chlimage_1-303.png)

## 视图聚合资产统计 {#viewing-aggregate-statistics-for-assets}

您可以使用&#x200B;**[!UICONTROL 分析视图]**&#x200B;同时查看文件夹中所有资产的分数。

1. 在资产UI中，导航到包含要视图洞察的资产的文件夹。
1. 点按／单击工具栏中的布局图标，然后选择 **[!UICONTROL 分析视图]**。
1. 该页面显示资产的使用分数。 比较各个资产的评级并进行分析。

## 计划背景作业 {#scheduling-background-job}

资产分析可定期从Adobe Analytics报表包获取资产的使用数据。 默认情况下，资产分析每24小时在凌晨2点运行一次后台作业以获取数据。 但是，您可以通过从Web控制台配置 **[!UICONTROL Adobe CQDAM资产性能报表同步作业服务]** ，来修改频率和时间。

1. 点按 AEM 徽标，然后转到&#x200B;**[!UICONTROL 工具 > 操作 > Web Console]**。
1. 打开 **[!UICONTROL Adobe CQDAM资产性能报表同步作业]** 服务配置。

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. 在属性调度程序表达式中指定作业的所需开始频率和调度程序时间。 保存更改。
