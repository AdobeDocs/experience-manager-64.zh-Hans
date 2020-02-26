---
title: 与Adobe Search&Promote集成
seo-title: 与Adobe Search&Promote集成
description: 了解如何与Adobe Search&Promote集成。
seo-description: 了解如何与Adobe Search&Promote集成。
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Integrating with Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

要从您的网站调用Adobe Search&amp;Promote服务，请执行以下任务：

1. 指定云的URL。
1. 配置与Search&amp;Promote服务的连接。
1. 将Search&amp;Promote组件添加到 [!UICONTROL Sidekick]。
1. 使用组件创作内容。 (请参 [阅将Search&amp;Promote功能添加到网页](/help/sites-authoring/search-and-promote.md)。)
1. 向页面添加横幅。 横幅图像对Search&amp;Promote数据很敏感。
1. 为要消费的Search&amp;Promote服务生成站点地图。

>[!NOTE]
>
>如果您使用Search&amp;Promote和自定义代理配置，则需要同时配置HTTP客户端代理配置，因为AEM的某些功能使用3.x API，而其他一些功能使用4.x API:
>
>* 3.x已配置http://localhost:4502/system/console/configMgr/com.day.commons.httpclient [](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x已配置http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator [](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



## 更改Search&amp;Promote服务URL {#changing-the-search-promote-service-url}

为Search&amp;Promote服务配置的默认URL为 `https://searchandpromote.omniture.com/px/`。 要使用其他服务，请使用OSGi控制台指定其他URL。

**要更改Search&amp;Promote服务URL**:

1. 打开 [!UICONTROL OSGi控制台] ，然后点按配 **[!UICONTROL 置选项卡]** 。 ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. 单击“ **[!UICONTROL Day CQ Search&amp;Promote配置”项]** 。
1. 在“远程 **[!UICONTROL 服务器URI]** ”文本字段中，输入URL，然后点按 **[!UICONTROL 保存]**。

## 配置与Search&amp;Promote的连接 {#configuring-the-connection-to-search-promote}

配置一个或多个与Search&amp;Promote的连接，以便您的网页可以与服务交互。 要进行连接，您需要Search&amp;Promote帐户的成员标识和帐号。

**配置与Search&amp;Promote的连接**:

1. 从“工 **[!UICONTROL 具]** ”图标>“ **[!UICONTROL 部署]**”中，选 **[!UICONTROL 择“云服务”]**。

   此操作会将您带到云服务控制面板。 如果在本地计算机上，功能板的url将类似于：

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. 在“ [!UICONTROL 云服务] ”页面中，点按 **[!UICONTROL Adobe Search&amp;Promote]** 链接或 **[!UICONTROL Search&amp;Promote图标]** 。

1. 如果这是您首次配置Adobe Search&amp;Promote，请点按 **[!UICONTROL 立即配置]** ，打开创建 [!UICONTROL 配置面板] 。

   如果您想了解有关Search&amp;Promote的更多信息，请单击“了 **[!UICONTROL 解更多]** ”。

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 输入可 **[!UICONTROL 识别页面作者的标题]** ，然后输入唯一的 **[!UICONTROL 名称]**，然后点按创 **[!UICONTROL 建]**。

   此外，新创建的配置会显示在 **[!UICONTROL Cloud services控制面板]****** Adobe Search&amp;Promote列表项的“可用配置”下方。

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在“编 [!UICONTROL 辑组件] ”对话框中，将以下内容添加到字段：

   * **[!UICONTROL 成员·ID]**
   * **[!UICONTROL 帐号]**
   >[!NOTE]
   >
   >要自行获取此信息，请登录以下网页：
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
   >其中 **XXXXXXXXX** 与您的 **[!UICONTROL 成员id对应]** , **[!UICONTROL spYYYYYYYYYYYYYYYY与您的帐号对应。]**

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   当显示连接成功消息时，点按确 **[!UICONTROL 定]**。

   (连接后，按钮文本将变 **[!UICONTROL 为“重新连接到Search&amp;Promote]**”。)

1. 点按 **[!UICONTROL 确定]**。 此时会显示“Search&amp;Promote设置”页，其中显示您刚刚创建的配置。

## 配置数据中心 {#configuring-the-data-center}

如果您的Search&amp;Promote帐户在亚洲或欧洲，您需要更改默认数据中心，以便它指向正确的数据中心（默认数据中心针对北美帐户）。

**配置数据中心**:

1. 导航到Web控制台，网址为 `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 根据服务器的位置，将URI更改为以下任一选项：

   * 北美： [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * 亚太： [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 点按&#x200B;**[!UICONTROL 保存]**。

## 将Search&amp;Promote组件添加到Sidekick {#adding-search-promote-components-to-sidekick}

在“ [!UICONTROL 设计] ”模式中，编辑 **[!UICONTROL par组件]** ，以允许Sidekick中的Search&amp;Promote [!UICONTROL 组件]。 (See the [Components](/help/sites-developing/components.md) documentation for more information.)

有关使用组件的信息，请参 [阅将Search&amp;Promote功能添加到网页](/help/sites-authoring/search-and-promote.md)。

## 指定页面使用的Search&amp;Promote服务 {#specifying-the-search-promote-service-that-your-pages-use}

配置网页，使其使用特定的Search&amp;Promote服务。 Search&amp;Promote组件会自动使用其主机页面的服务。

为页面配置Search&amp;Promote属性时，所有子页面都会继承设置。 如果需要，您可以配置子页面以覆盖继承的设置。

>[!NOTE]
>
>必须已配置服务连接。 请参 [阅配置与Search&amp;Promote的连接](#configuring-the-connection-to-search-promote)。

1. 打开“页 **[!UICONTROL 面属性]** ”对话框。 例如，在“网 **[!UICONTROL 站]** ”页面上，右键单击页面，然后单击“属 **[!UICONTROL 性”]**。

1. 单击“ **[!UICONTROL 云服务]** ”选项卡。

1. 要禁用从父页面继承云服务配置的功能，请单击继承路径旁的挂锁图标。

   ![松皮继承锁](assets/sandpinheritpadlock.png)

1. 单 **[!UICONTROL 击“添加服务]**”，选 **[!UICONTROL 择“Adobe Search&amp;Promote]**”，然后单击“ **[!UICONTROL 确定”]**。

1. 选择Search&amp;Promote帐户的连接配置，然后单击“确 **[!UICONTROL 定”]**。

## Product Feed {#product-feed}

通过Search&amp;Promote集成，您可以执行以下操作：

* 使用 [!UICONTROL eCommerce] API，独立于基础存储库结构和商务平台。
* 利用 [!UICONTROL Search&amp;Promote的Index Connector] （索引连接器）功能以XML格式提供产品源。
* 利用 [!UICONTROL Search&amp;Promote的Remote Control] （远程控制）功能执行产品源的按需或计划请求。
* 不同Search&amp;Promote帐户的源生成，配置为云服务配置。

有关详细信息，请参 [阅产品信息源](/help/sites-administering/product-feed.md)。
