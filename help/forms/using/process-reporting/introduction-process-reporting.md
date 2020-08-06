---
title: 流程报告简介
seo-title: 流程报告简介
description: AEM Forms在JEE过程报告中的介绍和关键功能
seo-description: AEM Forms在JEE过程报告中的介绍和关键功能
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# 流程报告简介 {#introduction-to-process-reporting}

![过程报告](assets/process-reporting.png)

流程报告是一个基于浏览器的工具，用于创建和视图有关AEM Forms流程和任务的报告。

流程报告提供一组现成报告，允许您过滤、视图有关长期运行的流程、流程持续时间和工作流卷的信息。

其他流程报告提供一个界面，用于运行临时查询并将自定义报告视图集成到流程报告用户界面中。

有关受支持浏览器的列表，请参阅 [AEM Forms支持的平台](/help/forms/using/aem-forms-jee-supported-platforms.md)。

流程报告建立在以下模块上：

* 从AEM Forms数据库读取处理数据
* 将流程数据发布到嵌入式流程报告库
* 为视图报告提供基于浏览器的用户界面

## 主要功能 {#key-capabilities}

### 始终在线报告 {#always-on-reporting}

![站点管理](assets/site-management.png)

视图长运行进程的列表、进程持续时间图表，并使用过滤器运行自定义查询。

流程报告还提供以CSV格式导出报表和查询数据的选项。

### 临时报告 {#adhoc-reports}

![打印和颜色](assets/print-&-colour.png)

使用过滤器获取特定视图的数据。

您可以按ID、持续时间、开始和结束日期、流程启动器等搜索流程或任务。

您可以合并多个过滤器以创建特定报表。

然后，您可以保存要在以后的日期或时间运行的报表过滤器。

### 进程/任务历史 {#process-task-history}

![文件管理](assets/file-management.png)

AEM Forms服务器并行运行多个进程。 这些过程会持续从一种状态过渡到另一种状态。 通过定期将Forms报告发布到进程报告库，进程数据保留有关在AEM Forms运行的进程的转换信息。

### 访问控制 {#access-control-br}

![未命名](assets/untitled.png)

流程报表提供对用户界面的基于权限的访问。

这意味着只有具有报告权限的用户才有权访问进程报告用户界面。


