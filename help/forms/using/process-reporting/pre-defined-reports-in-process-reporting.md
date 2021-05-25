---
title: 流程报表中的预定义报表
seo-title: 流程报表中的预定义报表
description: 查询JEE上的AEM Forms进程数据，以创建有关长时间运行的进程、进程持续时间和工作流卷的报告
seo-description: 查询JEE上的AEM Forms进程数据，以创建有关长时间运行的进程、进程持续时间和工作流卷的报告
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 流程报表中的预定义报表{#pre-defined-reports-in-process-reporting}

AEM Forms Process Reporting随以下&#x200B;*现成*&#x200B;报表一起提供：

* **[长时间运行的进程](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**:一份报告，其中包含所有AEM Forms进程，这些进程需要超过指定时间才能完成

* **[流程持续时间图](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**:按持续时间划分的指定AEM Forms进程的报告

* **[工作流卷](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**:按日期列出的指定流程的已运行和已完成实例的报告

## 长运行进程{#long-running-processes}

“长时间运行的进程”报表显示完成的AEM Forms进程超过指定时间。

### 执行长运行进程报告{#to-execute-a-long-running-process-report-br}

1. 要查看Process Reporting中的预定义报表列表，请在&#x200B;**Process Reporting**&#x200B;树视图上单击&#x200B;**Reports**&#x200B;节点。
1. 单击&#x200B;**长运行进程**&#x200B;报告节点。

   ![long_running_node](assets/long_running_node.png)

   选择报表时，树视图右侧会显示&#x200B;**报表参数**&#x200B;面板。

   ![长时间运行的进程报告参数面板](assets/report_parameters_panel.png)

   参数:

   * **持续时间**(*必填*):指定持续时间和时间单位。显示运行时间超过指定持续时间的所有AEM Forms进程。
   * **开始时间** (*可选*):选择日期。过滤报表以显示在指定日期之后开始的流程实例。
   * **开始时间之前** (*可选*):选择日期。过滤报表以显示在指定日期之前开始的流程实例。

1. 单击&#x200B;**Go**&#x200B;以执行报告。

   该报表显示在&#x200B;**Process Reporting**&#x200B;窗口右侧的&#x200B;**Report**&#x200B;面板中。

   ![long_running_processes](assets/long_running_processes.png)

   使用&#x200B;**报表**&#x200B;面板右上角的选项对报表执行以下操作。

   * **刷新**:使用存储中的最新数据刷新报表
   * **更改图例颜色**:选择并更改报表图例的颜色
   * **导出到CSV**:将数据从报表导出并下载到以逗号分隔的文件

## 进程持续时间报表{#process-duration-report-br}

“进程持续时间”报表按每个实例运行的天数显示Forms进程的实例数。

### 执行进程持续时间报告{#to-execute-a-process-duration-report-br}

1. 要在“Process Reporting”（流程报表）中查看预定义的报表，请在&#x200B;**Process Reporting**&#x200B;树视图上单击&#x200B;**Reports**&#x200B;节点。
1. 单击&#x200B;**Processes Duration**&#x200B;报表节点。

   ![process_duration_node](assets/process_duration_node.png)

   选择报表时，树视图右侧会显示&#x200B;**报表参数**&#x200B;面板。

   ![长时间运行的进程报告参数面板](assets/process_duration_params.png)

   参数:

   * **选择流程** (*必填*):选择AEM Forms进程。

1. 单击&#x200B;**Go**&#x200B;以执行报告。

   报表显示在“流程报告”窗口右侧的&#x200B;**报表**&#x200B;面板中。

   ![process_duration_report](assets/process_duration_report.png)

   使用&#x200B;**报表**&#x200B;面板右上角的选项对报表执行以下操作。

   * **刷新**:使用存储中的最新数据刷新报表
   * **更改图例颜色**:选择并更改报表图例的颜色
   * **导出到CSV**:将数据从报表导出并下载到以逗号分隔的文件

## 工作流量报告{#workflow-volume-report}

“工作流量”报表按日历日显示AEM Forms进程当前运行和已完成的实例数。

### 执行工作流卷报告{#to-execute-a-workflow-volume-report-br}

1. 要在“Process Reporting”（流程报表）中查看预定义的报表，请在&#x200B;**Process Reporting**&#x200B;树视图上单击&#x200B;**Reports**&#x200B;节点。
1. 单击&#x200B;**工作流卷**&#x200B;报告节点。

   ![workflow_volume_node](assets/workflow_volume_node.png)

   选择报表时，树视图右侧会显示&#x200B;**报表参数**&#x200B;面板。

   ![长时间运行的进程报告参数面板](assets/workflow_volume_params.png)

   参数:

   * **选择流程**(*必填*):选择AEM Forms进程。
   * **开始时间** (*可选*):选择日期。过滤报表以显示在指定日期之后开始的流程实例。
   * **开始时间之前** (*可选*):选择日期。过滤报表以显示在指定日期之前开始的流程实例。

1. 单击&#x200B;**Go**&#x200B;以执行报告。

   该报表显示在&#x200B;**Process Reporting**&#x200B;窗口右侧的&#x200B;**Report**&#x200B;面板中。

   ![workflow_volume_report](assets/workflow_volume_report.png)

   使用&#x200B;**报表**&#x200B;面板右上角的选项对报表执行以下操作。

   * **刷新**:使用存储中的最新数据刷新报表
   * **更改图例颜色**:选择并更改报表图例的颜色
   * **导出到CSV**:将数据从报表导出并下载到以逗号分隔的文件
