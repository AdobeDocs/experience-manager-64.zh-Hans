---
title: 外部化URL
seo-title: 外部化URL
description: Externalizer是一种OSGI服务，它允许您以编程方式将资源路径转换为外部和绝对URL
seo-description: Externalizer是一种OSGI服务，它允许您以编程方式将资源路径转换为外部和绝对URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# 外部化URL{#externalizing-urls}

在AEM中， **Externalizer** 是一个OSGI服务，它允许您以编程方式转换资源路径(例如， `/path/to/my/page`)到外部和绝对URL(例如， `https://www.mycompany.com/path/to/my/page`)，方法是使用预配置的DNS预先固定路径。

由于实例在Web层后面运行时无法知道其外部可见URL，并且由于有时必须在请求范围之外创建链接，因此此服务提供了一个中心位置来配置这些外部URL并构建它们。

本页介绍如何配置 **Externalizer** 服务以及如何使用它。 有关详细信息，请参阅 [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)。

## 配置Externalizer服务 {#configuring-the-externalizer-service}

Externalizer **** 服务允许您集中定义多个域，这些域可用于以编程方式为资源路径添加前缀。 每个域都由唯一名称标识，该名称用于以编程方式引用该域。

要为Externalizer服务定义域 **映射** :

1. 依次通过工具、Web控 **制台**，导 **航到配置管**&#x200B;理器，或输入 `https://<host>:<port>/system/console/configMgr.`
1. 单击 **Day CQ Link Externalizer** （Day CQ链接外部器）以打开配置对话框。

   >[!NOTE]
   >
   >到配置的直接链接是 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 定义域映射： 映射由唯一名称组成，该名称可在代码中用于引用域、空格和域：

   `<unique-name> [scheme://]server[:port][/contextpath]`，其中：

   * **方案** 通常为http或https，但也可以是ftp等。; 根据需要使用https强制使用https链接； 如果客户端代码在请求将URL外部化时不覆盖方案，则将使用它。
   * **server** 是主机名（可以是域名或ip地址）。
   * **port** （可选）是端口号。
   * **contextpath** （可选）仅在AEM安装为位于其他上下文路径下的web应用程序时才设置。

   例如：`production https://my.production.instance`

   以下映射名称是预定义的，必须始终设置为AEM依赖它们：

   * **local** —— 本地实例
   * **author** —— 创作系统DNS
   * **发布** -面向公共的网站DNS

   >[!NOTE]
   >
   >自定义配置允许您添加新类别，如“生产”、“暂存”，甚至外部非AEM系统，如“my-internal-webservice”，并且有助于避免在项目代码库的不同位置对此类URL进行硬编码。

1. 单击 **保存** ，以保存更改。

>[!NOTE]
>
>Adobe建议 [将配置添加到存储库](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)。

## 使用Externalizer服务 {#using-the-externalizer-service}

本节介绍如何使用Externalizer **服务** 的几个示例。

**在JSP中获取Externalizer服务：**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**要将路径外置为“publish”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

假定域映射“ `publish https://www.website.com`”,myExternalizedUrl的结尾值为“ `https://www.website.com/contextpath/my/page.html`”。

**要将路径外置为“author”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

假定域映射“ `author https://author.website.com`”,myExternalizedUrl的结尾值为“ `https://author.website.com/contextpath/my/page.html`”。

**要将路径外置为“本地”域，请执行以下操作：**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

假定域映射“ `local https://publish-3.internal`”,myExternalizedUrl的结尾值为“ `https://publish-3.internal/contextpath/my/page.html`”。

您可以在Javadocs中找到更多 [示例](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html)。
