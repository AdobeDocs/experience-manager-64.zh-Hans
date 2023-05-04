---
title: 自定义任务详细信息页
seo-title: Customizing the task details page
description: 如何在AEM Forms工作区中自定义任务详细信息页面，以修改显示的有关任务的默认信息。
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 2%

---

# 自定义任务详细信息页 {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

任务详细信息页面包含有关任务及其进程的信息。 但是，您可以自定义任务详细信息页面以添加或删除信息。

您可以将以下信息添加到任务详细信息页面：

* 任务的JSON对象( [AEM Forms工作区JSON对象描述](/help/forms/using/html-workspace-json-object-description.md))
* 进程实例的JSON对象( [AEM Forms工作区JSON对象描述](/help/forms/using/html-workspace-json-object-description.md))

要自定义任务详细信息页面，请执行以下操作：

1. 关注 [自定义AEM Forms工作区的一般步骤。](/help/forms/using/generic-steps-html-workspace-customization.md)
1. 要显示任何其他信息，请向 `translation.json` 文件位置 `todo`块> `details`块> `app`块> [ `required`块].

   的 [ `required`块] 是指可用的块，如任务信息的任务块、进程信息的进程块和待定任务信息的当前待定任务块。

   例如，要在任务详细信息页面中添加有关“所需路由选择”的信息，您可以在任务块中添加以下键值对：

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >为所有支持的语言添加相应的键值对。

1. 复制 `/libs/ws/js/runtime/templates/taskdetails.html` to `/apps/ws/js/runtime/templates/taskdetails.html`.

   将新信息添加到 `/apps/ws/js/runtime/templates/taskdetails.html`. 例如：

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. 打开/apps/ws/js/registry.js进行编辑。

   搜索和替换 `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` with `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>要使用在AEM Forms工作区的**开始流程**选项卡中创建的任务自定义任务详细信息页面，请将新信息添加到 `/apps/ws/js/runtime/templates/startprocess.html`.
>
>要为详细信息页面中添加的信息添加新样式，请使用 *用户界面更改* 部分 [工作区自定义](/help/forms/using/changing-locale-user-interface.md).
