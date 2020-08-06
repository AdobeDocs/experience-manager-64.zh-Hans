---
title: AEM Mobile点播
seo-title: AEM Mobile点播
description: 要开始新的AEM Mobile应用体验，需要在准备好进行内容编辑之前保持角色的一致性。 可查看本页以开始使用AEM mobile On-Demand服务。
seo-description: 要开始新的AEM Mobile应用体验，需要在准备好进行内容编辑之前保持角色的一致性。 可查看本页以开始使用AEM mobile On-Demand服务。
uuid: 175c609d-3cb8-4a1b-bfea-278df272e500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: dc6891cd-19cc-4dff-8bda-a41ed8af8bfb
translation-type: tm+mt
source-git-commit: 6c453c9497575a4be0172b86295186c74d0e50f5
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 1%

---


# AEM Mobile点播{#aem-mobile-on-demand}

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（如React）的项目使用SPA编辑器。 [了解更多](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>如果您未将AEM用作内容管理源，请参阅 [AEM Mobile On-demand Services帮助](https://helpx.adobe.com/digital-publishing-solution/topics.html)。

AEM提供了多种工具，使您能够将内容集成到移动应用程序中。

下图说明了AEM Mobile和点播服务的各个组件如何相互配合，将内容交付到移动App。

AEM Preflight应用程序可被视为在发布前预览应用程序和内容的测试环境; 而AEM Mobile应用程序是最终为分发而构建的应用程序。

>[!NOTE]
>
>要详细了解Preflight应用程序，请参阅“ [AEM Mobile On-demand Services帮助”中的](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) “使用AEM Preflight应用程序”。

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>在上图中，到AEM Mobile On-demand Services的典型部署方案不需要AEM发布实例。

## 启动新的移动应用程序 {#starting-a-new-mobile-app}

AEM Mobile只是构成整个AEM平台的支柱之一。

要开始新的AEM Mobile应用体验，需要在准备好进行内容编辑之前保持角色的一致性。 以下角色为创建新的AEM Mobile应用程序提供了一个起点：

* **管理员**
* **开发人员**
* **创作**

>[!NOTE]
>
>在与AEM Mobile合作并遵循本入门指南中的步骤之前，用户应熟悉AEM。 Learn the basics of AEM [here](/help/sites-deploying/deploy.md).

### 理解AEM Mobile应用程序仪表板 {#understanding-the-aem-mobile-application-dashboard}

在了解角色和责任之前，用户应充分了解 **AEM Mobile控制中心** 或应 **用仪表板**。 单 [击此](/help/mobile/mobile-apps-ondemand-application-dashboard.md) ，深入了解客户。

### AEM 管理员 {#aem-administrator}

AEM管 ***理员*** 负责通过使用创建向导创建新应用程序或导入现有应用程序来将新应用程序添加到AEM Mobile目录。 AEM管理员使用AEM Mobile的创建向 *导创建新应用* ，通常从现成的参考范例或（在大多数情况下）AEM开发人员创建的自定义应用程序模板中选择一个所需的应用程序 *模板。*

AEM管理员在使用AEM Mobile On-demand Services创建应用程序时负责以下任务:

* [建立AEM Mobile](/help/mobile/aem-mobile-setup.md)
* [配置用户和用户组](/help/mobile/aem-mobile-configure-users.md)
* [使用预检预览](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [管理内容服务](/help/mobile/developing-content-services.md)

要开始管理员的角色和职责，请参阅管 [理内容以使用AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)。

## AEM开发人员 {#aem-developer}

AEM开 **发人员** 扩展并创建自定义Web模板和组件，使*AEM作者*能够创建精美、引人入胜的移动体验。 这些模板和组件不仅针对移动App世界进行了优化； 但可以同时与设备和AEM服务器（任何远程服务器）通信到全渠道服务端点。 AEM内置内容编辑器供AEM作 *者使用* ，在应用程序中创建丰富且相关的体验，包括与Adobe Marketing Cloud其他地区的集成。

AEM开发人员在使用AEM Mobile On-demand Services创建应用程序时负责以下任务:

* [应用程序模板和组件](/help/mobile/app-templates-and-components1.md)
* [内容同步的移动设备](/help/mobile/mobile-ondemand-contentsync.md)
* [内容属性和导出内容](/help/mobile/on-demand-content-properties-exporting.md)
* [开发AEM Mobile内容服务](/help/mobile/developing-content-services.md)

要开始了解开发人员的角色和职责，请参阅为 [AEM Mobile On-demand Services开发AEM内容](/help/mobile/aem-mobile-on-demand.md)。

>[!NOTE]
>
>AEM *开发人员的角色* ，不会开始模板和组件的开发并结束开发。 AEM *开发人* 员可以创建一个全新的应用程序，而不是简单地扩展开箱即用的参考实施示例。

## AEM Author {#aem-author}

AEM ***作者&#x200B;*(或营销人*员&#x200B;***)使用自定义开发或现成的模板和组件来添加和编辑页面、拖放组件以及添加DAM中所有类型的媒体，包括图像、视频和文本片段（内容片段）。 AEM内置内容编辑器随后由AEM作*者使用&#x200B;*，在应用程序中创建丰富且相关的体验，包括与Adobe Marketing Cloud其他地区的集成。

AEM作者在使用AEM Mobile On-demand Services创建应用程序时必须了解以下主题：

* [AEM Mobile应用程序仪表板](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [应用程序创建和配置操作](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [云配置](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [管理内容](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [内容服务概述](/help/mobile/develop-content-as-a-service.md)

要开始使用作者的角色和职责，请参阅为AEM Mobile On-demand Services [应用程序创作AEM内容](/help/mobile/mobile-apps-ondemand.md)。

>[!NOTE]
>
>AEM作者还负责设置授权、创建卡和布局以及发送推送通知。 此外，有关创作内容的方法的更多信息； 管理文章和集合； 在AEM Mobile创建横幅、卡和布局，请参 [阅AEM Mobile点播门户](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2)。

