---
title: AEM Communities概述
seo-title: AEM Communities概述
description: AEM Communities功能和设置概述
seo-description: AEM Communities功能和设置概述
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 4%

---


# AEM Communities概述 {#aem-communities-overview}

利用 Adobe Experience Manager (AEM) Communities，可以快速创建内部部署社区网站，从而提升性能和网站管理能力，同时促进网站访客转化为有价值的社区成员。

请联系您的客户代表，了解有关AEM Communities的许可以及支持功能和Adobe Analytics的其他许可信息。

## 社区功能 {#communities-features}

AEM Communities支持与网站访客建立关系，通过博客、问题与答案和事件日历提供信息，同时通过论坛、评论和其他社区内容(通常称为用户生成内容(UGC))获得洞察。

此外，AEM Communities还允许发布环境中受信任成员进行仲裁，使用Twitter和Facebook进行社交登录，内联社区内容翻译，从已发布的社区站点创建社区组，对奖章进行评分、文件共享、通知和活动流。

社区功能可通过GitHub.com [上公开提供的](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) AEM Demo Machine或通过新的We.Retail参考实施进行演示。

## 社区站点 {#community-sites}

社区站点是使用简单的向导创建的AEM站点，该向导会生成具有许多预先连接到站点的常用功能的网站。

站点 [创建向导](sites-console.md):

