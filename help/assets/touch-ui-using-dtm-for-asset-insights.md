---
title: 通过DTM启用资产分析
description: 了解如何使用Adobe动态标签管理(DTM)来启用资产分析。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: 2b3a6972d703314d56d3dc711fb6a514cb1942d5
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# 通过DTM启用资产分析 {#enabling-asset-insights-through-dtm}

Adobe动态标签管理是一款可激活您的数字营销工具的工具。 该服务免费提供给Adobe Analytics客户。 您可以自定义跟踪代码，以启用第三方CMS解决方案来使用资产分析，也可以使用DTM插入资产分析标记。 仅支持并提供图像分析。

>[!CAUTION]
>
>AdobeDTM已弃用，支持[!DNL Adobe Experience Platform]，并且很快将结束[生命周期](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f)。 Adobe建议您[对资产分析](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)使用 [!DNL Adobe Experience Platform] 。

执行以下步骤以通过DTM启用资产分析：

1. 点按/单击AEM徽标，然后转到&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 资产]** > **[!UICONTROL 分析配置]**。
1. [使用DTM配置AEM实例Cloud Service](../sites-administering/dtm.md)

   在您登录到[https://dtm.adobe.com](https://dtm.adobe.com/)并从“配置文件”图标访问&#x200B;**[!UICONTROL 帐户设置]**&#x200B;后，API令牌才应该可用。 从资产分析的角度来看，不需要执行此步骤，因为AEM Sites与资产分析的集成仍在进行中。

1. 登录到[https://dtm.adobe.com](https://dtm.adobe.com/)，然后根据需要选择公司。
1. 创建/打开现有Web属性

   * 选择&#x200B;**[!UICONTROL Web属性]**&#x200B;选项卡，然后点按/单击&#x200B;**[!UICONTROL 添加属性]**。
   * 根据需要更新字段，然后点按/单击&#x200B;**[!UICONTROL 创建属性]**（请参阅[文档](https://helpx.adobe.com/experience-manager/using/dtm.html)）。

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. 在&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡中，从导航窗格中选择&#x200B;**[!UICONTROL Page Load Rules]** ，然后点按/单击&#x200B;**[!UICONTROL Create New Rule]**。

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. 展开&#x200B;**[!UICONTROL Javascript /Third Party Tags]**。 然后点按/单击&#x200B;**[!UICONTROL 连续HTML]**&#x200B;选项卡中的添加新脚本&#x200B;]**，以打开“脚本”对话框。**[!UICONTROL 

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. 点按/单击AEM徽标，然后转到&#x200B;**[!UICONTROL 工具> Assets]**。
1. 点按/单击&#x200B;**[!UICONTROL 分析页面跟踪器]**，复制跟踪器代码，然后将其粘贴到您在步骤6中打开的“脚本”对话框中。 保存更改。

   >[!NOTE]
   >
   >* `AppMeasurement.js` 已被删除。它预计可通过DTM的Adobe Analytics工具获取。
   >* 将删除对`assetAnalytics.dispatcher.init()`的调用。 当DTM的Adobe Analytics工具完成加载时，预期将调用函数。
   >* 根据资产分析页面跟踪器的托管位置(例如AEM、CDN等)，脚本源的来源可能需要进行更改。
   >* 对于AEM托管的页面跟踪器，源应使用调度程序实例的主机名指向发布实例。


1. 打开[https://dtm.adobe.com](https://dtm.adobe.com)。 单击Web属性中的概述，然后单击添加工具或打开现有的Adobe Analytics工具。 在创建工具时，可以将“配置方法”设置为“自动”。

   ![chlimage_1-196](assets/chlimage_1-196.png)

   根据需要选择暂存/生产报表包。

1. 展开&#x200B;**[!UICONTROL 库管理]**，并确保将&#x200B;**[!UICONTROL Load Library at]**&#x200B;设置为&#x200B;**[!UICONTROL Page Top]**。

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. 展开&#x200B;**[!UICONTROL 自定义页面代码]**，然后单击或点按&#x200B;**[!UICONTROL Open Editor]**。

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

   * DTM中的页面加载规则仅包含pagetracker.js代码。 任何`assetAnalytics`字段都被视为默认值的覆盖。 默认情况下，它们不是必需的。
   * 确保初始化`_satellite.getToolsByType('sc')[0].getS()`并且`assetAnalytics,dispatcher.init`可用后，代码会调用`assetAnalytics.dispatcher.init()`。 因此，您可以在步骤11中跳过添加它。
   * 如分析页面跟踪器代码（**[!UICONTROL 工具>资产>分析页面跟踪器]**）中的注释所示，当页面跟踪器未创建`AppMeasurement`对象时，前三个参数（RSID、跟踪服务器和访客命名空间）无关紧要。 将传递空字符串以突出显示此内容。

      其余参数与“分析配置”页面中配置的参数（**[!UICONTROL 工具>资产>分析配置]**）相对应。

   * 通过查询`satelliteLib`所有可用的SiteCatalyst引擎，可检索AppMeasurement对象。 如果配置了多个标记，请相应地更改数组选择器的索引。 数组中的条目按DTM界面中可用的SiteCatalyst工具排序。

1. 保存并关闭代码编辑器窗口，然后在工具配置中保存更改。
1. 在&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡中，批准两个待批准。 DTM标记已准备好插入您的网页。 有关如何在网页中插入DTM标记的详细信息，请参阅关于[在自定义页面模板中集成DTM的存档页面](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template)。
