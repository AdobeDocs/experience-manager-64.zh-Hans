---
title: 内容架构
seo-title: Content Architecture
description: 构建内容的提示（提示 — 所有内容都是内容）
seo-description: Tips for architecting your content in Adobe Experience Manager (AEM). (hint - everything is content)
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
exl-id: 9fff10fb-4b65-459a-a7a7-6ee9c0c26bf5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 1%

---

# 内容架构{#content-architecture}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 遵循David的模式 {#follow-david-s-model}

David&#39;s Model是多年前由David Nuescheler写的，但今天的想法仍然成立。 David&#39;s Model的主要原则如下：

* 数据先于数据，后于结构。 也许吧。
* 驱动内容层次结构，不要让它发生。
* 工作区适用于 `clone()`, `merge()`和 `update()`.
* 请注意同名同级。
* 参照被认为有害。
* 文件是文件。
* 身份是邪恶的。

David&#39;s Model可在Jackrabbit维基百科上找到，网址为 [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### 一切内容 {#everything-is-content}

所有内容都应存储在存储库中，而不是依赖单独的第三方数据源（如数据库）。 这适用于创作内容、二进制数据（如图像、代码、配置等）。 这允许我们使用一组API来管理所有内容并通过复制来管理此内容的促销活动。 我们还获得了备份、日志记录等的单一来源。

### 使用“内容模型优先”设计原则 {#use-the-content-model-first-design-principle}

构建新功能时，请始终先设计JCR内容结构，然后使用默认的Sling Servlet查看内容的读写操作。 这样，您就可以确保实施在开箱即用的访问控制机制中正常工作，并避免生成不必要的CRUD样式Servlet。

### RESTful {#be-restful}

Servlet应根据resourceTypes而不是路径进行定义。 这样，就可以使用JCR访问控制，遵守REST原则，以及使用请求中提供给我们的资源和资源解析程序。 这还允许我们更改在服务器端呈现URL的脚本，而无需从客户端更改任何URL，同时从客户端隐藏服务器端实施详细信息，以增加安全性。

### 避免定义新的节点类型 {#avoid-defining-new-node-types}

节点类型在基础结构层中的工作级别较低，大多数要求都可以通过使用分配给nt:unstructured、oak:Unstructured、sling:Folder或cq:Page节点类型的sling:resourceType来满足。 节点类型等同于存储库中的架构，而且更改节点类型可能会非常昂贵。

### 遵循JCR中的命名约定 {#adhere-to-naming-conventions-in-the-jcr}

遵守命名约定将增加代码库的一致性，降低缺陷的发生率，并提高系统中开发人员的工作速度。 Adobe在开发AEM时使用以下约定：

* 节点名称

   * 全部小写
   * 使用连字符的单词分隔

* 属性名称

   * 驼峰式，以小写字母开头

* 组件(JSP/HTML)

   * 全部小写
   * 使用连字符的单词分隔
