---
title: 启动和停止服务
seo-title: Starting and stopping services
description: 了解如何启动和停止与AEM Forms模块以及应用程序服务器和数据库相关的服务。
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---

# 启动和停止服务 {#starting-and-stopping-services}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM表单包含两种类型的服务：

* 控制AEM Forms应用程序服务器和数据库的服务。
* 控制AEM表单模块的服务

## 启动或停止与AEM表单模块关联的服务 {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM表单模块(例如，Forms、Rights Management、输出)作为服务运行。 有时，您可能需要停止或启动这些AEM表单模块的服务。 例如，在更改服务的设置后，必须停止并重新启动AEM表单服务。

1. 在管理控制台中，单击 **服务** > **应用程序和服务** > **服务管理**.
1. 在“服务管理”页面上，选中服务旁边的复选框以停止或启动，然后单击停止或启动。

## 启动或停止应用程序服务器和数据库的服务 {#start-or-stop-services-for-the-application-server-and-database}

AEM表单的完整实施包括应用程序服务器和数据库服务：

* *`[application server]`* 用于AEM表单
* *`[database]`* 用于AEM表单

在Windows上，可通过 **管理工具** > **“服务”面板**. 例如，如果您使用turnkey方法在JBoss上安装了AEM表单，则系统上可以使用以下服务：

* 适用于Adobe Experience Manager表单的JBoss
* MySQL for Adobe Experience Manager表单

通过从“服务”面板的列表中选择这些服务，然后单击面板上的相应操作按钮，开始或停止这些服务。

在UNIX®或Linux上，从命令行中输入以下文本，其中 *`[service name]`* 是您正在验证的服务的名称：

```as3
     ps -A | grep [service name]
```
