---
title: 为任务自定义选项卡
seo-title: Customizing tabs for a task
description: 如何在LiveCycleAEM Forms工作区中自定义任务的选项卡名称。
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 3%

---

# 为任务自定义选项卡 {#customizing-tabs-for-a-task}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以自定义 `Start Process` 组件 `Start Process` Uber视图和 `Task Details` 组件 `ToDo` 优步视图。

1. 关注 [AEM Forms工作区自定义的一般步骤](/help/forms/using/generic-steps-html-workspace-customization.md).
1. 更改 `tabname`在 `translation.json` 文件。

   例如，更改 `/apps/ws/locales/en-US/translation.json` 对下面的内容进行英语翻译。

   * 对于在启动过程中启动的任务，请使用 `"startprocess" : {}` 块。

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * 对于待办事项中的任务，请使用 `"todo" : {}` 块。

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >为所有支持的语言添加相应的键值对。
