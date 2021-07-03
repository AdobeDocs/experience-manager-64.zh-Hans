---
title: 配置资产分析
description: 了解如何在AEM Assets中配置资产分析。
contentOwner: AG
feature: 资产分析，资产报表
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 10%

---

# 配置资产分析 {#configuring-asset-insights}

Adobe Experience Manager(AEM)Assets会从Adobe Analytics中获取由第三方网站使用的AEM资产的使用情况数据。 要使资产分析能够检索此数据并生成分析，请首先配置该功能以与Adobe Analytics集成。

>[!NOTE]
>
>仅支持并提供图像分析。

1. 在 AEM 中，单击&#x200B;**[!UICONTROL 工具 > Assets]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 单击&#x200B;**[!UICONTROL 分析配置]**&#x200B;卡。
1. 在向导中，选择一个数据中心并提供您的凭据，包括您的组织名称、用户名和密码。

   ![chlimage_1-211](assets/insights_config2.png)

1. 单击／点按 **[!UICONTROL 身份验证]**。
1. 在AEM验证您的凭据后，从&#x200B;**[!UICONTROL 报表包]**&#x200B;列表中，选择一个Adobe Analytics报表包，您可以从中获取资产分析数据。 单击&#x200B;**[!UICONTROL 添加]**。
1. 在AEM设置您的报表包后，单击/点按&#x200B;**[!UICONTROL 完成]**。

## 页面跟踪器 {#page-tracker}

配置Analytics帐户后，将为您生成页面跟踪器代码。 要启用资产分析来跟踪第三方网站中使用的AEM资产，请在网站代码中包含页面跟踪器代码。 使用AEM Assets中的页面跟踪器实用程序生成页面跟踪器代码。 有关如何在第三方网页中包含页面跟踪器代码的更多信息，请参阅[在网页中使用页面跟踪器和嵌入代码](touch-ui-using-page-tracker.md)。

1. 在AEM中，单击&#x200B;**[!UICONTROL 工具> Assets]**。

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 从&#x200B;**[!UICONTROL 导航]**&#x200B;页面中，单击&#x200B;**[!UICONTROL 分析页面跟踪器]**&#x200B;卡。
1. 单击&#x200B;**[!UICONTROL 下载]**&#x200B;图标以下载页面跟踪器代码。
