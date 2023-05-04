---
title: 将反向链接过滤器设置为允许空
seo-title: Setting Your Referrer Filter to Allow Empty
description: 请阅读本页以了解反向链接过滤器。 为了允许AEM Mobile应用程序查看器查看创作实例上的应用程序，您需要将HTML反向链接过滤器设置为“允许为空”。
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 5%

---

# 将反向链接过滤器设置为允许空{#setting-your-referrer-filter-to-allow-empty}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（例如React）的项目使用SPA编辑器。 [了解详情](/help/sites-developing/spa-overview.md).

为了允许AEM Mobile应用程序查看器查看创作实例上的应用程序，您需要将HTML反向链接过滤器设置为“允许为空”。

如果您不打算使用应用程序查看器来查看处于开发和暂存状态的应用程序，则无需更改反向链接过滤器的默认设置。

在运行的AEM创作实例中，导航到： [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) 和搜索“Apache Sling反向链接过滤器”。 单击以编辑反向链接过滤器，并选中“允许空”复选框（请参阅下图）。 下一步，单击保存按钮并关闭浏览器页面。

![反向链接过滤器设置](assets/chlimage_1-106.png)
