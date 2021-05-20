---
title: 使用资产分析功能跟踪图像的使用情况
description: 资产分析功能可让您跟踪第三方网站、营销活动和Adobe创意解决方案中使用的图像的用户评级和使用统计数据。
contentOwner: AG
feature: 资产分析，资产报表
role: Business Practitioner,Administrator
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 8%

---

# 资产分析{#asset-insights}

了解资产分析功能如何让您跟踪第三方网站、营销活动和Adobe创意解决方案中使用的资产的用户评级和使用情况统计数据。

通过资产分析功能，您可以跟踪第三方网站、营销活动和Adobe的创意解决方案中使用的资产的用户评级和使用情况统计信息，从而获得有关资产性能和受欢迎程度的洞察。

资产分析可捕获用户活动详细信息，例如资产的评级、点击次数和展示次数（资产在网站上加载的次数）。 它会根据这些统计信息为资产分配分数。 您可以使用分数和绩效统计信息来选择热门资产，以将其纳入目录、营销活动等。 您甚至可以根据这些统计信息为资产制定存档和许可证续订策略。

要使资产分析从网站捕获资产的使用情况统计信息，您必须在网站代码中包含资产的嵌入代码。

要让资产分析显示资产的使用情况统计信息，请首先配置该功能以从[!DNL Adobe Analytics]获取报告数据。 有关详细信息，请参阅[配置资产分析](touch-ui-configuring-asset-insights.md)。 要使用此功能，请单独购买[!DNL Adobe Analytics]许可证。 [!DNL Managed Services]上的客户会收到与[!DNL Experience Manager]绑定的[!DNL Analytics]许可证。 请参阅[Managed Services产品说明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)。

>[!NOTE]
>
>支持并仅为图像提供洞察。

## 资产{#viewing-statistics-for-an-asset}的视图统计信息

您可以从元数据页面视图资产分析分数。

1. 从资产用户界面(UI)中，选择资产，然后点按/单击工具栏中的&#x200B;**[!UICONTROL 属性]**&#x200B;图标。
1. 在“属性”页中，点按/单击&#x200B;**[!UICONTROL 分析]**&#x200B;选项卡。
1. 在&#x200B;**[!UICONTROL Insights]**&#x200B;选项卡中查看资产的使用详细信息。 **[!UICONTROL Score]**&#x200B;部分描述资产的资产使用总数和性能存储。

   使用情况分数描述资产在各种解决方案中的使用次数。

   **[!UICONTROL 展示次数]**&#x200B;分数是资产在网站上加载的次数。 **[!UICONTROL 单击]**&#x200B;下显示的数字是单击资产的次数。

1. 查看&#x200B;**[!UICONTROL 使用统计信息]**&#x200B;部分，了解资产所属的实体以及最近使用的创意解决方案。 使用率越高，该资产在用户中受欢迎的可能性就越大。 使用数据显示在以下标题下：

   * **[!UICONTROL 资产]**:资产加入集合或复合资产的次数
   * **[!UICONTROL Web和移动]**:资产加入网站和应用程序的次数
   * **[!UICONTROL 社交]**:资产在解决方案(如Adobe Social和Adobe Campaign)中的使用次数
   * **[!UICONTROL 电子邮件]**:资产在电子邮件活动中的使用次数

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >“资产分析”功能会定期从[!DNL Adobe Analytics]中获取解决方案数据，解决方案部分可能不显示最新数据。 显示数据的时间段取决于资产分析运行以检索[!DNL Analytics]数据的提取操作的计划。

1. 要以图形方式查看一段时间内资产的性能统计信息，请在&#x200B;**[!UICONTROL 性能统计信息]**&#x200B;部分中选择时间段。包括点击次数和印象在内的详细信息将显示为图形的趋势线。

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >与“解决方案”部分中的数据不同，“性能统计”部分显示最新数据。

1. 要获取包含在网站中的资产的嵌入代码以获取性能数据，请单击资产缩略图下方的&#x200B;**[!UICONTROL 获取嵌入代码]**。 有关如何在第三方网页中包含嵌入代码的详细信息，请参阅[在网页中使用页面跟踪器和嵌入代码](touch-ui-using-page-tracker.md)。

   ![chlimage_1-303](assets/chlimage_1-303.png)

## 视图资产{#viewing-aggregate-statistics-for-assets}的聚合统计

您可以使用&#x200B;**[!UICONTROL 分析视图]**&#x200B;同时查看文件夹中所有资产的分数。

1. 在资产用户界面中，导航到包含要视图分析的资产的文件夹。
1. 点按/单击工具栏中的布局图标，然后选择&#x200B;**[!UICONTROL 分析视图]**。
1. 该页面显示资产的使用分数。 比较各个资产的评级并进行分析。

## 计划后台作业{#scheduling-background-job}

资产分析可定期从Adobe Analytics报表包获取资产的使用数据。 默认情况下，资产分析会在凌晨2点每24小时运行一个后台作业，以获取数据。 但是，您可以通过从Web控制台配置&#x200B;**[!UICONTROL Adobe CQ DAM资产性能报表同步作业]**&#x200B;服务来修改频率和时间。

1. 点按 AEM 徽标，然后转到&#x200B;**[!UICONTROL 工具 > 操作 > Web Console]**。
1. 打开&#x200B;**[!UICONTROL Adobe CQ DAM资产性能报表同步作业]**&#x200B;服务配置。

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. 在属性调度程序中指定作业所需的开始频率和调度程序时间。 保存更改。
