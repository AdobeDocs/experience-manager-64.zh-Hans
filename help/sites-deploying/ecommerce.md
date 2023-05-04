---
title: 电子商务概述
seo-title: eCommerce Overview
description: AEM通用电子商务作为标准安装的一部分提供，并为您提供电子商务框架的完整功能。
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
feature: Commerce Integration Framework
exl-id: d84cd0ec-4586-45c1-a07a-a4d50fcbb629
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 4%

---

# 电子商务概述{#ecommerce-overview}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM通用电子商务作为标准安装的一部分提供，并为您提供电子商务框架的完整功能。

Adobe提供了商务集成框架的两个版本：

|  | CIF上线 | CIF云 |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| 支持的 AEM 版本 | AEM on-prem或AMS 6.x | AEM AMS 6.4和6.5 |
| 后端 | - AEM、Java <br>  — 整体集成、预构建映射（模板）<br> - JCR存储库 | -Magento <br>- Java和Javascript <br>- JCR存储库中未存储商务数据 |
| 前端 | AEM服务器端渲染的页面 | 混合页面应用程序（混合渲染） |
| 产品目录 |  — 产品导入器，编辑器，AEM中的缓存 <br> — 包含AEM或代理页面的常规目录 |  — 无产品导入 <br> — 通用模板 <br> — 通过连接器按需数据 |
| 可扩展性 |  — 最多可支持数百万种产品（取决于用例） <br> - Dispatcher上的缓存 |  — 无卷限制 <br> — 在Dispatcher或CDN上缓存 |
| 标准化数据模型 | 否 | 是，MagentoGraphQL架构 |
| 可用性 | 是：<br> - SAPCommerce Cloud(扩展已更新以支持AEM 6.4和Hybris 5（默认），并维护与Hybris 4的兼容性 <br>- SalesforceCommerce Cloud(连接器开源支持AEM 6.4) | 是，可通过GitHub通过开源。 <br> Magento Commerce(支持Magento2.3.2（默认）并与Magento2.3.1兼容)。 |
| 何时使用 | 有限用例：对于可能需要导入小型静态目录的情况 | 大多数用例中的首选解决方案 |


## 部署其他实施 {#deploying-other-implementations}

* [SAPCommerce Cloud](/help/sites-deploying/sap-commerce-cloud.md)
* [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>有关概念和管理电子商务实施的信息，请参阅 [管理电子商务](/help/sites-administering/ecommerce.md).
>
>有关扩展电子商务功能的信息，请参阅 [发展电子商务](/help/sites-developing/ecommerce.md).
