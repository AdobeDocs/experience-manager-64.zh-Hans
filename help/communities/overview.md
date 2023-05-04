---
title: AEM Communities概述
seo-title: AEM Communities Overview
description: AEM Communities功能和设置概述
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---

# AEM Communities概述 {#aem-communities-overview}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager(AEM)Communities提供了快速创建内部部署社区网站的功能，该网站已改进性能、改进了网站管理，并鼓励将网站访客转换为有价值的社区成员。

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## 社区功能 {#communities-features}

AEM Communities支持与网站访客建立关系，通过博客、问答和事件日历提供信息，同时通过论坛、评论和其他社区内容(通常称为用户生成内容(UGC))获得洞察。

此外，AEM Communities还允许发布环境中受信任的成员进行审核、通过Twitter和Facebook进行社交登录、社区内容的内联翻译、从已发布的社区站点创建社区组、评分到奖章、文件共享、通知和活动流。

社区功能可使用 [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) 可在GitHub.com上公开获取，或通过新的We.Retail参考实施获取。

## 社区站点 {#community-sites}

社区站点是使用简单向导创建的AEM站点，该向导会生成一个网站，该网站具有许多预先连接到该站点的常用功能。

的 [站点创建向导](sites-console.md):

* 根据所选的 [社区站点模板](sites.md) 其中
   * 从 [社区功能](#community-functions)
   * 可选 [社区团体](#communitygroups) 功能
* 使用设置配置：
   * 审核
   * 登录
   * 翻译
* 提供基本功能：
   * 响应式设计：使用 [TwitterBootstrap主题](https://getbootstrap.com)
   * 登录：自我登记， [社交登录](social-login.md)，用户配置文件
   * 通知：成员会看到与他们相关的事件
   * 消息传送：会员可以在社区站点内发送或接收消息
   * 搜索：能够在社区站点内进行搜索
   * 语言切换：能够为 [多语言站点](../../help/sites-administering/translation.md)
   * 管理：授权成员有权审核和管理社区站点内的用户
* 消除了许多页面级别的创作步骤：
   * 品牌策略：可选上载横幅图像，以在社区网站的所有页面上显示
   * 导航菜单：为社区站点模板中包含的功能提供了导航链接

要体验快速创建新社区站点的轻松性，请访问 [开始使用AEM Communities](getting-started.md).

## 社区内容持久性 {#community-content-persistence}

为了提高社区内容的性能和同步，AEM Communities要求专门为所有AEM（创作和发布）实例之间共享的用户生成内容(UGC)提供一个通用存储区。

通过存储资源提供程序(SRP)可以轻松访问社区内容，该提供程序提供一个层，用于将访问与底层拓扑分离，并支持UGC的公共存储。

要了解有关社区内容持久性和推荐部署的更多信息，请访问：

* [社区内容存储](working-with-srp.md):讨论UGC的可用SRP存储选项
* [推荐的拓扑](topologies.md):讨论了基于用例的拓扑和SRP选择
* [升级到AEM 6.3 Communities](upgrade.md):提供有关移动到AEM 6.3时UGC的有用信息。

## 社区控制台 {#communities-consoles}

在创作环境中，全局导航控制台提供对 [社区控制台](consoles.md)，其中包含：

* [站点](sites-console.md) 控制台

   * 网站创建
   * 网站编辑
   * 站点管理
   * [社区组](groups.md) 控制台

* [审核](moderation.md) 控制台

   * 适用于创作和发布环境的常用批量审核UI
   * 新筛选条件

* [成员和组](members.md) 管理控制台

   * 提供从创作环境创建和管理发布端用户（成员）的功能
   * 提供禁止成员的功能
   * 提供从创作环境创建和管理发布端用户组（成员组）的功能

* [报表](reports.md) 控制台

   * 提供生成分配、帖子和视图报告的功能

* [资源](resources.md) 控制台

   * 提供创建支持资源和学习路径的功能
   * 提供对有关启用资源和学习路径的报告的访问权限

全局工具控制台提供对以下社区工具的访问：

* [网站模板](tools.md#sitetemplatesconsole) 控制台

   * 创建和管理社区站点模板

* [组模板](tools.md#grouptemplatesconsole) 控制台

   * 创建和管理社区组模板

* [社区功能](tools.md#communityfunctionsconsole) 控制台

   * 创建和管理社区功能

* [存储配置](tools.md#storageconfiguratonconsole) 控制台

   * 选择并配置 [公用商店](working-with-srp.md) 对于网站

* [组件指南](components-guide.md)

   * 一个示例网站， [社区组件](http://localhost:4502/editor.html/content/community-components/en.html)，为所有社区组件提供了示例以及其默认配置和试用功能

## 社区站点模板 {#community-site-templates}

社区站点创建基于社区站点模板的选择，以快速设置独立于任何示例站点的社区站点。

社区站点模板，由社区功能和社区组模板组成，为社区站点提供了结构，包括登录、用户档案、消息、站点菜单、搜索、主题和品牌特征。

请参阅 [站点模板控制台](sites.md).

## 社区功能 {#community-functions}

社区体验预期的功能已广为人知。 借助AEM Communities，这些功能可用作构建基块，称为社区功能。

社区功能是正常的AEM页面，由连接到功能中的组件组成，该功能可轻松融入社区站点模板中。

请参阅 [社区功能控制台](functions.md).

## 社区组和组模板 {#community-groups-and-group-templates}

社区组功能允许子社区由创作和发布环境的授权用户和社区成员在社区站点内动态创建。

在创作环境中，当模板的结构包含 [组函数](functions.md#groups-function).

创建社区组需要选择社区组模板，以提供社区组页面的设计。 在将群组功能添加到模板结构时，会将其配置为指定一个群组模板，或在创建新社区群组时提供模板选项。

另请参阅：

* [站点组控制台](groups.md)  — 在创作环境中创建子社区
* [组模板控制台](tools-groups.md)  — 为组创建站点结构
* [开始使用AEM Communities](getting-started.md)  — 快速创建包含嵌套群组的社区站点的教程

## 社区组件 {#community-components}

的 [社区组件](author-communities.md) 从中构建社区站点的社区站点可用于向任何AEM站点添加社区功能。

的 [社区组件指南](components-guide.md) 可用于组件的交互式探索。

## 社区类型 {#types-of-communities}

### 参与社区 {#engagement-community}

参与社区是一个社区站点，其重点是吸引客户告知、征求反馈并允许客户作为社区成员进行交互。

参与社区的功能可能包括：

* 登录
* 消息
* 论坛
* 评论
* 审核
* 评级
* 投票
* 博客
* 组
* 日历
* 翻译
* 审核
* 通知
* 评分和徽章
* Analytics报表

要体验快速创建新参与社区的轻松性，请访问 [开始使用AEM Communities](getting-started.md).

### 启用社区 {#enablement-community}

支持社区是一个社区网站，其中包含用于在线学习的功能。

支持社区的功能可能包括：

* 的所有功能 [参与社区](#engagement-community)
* 能够向成员和成员组分配内容和学习资源
* 支持SCORM内容，如测验和测试
* 跟踪分配完成情况
* 对报告与分析的访问权限
* 通过论坛、消息、评论和评级进行学习资源对话的能力

在 [已配置启用附加组件](enablement.md)，需要在生产环境中使用额外的许可。 支持社区网站将包括 [赋值函数](#community-functions).

要体验创建新支持社区的便利性，请访问 [AEM Communities启用入门](getting-started-enablement.md).

## AEM Demo Machine {#aem-demo-machine}

的 [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) 管理和运行AEM演示 [站点](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [资产](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [社区](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [应用程序](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) 和 [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)，这通常比启动快速启动实例需要更多的设置。 AEM演示计算机将设置其他 [基础架构](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) 例如MongoDB、Solr、MySQL、FFmpeg和电子邮件服务器。

AEM演示计算机由

* A [图形用户界面](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 可配置的Apache ANT脚本 [属性](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) 和 [目标](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* 安装AEM演示计算机的软件包已在Windows、MacOS和Linux上通过CQ 5.5、CQ 5.6.1、AEM 6.0、AEM 6.1、AEM 6.2和AEM 6.3成功测试。

AEM演示计算机需要有效的AEM许可证。

>[!NOTE]
>
>查看 [视频简介](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) 到AEM演示机(13:26)。

## AEM Communities文档 {#aem-communities-documentation}

* 访问 [部署社区](deploy-communities.md) 以了解建议的部署。

* 访问 [管理社区站点](administer-landing.md) 要了解有关创建社区站点、添加社区组、配置社区站点模板、审核社区内容、管理成员、标记、通知、评分和徽章的信息。

* 访问 [发展社区](communities.md) 了解社交组件框架(SCF)和自定义社区组件和功能。

* 访问 [创作社区组件](author-communities.md) 了解如何使用和配置社区组件进行创作。
