---
title: 最大限度地减少数据库增长的提示
seo-title: Tips for minimizing database growth
description: 持续时间较长的进程将进程数据存储在AEM Forms数据库中。 使用一些简单的流程设计和产品配置策略，可以最大限度地减少AEM表单数据库的增长。
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: 7b266170-c7e2-42e7-8ee0-153e1e73a901
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# 最大限度地减少数据库增长的提示 {#tips-for-minimizing-database-growth}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

持续时间较长的进程将进程数据存储在AEM Forms数据库中。 使用一些简单的流程设计和产品配置策略，可以最大限度地减少AEM表单数据库的增长。

## 流程设计提示 {#process-design-tips}

尽可能使用短时间的流程。 短暂的进程不会在数据库中存储进程数据。 使用短期进程的缺点是，在管理控制台中不会跟踪其状态和状态，并且该进程没有历史记录。

某些服务操作(如“分配任务”操作（“用户服务”）)要求在长寿命的进程中使用它们。 在这种情况下，您可以将流程划分为多个子流程，并尽可能缩短这些子流程的生命周期。 如果使用此策略，则短期子进程应处理大数据项，如文档值。

少用变量。 使用长寿命进程时，对于每个进程实例，在数据库中为进程中的每个变量分配空间。 战略性地使用变量可以节省大量空间。 例如，当流程中不再需要旧值时，您可以覆盖变量值。 并删除已创建且未使用的任何变量。 您可以验证该流程以查找未使用的变量。

使用简单的变量类型（例如，字符串或整数），并尽量避免使用复杂的变量类型。 即使变量不包含值，也会为变量分配数据库空间。 复杂变量通常比简单变量需要更多的空间。

## 产品管理提示 {#product-administration-tips}

有效地使用全局文档存储(GDS)。 表单服务器上的GDS目录用于存储传递到流程中AEM表单一部分的服务的文件，等等。 为了提高性能，较小的文档将存储在内存中并保留在数据库中。

管理控制台公开了“默认文档最大内联大小”属性，用于配置存储在内存中并保留在数据库中的文档的最大大小。 (请参阅 [配置常规AEM表单设置](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) 如果将此属性设置为低值，则大多数文档会保留在GDS目录中，而不是数据库中。 优势在于，当文件存储在GDS目录中时，不再需要时，您可以更轻松地删除这些文件。
