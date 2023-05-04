---
title: 通过DTM启用资产分析
description: 了解如何使用AdobeDynamic Tag Management(DTM)启用资产分析。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 1%

---

# 通过DTM启用资产分析 {#enabling-asset-insights-through-dtm}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe动态Tag Management是一个可激活您的数字营销工具的工具。 该服务免费提供给Adobe Analytics客户。 您可以自定义跟踪代码，以启用第三方CMS解决方案来使用资产分析，也可以使用DTM插入资产分析标记。 仅支持并提供图像分析。

>[!CAUTION]
>
>AdobeDTM已弃用，支持 [!DNL Adobe Experience Platform] 很快就会到 [生命周期终止](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). Adobe建议您 [use [!DNL Adobe Experience Platform] 用于资产分析](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

执行以下步骤以通过DTM启用资产分析：

1. 点按/单击 [!DNL Experience Manager] 徽标，然后转到 **[!UICONTROL 工具]** > **[!UICONTROL 资产]** > **[!UICONTROL 分析配置]**.
1. [配置 [!DNL Experience Manager] 使用DTM的实例Cloud Service](../sites-administering/dtm.md)

   API令牌应在您登录到 [https://dtm.adobe.com](https://dtm.adobe.com/) 访问 **[!UICONTROL 帐户设置]** 中。 从资产分析的角度来看，不需要执行此步骤，因为 [!DNL Experience Manager Sites] 资产分析功能仍在工作中。

1. 登录到 [https://dtm.adobe.com](https://dtm.adobe.com/)，然后根据需要选择公司。
1. 创建/打开现有Web属性

   * 选择 **[!UICONTROL Web属性]** 选项卡，然后点按/单击 **[!UICONTROL 添加属性]**.
   * 根据需要更新字段，然后点按/单击 **[!UICONTROL 创建资产]** (请参阅 [文档](https://helpx.adobe.com/experience-manager/using/dtm.html))。

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. 在 **[!UICONTROL 规则]** 选项卡，选择 **[!UICONTROL 页面加载规则]** ，然后点按/单击 **[!UICONTROL 创建新规则]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. 展开 **[!UICONTROL Javascript/第三方标记]**. 然后点按/单击 **[!UICONTROL 添加新脚本]** 在 **[!UICONTROL 顺序HTML]** 选项卡来打开“脚本”对话框。

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. 点按/单击 [!DNL Experience Manager] 徽标，然后转到 **[!UICONTROL 工具>资产]**.
1. 点按/单击 **[!UICONTROL 分析页面跟踪器]**，复制跟踪器代码，然后将其粘贴到您在步骤6中打开的“脚本”对话框中。 保存更改。

   >[!NOTE]
   >
   >* `AppMeasurement.js` 已被删除。 它预计可通过DTM的Adobe Analytics工具获取。
   >* 对 `assetAnalytics.dispatcher.init()` 删除。 当DTM的Adobe Analytics工具完成加载时，预期将调用函数。
   >* 根据资产分析页面跟踪器的托管位置(例如AEM、CDN等)，脚本源的来源可能需要进行更改。
   >* 对于AEM托管的页面跟踪器，源应使用调度程序实例的主机名指向发布实例。


1. 打开 [https://dtm.adobe.com](https://dtm.adobe.com). 单击Web属性中的概述，然后单击添加工具或打开现有的Adobe Analytics工具。 在创建工具时，可以将“配置方法”设置为“自动”。

   ![chlimage_1-196](assets/chlimage_1-196.png)

   根据需要选择暂存/生产报表包。

1. 展开 **[!UICONTROL 库管理]**，并确保 **[!UICONTROL 库加载位置]** 设置为 **[!UICONTROL 页面顶部]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. 展开 **[!UICONTROL 自定义页面代码]**，单击或点按 **[!UICONTROL Open Editor]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. 在窗口中粘贴以下代码：

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * DTM中的页面加载规则仅包含pagetracker.js代码。 任意 `assetAnalytics` 字段会被视为默认值的覆盖。 默认情况下，它们不是必需的。
   * 代码调用 `assetAnalytics.dispatcher.init()` 确保 `_satellite.getToolsByType('sc')[0].getS()` 初始化和 `assetAnalytics,dispatcher.init` 中。 因此，您可以在步骤11中跳过添加它。
   * 如分析页面跟踪器代码(**[!UICONTROL 工具>资产>分析页面跟踪器]**)，则页面跟踪器不会创建 `AppMeasurement` 对象中，前三个参数（RSID、跟踪服务器和访客命名空间）无关紧要。 将传递空字符串以突出显示此内容。

      其余参数与分析配置页面中配置的参数(**[!UICONTROL 工具>资产>分析配置]**)。

   * AppMeasurement对象通过查询进行检索 `satelliteLib` ，用于所有可用的SiteCatalyst引擎。 如果配置了多个标记，请相应地更改数组选择器的索引。 数组中的条目按DTM界面中可用的SiteCatalyst工具排序。

1. 保存并关闭代码编辑器窗口，然后在工具配置中保存更改。
1. 在 **[!UICONTROL 批准]** 选项卡，批准两个待批准。 DTM标记已准备好插入您的网页。 有关如何在网页中插入DTM标记的详细信息，请参阅存档页面关于 [在自定义页面模板中集成DTM](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
