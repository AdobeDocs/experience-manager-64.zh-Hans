---
title: 在生产就绪模式下运行AEM
seo-title: 在生产就绪模式下运行AEM
description: 了解如何在生产就绪模式下运行AEM。
seo-description: 了解如何在生产就绪模式下运行AEM。
uuid: f48c8bae-c72f-4772-967e-f1526f096399
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 32da99f0-f058-40ae-95a8-2522622438ce
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---


# 在生产就绪模式下运行AEM{#running-aem-in-production-ready-mode}

在AEM 6.1中，Adobe引入了新的运行 `"nosamplecontent"` 模式，旨在自动执行准备AEM实例以部署到生产环境所需的步骤。

新的运行模式不仅将自动配置实例以符合安全清单中描述的安全最佳实践，还将删除该过程中的所有示例geometrixx应用程序和配置。

>[!NOTE]
>
>由于实际原因，AEM生产就绪模式将仅涵盖保护实例所需的大多数任务，因此强烈建议您在与生产环境一起 [使用前](/help/sites-administering/security-checklist.md) ，先查阅安全核对清单。
>
>另外，请注意，在生产就绪模式中运行AEM将有效地禁用对CRXDE Lite的访问。 如果出于调试目的需要，请参阅在AEM [中启用CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md)。

![chlimage_1-83](assets/chlimage_1-83.png)

要在生产就绪模式下运行AEM，您只需通过runmode开关将 `nosamplecontent``-r` 添加到现有启动参数：

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

例如，您可以使用生产就绪启动具有MongoDB持久性的创作实例，如下所示：

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## 更改生产就绪模式的一部分 {#changes-part-of-the-production-ready-mode}

更具体地说，在生产就绪模式下运行AEM时将执行以下配置更改：

1. 默认 **情况下，在生产就绪模** 式下，CRXDE支持包( `com.adobe.granite.crxde-support`)处于禁用状态。 它可以随时从Adobe公共Maven存储库安装。 AEM 6.1需要版本3.0.0。

1. 对 **存储库()捆绑的Apache Sling Simple WebDAV** Access( `org.apache.sling.jcr.webdav`)仅在作者实例 **上可用** 。

1. 新创建的用户需要在首次登录时更改口令。 这不适用于管理员用户。
1. **Apache Java** Script Handler禁用 **了“生成调试信息”**。

1. **映射的内容** 和 **“生成调试信息** ”对于Apache Sling JSP脚 **本处理程序处于禁用状态**。

1. Day CQ **WCM过滤器** (Day CQ WCM Filter `edit` )设置为作 **者上** 和发布 `disabled` 实 **实例上** 。

1. **AdobeGranite HTML库管理器** 配置了以下设置：

   1. **小型：** `enabled`
   1. **调试：** `disabled`
   1. **Gzip:** `enabled`
   1. **时间：** `disabled`

1. 默 **认情况下** ,Apache SlingGETServlet设置为支持安全配置，如下所示：

| **配置** | **创作** | **发布** |
|---|---|---|
| TXT再现 | 已禁用 | 已禁用 |
| HTML再现 | 已禁用 | 已禁用 |
| JSON再现 | 已启用 | 已启用 |
| XML再现 | 已禁用 | 已禁用 |
| json.maximumresults | 1000 | 100 |
| 自动索引 | 已禁用 | 已禁用 |

