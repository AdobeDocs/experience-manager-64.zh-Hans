---
title: 流程中的预定义报告报告
seo-title: 流程中的预定义报告报告
description: 查询JEE上的AEM Forms流程数据，以创建有关长时间运行流程、流程持续时间和工作流卷的报告
seo-description: 查询JEE上的AEM Forms流程数据，以创建有关长时间运行流程、流程持续时间和工作流卷的报告
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# 流程中的预定义报告报告 {#pre-defined-reports-in-process-reporting}

AEM Forms Process报告随附 *以下现成报表* :

* **[长时间运行的进程](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: 所有AEM Forms进程的报告，这些进程需要超过指定的时间才能完成

* **[流程持续时间图表](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: 按持续时间列出的指定AEM Forms流程报告

* **[工作流卷](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: 按日期列出指定进程正在运行和已完成实例的报告

## 长时间运行的进程 {#long-running-processes}

“长时间运行的进程”报告显示完成所花费的时间超过指定时间的AEM Forms进程。

### 执行长进程运行报告 {#to-execute-a-long-running-process-report-br}

1. 要视图“流程报告”中预定义报表的列表，请在“流程 **报告”树** 视图中，单击“报 **表** ”节点。
1. 单击“长 **运行进程** ”报告节点。

   ![long_running_node](assets/long_running_node.png)

   选择报告时，树视图 **的右侧** 将显示“报告参数”面板。

   ![长运行进程报告参数面板](assets/report_parameters_panel.png)

   参数:

   * **持续时间**(*必填*): 指定持续时间和时间单位。 显示运行时间超过指定持续时间的所有AEM Forms进程。
   * **开始时间** (*可选*): 选择日期。 过滤报告以显示在指定日期之后开始的流程实例。
   * **开始时间** (*可选*): 选择日期。 过滤报告以显示在指定日期之前开始的流程实例。

1. 单击 **开始** ，以执行报告。

   该报表显示在“ **流程** ”报告窗口右 **侧的“报** 表”面板。

   ![long_running_processes](assets/long_running_processes.png)

   使用“报告”面板右上角的 **选项** ，对报告执行以下操作。

   * **刷新**: 刷新报表时，存储中会显示最新数据
   * **更改图例颜色**: 选择并更改报表图例的颜色
   * **导出到CSV**: 将数据从报告导出并下载到以逗号分隔的文件

## 流程持续时间报告 {#process-duration-report-br}

“流程持续时间”报告按每个实例运行的天数显示表单流程的实例数。

### 执行“进程持续时间”报告 {#to-execute-a-process-duration-report-br}

1. 要在“流程视图”报告中视图预定义的报表，请在“流程 **报告”树** ，单击“报 **表”节点** 。
1. 单击“进 **程持续时间** ”报告节点。

   ![process_duration_node](assets/process_duration_node.png)

   选择报告时，树视图 **的右侧** 将显示“报告参数”面板。

   ![长运行进程报告参数面板](assets/process_duration_params.png)

   参数:

   * **选择流程** (*必填*): 选择一个AEM Forms流程。

1. 单击 **开始** ，以执行报告。

   此报告显示在“ **流程** ”报告窗口右侧的“报告”面板中。

   ![process_duration_report](assets/process_duration_report.png)

   使用“报告”面板右上角的 **选项** ，对报告执行以下操作。

   * **刷新**: 刷新报表时，存储中会显示最新数据
   * **更改图例颜色**: 选择并更改报表图例的颜色
   * **导出到CSV**: 将数据从报告导出并下载到以逗号分隔的文件

## 工作流卷报告 {#workflow-volume-report}

工作流卷报告按日历日显示AEM Forms进程当前正在运行和已完成的实例数。

### 执行工作流卷报告 {#to-execute-a-workflow-volume-report-br}

1. 要在“流程视图”报告中视图预定义的报表，请在“流程 **报告”树** ，单击“报 **表”节点** 。
1. 单击“工 **作流卷** ”报告节点。

   ![workflow_volume_node](assets/workflow_volume_node.png)

   选择报告时，树视图 **的右侧** 将显示“报告参数”面板。

   ![长运行进程报告参数面板](assets/workflow_volume_params.png)

   参数:

   * **选择进程**(*必填*): 选择一个AEM Forms流程。
   * **开始时间** (*可选*): 选择日期。 过滤器报表以显示在指定日期之后开始的流程实例。
   * **开始时间** (*可选*): 选择日期。 过滤器报表以显示在指定日期之前开始的流程实例。

1. 单击 **开始** ，以执行报告。

   该报表显示在“ **流程** ”报告窗口右 **侧的“报** 表”面板。

   ![workflow_volume_report](assets/workflow_volume_report.png)

   使用“报告”面板右上角的 **选项** ，对报告执行以下操作。

   * **刷新**: 刷新报表时，存储中会显示最新数据
   * **更改图例颜色**: 选择并更改报表图例的颜色
   * **导出到CSV**: 将数据从报告导出并下载到以逗号分隔的文件

