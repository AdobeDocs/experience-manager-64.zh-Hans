---
title: SRP —— 社区内容存储
seo-title: SRP —— 社区内容存储
description: 从AEM Communities6.1开始，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
seo-description: 从AEM Communities6.1开始，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP —— 社区内容存储 {#srp-community-content-storage}

## 简介 {#introduction}

从AEM Communities6.1开始，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中。 可以选择多个SRP选项，如ASRP、MSRP和JSRP。

与以前的版本不同，不会跨AEM实例反向／正向复制UGC。 相反，SRP使UGC能够直接从所有作者和发布实例中进行创建、读取、更新和删除(CRUD)操作，JSRP例外。

以下是每 [个SRP选项的特点](#characteristics-of-srp-options)，这是选择适当SRP和基础部署时决策过程的关 [键信息](topologies.md)。

有关使用UGC的SRP的详细信息，请参阅 [存储资源提供程序概述](srp.md)。

>[!NOTE]
>
>SRP仅适用于社区内容。 它不影响站点内容的存储位置(节[点存储](../../help/sites-deploying/data-store-config.md))，也不影响AEM实例之间用户注册、用户用户档案和用户组的安全处理(另请参阅 [管理用户数据](#managing-user-data))。

>[!CAUTION]
>
>从AEM 6.1开始， [UGC从不复制](#ugc-never-replicated)。
>
>当部署中不包括公用存储(如默认的 [JSRP](topologies.md#jsrp) 拓扑)时，UGC将仅在输入它的AEM发布或作者实例上可见。 仅当拓扑包含发布群集时，UGC才会在任何发布实例上可见。

## SRP选项的特点 {#characteristics-of-srp-options}

[ASRP -Adobe存储资源提供程序](asrp.md)\
通过此选项，UGC将远程保留在由Adobe托管和管理的云服务中。 它需要额外的许可证并与帐户代表一起为该特定许可证提供帐户。

* 需要Adobe提供并支持的关联云服务来存储社区内容
* 需要在特定地理位置（美国、欧洲、中东和非洲）选择数据中心
* 需要通过SRP API访问UGC的所有程序化访问
* 适用于TarMK发布场
* 当无意投资于本地存储时适用

>[!NOTE]
>
>在ASRP中，将附件上传到帖子（或评论）的限制为50 MB。

[MSRP - MongoDB存储资源提供程序](msrp.md)\
使用此选项，UGC将直接保留在本地MongoDB实例中。

* 需要本地的授权安装MongoDB以存储社区内容
* 需要本地安装Apache Solr
* 需要通过SRP API访问UGC的所有程序化访问
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适用

[DSRP —— 关系存储库资源提供程序](dsrp.md)\
使用此选项，UGC将直接保留在本地MySQL数据库实例中。

* 需要本地安装MySQL以存储社区内容
* 需要本地安装Apache Solr
* 需要通过SRP API访问UGC的所有程序化访问
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适用

[JSRP - JCR存储资源提供商](jsrp.md)\
使用默认选项，不存在通用商店。 UGC仅与输入UGC的AEM实例保留在同一JCR存储库中。

* 将社区内容存储在AEM作者的JCR存储库或发布实例中，该实例已发布到该实例
* 需要通过SRP API访问UGC的所有程序化访问
* 如果部署了多个发布实例，则需要发布群集（TarMK场中的发布实例之间没有复制机制）
* 仲裁仅在发布环境中执行（创作和发布之间没有反向／正向复制机制）
* 通常最适合开发、演示和培训

## 配置SRP {#configuring-srp}

根据基础部署指定默认存储选项是通过存储配 [置控制台](srp-config.md)。

有关每个选项的配置详细信息，请参阅：

* [ASRP -Adobe存储资源提供程序](asrp.md)
* [MSRP - MongoDB存储资源提供程序](msrp.md)
* [DSRP —— 关系存储库资源提供程序](dsrp.md)
* [JSRP - JCR存储资源提供商](jsrp.md)

如果未主动选择存储选项，则默认情况下启用JSRP。

## 附加信息 {#additional-information}

### UGC从未复制 {#ugc-never-replicated}

在创作环境中，作者创建页面内容并将其复制到发布环境。 当页面包含交互式AEM Communities功能（如评论、评论、论坛、博客或QnA）时，成员(在站点访客中签名)对发布实例的交互会导致用户生成的内容(UGC)进入发布环境。

以前，此社区内容会反向复制到作者实例，以及从作者复制到发布实例。 在具有反向和正向复制的AEM实例之间保持一致性存在问题。

从AEM Communities6.1开始，已经消除了复制UGC的需要，如上所述，对UGC使用共享存储。

复制站点内容时，从不复制UGC。

### 管理用户数据 {#managing-user-data}

社区还关注用 [*户&#x200B;*、*&#x200B;用户组&#x200B;*和用*&#x200B;户用户档案&#x200B;*](users.md)。 当拓扑为发布场时，在发布环境中创建和更新此用户相关数据时，需要为其他发布实例提供此[数据](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)。

从AEM Communities6.1开始，与用户相关的数据使用Sling分发而不是复制进行同步。 有关详细信息，请 [访问用户同步](sync.md)。

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

升级到AEM Communities6.3时，如果需要保留先前存在的UGC，则应根据AEM 5.6.1或AEM 6.0社区是使用Adobe点播存储还是内部部署UGC存储采取步骤。

有关详细信息， [请访问升级到AEM Communities6.3](upgrade.md)。
