---
title: 自定义任务的选项卡
seo-title: 自定义任务的选项卡
description: 如何在LiveCycleAEM Forms工作区中自定义任务的选项卡名称。
seo-description: 如何在LiveCycleAEM Forms工作区中自定义任务的选项卡名称。
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# 自定义任务的选项卡 {#customizing-tabs-for-a-task}

您可以为Uber视图中的组 `Start Process` 件和Uber `Start Process` 视图中的组 `Task Details` 件自定义选 `ToDo` 项卡名称。

1. 按照AEM Forms [工作区自定义的通用步骤操作](/help/forms/using/generic-steps-html-workspace-customization.md)。
1. 更改文件 `tabname`中的 `translation.json` 值。

   例如，将“英 `/apps/ws/locales/en-US/translation.json` 语”更改为以下内容。

   * 对于在开始过程中启动的任务，请使用块中的以下代 `"startprocess" : {}` 码片断。

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * 对于“待办事项”中的任务，请使用块中的以下代 `"todo" : {}` 码片断。

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
