---
title: 在摘要URL中获取任务变量
seo-title: Getting Task Variables in Summary URL
description: 如何重复使用有关任务的信息并生成摘要URL以汇总或描述任务。
seo-description: How-to reuse the information about a task and generate a Summary URL to summarize or describe a task.
uuid: 9eab3a6a-a99a-40ae-b483-33ec7d21c5b6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6dc31bec-b02d-47db-a4f4-be8c14c5619e
exl-id: f80d006b-6970-4448-aa38-3ffec8b08c18
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 1%

---

# 在摘要URL中获取任务变量 {#getting-task-variables-in-summary-url}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

摘要页显示与任务相关的信息。 本文介绍了如何重复使用摘要页面中与任务相关的信息。

在此编排示例中，员工提交了休假申请表。 然后，申请表将转至员工经理进行审批。

1. 为resourceType创建示例HTML渲染器(html.esp) **员工/PtoApplication**.

   呈现器假定要在节点上设置以下属性：

   * name
   * empid
   * 原因
   * 持续时间

   >[!NOTE]
   >
   >此渲染器是摘要页面模板。

   此渲染器的以下示例代码包含在中：

   `apps/Employees/PtoApplication/html.esp`

   ```
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. 修改编排以从提交的表单数据中提取四个属性。 之后，在CRX中创建一个类型为 **员工/PtoApplication**，并填充资产。

   1. 创建流程 **创建PTO汇总** 并将其用作子进程，然后再使用 **分配任务** 操作。
   1. 定义 **employeeName**, **employeeID**, **ptoReason**, **totalDays**&#x200B;和 **nodeName** 作为新流程中的输入变量。 这些变量将作为提交的表单数据进行传递。

      此外，还定义一个输出变量**ptoNodePath **，该变量将在设置摘要Url时使用。

   1. 在 **创建PTO汇总** 流程，使用 **设置值** 用于在**nodeProperty **(**nodeProps**)映射。

      此映射中的键应与上一步中在HTML渲染器中定义的键相同。

      此外，添加 **sling:resourceType** 值键 **员工/PtoApplication** 地图中。

   1. 使用子进程 **storeContent** 从 **ContentRepositoryConnector** 服务 **创建PTO汇总** 进程。 此子进程会创建一个CRX节点。

      它需要三个输入变量：

      * **文件夹路径**:创建新CRX节点的路径。 将路径设置为 **/content**.
      * **节点名称**:将输入变量nodeName分配给此字段。 这是唯一的节点名称字符串。
      * **节点类型**:将类型定义为 **nt：非结构化**. 此进程的输出为nodePath。 nodePath是新创建节点的CRX路径。 ndoePath将是 **创建PTO** 摘要过程。
   1. 传递提交的表单数据(**employeeName**, **employeeID**, **ptoReason**&#x200B;和 **totalDays**)作为新流程的输入 **创建PTO汇总**. 将输出作为 **ptoSummaryNodePath**.


1. 将摘要Url定义为包含服务器详细信息的XPath表达式，以及 **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

在AEM Forms工作区中，打开任务时，摘要Url将访问CRX节点，HTML呈现器将显示摘要。

无需修改流程，即可更改摘要布局。 HTML渲染器会相应地显示摘要。
