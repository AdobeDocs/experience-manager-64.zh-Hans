---
title: 解决方案集成
seo-title: Solutions Integration
description: 进一步了解AEM中的解决方案集成。
seo-description: Learn more about Solutions Integration in AEM.
uuid: 3bf56b1b-284d-4f14-8974-0a595ece5028
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b5ff918d-08ab-4307-a807-693468fc083b
exl-id: 1ee7ccbd-8654-4d03-8a67-2c41863ae951
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 25%

---

# 解决方案集成{#solutions-integration}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

* [与Adobe Marketing Cloud集成](/help/sites-administering/marketing-cloud.md)
* [与第三方服务集成](/help/sites-administering/third-party-services.md)
* [Analytics与外部提供程序](/help/sites-administering/external-providers.md)
* [目录制作者](/help/sites-administering/catalog-producer.md)
* [SharePoint Connector](/help/sites-administering/sharepoint-connector.md)

以下信息介绍了如何将AEM与其他Adobe或第三方服务集成：

>[!NOTE]
>
>如果您将自定义代理配置与集成一起使用，则需要配置两个HTTP客户端代理配置，因为AEM的某些功能使用3.x API，而其他一些功能使用4.x API:
>
>* 3.x 通过 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) 进行配置
>* 4.x 通过 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) 进行配置
>

