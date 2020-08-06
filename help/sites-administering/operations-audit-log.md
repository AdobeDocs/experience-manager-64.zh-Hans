---
title: AEM 6中的审核日志维护
seo-title: AEM 6中的审核日志维护
description: 了解AEM中的审核日志维护。
seo-description: 了解AEM中的审核日志维护。
uuid: 212de4df-6bf4-434c-94e1-74186d21945a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 565d89de-b3ca-41a5-8e1c-d10905c25fb5
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# AEM 6中的审核日志维护{#audit-log-maintenance-in-aem}

符合审核记录资格的AEM事件会生成大量归档数据。 由于复制、资产上传和其他系统活动，这些数据会随着时间的推移而快速增长。

“审核日志维护”包括几个功能部分，这些功能允许根据特定策略自动执行审核日志维护。

它作为可配置的每周维护任务实施，并可通过“操作仪表板”监控控制台访问。

有关详细信息，请参阅操 [作仪表板文档](/help/sites-administering/operations-dashboard.md)。

审核日志清除选项有三种类型：

1. [页面审核日志清除](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM审核日志清除](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [复制审核日志更新](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

每项配置均可通过在AEM Web控制台中创建规则来进行。 配置完它们后，您可以转到“工具”-“操作”-“ **维护”-“每周维护”窗口并运行“审核日志”** “维护” **任务来触发它们**。

## 配置页面审核日志清除 {#configure-page-audit-log-purging}

按照以下步骤配置审核日志清除：

1. 通过将浏览器指向 `http://localhost:4502/system/console/configMgr/`

1. 搜索名为“页面审核日 **志清除”规则的项** ，然后单击它。

   ![chlimage_1-365](assets/chlimage_1-365.png)

1. 然后，根据您的要求配置清除调度程序。 可用选项有：

   * **规则名称：** 审计政策规则的名称；
   * **内容路径：** 规则将应用到的内容的路径；
   * **最低年龄：** 需要保存审计日志的时间（以天为单位）;
   * **审核日志类型：** 应清除的审核日志类型。

   >[!NOTE]
   >
   >内容路径仅适用于存储库中 `/var/audit/com.day.cq.wcm.core.page` 节点的子项。

1. 保存规则。
1. 您刚刚创建的规则需要在“操作”仪表板中公开才能执行。 为此，请从AEM欢 **迎屏幕转至** “工具”-“操作”-“维护”。

1. 按“Weekly **Maintenance Window** （每周维护窗口）”卡。

1. 您会在AuditLog维护任务卡下找到 **已存在的维护任务** 。

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. 您可以检查下次执行的日期、对其进行配置或通过按播放按钮手动执行。

在AEM 6.3中，如果计划的维护窗口在“审核日志清除”任务完成之前关闭，则任务会自动停止。 下次维护窗口打开时，它将恢复。

**在AEM 6.4中**，您可以单击“停止”图标，手动停止正在运行的“审核日志清除 **任务** ”。 下次执行时，任务将安全恢复。

>[!NOTE]
>
>停止维护任务意味着暂停其执行，而不丢失对已进行作业的跟踪。

## 配置DAM审核日志清除 {#configure-dam-audit-log-purging}

1. 导航到位于以下位置 *的“系统控制台”:https://&lt;serverport>:&lt;serverport>/system/console/configMgr*
1. 搜索DAM **审核日志清除规** 则，然后单击结果。
1. 在下一个窗口中，相应地配置您的规则。 选项有：

   * **规则名称：** 审计政策规则的名称；
   * **内容路径：** 规则将应用到的内容的路径
   * **最低年龄：** 需要保存审计日志的时间（以天为单位）
   * **审核日志Dam事件类型:** 应清除的DAM审核事件类型。

1. 单击 **保存** ，以保存配置

## 配置复制审核日志清除  {#configure-replication-audit-log-purging}

1. 导航到位于以下位置 *的“系统控制台”:https://&lt;serverport>:&lt;serverport>/system/console/configMgr*
1. 搜索复 **制审核日志清除调度程序** ，然后单击结果
1. 在下一个窗口中，相应地配置您的规则。 选项有：

   * **规则名称：** 审计策略规则的名称
   * **内容路径：** 规则将应用到的内容的路径
   * **最低年龄：** 需要保存审计日志的时间（以天为单位）
   * **审核日志复制事件类型:** 应清除的复制审核事件类型

1. 单击 **保存** ，以保存配置。

