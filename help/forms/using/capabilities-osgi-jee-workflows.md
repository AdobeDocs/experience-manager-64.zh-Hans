---
title: OSGi和AEM Forms JEE工作流中以表单为中心的AEM工作流的操作和功能
seo-title: Actions and capabilities of Form-centric AEM Workflows on OSGi and AEM Forms JEE workflows
description: 进一步了解AEM收件箱和HTML工作区支持的操作之间的差异，OSGi和AEM Forms JEE工作流上以表单为中心的AEM工作流支持的功能的差异，以及AEM收件箱和AEM Forms应用程序功能之间的差异。
seo-description: Learn more about the differences in actions supported by AEM Inbox and HTML Workspace, differences in capabilities supported by Form-centric AEM Workflows on OSGi and AEM Forms JEE Workflows, and differences between AEM Inbox and AEM Forms app features.
uuid: ce2a05fe-ba45-42ed-880e-fb1d6efc1d26
contentOwner: khsingh
topic-tags: publish
discoiquuid: 4c7ba430-25b2-4ba2-a5eb-4edaed0d599a
exl-id: 6172d936-9348-4f3f-a437-6465dd156f3b
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 20%

---

# OSGi和AEM Forms JEE工作流中以表单为中心的AEM工作流的操作和功能  {#actions-and-capabilities-of-form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

## AEM收件箱和HTML工作区 {#aem-inbox-and-html-workspace}

AEM收件箱用于在OSGi上运行和监控以Forms为中心的AEM工作流。 HTML工作区允许您运行和监视AEM Forms JEE工作流。 下表列出了以AEM为中心的AEM Workflows on OSGi和Analytics Workspace for AEM Forms JEE Workflows中的重要操作。

<table> 
 <tbody>
  <tr>
   <td>操作</td> 
   <td>AEM 收件箱</td> 
   <td>HTML工作区</td> 
  </tr>
  <tr>
   <td>启动进程、任务或表单应用程序<br /> </td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>提交任务</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>将任务分配给组</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>提交到多条路由</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>跟踪任务历史记录和任务摘要</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>电子邮件通知</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>重新分配任务</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>自适应表单的字段级附件</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>日历视图</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>任务级别注释</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>队列（共享的个人队列，从队列中声明任务）</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>离职通知</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>将任务分配给多个用户</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
 </tbody>
</table>

## OSGi和AEM Forms JEE工作流上以表单为中心的AEM工作流 {#form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

OSGi和AEM Forms JEE工作流(JEE流程管理上的AEM Forms)上以表单为中心的AEM工作流具有一组不同的功能。 下表列出了OSGi上以表单为中心的AEM工作流和JEE工作流上的AEM Forms中的功能可用的重要功能和支持：

<table> 
 <tbody>
  <tr>
   <td>功能</td> 
   <td>OSGi上以表单为中心的AEM工作流<br /> </td> 
   <td>AEM Forms JEE工作流</td> 
  </tr>
  <tr>
   <td>自适应表单</td> 
   <td>支持</td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>与其他AEM解决方案集成</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>潦草签名</td> 
   <td>支持</td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>自定义电子邮件模板</td> 
   <td>支持</td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>定义任务优先级</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>在到期日期后超时任务</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>工作流中的循环</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>动态选择受让人 </td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>使用自定义元数据</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>电子签名(Acrobat Sign)</td> 
   <td>支持 <sup>[1]</sup></td> 
   <td>支持 <sup>[5]</sup></td> 
  </tr>
  <tr>
   <td>管理任务和表单应用程序</td> 
   <td>支持 <sup>[2]</sup><br /> </td> 
   <td>支持 <sup>[2]</sup></td> 
  </tr>
  <tr>
   <td>文档服务</td> 
   <td>支持 <sup>[3]</sup></td> 
   <td>支持 <sup>[3]</sup></td> 
  </tr>
  <tr>
   <td>将已完成的任务渲染为自适应表单或PDF文档</td> 
   <td>支持</td> 
   <td>支持 [4]</td> 
  </tr>
  <tr>
   <td>与通信管理集成</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>“重置”按钮</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>工作流暂存</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>只读自适应表单</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>隐藏默认保存按钮</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>对工作流详细信息部分的精细控制</td> 
   <td>支持</td> 
   <td>不支持</td> 
  </tr>
  <tr>
   <td>HTML5 Forms，交互式PDF forms，表单集<br /> </td> 
   <td>不支持<br /> </td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>进程报告</td> 
   <td>不支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>数字签名</td> 
   <td>支持<br /> </td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>起点类别</td> 
   <td>不支持 </td> 
   <td>支持 </td> 
  </tr>
  <tr>
   <td>批量任务批准 </td> 
   <td>不支持 </td> 
   <td>支持 </td> 
  </tr>
  <tr>
   <td>使用自定义名称保存草稿</td> 
   <td>不支持 </td> 
   <td>支持 </td> 
  </tr>
  <tr>
   <td>使用现有流程数据启动流程<br /> </td> 
   <td>不支持</td> 
   <td>支持 </td> 
  </tr>
  <tr>
   <td>将起点另存为草稿</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>用户头像</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>管理器视图</td> 
   <td>不支持</td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>搜索数据集</td> 
   <td>不支持</td> 
   <td>支持<br /> </td> 
  </tr>
  <tr>
   <td>与第三方应用程序集成</td> 
   <td>支持 <sup>[6]</sup></td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>工作流应用程序或起点的任务级附件</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>提醒电子邮件</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>更改任务超时的标题</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>关于任务委派和任务声明的电子邮件</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>在工作流结束时发送电子邮件</td> 
   <td>支持 <sup>[7]</sup></td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>在不相交的组之间委派</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>从工作流中调用Web服务</td> 
   <td>支持 <sup>[6]</sup></td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>XSLT转换</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>网关，无等待</td> 
   <td>支持 </td> 
   <td>支持 </td> 
  </tr>
  <tr>
   <td>或和拆分</td> 
   <td>不支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>动态任务优先级</td> 
   <td>不支持</td> 
   <td>不支持</td> 
  </tr>
 </tbody>
