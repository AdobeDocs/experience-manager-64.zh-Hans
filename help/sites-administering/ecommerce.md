---
title: 电子商务
seo-title: 电子商务
description: 'AEM eCommerce帮助营销人员跨网络、移动和社交接触点提供品牌化、个性化的购物体验。 '
seo-description: 'AEM eCommerce帮助营销人员跨网络、移动和社交接触点提供品牌化、个性化的购物体验。 '
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
translation-type: tm+mt
source-git-commit: eb1ae2b4910e7adef48865996db4837175f588d9
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 2%

---


# 电子商务{#ecommerce}

* [概念 ](/help/sites-administering/concepts.md)
* [管理（一般）](/help/sites-administering/generic.md)
* [SAPCommerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

Adobe提供了两个版本的商务集成框架：

|  | CIF在预装 | CIF云 |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| 支持的 AEM 版本 | AEM on-prem或AMS 6.x | AEM AMS 6.4和6.5 |
| 后端 | - AEM、Java <br> -整体集成、预构建映射（模板）<br> - JCR存储库 | -Magento <br>- Java和Javascript <br>-无商务数据存储在JCR存储库中 |
| 前端 | AEM服务器端呈现的页面 | 混合页面应用程序（混合渲染） |
| 产品目录 | -产品导入程序、编辑器、AEM中的 <br>缓存——带有AEM或代理页面的常规目录 | -无产品导 <br>入——通用模 <br>板——通过连接器点播数据 |
| 可伸缩性 | -最多可支持几百万种产品（取决于用例）- <br> Dispatcher上的缓存 | -无卷限制- <br>在Dispatcher或CDN上缓存 |
| 标准化数据模型 | 否 | 是，Magento图QL模式 |
| 可用性 | 是：<br> - SAPCommerce Cloud(Extension updated to support AEM 6.4 and Hybris 5(default)and maintains compatibility with Hybris 4 <br>- SalesforceCommerce Cloud(Connector open-sourced to support AEM 6.4) | 是，通过GitHub开放源。 <br> Magento Commerce(支持Magento2.3.2（默认），并兼容Magento2.3.1)。 |
| 何时使用 | 有限用例： 对于需要导入小型静态目录的情况 | 大多数用例中的首选解决方案 |

电子商务与产品信息管理(PIM)一起，处理网站的活动，重点通过在线商店销售产品：

* 产品的创建、生命周期和过时
* 价格管理
* 交易管理
* 管理整个目录
* 实时和集中的存储记录
* Web界面

AEM eCommerce帮助营销人员跨网络、移动和社交接触点提供品牌化、个性化的购物体验。 AEM创作环境允许您根据目标访客环境和销售战略自定义页面和组件； 例如：

* 产品页面
* 购物车组件
* 结帐组件

该实施允许对产品信息进行实时访问。 这可用于强制：

* 产品信息完整性
* 定价
* 库存库存
* 购物车状态变化

>[!NOTE]
>
>要将集成框架与外部电子商务提供商一起使用，您首先需要安装所需的包。 有关详细信息，请参 [阅部署电子商务](/help/sites-deploying/ecommerce.md)。
>
>有关扩展电子商务功能的信息，请参 [阅开发电子商务](/help/sites-developing/ecommerce.md)。

## 主要功能 {#main-features}

AEM eCommerce提供：

* 大量现 **成的AEM组件** ，用于说明可以为项目实现哪些目标：

   * 产品显示
   * 购物车
   * 结帐
   * 最近查看的产品
   * 优惠券
   * 和其他

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >AEM提供的集成框架还允许您为独立于特定电子商务引擎的商务功能构建其他AEM组件。

* **搜索** -使用以下任一方式：

   * AEM搜索
   * 电子商务系统的探索
   * 第三方搜索(如Search&amp;Promote)
   * 或其组合。

   ![chlimage_1-151](assets/chlimage_1-151.png)

* 使用AEM功能在多 **个渠道上展示您的内容**，无论是整个浏览器窗口还是移动设备。 这以您的访客需要的格式提供您的内容。

   ![chlimage_1-152](assets/chlimage_1-152.png)

* 能够基于 **AEM eCommerce框架开发您自己[的集成实施](#the-framework)**。

   当前可用的两种实现都基于相同的基础构建——在常规API（框架）之上。 实施新集成只涉及实施您的集成需要的功能。 任何新的实现都可以使用前端组件，因为它们使用接口（因此与实现无关）。

* 基于购物者数 **据和活动开发体验驱动型商务的可能性**。 这使您能够实现许多场景：

   * 例如，当订单总额超过特定金额时，可能会降低运输成本。
   * 另一种方式可能允许您提供使用优惠数据的季节性用户档案（例如位置）。 然后，根据其他因素，根据需要再次突出显示这些内容。

   在以下示例中，一个Teaser显示为购物车的内容小于$75:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   当购物车内容超过$75时，可以更改此设置：

   ![chlimage_1-154](assets/chlimage_1-154.png)

* 其他功能包括：

   * 跨会话保留的购物车内容
   * 完整订单历史记录
   * 快速目录更新

## 框架 {#the-framework}

概 [念部分](/help/sites-administering/concepts.md) 更详细地介绍了框架，但下面提供了框架的高级、高速视图:

### 什么？ {#what}

* 集成框架提供API、用于说明功能的一系列组件以及提供连接方法示例的几个扩展。
* 该框架提供了项目实施所需的基本结构。
* 该框架是可扩展的。
* 框架不提供现成的、随时可用的站点。 总是需要一定量的开发工作来调整框架，使其符合您的规范。

### 为什么？ {#why}

* 提供快速实现自定义电子商务站点所需的基本机制。
* 提供开发真实电子商务站点所需的灵活性。
* 说明最佳实践。

