---
title: 与 Adobe Analytics 集成
seo-title: 与 Adobe Analytics 集成
description: 了解如何将AEM与Adobe Analytics集成。
seo-description: 了解如何将AEM与Adobe Analytics集成。
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
translation-type: tm+mt
source-git-commit: ee380780bb7b62d348051b29edb9d13e14407377

---


# 与 Adobe Analytics 集成{#integrating-with-adobe-analytics}

将Adobe Analytics与AEM集成后，您可以跟踪网页活动：

* Adobe Analytics配置使AEM能够使用Adobe Analytics进行身份验证。
* 框架可标识发送到Adobe Analytics报告包的数据。

数据包括页面数据和用户数据；例如：

* AEM组件收集的数据
* 链接点击
* 视频使用信息
* Adobe Analytics的页面访问次数

以下页面可帮助您配置集成：

* [连接到Adobe Analytics和创建框架](/help/sites-administering/adobeanalytics-connect.md)
* [为Adobe Analytics配置链接跟踪](/help/sites-administering/adobeanalytics-link.md)
* [使用Adobe Analytics属性映射组件数据](/help/sites-administering/adobeanalytics-mapping.md)
* [为Adobe Analytics配置视频跟踪](/help/sites-administering/adobeanalytics-video.md)

您还可以使用 [加入向导](/help/sites-administering/opt-in.md) ，轻松执行集成。

>[!NOTE]
>
>另请参阅操作方法文章：使 [用DTM将AEM与Adobe Target和Adobe Analytics集成](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html)。

## 更多信息 {#further-information}

请参阅：

* [扩展Adobe Analytics集成](/help/sites-developing/extending-analytics.md) ，以了解有关开发收集用户数据的组件和自定义Adobe Analytics框架的信息。
* 有关Adobe Analytics集成疑难 [解答的信息，请参阅知识库文章](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html),Adobe Analytics集成——疑难解答问题。

>[!NOTE]
>
>如果您使用的是具有自定义代理配置的 Adobe Analytics，则需要配置 **Apache HTTP Client** 代理配置所需的[两个 OSGi 包](/help/sites-deploying/configuring-osgi.md)（例如，使用 Web Console）。这两个包都是必需的，因为 AEM 的某些功能使用 3.x API，而其他功能使用 4.x API。配置：
>
>* **Day Commons HTTP Client 3.1** ，配置3.x API;\
   >  例如， [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP Components代理配置** ，用于配置4.x API;\
   >  例如， [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



