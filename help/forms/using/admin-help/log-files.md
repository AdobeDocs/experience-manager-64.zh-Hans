---
title: 日志文件
seo-title: Log files
description: 运行时或启动错误等事件将记录到应用程序服务器日志文件中，可以使用任何文本编辑器打开这些文件。
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# 日志文件 {#log-files}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

运行时或启动错误等事件将记录到应用程序服务器日志文件中。 如果在部署到应用程序服务器时遇到任何问题，可以使用日志文件帮助您查找问题。 您可以使用任何文本编辑器打开日志文件。

(JBoss)以下日志文件位于 `*[appserver root]*/server/*[server]*/log` 目录：

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic)域日志文件位于 *[appserverdomain]* 目录和服务器日志文件位于*[appserverdomain]/servers/[appserver name]/logs *directory:

* access.log
* *[appserver name]*.log
* *[appserver name]*.out.*[增量数]*

(WebSphere)以下日志文件位于 *[appserver根]*/profiles/default/logs/*[appserver name]* 目录：

* SystemErr.log
* SystemOut.log
* StartServer.log