* 根据选定的社区站点模板(该模 [板是](sites.md) :
   * 从社区功 [能构建](#community-functions)
   * 可选 [社区组功](#communitygroups) 能
* 使用设置进行配置：
   * 审核
   * 登录
   * 翻译
* 提供基本功能：
   * 响应式设计： 使用 [TwitterBootstrap主题](https://getbootstrap.com)
   * 登录： 自助注册、社 [交登录](social-login.md)、用户用户档案
   * 通知： 会员可以看到与他们相关的事件
   * 消息： 会员可以在社区站点内发送或接收消息
   * 搜索： 能够在社区站点内进行搜索
   * 语言切换： 能为多语言站点选 [择语言](../../help/sites-administering/translation.md)
   * 管理： 授权成员有权审核和管理社区站点内的用户
* 消除许多页面级创作步骤：
   * 品牌： 可选上传横幅图像以显示在社区站点的所有页面上
   * 导航菜单： 为社区站点模板中包含的功能提供了导航链接

要体验快速创建新社区站点的便利性，请访 [问AEM Communities入门](getting-started.md)。

## 社区内容持久性 {#community-content-persistence}

为了改进社区内容的性能和同步，AEM Communities要求为所有AEM（作者和发布）实例之间共享的用户生成内容(UGC)建立一个专用的公用存储。

社区内容可通过存储资源提供者(SRP)轻松访问，该提供者提供一个层，用于将访问与底层拓扑分离，并支持UGC的公共存储。

要进一步了解社区内容持久性和推荐的部署，请访问：

* [社区内容存储](working-with-srp.md): 讨论UGC的可用SRP存储选项
* [推荐的拓扑](topologies.md): 讨论基于用例的拓扑和SRP选择
* [升级到AEM 6.3 Communities](upgrade.md): 在移至AEM 6.3时提供有关UGC的有用信息。

## 社区控制台 {#communities-consoles}

在创作环境中，全局导航控制台提供对“社区”控 [制台的访问](consoles.md)，该控制台包含：

* [站点](sites-console.md)控制台

   * 站点创建
   * 站点编辑
   * 站点管理
   * [“社区组](groups.md) ”控制台

* [审核控制](moderation.md) 台

   * 创作和发布环境的通用批量协调UI
   * 新的筛选条件

* [成员和组管理](members.md) 控制台

   * 提供从创作环境创建和管理发布端用户（成员）的功能
   * 提供禁止会员的功能
   * 提供从创作环境创建和管理发布端用户组（成员组）的功能

* [“报告](reports.md) ”控制台

   * 提供生成任务、帖子和视图报告的功能

* [“资源](resources.md) ”控制台

   * 提供创建支持资源和学习路径的能力
   * 提供对有关启用资源和学习路径的报告的访问

全局工具控制台提供对以下社区工具的访问：

* [站点模板控制](tools.md#sitetemplatesconsole) 台

   * 创建和管理社区站点模板

* [“组模板](tools.md#grouptemplatesconsole) ”控制台

   * 创建和管理社区组模板

* [社区功能控制](tools.md#communityfunctionsconsole) 台

   * 创建和管理社区功能

* [存储配置](tools.md#storageconfiguratonconsole) 控制台

   * 选择并配置站 [点的公](working-with-srp.md) 用商店

* [组件指南](components-guide.md)

   * 示例站点“ [社区组件](http://localhost:4502/editor.html/content/community-components/en.html)”，它提供所有社区组件的示例以及它们的默认配置和试验能力

## 社区站点模板 {#community-site-templates}

社区站点创建基于社区站点模板的选择，以快速设置独立于任何示例站点的社区站点。

社区站点模板由社区功能和社区组模板组成，它提供社区站点的结构，包括登录名、用户用户档案、消息、站点菜单、搜索、主题和品牌特征。

请参阅站 [点模板控制台](sites.md)。

## 社区功能 {#community-functions}

社区体验预期的功能众所周知。 在AEM Communities，这些功能可以作为构件，称为社区功能。

社区功能是由连接到功能中的组件组成的普通AEM页面，该功能可轻松融入社区站点模板中。

请参阅“社 [区功能”控制台](functions.md)。

## 社区组和组模板 {#community-groups-and-group-templates}

社区组功能是允许来自作者和发布环境的授权用户和社区成员在社区站点内动态创建子社区的功能。

从作者环境，当模板的结构包含“组”功能时，可以在现有社区站点内创建社区组（子社区）或嵌套在现有 [组内](functions.md#groups-function)。

创建社区组需要选择提供社区组页面设计的社区组模板。 将“组”功能添加到模板结构后，将配置为指定一个组模板或在创建新社区组时提供模板选项。

另请参阅：

* [站点组控制台](groups.md) -在创作环境中创建子社区
* [组模板控制台](tools-groups.md) -为组创建站点结构
* [AEM Communities入门](getting-started.md) -快速创建包含嵌套组的社区站点的教程

## 社区组件 {#community-components}

构 [建社区站点](author-communities.md) 的社区组件可用于向任何AEM站点添加社区功能。

社区 [组件指南](components-guide.md) ，可用于交互式探索这些组件。

## 社区类型 {#types-of-communities}

### 参与社区 {#engagement-community}

参与社区是一个社区站点，其重点是吸引客户通知、征求反馈并允许客户作为社区成员进行交互。

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
* 分析报告

要体验快速创建新参与社区的便利性，请访 [问AEM Communities入门](getting-started.md)。

### Enablement Community {#enablement-community}

支持社区是一个社区站点，其中包含在线学习功能。

支持社区的功能可能包括：

* 参与社区的所 [有功能](#engagement-community)
* 能够向成员和成员组分配内容和学习资源
* 支持SCORM内容，如测验和测试
* 任务完成跟踪
* 访问报告和分析
* 能够通过论坛、消息、评论和评级与学习资源进行对话

配置Enablement Add-on时可以创建 [Enablement Community](enablement.md)，这要求在生产环境中使用额外的许可。 支持社区站点将包含 [任务功能](#community-functions)。

要体验创建新的支持社区的轻松性，请访 [问AEM Communities支持入门](getting-started-enablement.md)。

## AEM Demo Machine {#aem-demo-machine}

AEM [Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) 管理和运行AEM Sites [、Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites)、 [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets)、 Apps [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps)[](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)和BildoMachine的演示，它通常要求设置比只启动QuickStart实例更多。 AEM Demo Machine将设置其他 [基础](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) 架构，如MongoDB、Solr、MySQL、FFmpeg和电子邮件服务器。

AEM Demo Machine由

* 图 [形用户界面](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 具有可配置属性和 [目标](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) 的Apache [ANT脚本](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* 安装包在Windows、MacOS和Linux上，AEM Demo Machine已通过CQ 5.5、CQ 5.6.1、AEM 6.0、AEM 6.1、AEM 6.2和AEM 6.3成功测试。

AEM Demo Machine需要有效的AEM许可证。

>[!NOTE]
>
>视图 [AEM](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) 演示机的简介视频(13:26)。

## AEM Communities文档 {#aem-communities-documentation}

* 访问 [部署社区](deploy-communities.md) ，了解建议的部署。

* 访问 [管理社区站点](administer-landing.md) ，了解如何创建社区站点、添加社区组、配置社区站点模板、管理社区内容、管理成员、标记、通知、评分和徽章。

* 访 [问开发社区](communities.md) ，了解社交组件框架(SCF)和自定义社区组件和功能。

* 访问 [创作社区组件](author-communities.md) ，了解如何创作和配置社区组件。

