---
title: 启动和停止WebSphere Application Server
seo-title: 启动和停止WebSphere Application Server
description: 几个过程要求您停止或开始要部署AEM表单产品的WebSphere实例。 本文档介绍如何开始和停止WebSphere Application Server。
seo-description: 几个过程要求您停止或开始要部署AEM表单产品的WebSphere实例。 本文档介绍如何开始和停止WebSphere Application Server。
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# 启动和停止WebSphere Application Server {#starting-and-stopping-websphere-application-server}

几个过程要求您停止或开始要部署AEM表单产品的WebSphere实例。 如果不确定应用程序服务器是否已启动，可以先视图WebSphere Application Server的状态。

## 视图WebSphere Application Server的状态 {#view-the-status-of-websphere-application-server}

1. 从命令提示符中，转到 *[appserver root]*/bin目录。
1. 输入以下命令， *将server_name* 替换为WebSphere Application Server的名称：

   * (Windows) `serverStatus.bat`*server_name *
   * (Linux、UNIX)。/ `serverStatus.sh`*server_name *

## 开始WebSphere Application Server {#start-websphere-application-server}

1. 从命令提示符中，转到 *[appserver root]*/bin目录。
1. 输入以下命令， *将server_name* 替换为WebSphere Application Server的名称：

   * (Windows) `startServer.bat`*server_name *
   * (Linux、UNIX)。/ `startServer.sh`*server_name *

## 停止WebSphere Application Server {#stop-websphere-application-server}

1. 从命令提示符中，转到 *[appserver root]*/bin目录。
1. 输入以下命令， *将server_name* 替换为WebSphere Application Server的名称：

   * (Windows) `stopServer.bat`*server_name *
   * (Linux、UNIX)。/ `stopServer.sh`*server_name *

