---
title: 配置启用功能
seo-title: 配置启用功能
description: 在社区中配置启用功能
seo-description: 在社区中配置启用功能
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Administrator
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 5%

---

# 配置启用功能{#configuring-enablement-features}

## 概述 {#overview}

启用功能提供创建[启用社区](overview.md#enablement-community)的功能。

* 此功能需要额外的许可才能在生产环境中使用。

使用启用功能需要满足以下条件：

安装：

* ****
SCORMSharable Content Object Reference Model(SCORM)是用于电子学习的标准和规范的集合。SCORM还定义如何将内容打包到可传输的ZIP文件中。

* ****
MySQLMySQL是一个关系数据库，主要用于SCORM跟踪和报告启用数据，以及用于跟踪视频进度的表。SCORM for enablement feature pack需要MySQL JDBC驱动程序。

* ****
FFmpegFFmpeg是一种用于转换和流式传输音频和视频的解决方案，安装后可用于对视频资产进行正确 [转码](../../help/sites-authoring/default-components-foundation.md#video)。对于启用社区，可在创作环境中使用该变量来获取已上传资源的元数据，并生成在列出资源时要显示的缩略图。

设置：

* **社区**
经理对于支持社区，仅 
`Community Enablement Managers` 可以为用户组分配角色，其 `*Community Site* Enablement Manager`权限可以包括内容创建、分配和发布环境中的成员管理。

可选配置：

* **Adobe**
Analytics与Adobe Analytics的集成添加了全面的报表功能，并支持将视频心率添加到Analytics中。

* **Dispatcher**

## 配置步骤{#configuration-steps}

以下是启用社区所需的步骤。

每个步骤都链接到文档，其中提供了必需的详细信息。

**在所有创作/发布实例上：**

1. **[为MySQLUse Web控制](deploy-communities.md#jdbc-driver-for-mysql)**
台（包）安装JDBC驱动程序：安装 *http://localhost:4502/system/console/*
包安装 ** 前安装SCORM包

1. **[安装SCORM包](deploy-communities.md#scorm-package)**
使用包管理器： 
*http://localhost:4502/crx/packmgr/*

**在任何服务器上：**

1. **[安装MySQL、MySQL Workbench](mysql.md)**

1. **[安装MySQL数](mysql.md#database-setup)**
据库执行从创作实例下载的SQL脚本
\
   使用MySQL Workbench

**在托管创作实例的同一服务器上：**

1. **[安装FFmpeg](ffmpeg.md)**

**在所有创作/发布实例上：**

1. **[配置JDBC连接](mysql.md#configure-jdbc-connections)**
池使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置SCORM引擎](mysql.md#aem-communities-scormengine-service)**
服务使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置CSRF过](mysql.md#adobe-granite-csrf-filter)**
滤器使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

**在创作实例上：**

1. （*可选*）**[配置Analytics服务](analytics.md)**
使用工具、部署、Cloud Services控制台： 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[配置](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpeg使用工作流/模型控制台

1. **[启用通](deploy-communities.md#tunnel-service-on-author)**
道服务使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[创建社区管](users.md#creating-community-members)** 理员对于创作环境，请使用经典UI安全控制台： *http://localhost:4502/*
useradmincreate user(s)，其路径为： /home/users/community

   * 将成员添加到以下组：

      * 社区支持经理
      * 社区管理员

## Dispatcher {#dispatcher}

当部署包含[AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)时，为了使启用功能正常工作，`clientheader`和`filter`部分需要修改。 请参阅[为Communities配置Dispatcher](dispatcher.md#enablement)。
