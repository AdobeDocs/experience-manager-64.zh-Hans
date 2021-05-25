---
title: 清除流程数据
seo-title: 清除流程数据
description: 在调用长生命周期进程时生成的进程数据可能会过大，从而降低AEM表单性能并使用不必要的磁盘空间。 了解如何清除流程数据。
seo-description: 在调用长生命周期进程时生成的进程数据可能会过大，从而降低AEM表单性能并使用不必要的磁盘空间。 了解如何清除流程数据。
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 清除进程数据{#purging-process-data}

在调用长生命周期进程时生成的进程数据可能会过大，从而降低AEM表单性能并使用不必要的磁盘空间。 最好在不再需要记录时清除流程数据。 AEM Forms提供了多种清除流程数据的方法：

* 您可以使用管理控制台执行与长期流程相关的过时记录一次性清除，或计划定期自动清除。 （请参阅[从作业管理器数据库中清除记录](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database)。）
* 您可以使用AEM Forms Java API和Web服务API以编程方式清除与长期流程相关的流程数据。 (请参阅[使用AEM表单编程](https://www.adobe.com/go/learn_aemforms_programming_63)中的“清除流程数据”。)
* 使用流程清除工具根据流程名称和其他参数清除流程。 有关详细信息，请参阅进程清除工具自述文件，该文件位于&#x200B;*[aem_forms根]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt中。
