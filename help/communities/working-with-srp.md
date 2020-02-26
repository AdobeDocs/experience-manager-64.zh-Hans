---
title: SRP —— 社区内容存储
seo-title: SRP —— 社区内容存储
description: 自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
seo-description: 自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465

---


# SRP —— 社区内容存储 {#srp-community-content-storage}

## 简介 {#introduction}

自AEM Communities 6.1起，用户生成的内容(UGC)存储在由存储资源提供商(SRP)提供的单个公共存储中。 可以从多个SRP选项中进行选择，如ASRP、MSRP和JSRP。

与以前的版本不同，AEM实例之间不存在UGC的反向／正向复制。 相反，SRP使UGC可以直接从所有作者和发布实例创建、读取、更新和删除(CRUD)操作访问，JSRP除外。

以下是每 [个SRP选项的特点](#characteristics-of-srp-options)，这是选择适当的SRP和基础部署时决策过程的关 [键信息](topologies.md)。

有关使用UGC的SRP的详细信息，请参阅存 [储资源提供者概述](srp.md)。

>[!NOTE]
>
>SRP仅适用于社区内容。 它不影响站点内容的存储位置(节点存[储](../../help/sites-deploying/data-store-config.md))，也不影响在AEM实例之间对用户注册、用户配置文件和用户组的安全处理(另请参阅 [管理用户数据](#managing-user-data))。

>[!CAUTION]
>
>自AEM 6.1起， [UGC不会复制](#ugc-never-replicated)。
>
>当部署不包括公用存储(如默认 [JSRP](topologies.md#jsrp) 拓扑)时，UGC将仅在输入AEM发布或作者实例上可见。 只有当拓扑包含发布群集时，UGC才会在任何发布实例上可见。

## SRP选项的特点 {#characteristics-of-srp-options}

[ASRP - adobe存储资源提供商](asrp.md)\
通过此选项，UGC将在由Adobe托管和管理的云服务中远程保留。 它需要额外的许可证并与客户代表合作为该特定许可证提供帐户。

* 需要Adobe提供并支持的关联云服务来存储社区内容
* 需要在特定地理位置（美国、EMEA、APAC）选择数据中心
* 需要通过SRP API以编程方式访问UGC
* 适用于TarMK发布场
* 当无意投资本地存储时适合

>[!NOTE]
>
>在ASRP中，将附件上传到帖子（或评论）的限制为50 MB。

[MSRP - MongoDB存储资源提供程序](msrp.md)\
使用此选项，UGC将直接保留在本地MongoDB实例中。

* 需要本地安装MongoDB以存储社区内容
* 需要本地安装Apache Solr
* 需要通过SRP API以编程方式访问UGC
* 适用于现有的TarMK发布农场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适合

[DSRP —— 关系数据库存储资源提供程序](dsrp.md)\
使用此选项，UGC将直接保留在本地MySQL数据库实例中。

* 需要本地安装MySQL以存储社区内容
* 需要本地安装Apache Solr
* 需要通过SRP API以编程方式访问UGC
* 适用于现有的TarMK发布农场
* 适用于MongoMK或RdbMK群集
* 当需要大量社区内容时适合

[JSRP - JCR存储资源提供商](jsrp.md)\
使用默认选项时，不存在公用商店。 UGC仅会与输入AEM实例的JCR存储库中保留。

* 将社区内容存储在AEM作者的JCR存储库中或发布到其的发布实例中
* 需要通过SRP API以编程方式访问UGC
* 如果部署了多个发布实例，则需要发布群集（TarMK农场中的发布实例之间没有复制机制）
* 仲裁仅在发布环境中执行（创作和发布之间没有反向／正向复制机制）
* 通常最适合开发、演示和培训

## 配置SRP {#configuring-srp}

根据底层部署指定默认存储选项是通过存储配置控制 [台进行的](srp-config.md)。

有关每个选项的配置详细信息，请参阅：

* [ASRP - adobe存储资源提供商](asrp.md)
* [MSRP - MongoDB存储资源提供程序](msrp.md)
* [DSRP —— 关系数据库存储资源提供程序](dsrp.md)
* [JSRP - JCR存储资源提供商](jsrp.md)

如果未主动选择任何存储选项，则默认情况下将启用JSRP。

## 附加信息 {#additional-information}

### UGC从未复制 {#ugc-never-replicated}

在创作环境中，作者创建页面内容并将其复制到发布环境。 当页面包含交互式AEM Communities功能（如评论、评论、论坛、博客或问题与答案）时，成员（在站点访问者中签名）对发布实例的交互会导致用户生成的内容(UGC)在发布环境中输入。

以前，此社区内容会反向复制到作者实例中，并从作者复制到发布实例中。 在具有反向和正向复制的AEM实例之间保持一致性存在问题。

从AEM Communities 6.1开始，通过使用UGC的共享存储，消除了复制UGC的需求，如上所述。

复制站点内容时，从不复制UGC。

### 管理用户数据 {#managing-user-data}

社区还关注用户 [*、用&#x200B;**&#x200B;户组&#x200B;*和用*&#x200B;户档案&#x200B;*](users.md)。 当拓扑为发布场时，在发布环境中创建和更新此用户相关数据时，需要使其他发布实例可[用](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)。

自AEM Communities 6.1起，与用户相关的数据将使用Sling分发而不是复制进行同步。 有关详细信息，请访 [问用户同步](sync.md)。

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

升级到AEM Communities 6.3时，如果需要保留预先存在的UGC，则应根据AEM 5.6.1还是AEM 6.0社区是使用Adobe点播存储还是UGC的预置存储来采取相应步骤。

有关详细信息， [请访问升级到AEM Communities 6.3](upgrade.md)。
