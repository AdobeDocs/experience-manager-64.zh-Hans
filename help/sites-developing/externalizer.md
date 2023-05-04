---
title: 外部化URL
seo-title: Externalizing URLs
description: Externalizer是一种OSGI服务，它允许您以编程方式将资源路径转换为外部和绝对URL
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# 外部化URL{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在AEM中， **外部器** 是一种OSGi服务，它允许您以编程方式转换资源路径(例如， `/path/to/my/page`)到外部和绝对URL(例如， `https://www.mycompany.com/path/to/my/page`)，方法是使用预配置的DNS来预定路径。

由于实例在Web层后面运行时无法知道其外部可见URL，并且由于有时必须在请求范围之外创建链接，因此此服务提供了一个配置和构建这些外部URL的中心位置。

本页介绍如何配置 **外部器** 服务和使用方法。 有关更多详细信息，请参阅 [Javaocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## 配置外部器服务 {#configuring-the-externalizer-service}

的 **外部器** 服务允许您集中定义多个域，这些域可用于以编程方式为资源路径添加前缀。 每个域都由一个唯一名称来标识，该名称用于以编程方式引用该域。

为定义域映射 **外部器** 服务：

1. 通过导航到配置管理器 **工具**，则 **Web控制台**，或输入 `https://<host>:<port>/system/console/configMgr.`
1. 单击 **Day CQ链接外部器** 打开配置对话框。

   >[!NOTE]
   >
   >配置的直接链接是 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 定义域映射：映射由唯一名称组成，该名称可在代码中用于引用域、空格和域：

   `<unique-name> [scheme://]server[:port][/contextpath]`，其中：

   * **方案** 通常为http或https，但也可以是ftp等。;如果需要，可使用https强制执行https链接；如果客户端代码在请求将URL外部化时不覆盖方案，则将使用该URL。
   * **服务器** 是主机名（可以是域名或ip地址）。
   * **端口** （可选）是端口号。
   * **contextpath** （可选）仅当AEM作为Web应用程序安装在其他上下文路径下时才进行设置。

   例如：`production https://my.production.instance`

   以下映射名称是预定义的，且必须始终设置，因为AEM依赖于这些映射名称：

   * **本地**  — 本地实例
   * **作者**  — 创作系统DNS
   * **发布**  — 面向公众的网站DNS

   >[!NOTE]
   >
   >自定义配置允许您添加新类别，如“生产”、“暂存”，甚至外部非AEM系统（如“my-internal-webservice”），这有助于避免在项目代码库的不同位置对此类URL进行硬编码。

1. 单击 **保存** 以保存更改。

>[!NOTE]
>
>Adobe建议您 [将配置添加到存储库](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## 使用外部器服务 {#using-the-externalizer-service}

此部分显示一些示例，说明 **外部器** 服务。

**要在JSP中获取Externalizer服务，请执行以下操作：**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**要将路径外部化为“publish”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

假定域映射“ `publish https://www.website.com`&quot;, myExternaledUrl的结尾为值&quot; `https://www.website.com/contextpath/my/page.html`&quot;

**要将路径外部化为“author”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

假定域映射“ `author https://author.website.com`&quot;, myExternaledUrl的结尾为值&quot; `https://author.website.com/contextpath/my/page.html`&quot;

**要将路径外部化为“本地”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

假定域映射“ `local https://publish-3.internal`&quot;, myExternaledUrl的结尾为值&quot; `https://publish-3.internal/contextpath/my/page.html`&quot;

您可以在 [Javaocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
