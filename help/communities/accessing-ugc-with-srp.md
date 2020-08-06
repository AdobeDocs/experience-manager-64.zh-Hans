---
title: 使用SRP访问UGC
seo-title: 使用SRP访问UGC
description: 将站点配置为使用ASRP或MSRP时，实际UGC不会存储在AEM节点存储(JCR)中
seo-description: 将站点配置为使用ASRP或MSRP时，实际UGC不会存储在AEM节点存储(JCR)中
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# 使用SRP访问UGC {#accessing-ugc-with-srp}

## 关于SRP {#about-srp}

所有AEM Communities组件和功能都构建 [在社交组件框架(SCF)上](scf.md)，该框架调用SocialResourceProvider API访问所有用户生成的内容(UGC)。

在创建社区站点之前， [存储资源提供者](working-with-srp.md) (SRP)必须配置为选择与基础拓扑一致的 [实现](topologies.md)。 SRP实现基于三个存储选项：

1. [ASRP](asrp.md) -Adobe点播存储
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## 关于UGC存储 {#about-ugc-storage}

UGC存储的重要信息是，当站点配置为使用ASRP或MSRP时，实际UGC不会存储在AEM节 [点存储](../../help/sites-deploying/data-store-config.md) (JCR)中。

虽然JCR中可能存在使UGC阴影的节点，以提供有用的元数据，但不要将这些节点与实际UGC混淆。

请参 [阅存储资源提供程序概述。](srp.md)

## 最佳实践 {#best-practice}

在开发自定义组件时，开发人员应当注意独立于当前选择的拓扑进行编码，从而保留将来迁移到新拓扑的灵活性。

### 假定JCR不可用 {#assume-jcr-not-available}

应避免特定于JCR的方法。

使用方法：

* Sling API(Sling Resource)
   * 不要假设存在JCR节点

* OSGi事件
   * 不要假定存在JCR事件

* [社交资源实用程序](socialutils.md#socialresourceutilities-package)
* [SCF实用程序](socialutils.md#scfutilities-package)

避免的方法：

* 节点API
* JCR事件
* 工作流启动器(使用JCR事件)

### 使用搜索集合 {#use-search-collections}

不同的SRP可以有不同的本机查询语言。 建议使用com.adobe.cq.so [cial.ugc.api包中的方法](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) ，调用相应的查询语言。

有关详细信息，请参 [阅Search Essentials](search-implementation.md)。

## 资源 {#resources}

* [社区内容存储](working-with-srp.md) -讨论UGC公用商店的可用SRP选项
* [存储资源提供程序概述](srp.md) -简介和存储库使用概述
* [SRP和UGC Essentials](srp-and-ugc.md) - SRP实用程序方法和示例
* [Search Essentials](search-implementation.md) —— 用于搜索UGC的基本信息
* [SocialUtils重构](socialutils.md) -将已弃用的实用程序方法映射到当前SRP实用程序方法
