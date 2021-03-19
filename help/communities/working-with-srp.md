---
title: SRP — 社区内容存储
seo-title: SRP — 社区内容存储
description: 自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
seo-description: 自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: 管理员
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---


# SRP — 社区内容存储{#srp-community-content-storage}

## 简介 {#introduction}

自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中。 可以选择若干SRP选项，如ASRP、MSRP和JSRP。

与以前的版本不同，UGC在AEM实例中不进行反向/正向复制。 相反，SRP使UGC能够从所有作者实例和发布实例中直接访问创建、读取、更新和删除(CRUD)操作，JSRP除外。

以下是每个SRP选项](#characteristics-of-srp-options)的[特性，在选择适当的SRP和[基础部署](topologies.md)时，这是决策过程的关键信息。

有关UGC使用SRP的详细信息，请参阅[存储资源提供程序概述](srp.md)。

>[!NOTE]
>
>SRP仅适用于社区内容。 它不影响存储站点内容的位置([node store](../../help/sites-deploying/data-store-config.md))，也不影响AEM实例之间用户注册、用户用户档案和用户组的安全处理（另请参阅[管理用户数据](#managing-user-data)）。

>[!CAUTION]
>
>自AEM 6.1起，[UGC从不复制](#ugc-never-replicated)。
>
>当部署不包括公用存储（如默认的[JSRP](topologies.md#jsrp)拓扑）时，UGC将仅在输入UGC的AEM发布或作者实例上可见。 仅当拓扑包含发布群集时，UGC才会显示在任何发布实例上。

## SRP选项{#characteristics-of-srp-options}的特性

[ASRP -Adobe存储资源提供程序](asrp.md)\
通过此选项，UGC将在由Adobe托管和管理的云服务中远程保留。 它需要额外的许可证并与帐户代表合作来为该特定许可证提供帐户。

* 需要Adobe提供并支持的关联云服务来存储社区内容
* 需要在特定地理位置（美国、欧洲、中东/非洲、亚太地区）选择数据中心
* 要求通过SRP API对UGC进行所有编程访问
* 适用于TarMK发布场
* 当无意投资于本地存储时适用

>[!NOTE]
>
>限制将附件上传到ASRP中的帖子（或评论），这是50 MB。

[MSRP - MongoDB存储资源提供程序](msrp.md)\
使用此选项，UGC将直接保留在本地MongoDB实例中。

* 需要本地的授权安装MongoDB以存储社区内容
* 需要本地安装Apache Solr
* 要求通过SRP API对UGC进行所有编程访问
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适合

[DSRP — 关系数据库存储资源提供程序](dsrp.md)\
使用此选项，UGC将直接保留在本地MySQL数据库实例中。

* 需要本地安装MySQL以存储社区内容
* 需要本地安装Apache Solr
* 要求通过SRP API对UGC进行所有编程访问
* 适用于现有TarMK发布场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适合

[JSRP - JCR存储资源提供程序](jsrp.md)\
使用默认选项时，不存在通用商店。 UGC仅会与输入UGC的AEM实例保存在同一JCR存储库中。

* 将社区内容存储在AEM作者的JCR存储库或发布实例中，该实例已发布到
* 要求通过SRP API对UGC进行所有编程访问
* 如果部署了多个发布实例，则需要发布群集（TarMK场中的发布实例之间没有复制机制）
* 审核仅在发布环境中执行（创作和发布之间没有反向/正向复制机制）
* 通常最适合开发、演示和培训

## 配置SRP {#configuring-srp}

通过[存储配置控制台](srp-config.md)指定默认的存储选项（基于基础部署）。

有关每个选项的配置详细信息，请参阅：

* [ASRP -Adobe存储资源提供程序](asrp.md)
* [MSRP - MongoDB存储资源提供程序](msrp.md)
* [DSRP — 关系数据库存储资源提供程序](dsrp.md)
* [JSRP - JCR存储资源提供程序](jsrp.md)

如果未主动选择存储选项，则默认情况下启用JSRP。

## 附加信息 {#additional-information}

### UGC从未复制{#ugc-never-replicated}

在创作环境中，作者创建页面内容并将其复制到发布环境。 当页面包含交互式AEM Communities功能（如注释、审阅、论坛、博客或问题与答案）时，成员(在站点访客中签名)对发布实例的交互会导致用户生成的内容(UGC)进入发布环境。

以前，此社区内容会反向复制到作者实例，并从作者复制到发布实例。 在具有反向和正向复制的AEM实例之间保持一致性是有问题的。

从AEM Communities 6.1开始，已通过使用UGC的共享存储（如上所述），消除了复制UGC的需要。

复制站点内容时，从不复制UGC。

### 管理用户数据{#managing-user-data}

Communites同样感兴趣的是&#x200B;[*用户*、*用户组*&#x200B;和&#x200B;*用户用户档案*](users.md)。 当拓扑为[发布场](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)时，当在发布环境中创建和更新此用户相关数据时，需要使其他发布实例可用。

自AEM Communities 6.1起，将使用Sling分发（而非复制）同步与用户相关的数据。 有关详细信息，请访问[用户同步](sync.md)。

### 升级到AEM Communities 6.2 {#upgrading-to-aem-communities}

升级到AEM Communities 6.3时，如果需要保留预先存在的UGC，则应根据AEM 5.6.1或AEM 6.0社区是使用Adobe点播存储还是内部部署存储UGC采取相应步骤。

有关详细信息，请访问[升级到AEM Communities 6.3](upgrade.md)。
