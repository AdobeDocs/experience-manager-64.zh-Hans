---
title: 存储资源提供程序概述
seo-title: Storage Resource Provider Overview
description: 社区的通用存储
seo-description: Common storage for Communities
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
exl-id: 17105abe-177b-4e73-bb4f-22b208c436ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 0%

---

# 存储资源提供程序概述 {#storage-resource-provider-overview}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

自AEM Communities 6.1起，社区内容(通常称为用户生成内容(UGC))存储在由 [存储资源提供程序](working-with-srp.md) (SRP)。

有几个SRP选项，所有选项都通过新的AEM Communities界面( [SocialResourceProvider API](srp-and-ugc.md) (SRP API)，包括所有创建、读取、更新和删除(CRUD)操作。

所有SCF组件都使用SRP API来实施，这允许在不了解 [底层拓扑](topologies.md) 或UGC的位置。

***SocialResourceProvider API仅适用于AEM Communities的授权客户。***

>[!NOTE]
>
>**自定义组件**:对于AEM Communities的授权客户，自定义组件的开发人员可以使用SRP API，以便访问UGC，而不考虑底层拓扑。 请参阅 [SRP和UGC要点](srp-and-ugc.md).

另请参阅：

* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法

## 关于存储库 {#about-the-repository}

要了解SRP，了解AEM存储库(OAK)在AEM社区站点中的角色将会有所帮助。

**Java内容存储库(JCR)**
该标准定义了数据模型和应用程序编程接口([JCR API](https://jackrabbit.apache.org/jcr/jcr-api.html))。 它将传统文件系统的特性与关系数据库的特性相结合，并添加了内容应用程序通常需要的许多其他特性。

JCR的一个实施是AEM存储库OAK。

**Apache Jackrabbit Oak(OAK)**
[OAK](../../help/sites-deploying/platform.md) 是JCR 2.0的一项实施，它是专门为以内容为中心的应用程序而设计的数据存储系统。 它是一种针对非结构化和半结构化数据而设计的分层数据库。 存储库不仅存储面向用户的内容，还存储应用程序使用的所有代码、模板和内部数据。 用于访问内容的UI是 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

JCR和OAK通常都用于表示AEM存储库。

在专用创作环境中开发站点内容后，必须将其复制到公共发布环境。 这通常通过名为的操作来完成 *[复制](deploy-communities.md#replication-agents-on-author)*. 这在作者/开发人员/管理员的控制下发生。

对于UGC，内容由注册的站点访客（社区成员）在公共发布环境中输入。 这是随机发生的。

出于管理和报告目的，从专用创作环境访问UGC非常有用。 使用SRP，从作者处访问UGC将更加一致，并且性能更好，因为无需从发布到作者的反向复制。

## 关于SRP {#about-srp}

将UGC保存到共享存储时，会有一个成员内容的单个实例，在大多数部署中，该实例可以从创作和发布环境访问。 无论SRP选择如何(MSRP、ASRP、JSRP)，都必须使用SRP API以编程方式访问。

>[!NOTE]
>
>请参阅 [SRP和UGC要点](srp-and-ugc.md) 以了解示例代码和其他详细信息。
>
>请参阅 [使用SRP访问UGC](accessing-ugc-with-srp.md) 以了解编码时的最佳实践。

### ASRP {#asrp}

对于ASRP，UGC不会存储在JCR中，而是存储在由Adobe托管和管理的云服务中。 存储在ASRP中的UGC既不能通过CRXDE Lite查看，也不能使用JCR API访问。

请参阅 [ASRP -Adobe存储资源提供程序](asrp.md).

开发人员无法直接访问UGC。

ASRP使用Adobe云进行查询。

### MSRP {#msrp}

对于MSRP，UGC不存储在JCR中，而是存储在MongoDB中。 存储在MSRP中的UGC既不能通过CRXDE Lite查看，也不能使用JCR API访问。

请参阅 [MSRP - MongoDB存储资源提供程序](msrp.md).

虽然MSRP与ASRP类似，但由于所有AEM服务器实例都在访问相同的UGC，因此可以使用常用工具直接访问存储在MongoDB中的UGC。

MSRP使用Solr进行查询。

### JSRP {#jsrp}

JSRP是在单个AEM实例上访问所有UGC的默认提供程序。 它提供了快速体验AEM Communities 6.1的功能，而无需设置MSRP或ASRP。

请参阅 [JSRP - JCR存储资源提供程序](jsrp.md).

对于JSRP，虽然UGC存储在JCR中，并可通过CRXDE Lite和JCR API访问，但强烈建议永远不要使用JCR API，否则将来的更改可能会影响自定义代码。

此外，不会共享创作和发布环境的存储库。 虽然发布实例群集会生成共享发布存储库，但在发布时输入的UGC在创作时不可见，因此无法从创作中管理UGC。 UGC仅会保留在输入UGC的实例的AEM存储库(JCR)中。

JSRP使用Oak索引进行查询。

## 关于JCR中的阴影节点 {#about-shadow-nodes-in-jcr}

模拟UGC路径的阴影节点存在于本地存储库中，以用于两个目的：

1. [访问控制(ACL)](#for-access-control-acls))
1. [非现有资源](#for-non-existing-resources-ners)

无论SRP如何实施，实际的UGC都将*不会*在与阴影节点相同的位置可见。

### 用于访问控制(ACL) {#for-access-control-acls}

一些SRP实现（如ASRP和MSRP）将社区内容存储在不提供ACL验证的数据库中。 卷影节点在本地存储库中提供了可应用ACL的位置。

使用SRP API，所有SRP选项在执行所有CRUD操作之前对卷影位置执行相同的检查。

ACL检查使用实用程序方法，该方法返回一个适用于检查应用于资源UGC的权限的路径。

请参阅 [SRP和UGC要点](srp-and-ugc.md) 示例代码。

### 对于非现有资源 {#for-non-existing-resources-ners}

某些社区组件可包含在脚本中，因此需要Sling可寻址节点才能支持社区功能。 [包含的组件](scf.md#add-or-include-a-communities-component) 称为非现有资源。

卷影节点在存储库中提供了Sling可寻址位置。

>[!CAUTION]
>
>由于阴影节点具有多种用途，因此存在阴影节点确实会 *not* 暗示组件是NER。

### 存储位置 {#storage-location}

以下是使用 [注释组件](http://localhost:4502/content/community-components/en/comments.html) 在 [社区组件指南](components-guide.md):

* 组件存在于本地存储库中，位置为：

   /content/community-components/en/comments/jcr:content/content/include/comments

* 本地存储库中存在对应的卷影节点：

   /content/usergenerated/content/community-components/en/comments/jcr:content/content/include/comments

在阴影节点下找不到UGC。

默认行为是在每次为读或写引用相关子树时，在发布实例上设置卷影节点。

例如，假设部署为 [MSRP](msrp.md) 和TarMK发布场。

当 [会员](users.md) 在pub1上发布UGC（存储在MongoDB中），在pub1上的JCR中创建阴影节点。

首次在pub2上读取UGC时，如果未设置任何内容，则默认行为是创建阴影节点。

如果需要默认行为之外的其他行为，则必须在创作实例上设置该行为，并将其转发到所有发布实例，这通常是手动过程。
