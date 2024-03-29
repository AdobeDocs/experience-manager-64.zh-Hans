---
title: 流程报表的工作原理
seo-title: How Process Reporting Works
description: JEE流程报表中构成AEM Forms的服务描述以及流程报表UI简介
seo-description: Description of the services that make up the AEM Forms on JEE Process Reporting and an introduction to the Process Reporting UI
uuid: 00a2dd6d-8a6f-4c7b-b03e-81cfd4bcf50d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: 4afc68fc-6b39-4c31-95fa-2ef3111c57da
exl-id: 05ef8b08-bb1d-441d-8b02-5f047efbabcb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 1%

---

# 流程报表的工作原理 {#how-process-reporting-works}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

“流程报告”是AEM Forms JEE上的报告模块。

“流程报表”允许您对AEM Forms流程和任务运行报表。

“流程报表”使用嵌入的“流程报表”存储库发布Forms数据。 然后，它使用该数据来运行报表。

Process Reporting包含以下模块：

* [ProcessDataPublisher服务](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [ProcessDataStorage服务](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [OSGi服务](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [查询数据Servlet](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [流程报表用户界面](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## 流程报告架构 {#process-reporting-architecture-br}

![处理报告架构](assets/processreportingarchitecture.png)

## 流程报告模块 {#process-reporting-modules}

### ProcessDataPublisher服务 {#processdatapublisher-service-br}

ProcessDataPublisher服务器在AEM Forms数据库上定期运行，并提取自上次运行服务以来更改的数据。 然后，它会将数据发布到进程数据存储服务。

有关配置服务的详细信息，请参阅 [配置ProcessDataPublisher服务](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider服务 {#processdatastorageprovider-service-br}

ProcessDataStorageProvider服务从ProcessDataPublisher服务接收进程数据，并将数据保存到Process Reporting存储库。

有关配置服务的详细信息，请参阅 [配置ProcessDataStorageProvider服务](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi服务 {#osgi-service-br}

QueryDataServlet使用此服务从Process Reporting存储库获取报表数据。

### QueryDataServlet服务 {#querydataservlet-service-br}

QueryDataServlet服务接受来自Process Reporting用户界面的查询。

然后，该服务使用OSGi服务获取相关的报告数据，处理该数据，并将该数据返回到用户界面。

### 流程报表用户界面 {#process-reporting-user-interface-br}

“流程报表”用户界面是基于Web浏览器的界面。 使用此界面可查看从AEM Forms数据库发布的流程和任务信息。

### QueryDataServlet服务 {#querydataservlet-service-br-1}

QueryDataServlet服务接受来自Process Reporting用户界面的查询。

然后，该服务使用OSGi服务获取相关的报告数据，处理该数据，并将该数据返回到用户界面。

### 自定义报表 {#custom-reports-br}

您可以创建自己的自定义报表，并在“流程报表”用户界面的“自定义报表”选项卡中显示这些报表。

有关创建自定义报表的步骤，请参阅文章中的创建自定义报表 [流程中的自定义报表](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
