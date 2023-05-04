---
title: 清除流程数据
seo-title: Purging process data
description: 在调用长生命周期进程时生成的进程数据可能会变得过大，从而降低AEM表单性能并使用不必要的磁盘空间。 了解如何清除流程数据。
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 2%

---

# 清除流程数据 {#purging-process-data}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在调用长生命周期进程时生成的进程数据可能会变得过大，从而降低AEM表单性能并使用不必要的磁盘空间。 最好在不再需要记录时清除流程数据。 AEM Forms提供了多种清除流程数据的方法：

* 您可以使用管理控制台执行与长期流程相关的过时记录一次性清除，或计划定期自动清除。 (请参阅 [从作业管理器数据库中清除记录](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* 您可以使用AEM Forms Java API和Web服务API以编程方式清除与长期流程相关的流程数据。 (请参阅 [使用AEM表单进行编程](https://www.adobe.com/go/learn_aemforms_programming_63).)
* 使用流程清除工具根据流程名称和其他参数清除流程。 有关详细信息，请参阅流程清除工具自述文件(位于 *[aem_forms根]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt。
