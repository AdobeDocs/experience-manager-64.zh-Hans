---
title: 在中配置异步操作 [!DNL Adobe Experience Manager]。
description: 异步完成一些资源密集型任务以优化性能 [!DNL Experience Manager Assets]。
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Asynchronous operations {#asynchronous-operations}

为了减少对性能的不利影响， [!DNL Adobe Experience Manger Assets] 请异步处理某些长时间运行和资源密集型资产操作。 异步处理涉及将多个任务入队，并最终以串行方式执行它们，这取决于系统资源的可用性。 这些操作包括：

* 删除许多资产。
* 移动许多资产或包含许多引用的资产.
* 批量导出和导入资产元数据。

您可以从“异步作业状态”页视图异 **[!UICONTROL 步任务的状]** 态。

>[!NOTE]
>
>默认情况下， [!DNL Assets] 任务并行执行。 If `N` is the number of CPU cores, `N/2` tasks can execute in parallel, by default. 要对任务队列使用自定义设置，请从 **[!UICONTROL Web控制台中修改“异步操作]** ”“默 [!UICONTROL 认队列”配置]。 有关更多信息，请参阅[队列配置](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)。

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Whenever [!DNL Assets] processes an operation asynchronously, you receive a notification in your [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) and via an email. 要查看异步操作状态的详细信息，请导航到&#x200B;**[!UICONTROL 异步作业状态]**&#x200B;页面。

1. In the [!DNL Experience Manager] interface click **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. 在&#x200B;**[!UICONTROL 异步作业状态]**&#x200B;页面中，查看操作的详细信息。

   ![异步操作的状态和详细信息](assets/job_status.png)

   要确定操作的进度，请参阅“状 **[!UICONTROL 态]** ”列。 根据进度，将显示以下状态之一：

   * **[!UICONTROL 活动]**：正在处理操作。
   * **[!UICONTROL 成功]**：操作已完成.
   * **[!UICONTROL 失败]**&#x200B;或&#x200B;**[!UICONTROL 错误]**：无法处理该操作.
   * **[!UICONTROL 已计划]**：该操作计划稍后处理.

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) from the toolbar.

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) from the toolbar. 将显示任务详细信息页面。

   ![元数据导入任务的详细信息](assets/job_details.png)

1. 要从列表中删除该操作，请从工具栏中选择&#x200B;**[!UICONTROL 删除]**。要以 CSV 文件下载详细信息，请单击&#x200B;**[!UICONTROL 下载]**。

   >[!NOTE]
   >
   >如果任务的状态为活动或排队，则无法删除该订阅。

## 清除已完成任务 {#purge-completed-tasks}

[!DNL Experience Manager Assets] 每天01时执行清除任务，删除已完成且已超过一天的异步任务。

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

您可以修改清除计划的任务以及删除之前保留已完成任务详细信息的持续时间。 您还可以配置在任何时间点保留详细信息的已完成任务的最大数量。

1. 在界面 [!DNL Experience Manager] 中，单 **[!UICONTROL 击“工具]** ”>“ **[!UICONTROL 操作]** ” **[!UICONTROL >“]** Web控制台”。
1. 打开 **[!UICONTROL Adobe CQDAM异步作业清除计划任务]** 。
1. 指定删除完成任务的天数阈值，以及保留历史记录详细信息的任务的最大天数。 保存更改。

   ![配置以计划异步任务的清除](assets/purge_job.png)

## 为异步删除操作配置阈值 {#configure-thresholds-for-asynchronous-delete-operations}

如果要删除的资产或文件夹数超过设置的阈值数，将异步执行删除操作。

1. 在界面 [!DNL Experience Manager] 中，单 **[!UICONTROL 击“工具]** ”>“ **[!UICONTROL 操作]** ” **[!UICONTROL >“]** Web控制台”。
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. 在“资 **[!UICONTROL 产的阈值数]** ”框中，指定阈值数以异步删除资产、文件夹或引用。 保存更改。

   ![设置任务删除资产的阈值限制](assets/delete_threshold.png)

## 为异步移动操作配置阈值 {#configure-thresholds-for-asynchronous-move-operations}

如果要移动的资产、文件夹或引用数超过设置的阈值数，则异步执行移动操作。

1. 在界面 [!DNL Experience Manager] 中，单击 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web控制台]**。
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. 在“资 **[!UICONTROL 产／引用的阈值数]** ”框中，指定用于异步移动资产、文件夹或引用的阈值数。 保存更改。

   ![设置任务移动资产的阈值限制](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [在Experience Manager中配置电子邮件](/help/sites-administering/notification.md)。
>* [批量导入和导出资产元数据](/help/assets/metadata-import-export.md)。

