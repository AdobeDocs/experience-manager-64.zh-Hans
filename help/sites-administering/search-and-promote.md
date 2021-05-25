---
title: 与AdobeSearch&Promote集成
seo-title: 与AdobeSearch&Promote集成
description: 了解如何与AdobeSearch&Promote集成。
seo-description: 了解如何与AdobeSearch&Promote集成。
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
exl-id: 2bbcc8d0-c1c7-4901-836f-44b8a2153a46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---

# 与AdobeSearch&amp;Promote集成{#integrating-with-adobe-search-promote}

要从您的网站调用AdobeSearch&amp;Promote服务，请执行以下任务：

1. 指定云的URL。
1. 配置与Search&amp;Promote服务的连接。
1. 将Search&amp;Promote组件添加到[!UICONTROL Sidekick]。
1. 使用组件创作内容。 (请参阅[向网页添加Search&amp;Promote功能](/help/sites-authoring/search-and-promote.md)。)
1. 将横幅添加到您的页面。 横幅图像对Search&amp;Promote数据敏感。
1. 为要使用的Search&amp;Promote服务生成站点映射。

>[!NOTE]
>
>如果您使用的是具有自定义代理配置的Search&amp;Promote，则需要配置两个HTTP客户端代理配置，因为AEM的某些功能使用3.x API，而其他一些功能使用4.x API:
>
>* 3.x配置了[http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x配置了[http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## 更改Search&amp;Promote服务URL {#changing-the-search-promote-service-url}

为Search&amp;Promote服务配置的默认URL为`https://searchandpromote.omniture.com/px/`。 要使用其他服务，请使用OSGi控制台指定其他URL。

**要更改Search&amp;Promote服务URL**，请执行以下操作：

1. 打开[!UICONTROL OSGi]控制台，然后点按&#x200B;**[!UICONTROL Configuration]**&#x200B;选项卡。 ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. 单击&#x200B;**[!UICONTROL Day CQSearch&amp;Promote配置]**&#x200B;项。
1. 在&#x200B;**[!UICONTROL Remote Server URI]**&#x200B;文本字段中，输入URL，然后点按&#x200B;**[!UICONTROL Save]**。

## 配置与Search&amp;Promote{#configuring-the-connection-to-search-promote}的连接

配置一个或多个与Search&amp;Promote的连接，以便网页可以与服务进行交互。 要连接，您需要您的Search&amp;Promote帐户的成员标识和帐号。

**要配置与Search&amp;Promote的连接**，请执行以下操作：

1. 从&#x200B;**[!UICONTROL 工具]**&#x200B;图标> **[!UICONTROL 部署]**&#x200B;中，选择&#x200B;**[!UICONTROL Cloud Services]**。

   这会将您转到“Cloud Services”功能板。 如果在本地计算机上，功能板的url将如下所示：

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. 在[!UICONTROL Cloud Services]页面中，点按&#x200B;**[!UICONTROL AdobeSearch&amp;Promote]**&#x200B;链接或&#x200B;**[!UICONTROL Search&amp;Promote]**&#x200B;图标。

1. 如果这是您首次配置AdobeSearch&amp;Promote，请点按&#x200B;**[!UICONTROL 立即配置]**&#x200B;以打开[!UICONTROL 创建配置]面板。

   如果您想了解有关Search&amp;Promote的更多信息，请点击&#x200B;**[!UICONTROL 了解更多]**。

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 输入可对页面作者识别的&#x200B;**[!UICONTROL 标题]**，然后输入唯一的&#x200B;**[!UICONTROL 名称]**，然后点按&#x200B;**[!UICONTROL 创建]**。

   此外，新创建的配置显示在&#x200B;**[!UICONTROL Cloud Services功能板]** AdobeSearch&amp;Promote列表项的&#x200B;**[!UICONTROL 可用配置]**&#x200B;下方。

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在[!UICONTROL 编辑组件]对话框中，将以下内容添加到字段：

   * **[!UICONTROL 成员·ID]**
   * **[!UICONTROL 帐号]**

   >[!NOTE]
   >
   >要自行获取此信息，请登录以下网站：
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >使用您的有效Seach&amp;Promote凭据（电子邮件/密码）。
   >
   >请注意浏览器地址栏中的URL。 它应类似于以下内容：
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >其中， **XXXXXXXX**&#x200B;对应于您的&#x200B;**[!UICONTROL 成员id]**，而&#x200B;**[!UICONTROL spYYYYYY]**&#x200B;对应于您的帐号。

1. 点按&#x200B;**[!UICONTROL 连接到Search&amp;Promote]**。

   出现连接成功消息时，点按&#x200B;**[!UICONTROL 确定]**。

   (连接后，按钮文本将变为&#x200B;**[!UICONTROL Re-Connect To Search&amp;Promote]**。)

1. 点按&#x200B;**[!UICONTROL 确定]**。 此时将显示您刚刚创建的配置的Search&amp;Promote设置页面。

## 配置数据中心{#configuring-the-data-center}

如果您的Search&amp;Promote帐户位于亚洲或欧洲，则需要更改默认的数据中心，以使其指向正确的数据中心（默认的数据中心适用于北美帐户）。

**要配置数据中心**:

1. 导航到位于`http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`的Web控制台

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 根据服务器的位置，将URI更改为以下URI之一：

   * 北美：[https://center.atomz.com/px/](https://center.atomz.com/px/)
   * 欧洲、中东和非洲地区：[https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC:[https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 点按&#x200B;**[!UICONTROL 保存]**。

## 将Search&amp;Promote组件添加到Sidekick {#adding-search-promote-components-to-sidekick}

在[!UICONTROL 设计]模式中，编辑&#x200B;**[!UICONTROL par]**&#x200B;组件，以允许在[!UICONTROL Sidekick]中Search&amp;Promote组件。 （有关更多信息，请参阅[组件](/help/sites-developing/components.md)文档。）

有关使用组件的信息，请参阅[将Search&amp;Promote功能添加到网页](/help/sites-authoring/search-and-promote.md)。

## 指定页面使用{#specifying-the-search-promote-service-that-your-pages-use}的Search&amp;Promote服务

配置网页，以便它们使用特定的Search&amp;Promote服务。 Search&amp;Promote组件会自动使用其主页的服务。

在为页面配置Search&amp;Promote属性时，所有子页面都会继承设置。 如果需要，您可以配置子页面以覆盖继承的设置。

>[!NOTE]
>
>必须已配置服务连接。 请参阅[配置与Search&amp;Promote的连接](#configuring-the-connection-to-search-promote)。

1. 打开&#x200B;**[!UICONTROL 页面属性]**&#x200B;对话框。 例如，在&#x200B;**[!UICONTROL Websites]**&#x200B;页面上，右键单击该页面，然后单击&#x200B;**[!UICONTROL 属性]**。

1. 单击&#x200B;**[!UICONTROL Cloud Services]**&#x200B;选项卡。

1. 要禁用父页面中云服务配置的继承，请单击继承路径旁边的挂锁图标。

   ![松质遗锁](assets/sandpinheritpadlock.png)

1. 单击&#x200B;**[!UICONTROL 添加服务]**，选择&#x200B;**[!UICONTROL AdobeSearch&amp;Promote]**，然后单击&#x200B;**[!UICONTROL 确定]**。

1. 选择Search&amp;Promote帐户的连接配置，然后单击&#x200B;**[!UICONTROL 确定]**。

## 产品馈送{#product-feed}

Search&amp;Promote集成允许您执行以下操作：

* 使用[!UICONTROL eCommerce] API，与基础存储库结构和商务平台无关。
* 利用Search&amp;Promote的[!UICONTROL 索引连接器]功能以XML格式提供产品馈送。
* 利用Search&amp;Promote的[!UICONTROL 远程控制]功能，执行产品馈送的按需请求或计划请求。
* 不同Search&amp;Promote帐户的信息源生成，配置为云服务配置。

有关更多信息，请参阅[产品信息源](/help/sites-administering/product-feed.md)。
