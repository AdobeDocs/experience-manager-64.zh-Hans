---
title: 电子商务
seo-title: 电子商务
description: 'AEM eCommerce可帮助营销人员在Web、移动和社交接触点中提供品牌化的个性化购物体验。 '
seo-description: 'AEM eCommerce可帮助营销人员在Web、移动和社交接触点中提供品牌化的个性化购物体验。 '
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: 商务集成框架
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 2%

---

# 电子商务{#ecommerce}

* [概念 ](/help/sites-administering/concepts.md)
* [管理（一般）](/help/sites-administering/generic.md)
* [SAPCommerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

Adobe提供了商务集成框架的两个版本：

|  | CIF上线 | CIF云 |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| 支持的 AEM 版本 | AEM on-prem或AMS 6.x | AEM AMS 6.4和6.5 |
| 后端 | - AEM、Java <br> — 整体集成、预构建映射（模板）<br> - JCR存储库 | -Magento<br>- Java和Javascript <br> — 无商务数据存储在JCR存储库中 |
| 前端 | AEM服务器端渲染的页面 | 混合页面应用程序（混合渲染） |
| 产品目录 | - AEM <br>中的产品导入器、编辑器、缓存 — 具有AEM或代理页面的常规目录 |  — 无产品导入<br> — 通用模板<br> — 通过连接器按需数据 |
| 可扩展性 |  — 最多可支持数百万种产品（取决于用例）<br> - Dispatcher上的缓存 |  — 无卷限制<br> - Dispatcher或CDN上的缓存 |
| 标准化数据模型 | 否 | 是，MagentoGraphQL架构 |
| 可用性 | 是：<br> - SAPCommerce Cloud(扩展已更新以支持AEM 6.4和Hybris 5（默认），并维护与Hybris 4 <br> - SalesforceCommerce Cloud(连接器开源支持AEM 6.4)的兼容性 | 是，可通过GitHub通过开源。 <br> Magento Commerce(支持Magento2.3.2（默认）并与Magento2.3.1兼容)。 |
| 何时使用 | 有限用例：对于可能需要导入小型静态目录的情况 | 大多数用例中的首选解决方案 |

电子商务与产品信息管理(PIM)一起处理网站的活动，重点是通过在线商店销售产品：

* 产品的创建、生命周期和过期
* 价格管理
* 交易管理
* 管理整个目录
* 实时和集中存储记录
* Web界面

AEM eCommerce可帮助营销人员在Web、移动和社交接触点中提供品牌化的个性化购物体验。 AEM创作环境允许您根据目标访客上下文和促销策略自定义页面和组件；例如：

* 产品页面
* 购物车组件
* 结帐组件

该实施允许实时访问产品信息。 这可用于强制执行：

* 产品信息完整性
* 定价
* 库存库存
* 购物车状态的变化

>[!NOTE]
>
>要将集成框架与外部电子商务提供程序结合使用，您首先需要安装所需的包。 有关更多信息，请参阅[部署eCommerce](/help/sites-deploying/ecommerce.md)。
>
>有关扩展电子商务功能的信息，请参阅[开发电子商务](/help/sites-developing/ecommerce.md)。

## 主要功能{#main-features}

AEM电子商务提供：

* 许多&#x200B;**现成的AEM组件**&#x200B;以说明可为项目实现的目标：

   * 产品显示
   * 购物车
   * 结帐
   * 最近查看的产品
   * 优惠券
   * 其他

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >AEM提供的集成框架还允许您为独立于特定电子商务引擎的商务功能构建其他AEM组件。

* **搜索**  — 使用以下任一方式：

   * AEM搜索
   * 电子商务系统的探索
   * 第三方搜索(如Search&amp;Promote)
   * 或两者的组合。

   ![chlimage_1-151](assets/chlimage_1-151.png)

* 使用AEM功能&#x200B;**在多个渠道（无论是整个浏览器窗口还是移动设备）上显示您的内容**。 这会以访客所需的格式交付内容。

   ![chlimage_1-152](assets/chlimage_1-152.png)

* 能够根据[AEM电子商务框架&#x200B;](#the-framework)**开发您自己的集成实施。**

   当前可用的两个实施都基于相同的基础构建 — 基于常规API（框架）。 实施新集成仅涉及实施集成所需的功能。 前端组件可供任何新实施使用，因为它们使用的是接口（因此与实施无关）。

* 根据购物者数据和活动&#x200B;**开发**&#x200B;体验驱动型商务的可能性。 这样，您就可以了解许多情景：

   * 例如，当总订单超过特定金额时，可能会降低运输成本。
   * 另一种方法可能允许您提供使用用户档案数据（例如位置）的季节性选件。 然后，可根据其他因素在必要时再次突出显示这些内容。

   在以下示例中，显示了一个Teaser，因为购物车的内容小于$75:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   当购物车内容超过$75时，可以更改此设置：

   ![chlimage_1-154](assets/chlimage_1-154.png)

* 以及其他功能，包括：

   * 会话期间保留的购物车内容
   * 完整订单历史记录
   * 快速目录更新

## 框架{#the-framework}

[Concepts](/help/sites-administering/concepts.md)部分更详细地介绍了框架，但以下部分提供了框架的高级、高速视图：

### 什么？ {#what}

* 集成框架提供了API、一系列用于说明功能的组件以及多个用于提供连接方法示例的扩展。
* 该框架提供了项目实施所需的基本结构。
* 该框架是可扩展的。
* 该框架不提供现成可用的站点。 要使框架符合您的规范，始终需要进行一定量的开发工作。

### 为什么？ {#why}

* 提供快速实现自定义电子商务网站所需的基本机制。
* Tp提供开发真实电子商务网站所需的灵活性。
* 说明最佳实践。
