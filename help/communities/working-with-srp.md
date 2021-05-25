---
title: SRP — 社区内容存储
seo-title: SRP — 社区内容存储
description: 从AEM Communities 6.1开始，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
seo-description: 从AEM Communities 6.1开始，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Administrator
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---

# SRP — 社区内容存储{#srp-community-content-storage}

## 简介 {#introduction}

自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中。 可以选择多个SRP选项，如ASRP、MSRP和JSRP。

与以前的版本不同，AEM实例中不存在UGC的反向/正向复制。 SRP使UGC可以直接访问，以便从所有创作和发布实例中执行创建、读取、更新和删除(CRUD)操作，JSRP除外。

以下是每个SRP选项](#characteristics-of-srp-options)的[特性，在选择适当的SRP和[底层部署](topologies.md)时，这是决策过程的关键信息。

有关UGC使用SRP的详细信息，请参阅[存储资源提供程序概述](srp.md)。

>[!NOTE]
>
>SRP仅适用于社区内容。 它不会影响存储网站内容的位置（[节点存储](../../help/sites-deploying/data-store-config.md)），也不会影响AEM实例之间用户注册、用户配置文件和用户组的安全处理（另请参阅[管理用户数据](#managing-user-data)）。

>[!CAUTION]
>
>自AEM 6.1起，从未复制[UGC](#ugc-never-replicated)。
>
>当部署中不包含公共存储（如默认的[JSRP](topologies.md#jsrp)拓扑）时，UGC将仅在输入UGC的AEM发布或创作实例上可见。 只有当拓扑包含发布群集时，UGC才会在任何发布实例上可见。

## SRP选项{#characteristics-of-srp-options}的特点

[ASRP -Adobe存储资源提供程序](asrp.md)\
通过此选项，UGC将在托管并由Adobe管理的云服务中远程保留。 它需要额外的许可证并与客户代表合作来为该特定许可证配置帐户。

* 需要提供并受Adobe支持的关联云服务来存储社区内容
* 需要在特定地理位置（美国、EMEA、APAC）选择数据中心
* 要求所有通过SRP API以编程方式访问UGC
* 适用于TarMK发布场
* 当无意投资于本地存储时适合

>[!NOTE]
>
>在ASRP中，将附件上传到帖子（或评论）存在限制，为50 MB。

[MSRP - MongoDB存储资源提供程序](msrp.md)\
使用此选项，UGC将直接保留在本地MongoDB实例中。

* 需要本地安装许可的MongoDB来存储社区内容
* 需要本地安装Apache Solr
* 要求所有通过SRP API以编程方式访问UGC
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 适合期待大量社区内容时

[DSRP — 关系数据库存储资源提供程序](dsrp.md)\
使用此选项，UGC将直接保留在本地MySQL数据库实例中。

* 需要本地安装MySQL才能存储社区内容
* 需要本地安装Apache Solr
* 要求所有通过SRP API以编程方式访问UGC
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 适合期待大量社区内容时

[JSRP - JCR存储资源提供程序](jsrp.md)\
使用默认选项，不存在常用商店。 UGC仅与输入UGC的AEM实例保留在同一JCR存储库中。

* 将社区内容存储在发布到的AEM创作或发布实例的JCR存储库中
* 要求所有通过SRP API以编程方式访问UGC
* 如果部署了多个发布实例，则需要发布群集（TarMK场中的发布实例之间没有复制机制）
* 审核仅在发布环境中执行（创作和发布之间没有反向/转发复制机制）
* 通常最适合于开发、演示和培训

## 配置SRP {#configuring-srp}

根据底层部署，通过[存储配置控制台](srp-config.md)指定默认存储选项。

有关每个选项的配置详细信息，请参阅：

* [ASRP -Adobe存储资源提供程序](asrp.md)
* [MSRP - MongoDB存储资源提供程序](msrp.md)
* [DSRP — 关系数据库存储资源提供程序](dsrp.md)
* [JSRP - JCR存储资源提供程序](jsrp.md)

如果未主动选择存储选项，则默认启用JSRP。

## 附加信息 {#additional-information}

### UGC从未复制{#ugc-never-replicated}

在创作环境中，作者创建页面内容并将其复制到发布环境。 当页面包含交互式AEM Communities功能（如评论、评论、论坛、博客或QnA）时，成员（在站点访客中签名）在发布实例上的交互会导致用户生成内容(UGC)进入发布环境。

以前，此社区内容会反向复制到创作实例，而从创作复制到发布实例。 在具有反向和正向复制的AEM实例之间保持一致性时出现问题。

从AEM Communities 6.1开始，使用UGC的共享存储消除了复制UGC的需要，如上所述。

复制站点内容时，UGC从不复制。

### 管理用户数据{#managing-user-data}

社区还关注&#x200B;[*用户*、*用户组*&#x200B;和&#x200B;*用户配置文件*](users.md)。 当拓扑为[发布场](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)时，在发布环境中创建和更新此用户相关数据时，需要将其提供给其他发布实例。

自AEM Communities 6.1起，使用Sling分发而不是复制来同步与用户相关的数据。 有关更多信息，请访问[用户同步](sync.md)。

### 升级到AEM Communities 6.2 {#upgrading-to-aem-communities}

在升级到AEM Communities 6.3时，如果需要保留预先存在的UGC，则应根据AEM 5.6.1或AEM 6.0社区是使用Adobe按需存储还是内部部署存储UGC来采取相应步骤。

有关详细信息，请访问[升级到AEM Communities 6.3](upgrade.md)。
