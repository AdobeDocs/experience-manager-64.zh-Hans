---
title: 使用资产分析功能跟踪图像的使用情况
description: 资产分析功能允许您跟踪用户评级以及在第三方网站、营销活动和Adobe的创意解决方案中使用的图像的使用情况统计信息。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 6%

---

# 资产分析 {#asset-insights}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

了解资产分析功能如何让您跟踪用户评级和第三方网站、营销活动和Adobe创意解决方案中使用的资产使用情况统计信息。

通过Adobe分析功能，您可以跟踪用户评级和资产使用情况统计信息，这些信息在第三方网站、营销活动和资产的创意解决方案中使用，从而深入了解资产的性能和受欢迎程度。

资产分析可捕获用户活动详细信息，如资产的评级、点击次数和展示次数（资产在网站上加载的次数）。 它会根据这些统计信息为资产分配分数。 您可以使用得分和性能统计信息来选择要包含在目录、营销活动等中的热门资产。 您甚至可以根据这些统计数据为资产制定存档和许可证续订策略。

要使资产分析从网站中捕获资产的使用情况统计信息，您必须在网站代码中包含资产的嵌入代码。

要让资产分析显示资产的使用情况统计信息，请首先配置功能，以从 [!DNL Adobe Analytics]. 有关详细信息，请参阅 [配置资产分析](touch-ui-configuring-asset-insights.md). 要在内部部署安装中使用此功能，请购买 [!DNL Adobe Analytics] 单独许可。 客户 [!DNL Managed Services] 接收 [!DNL Analytics] 与 [!DNL Experience Manager]. 请参阅 [Managed Services产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>仅支持对图像提供分析。

## 查看资产的统计信息 {#viewing-statistics-for-an-asset}

您可以从元数据页面查看资产分析得分。

1. 从资产用户界面(UI)中，选择资产，然后点按/单击 **[!UICONTROL 属性]** 图标。
1. 在属性页面中，点按/单击 **[!UICONTROL 分析]** 选项卡。
1. 在 **[!UICONTROL 分析]** 选项卡。 的 **[!UICONTROL 得分]** 部分介绍资产的资产使用总数和性能商店。

   使用情况分数描述了资产在各种解决方案中使用的次数。

   的 **[!UICONTROL 展示次数]** score是资产在网站上加载的次数。 显示在 **[!UICONTROL 点击次数]** 是点击资产的次数。

1. 查看 **[!UICONTROL 使用情况统计信息]** 部分以了解资产所属的实体以及最近使用过的创意解决方案。 使用率越高，资产在用户中受欢迎的可能性就越大。 使用情况数据显示在以下标题下：

   * **[!UICONTROL 资产]**:资产属于收藏集或复合资产的次数
   * **[!UICONTROL Web和移动设备]**:资产成为网站和应用程序一部分的次数
   * **[!UICONTROL 社交]**:资产在解决方案(如Adobe Social和Adobe Campaign)中使用的次数
   * **[!UICONTROL 电子邮件]**:资产在电子邮件促销活动中使用的次数

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >资产分析功能可从中提取解决方案数据 [!DNL Adobe Analytics] 解决方案部分可能会定期显示最新数据。 显示数据的时间段取决于资产分析运行以检索的获取操作的计划 [!DNL Analytics] 数据。

1. 要以图形方式查看一段时间内资产的性能统计信息，请在&#x200B;**[!UICONTROL 性能统计信息]**&#x200B;部分中选择时间段。包括点击次数和印象在内的详细信息将显示为图形的趋势线。

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >与解决方案部分中的数据不同，性能统计部分显示最新的数据。

1. 要获取您包含在网站中的资产的嵌入代码以获取性能数据，请单击 **[!UICONTROL 获取嵌入代码]** 资产缩略图下方。 有关如何将嵌入代码包含在第三方网页中的更多信息，请参阅 [在网页中使用页面跟踪器和嵌入代码](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## 查看资产的汇总统计信息 {#viewing-aggregate-statistics-for-assets}

您可以使用&#x200B;**[!UICONTROL 分析视图]**&#x200B;同时查看文件夹中所有资产的分数。

1. 在资产UI中，导航到要查看其分析的资产所在的文件夹。
1. 点按/单击工具栏中的布局图标，然后选择 **[!UICONTROL 分析视图]**.
1. 页面会显示资产的使用情况分数。 比较各个资产的评级并进行分析。

## 计划后台作业 {#scheduling-background-job}

资产分析会定期从Adobe Analytics报表包中获取资产的使用情况数据。 默认情况下，资产分析会在凌晨2点运行一个后台作业，以获取数据。 但是，您可以通过配置 **[!UICONTROL Adobe CQ DAM资产性能报表同步作业]** 服务。

1. 点按 [!DNL Experience Manager] 徽标，然后转到 **[!UICONTROL “工具”>“操作”>“Web控制台”]**.
1. 打开 **[!UICONTROL Adobe CQ DAM资产性能报表同步作业]** 服务配置。

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. 在属性调度程序表达式中指定所需的调度程序频率和作业的开始时间。 保存更改。
