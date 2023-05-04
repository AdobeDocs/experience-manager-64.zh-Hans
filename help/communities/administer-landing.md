---
title: 社区站点
seo-title: Communities Sites
description: AEM Communities文档概述
seo-description: Overview of the AEM Communities documentation
uuid: 9842ce6c-1af8-4b27-b199-07410e797ab2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 8799386a-c3b8-43cf-9f71-580ff2a81abc
role: Admin
exl-id: b5d20819-3a3f-4b9e-99a3-e7ae5ae28baf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 5%

---

# 社区站点 {#communities-sites}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本节面向那些管理AEM Communities并熟悉AEM Communities功能的用户。

## 概述 {#overview}

有关概述和快速入门教程，请访问：

* [AEM Communities概述](overview.md)
* [开始使用AEM Communities](getting-started.md)
* [AEM Communities启用入门](getting-started-enablement.md)

## 管理和配置主题 {#administration-and-configuration-topics}

### 社区站点创建和管理 {#communities-site-creation-and-management}

* 社区 [控制台](consoles.md)

   * [Sites](sites-console.md)

      * [组（子社区）](groups.md)
   * [审核](moderation.md)
   * [成员和组管理](members.md)
   * [启用资源](resources.md)
   * [报表](reports.md)


* 社区 [*工具*](tools.md):

   * [站点模板](sites.md)
   * [组模板](tools-groups.md)
   * [社区功能](functions.md)
   * [存储配置](srp-config.md)
   * [组件指南](components-guide.md)
   * [徽章](badges.md)


### 用户生成的内容 {#user-generated-content}

AEM Communities的一项主要功能是，通过登录网站访客（成员）生成用户生成的内容(UGC)。 要了解有关使用UGC的更多信息，请访问：

* [常用UGC存储](working-with-srp.md):UGC共享存储SRP的选择
* [审核UGC](moderate-ugc.md):受信任的成员可以批量审核或在上下文中审核UGC
* [标记UGC](tag-ugc.md):功能可配置为允许成员标记内容
* [翻译UGC](translate-ugc.md):功能可配置为翻译所有UGC或允许成员翻译所选帖子
* [Analytics配置](analytics.md):使Adobe Analytics能够报告与成员活动有关的各种量度

### 社区成员 {#community-members}

* [管理用户和用户组](users.md):社区成员和成员组（包括特权成员）的详细信息
* [贡献限制](limits.md):能够限制由新成员发布的内容
* [隧道服务](deploy-communities.md#tunnel-service-on-author):允许从创作环境访问发布端成员和成员组
* [“成员”和“组”控制台](members.md):允许从创作环境创建和管理发布端成员和成员组
* [用户同步](sync.md):用于在多个发布实例中同步成员和成员组
* [使用Facebook和Twitter进行社交登录](social-login.md):站点访客能够使用其Facebook或Twitter凭据成为社区成员
* [评分和徽章](implementing-scoring.md):能够分配徽章以识别成员的角色，以及通过成员参与社区获得徽章
* [通知](notifications.md):能够向成员发出其所跟踪活动的通知
* [订阅](subscriptions.md):使成员能够使用外部电子邮件与社区交互
* [消息传送](messaging.md):成员能够使用内部消息与社区进行交互

### 启用功能 {#enablement-features}

* [配置启用](enablement.md):正确设置启用功能的必要信息
* [Analytics配置](analytics.md):启用Adobe Analytics for Communities功能的必要信息
* [标记支持资源](tag-resources.md):创建启用目录的必要信息

### 部署 {#deployment}

部署部分包含特定于AEM Communities的信息。

使用社区内容的性质会影响部署的结构：

* [推荐的社区拓扑](topologies.md)

在AEM平台上安装最新的Communities版本很重要：

* [最新社区功能包](deploy-communities.md#latestfeaturepack)

有关其他特定于Communities的信息，请参阅部署页面，例如 [升级](upgrade.md), [Dispatcher](dispatcher.md) 和 [复制](deploy-communities.md#replication-agents-on-author).

## 相关社区文档 {#related-communities-documentation}

* 访问 [部署社区](deploy-communities.md) 以了解建议的部署。

* 访问 [发展社区](communities.md) 了解社交组件框架(SCF)和自定义社区组件和功能。

* 访问 [创作社区组件](author-communities.md) 了解如何使用和配置社区组件进行创作。
