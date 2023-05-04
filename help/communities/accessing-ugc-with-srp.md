---
title: 使用SRP访问UGC
seo-title: Accessing UGC with SRP
description: 将站点配置为使用ASRP或MSRP时，实际UGC不会存储在AEM节点存储(JCR)中
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 1%

---

# 使用SRP访问UGC {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 关于SRP {#about-srp}

所有AEM Communities组件和功能都基于 [社会构成框架](scf.md)，调用SocialResourceProvider API以访问所有用户生成的内容(UGC)。

在创建社区站点之前， [存储资源提供程序(SRP)](working-with-srp.md) 必须配置为选择与基础一致的实施 [拓扑](topologies.md). SRP实施基于三个存储选项：

1. [ASRP](asrp.md) -Adobe按需存储
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## 关于UGC存储 {#about-ugc-storage}

有关UGC存储的重要信息是，当站点配置为使用ASRP或MSRP时，实际UGC不会存储在AEM中 [节点存储](../../help/sites-deploying/data-store-config.md) (JCR)。

虽然JCR中可能存在将UGC阴影化以提供有用元数据的节点，但不要将这些节点与实际UGC混淆。

请参阅 [存储资源提供程序概述。](srp.md)

## 最佳实践 {#best-practice}

在开发自定义组件时，开发人员应当谨慎地进行编码，而不依赖于当前选择的拓扑，从而保留将来迁移到新拓扑的灵活性。

### 假定JCR不可用 {#assume-jcr-not-available}

应避免使用特定于JCR的方法。

使用方法：

* Sling API（Sling资源）
   * 不要假定存在JCR节点

* OSGi事件
   * 请勿假定存在JCR事件

* [社交资源实用程序](socialutils.md#socialresourceutilities-package)
* [SCF实用程序](socialutils.md#scfutilities-package)

避免方法：

* 节点API
* JCR事件
* 工作流启动器（使用JCR事件）

### 使用搜索收藏集 {#use-search-collections}

不同的SRP可以具有不同的本机查询语言。 建议使用 [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) 包来调用相应的查询语言。

有关更多信息，请参阅 [搜索要点](search-implementation.md).

## 资源 {#resources}

* [社区内容存储](working-with-srp.md)  — 讨论UGC公用存储的可用SRP选项
* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [搜索要点](search-implementation.md)  — 搜索UGC的基本信息
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法
