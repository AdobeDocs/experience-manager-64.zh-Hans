---
title: 启动和停止WebSphere应用程序服务器
seo-title: Starting and stopping WebSphere Application Server
description: 有几个步骤要求您停止或启动要在其中部署AEM表单产品的WebSphere实例。 本文档介绍如何启动和停止WebSphere应用程序服务器。
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 启动和停止WebSphere应用程序服务器 {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

有几个步骤要求您停止或启动要在其中部署AEM表单产品的WebSphere实例。 如果不确定应用程序服务器是否已启动，您可以首先查看WebSphere应用程序服务器的状态。

## 查看WebSphere应用程序服务器的状态 {#view-the-status-of-websphere-application-server}

1. 在命令提示符下，转到 *[appserver根]*/bin目录。
1. 输入以下命令，替换 *server_name* ，其名称为WebSphere应用程序服务器：

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux、UNIX)。/ `serverStatus.sh`*server_name*

## 启动WebSphere应用程序服务器 {#start-websphere-application-server}

1. 在命令提示符下，转到 *[appserver根]*/bin目录。
1. 输入以下命令，替换 *server_name* ，其名称为WebSphere应用程序服务器：

   * (Windows) `startServer.bat`*server_name*
   * (Linux、UNIX)。/ `startServer.sh`*server_name*

## 停止WebSphere应用程序服务器 {#stop-websphere-application-server}

1. 在命令提示符下，转到 *[appserver根]*/bin目录。
1. 输入以下命令，替换 *server_name* ，其名称为WebSphere应用程序服务器：

   * (Windows) `stopServer.bat`*server_name*
   * (Linux、UNIX)。/ `stopServer.sh`*server_name*
