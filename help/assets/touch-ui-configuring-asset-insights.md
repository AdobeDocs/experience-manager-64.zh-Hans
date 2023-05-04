---
title: 配置资产分析
description: 了解如何在 [!DNL Experience Manager] 资产。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 10%

---

# 配置资产分析 {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets会获取有关 [!DNL Experience Manager] 第三方网站使用的资产。Adobe Analytics 要使资产分析能够检索此数据并生成分析，请首先配置该功能以与Adobe Analytics集成。

>[!NOTE]
>
>仅支持并提供图像分析。

1. 在 AEM 中，单击&#x200B;**[!UICONTROL 工具 > Assets]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 单击&#x200B;**[!UICONTROL 分析配置]**&#x200B;卡。
1. 在向导中，选择一个数据中心并提供您的凭据，包括您的组织名称、用户名和密码。

   ![chlimage_1-211](assets/insights_config2.png)

1. 单击／点按 **[!UICONTROL 身份验证]**。
1. 之后 [!DNL Experience Manager] 验证您的凭据，通过 **[!UICONTROL 报表包]** 列表中，选择一个Adobe Analytics报表包，您可以从中获取资产分析的数据。 单击 **[!UICONTROL 添加]**.
1. 之后 [!DNL Experience Manager] 设置报表包，单击/点按 **[!UICONTROL 完成]**.

## 页面跟踪器 {#page-tracker}

配置Analytics帐户后，将为您生成页面跟踪器代码。 启用资产分析以跟踪 [!DNL Experience Manager] 第三方网站中使用的资产，请在网站代码中包含页面跟踪器代码。 在 [!DNL Experience Manager] 用于生成页面跟踪器代码的资产。 有关如何在第三方网页中包含页面跟踪器代码的更多信息，请参阅 [在网页中使用页面跟踪器和嵌入代码](touch-ui-using-page-tracker.md).

1. 在AEM中，单击 **[!UICONTROL 工具>资产]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 从&#x200B;**[!UICONTROL 导航]**&#x200B;页面中，单击&#x200B;**[!UICONTROL 分析页面跟踪器]**&#x200B;卡。
1. 单击 **[!UICONTROL 下载]** 图标以下载页面跟踪器代码。
