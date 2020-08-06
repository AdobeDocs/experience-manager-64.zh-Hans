---
title: 配置资产分析
description: 了解如何在AEM Assets配置资产分析。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 10%

---


# 配置资产分析 {#configuring-asset-insights}

Adobe Experience Manager(AEM)资产会从Adobe Analytics获取由第三方网站使用的AEM资产的使用数据。 要使资产分析能够检索此数据并生成洞察，请首先配置该功能以与Adobe Analytics集成。

>[!NOTE]
>
>只支持并提供图像洞察。

1. 在 AEM 中，单击&#x200B;**[!UICONTROL 工具 > Assets]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 单击&#x200B;**[!UICONTROL 分析配置]**&#x200B;卡。
1. 在向导中，选择一个数据中心并提供您的凭据，包括您的单位名称、用户名和密码。

   ![chlimage_1-211](assets/insights_config2.png)

1. 单击／点按 **[!UICONTROL 身份验证]**。
1. 在AEM验证您的凭据后，从报 **[!UICONTROL 表包列表中]** ，选择您希望资产分析从中获取数据的Adobe Analytics报表包。 单击&#x200B;**[!UICONTROL 添加]**。
1. AEM设置报表包后，单击／点按完 **[!UICONTROL 成]**。

## 页面跟踪器 {#page-tracker}

配置Analytics帐户后，将为您生成页面跟踪器代码。 要使资产分析能够跟踪第三方网站中使用的AEM资产，请在网站代码中包含页面跟踪器代码。 使用AEM Assets的页面跟踪器实用程序生成页面跟踪器代码。 有关如何在第三方网页中包含页面跟踪器代码的更多信息，请参 [阅使用页面跟踪器和在网页中嵌入代码](touch-ui-using-page-tracker.md)。

1. In AEM, click the **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 从&#x200B;**[!UICONTROL 导航]**&#x200B;页面中，单击&#x200B;**[!UICONTROL 分析页面跟踪器]**&#x200B;卡。
1. 单击“ **[!UICONTROL 下载]** ”图标以下载页面跟踪器代码。