</table>

1. 您可以在OSGi上使用以表单为中心的AEM工作流来签署已填写的自适应表单。 OSGi上以表单为中心的AEM工作流支持表单外签名。 的 [表单内签名](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) 不支持体验。

1. 您需要访问AEM收件箱来运行和监视AEM Forms OSGi AEM工作流，并HTML工作区来运行和监视AEM Forms JEE工作流。
1. 本机AEM Forms文档服务适用于OSGi上以表单为中心的AEM工作流和JEE工作流上的AEM Forms。 AEM Workflow使用本机文档服务在OSGi和AEM Forms JEE（流程管理）工作流上以表单为中心的AEM Workflows。
1. AEM Forms JEE工作流只能渲染自适应表单。 它不支持将自适应表单渲染为PDF文档。
1. AEM forms JEE工作流没有单独的Acrobat Sign步骤。 您需要启用Acrobat Sign的AEM Forms JEE工作流自适应表单。 有关更多详细信息，请参阅 [Acrobat Sign文档](/help/forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. 您可以使用 [调用表单数据模型服务](/help/forms/using/aem-forms-workflow-step-reference.md#p-invoke-form-data-model-service-step-p) 调用web服务并从第三方应用程序发布或检索数据的步骤。
1. 您可以使用 [发送电子邮件](/help/forms/using/aem-forms-workflow-step-reference.md#send-email-step) 发送电子邮件的步骤。

## AEM收件箱和AEM Forms应用程序功能之间的差异 {#differences-between-aem-inbox-and-aem-forms-app-features}

启动以Forms为中心的工作流的两种主要方法是 [AEM收件箱](/help/forms/using/manage-applications-inbox.md) 和AEM Forms应用程序。 但是，AEM收件箱和AEM Forms应用程序的功能有所不同。 AEM收件箱仅适用于 [以Forms为中心的工作流](/help/forms/using/aem-forms-workflow.md) 而AEM Forms应用程序可与以Forms为中心的工作流以及流程管理配合使用。

下表列出了AEM收件箱和AEM Forms应用程序的功能：

<table> 
 <tbody>
  <tr>
   <td><p><strong>操作</strong></p> </td> 
   <td><p><strong>AEM 收件箱</strong></p> </td> 
   <td><p><strong>AEM Forms 应用程序</strong></p> </td> 
  </tr>
  <tr>
   <td><p>启动表单应用程序</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
  <tr>
   <td><p>提交任务</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
  <tr>
   <td><p>委派任务</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>不支持</p> </td> 
  </tr>
  <tr>
   <td><p>跟踪任务历史记录和任务摘要</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>不支持</p> </td> 
  </tr>
  <tr>
   <td><p>添加任务级附件</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
  <tr>
   <td><p>查看任务级附件</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
  <tr>
   <td><p>添加字段级别附件</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
  <tr>
   <td><p>显示日历视图</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>不支持</p> </td> 
  </tr>
  <tr>
   <td><p>添加注释</p> </td> 
   <td><p>支持</p> </td> 
   <td><p>支持</p> </td> 
  </tr>
 </tbody>
</table>
