---
title: AEM Communities 发行说明
seo-title: AEM Communities
description: 以下发行说明特定于 Adobe Experience Manager 6.4 Communities。
seo-description: 以下发行说明特定于 Adobe Experience Manager 6.4 Communities。
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 12%

---


# AEM Communities 发行说明 {#aem-communities-release-notes}

本节提供有关自6.3版本以来对AEM Communities的改进的信息。 要更详细地了解新增功能，请参 [阅AEM 6.4 Communities的新增功能](/help/communities/whats-new-aem-communities.md)。

To obtain the latest release, see the [Deploying Communities](/help/communities/deploy-communities.md#latest-releases) section of the documentation.

## 主要改进 {#main-improvements}

社区站点:

* 社区管理员现在可以：

   * 永久删除社区站点
   * 为社区站点选择上下文感知配置文件夹

社区组:

* 社区管理员现在可以：

   * 永久删除社区组
   * 创建多语言社区组
   * 在社区组中添加Enablement Catalog和任务

* Enablement Manager现在可以

   * 在社区组中创建和分配资源和学习路径

文件库:

* 社区成员现在对文件库进行了多项增强，如排序、标记……

通知:

* 社区会员现在在批准通过审核流程进行的捐款后收到通知

审核:

* 自动垃圾邮件检测过滤器
* 社区版主具有其他审核过滤器（例如已回答／未回答的问题）
* 社区版主可以将审核书加入书签并将审核链接到预定义过滤器（例如，所有待批准的帖子）

与AEM 6.4中基本更改的整体兼容性。

注意： AEM 6.3也提供所有这些功能。请查看AEM Communities发行说明以了解 [6.3](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html)。

## 已知问题 {#known-issues}

* **审核** -无法从批量审核UI中将父帖子作为单个删除操作删除(CQ-4236797)
* **控制台** -忘记用户名或密码链接正在重定向到登录页面，而不是相应的密码检索表单(CQ-4237682)

## 选择功能 {#select-features}

专家评分(*由Sensei提供支持*)用于启用游戏化，这是鼓励和奖励宝贵社区行为的有效方式。 它还可用于为推荐或营销目的确定专家。

## 演示 {#demonstrations}

在使用AEM Communities演示方案时， [也可以在新的We.Retail参考实施中](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) ，使用GitHub.com上公开提供的AEM Demo Machine来演示所有这些功能。
