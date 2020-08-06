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
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---


# Integrating with Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

要从您的网站调用AdobeSearch&amp;Promote服务，请执行以下任务:

1. 指定云的URL。
1. 配置与Search&amp;Promote服务的连接。
1. 将Search&amp;Promote组件添 [!UICONTROL 加到Sidekick]。
1. 使用组件创作内容。 (请参 [阅将Search&amp;Promote功能添加到网页](/help/sites-authoring/search-and-promote.md)。)
1. 向页面添加横幅。 横幅图像对Search&amp;Promote数据敏感。
1. 为要使用的Search&amp;Promote服务生成站点地图。

>[!NOTE]
>
>如果您使用具有自定义代理配置的Search&amp;Promote，则需要配置两个HTTP客户端代理配置，因为AEM的某些功能使用3.x API，而其他一些则使用4.x API:
>
>* 3.x已配置为 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x配置为 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## 更改Search&amp;Promote服务URL {#changing-the-search-promote-service-url}

为Search&amp;Promote服务配置的默认URL为 `https://searchandpromote.omniture.com/px/`。 要使用其他服务，请使用OSGi控制台指定其他URL。

**要更改Search&amp;Promote服务URL**:

1. 打开OSGi [!UICONTROL 控制台] ，然后点按 **[!UICONTROL 配置选]** 项卡。 ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. 单击“ **[!UICONTROL Day CQSearch&amp;Promote配置]** ”项。
1. 在“远 **[!UICONTROL 程服务器]** URI”文本字段中，输入URL，然后点按 **[!UICONTROL 保存]**。

## 配置与Search&amp;Promote的连接 {#configuring-the-connection-to-search-promote}

配置一个或多个与Search&amp;Promote的连接，以便网页能够与服务交互。 要进行连接，您需要您的Search&amp;Promote帐户的成员标识和帐户号。

**配置与Search&amp;Promote的连接**:

1. 从工具 **[!UICONTROL 图标]** >部 **[!UICONTROL 署中]**，选 **[!UICONTROL 择Cloud Services]**。

   这会带你去Cloud Services仪表板。 如果在本地计算机上，仪表板的url将类似于：

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. 在Cloud Services [!UICONTROL 页面中] ，点按 **[!UICONTROL Adobe]** Search&amp;Promote **[!UICONTROL 链接或]** Search&amp;Promote图标。

1. 如果这是您首次配置AdobeSearch&amp;Promote，请点按 **[!UICONTROL 立即配置]** ，打开 [!UICONTROL 创建配置面板] 。

   如果您想了解有关Search&amp;Promote的更多信息，请改为 **[!UICONTROL 单击“了解更]** 多”。

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 输入页 **[!UICONTROL 面作]** 者可识别的标题，输入唯一 **[!UICONTROL 名称]**，然后点 **[!UICONTROL 按创建]**。

   此外，新创建的配置会显示在 **[!UICONTROL Cloud Services仪表板]** Adobe **[!UICONTROL Search&amp;Promote]** 项的可用配置下方。

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在“编 [!UICONTROL 辑组件] ”对话框中，将以下内容添加到字段：

   * **[!UICONTROL 成员·ID]**
   * **[!UICONTROL 帐号]**

   >[!NOTE]
   >
   >要亲自获取此信息，请登录以下网页：
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >使用有效的Seach&amp;Promote凭据（电子邮件／密码）。
   >
   >注意您浏览者的地址栏中的URL。 它应类似于以下内容：
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >其中 **XXXXXXXXXXX** 与您的 **[!UICONTROL 成员id相对应]** , **[!UICONTROL spYYYYYYYYYYYYYYYY]** 与您的帐户号相对应。

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   当显示连接成功消息时，点按 **[!UICONTROL 确定]**。

   (连接后，按钮文本变为“ **[!UICONTROL 重新连接到Search&amp;Promote]**”。)

1. 点按 **[!UICONTROL 确定]**。 此时将显示您刚刚创建的配置的Search&amp;Promote设置页。

## 配置数据中心 {#configuring-the-data-center}

如果您的Search&amp;Promote帐户位于亚洲或欧洲，您需要更改默认数据中心，以便它指向正确的数据中心（默认数据中心针对北美客户）。

**要配置数据中心**:

1. 导航到Web控制台，网址为 `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 根据服务器的位置，将URI更改为以下值之一：

   * 北美： [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * 亚太： [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 点按&#x200B;**[!UICONTROL 保存]**。

## 将Search&amp;Promote组件添加到Sidekick {#adding-search-promote-components-to-sidekick}

在 [!UICONTROL 设计] 模式中，编 **[!UICONTROL 辑par组]** 件 [!UICONTROL ，以允许Sidekick中的]Search&amp;Promote组件。 (See the [Components](/help/sites-developing/components.md) documentation for more information.)

有关使用这些组件的信息，请 [参阅将Search&amp;Promote功能添加到网页](/help/sites-authoring/search-and-promote.md)。

## 指定页面使用的Search&amp;Promote服务 {#specifying-the-search-promote-service-that-your-pages-use}

配置网页，使其使用特定的Search&amp;Promote服务。 Search&amp;Promote组件自动使用其主机页的服务。

为页面配置Search&amp;Promote属性时，所有子页面都会继承设置。 如果需要，您可以配置子页面以覆盖继承的设置。

>[!NOTE]
>
>必须已配置服务连接。 请参 [阅配置与Search&amp;Promote的连接](#configuring-the-connection-to-search-promote)。

1. 打开“ **[!UICONTROL 页面属性]** ”对话框。 例如，在“网 **[!UICONTROL 站]** ”页面上，右键单击页面，然后单击 **[!UICONTROL 属性]**。

1. 单击“ **[!UICONTROL Cloud Services]** ”选项卡。

1. 要从父页面禁用云服务配置的继承，请单击继承路径旁的挂锁图标。

   ![松皮继承锁](assets/sandpinheritpadlock.png)

1. 单击 **[!UICONTROL 添加服务]**，选择 **[!UICONTROL AdobeSearch&amp;Promote]**，然后单 **[!UICONTROL 击确定]**。

1. 选择Search&amp;Promote帐户的连接配置，然后单击“ **[!UICONTROL 确定]**”。

## Product Feed {#product-feed}

Search&amp;Promote集成允许您执行以下操作：

* 使用 [!UICONTROL eCommerce] API，独立于基础存储库结构和商务平台。
* 利用Search&amp;Promote [!UICONTROL 的“索引连接] ”功能，以XML格式提供产品信息源。
* 利用 [!UICONTROL Search&amp;Promote的] “远程控制”功能执行产品源的按需或计划请求。
* 不同Search&amp;Promote帐户的源生成，配置为云服务配置。

有关详细信息，请参 [阅产品信息](/help/sites-administering/product-feed.md)。
