---
title: 日志文件
seo-title: 日志文件
description: 运行时或启动错误等事件将记录到应用程序服务器日志文件中，可以使用任何文本编辑器打开这些文件。
seo-description: 运行时或启动错误等事件将记录到应用程序服务器日志文件中，可以使用任何文本编辑器打开这些文件。
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 日志文件{#log-files}

运行时或启动错误等事件将记录到应用程序服务器日志文件中。 如果在部署到应用程序服务器时遇到任何问题，可以使用日志文件帮助您查找问题。 您可以使用任何文本编辑器打开日志文件。

(JBoss)以下日志文件位于`*[appserver root]*/server/*[server]*/log`目录中：

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic)域日志文件位于&#x200B;*[appserverdomain]*&#x200B;目录中，服务器日志文件位于*[appserverdomain]/servers/[appserver name]/logs *目录中：

* access.log
* *[appserver name]*.log
* *[appserver name]*.out。*[增量数]*

(WebSphere)以下日志文件位于&#x200B;*[appserver root]*/profiles/default/logs/*[appserver name]*&#x200B;目录中：

* SystemErr.log
* SystemOut.log
* StartServer.log
