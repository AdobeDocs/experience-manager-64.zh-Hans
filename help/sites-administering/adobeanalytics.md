---
title: 与 Adobe Analytics 集成
seo-title: Integrating with Adobe Analytics
description: 了解如何将AEM与Adobe Analytics集成。
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 61%

---

# 与 Adobe Analytics 集成{#integrating-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

将Adobe Analytics和AEM集成后，您可以跟踪网页活动：

* Adobe Analytics 配置可让 AEM 通过 Adobe Analytics 进行身份验证。
* 框架标识发送到 Adobe Analytics 报告包的数据。

数据包括页面数据和用户数据；例如：

* AEM 组件收集的数据
* 链接点击次数
* 视频使用信息
* 来自 Adobe Analytics 的页面访问次数

以下页面可帮助您配置集成：

* [连接到Adobe Analytics和创建框架](/help/sites-administering/adobeanalytics-connect.md)
* [为 Adobe Analytics 配置链接跟踪](/help/sites-administering/adobeanalytics-link.md)
* [建立组件数据与 Adobe Analytics 属性的映射](/help/sites-administering/adobeanalytics-mapping.md)
* [为 Adobe Analytics 配置视频跟踪](/help/sites-administering/adobeanalytics-video.md)

您还可以使用 [选择加入向导](/help/sites-administering/opt-in.md) 以轻松执行集成。

>[!NOTE]
>
>另请参阅操作方法文章： [使用DTM将AEM与Adobe Target和Adobe Analytics集成](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## 更多信息 {#further-information}

请参阅：

* [扩展 Adobe Analytics 集成](/help/sites-developing/extending-analytics.md)，了解有关开发用于收集用户数据的组件和自定义 Adobe Analytics 框架的信息。
* 知识库文章 [Adobe Analytics 集成 – 解决问题](https://helpx.adobe.com/cn/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)，了解有关排查 Adobe Analytics 集成问题的信息。

>[!NOTE]
>
>如果您使用的是具有自定义代理配置的 Adobe Analytics，则需要配置 **Apache HTTP Client** 代理配置所需的[两个 OSGi 包](/help/sites-deploying/configuring-osgi.md)（例如，使用 Web Console）。这两个包都是必需的，因为 AEM 的某些功能使用 3.x API，而其他功能使用 4.x API。配置：
>
>* **Day Commons HTTP 客户端 3.1** 以配置 3.x API；\
   >  例如， [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP 组件代理配置**&#x200B;以配置 4.x API；
>
>  例如， [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
