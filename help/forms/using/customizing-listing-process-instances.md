---
title: 自定义进程实例列表
seo-title: Customizing the listing of process instances
description: 如何在AEM Forms工作区中自定义流程实例中显示的属性。
seo-description: How-to customize the properties displayed in process instance in AEM Forms workspace.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
exl-id: e7b8206c-bac2-48a6-b353-d06bc73b29f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 4%

---

# 自定义进程实例列表 {#customizing-the-listing-of-process-instances}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

进程实例列表显示在AEM Forms工作区的“跟踪”选项卡中。

在流程实例列表中，对于每个流程实例，AEM Forms工作区会显示该实例的某些属性。 每个进程实例都可使用以下属性。 这些属性将作为属性存储在流程实例组件模型中，并可在其视图和模板中使用。

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td><strong>评论</strong></td> 
  </tr> 
  <tr> 
   <td>说明</td> 
   <td>流程实例的描述。</td> 
  </tr> 
  <tr> 
   <td>发起者</td> 
   <td>进程实例的启动器名称。</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>进程实例的启动器ID。</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>进程完成时的时间戳。</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>进程实例的ID。</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 =已启动<br /> 1 =正在运行<br /> 2 =完成<br /> 3 =完成<br /> 4 =终止<br /> 5 =终止<br /> 6 =暂停<br /> 7 =暂停<br /> 8 =取消暂停</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>进程的名称。</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>进程开始时的时间戳。</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>进程变量对象数组。 每个进程变量对象都包含 <strong>name</strong> （进程变量的名称）、 <strong>值</strong> （进程变量的值）和<strong> type</strong> （进程变量的类型）。</td> 
  </tr> 
 </tbody> 
</table>

**示例:**

显示 `description` 进程实例卡中进程实例的属性，请执行以下步骤。

1. 关注 [AEM Forms工作区自定义的一般步骤](/help/forms/using/generic-steps-html-workspace-customization.md).
1. 执行以下操作：

   1. 将/libs/ws/js/runtime/templates/processinstance.html复制到/apps/ws/js/runtime/templates/（如果不存在）。 单击 **全部保存**.
   1. 使用类= &#39;processDescription&#39; inprocessinstance.html添加流程描述div。

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. 执行以下操作：

   1. 打开/apps/ws/js/registry.js进行编辑。
   1. 搜索和替换 `text!/lc/libs/ws/js/runtime/templates/processinstance.html`with `text!/lc/`**应用程序**/ws/js/runtime/templates/processinstance.html。

1. 上述更改可能需要通过以下方式在样式表/apps/ws/css/newStyle.css中添加一个条目来更新CSS文件：

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
