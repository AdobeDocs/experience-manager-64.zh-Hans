---
title: 基于OSGi的以Forms为中心的工作流
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: 使用AEM Forms工作流自动化并快速构建审阅和批准、启动文档服务(例如，将PDF文档转换为其他格式)、与Acrobat Sign签名工作流集成等。
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2902'
ht-degree: 2%

---

# 基于OSGi的以Forms为中心的工作流 {#forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

![](do-not-localize/header.png)

企业从成千上万的表单、各种后端系统以及在线或离线数据源中收集数据。 他们还拥有一组动态的用户来对数据做出决策，其中涉及迭代审核和批准流程。

除了针对内部和外部受众的审核和批准工作流程外，大型组织和企业还会执行重复的任务。 例如，将PDF文档转换为其他格式。 手动完成这些任务时，需要花费大量时间和资源。 企业还有法律要求对文档进行数字签名并将表单数据存档，以供以后以预定义格式使用。

## OSGi上以Forms为中心的工作流简介 {#introduction-to-forms-centric-workflow-on-osgi}

您可以使用AEM工作流快速构建基于表单的自适应工作流。 这些工作流可用于审核和批准、业务流程、启动文档服务、与Acrobat Sign签名工作流集成以及类似操作。 例如，信用卡申请处理、员工休假审批工作流、将表单另存为PDF文档。 此外，这些工作流可以在组织内或跨网络防火墙使用。

借助OSGi上以Forms为中心的工作流，您可以在OSGi堆栈上为各种任务快速构建和部署工作流，而无需在JEE堆栈上安装完整的流程管理功能。 工作流的开发和管理使用了熟悉的AEM工作流和AEM收件箱功能。 工作流是自动化现实业务流程的基础，这些业务流程跨多个软件系统、网络、部门甚至组织进行。

设置后，可以手动触发这些工作流以完成定义的流程，或在用户提交表单或 [通信管理](/help/forms/using/cm-overview.md) 信。 通过这项增强的AEM工作流功能，AEM Forms提供了两项不同但相似的功能。 在部署策略中，您需要决定哪种方法适合您。 查看 [比较](/help/forms/using/capabilities-osgi-jee-workflows.md) OSGi上以Forms为中心的AEM工作流和JEE上的流程管理。 此外，对于部署拓扑，请参见， [AEM Forms的架构和部署拓扑](/help/forms/using/aem-forms-architecture-deployment.md).

基于OSGi的以Forms为中心的工作流扩展 [AEM收件箱](/help/sites-authoring/inbox.md) 和为AEM工作流编辑器提供了额外的组件（步骤），以添加对以AEM Forms为中心的工作流的支持。 扩展的AEM收件箱具有类似于 [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). 除了管理以人为中心的工作流程（审批、审核等）之外，您还可以使用AEM工作流程实现自动化 [文档服务](/help/sites-developing/workflows-step-ref.md) — 相关操作(例如，生成PDF)和电子签名(Acrobat Sign)文档。

下图描述了在OSGi上创建、运行和监视以Forms为中心的工作流的端到端过程。

![aem-forms-workflow简介](assets/introduction-to-aem-forms-workflow.jpg)

## 开始之前 {#before-you-start}

* 工作流是真实业务流程的表示。 让您的真实业务流程和业务流程参与者列表随时可用。 此外，在开始创建工作流之前，请准备好宣传资料(自适应表单、PDF文档等)。
* 一个工作流可以具有多个阶段。 这些阶段显示在AEM收件箱中，并帮助报告工作流的进度。 将您的业务流程划分为逻辑阶段。
* 您可以配置AEM Workflow的分配任务步骤，以向用户或受分配者发送电子邮件通知。 所以， [启用电子邮件通知](#configure-email-service).
* 工作流还可以使用Acrobat Sign进行数字签名。 如果您计划在工作流中使用Acrobat Sign，则 [配置Acrobat Sign for AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 在工作流中使用之前，请执行以下操作：

## 创建工作流模型 {#create-a-workflow-model}

工作流模型由业务流程的逻辑和流程组成。 它由一系列步骤组成。 这些步骤是AEM组件。 您可以根据需要通过参数和脚本扩展工作流步骤，以提供更多功能和控制。 除了开箱即用的AEM步骤之外，AEM Forms还提供了一些步骤。 有关AEM和AEM Forms步骤的详细列表，请参阅 [AEM工作流步骤参考](/help/sites-developing/workflows-step-ref.md) 和 [基于OSGi的以Forms为中心的工作流 — 步骤参考](/help/forms/using/aem-forms-workflow.md).

AEM提供了直观的用户界面，以使用提供的工作流步骤创建工作流模型。 有关创建工作流模型的分步说明，请参阅 [创建工作流模型](/help/sites-developing/workflows-models.md). 以下示例提供了为审批和审核工作流创建工作流模型的分步说明：

>[!NOTE]
>
>您必须是工作流编辑器组的成员才能创建或编辑工作流模型。

### 为审批和审核工作流程创建模型 {#create-a-model-for-an-approval-and-review-workflow}

审批和审核工作流是针对需要人为干预才能做出决策的任务。 以下示例为要由前台银行代理填写的按揭贷款应用程序创建工作流模型。 填写申请后，将发送该申请以供审批。 随后，将批准的申请发给申请人，请其使用Acrobat Sign进行电子签名。

该示例以下附加的包形式提供。 使用包管理器导入和安装示例。 您还可以执行以下步骤来为应用程序手动创建工作流模型：

该示例创建一个工作流模型，该工作流模型是由前台银行代理填写的抵押申请。 填写完毕后，将发送该申请以供审批。 稍后，批准的申请将发送给客户，以便使用Acrobat Sign进行电子签名。 您可以使用包管理器导入和安装示例。

[获取文件](assets/example-mortgage-loan-application.zip)

1. 打开“工作流模型”控制台。 默认URL为 `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. 选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建模型]**. 此时将出现“添加工作流模型”(Add Workflow Model)对话框。
1. 输入 **[!UICONTROL 标题]** 和 **[!UICONTROL 名称]** （可选）。 例如，抵押申请。 点按 **[!UICONTROL 完成]**.
1. 选择新创建的工作流模型并点按 **编辑。** 现在，您可以添加工作流步骤以构建业务逻辑。 首次创建工作流模型时，它包含：

   * 步骤：流量开始和流量结束。 这些步骤表示工作流的开始和结束。 这些步骤是必需的，无法编辑或删除。
   * 名为步骤1的“参与者”步骤示例。 此步骤配置为将工作项分配给管理员用户。 删除此步骤。

1. 启用电子邮件通知。 您可以在OSGi上配置以Forms为中心的工作流，以向用户或受分配者发送电子邮件通知。 执行以下配置以启用电子邮件通知：

   1. 转到AEM配置管理器(位于 `https://[server]:[port]/system/console/configMgr`.
   1. 打开 **[!UICONTROL Day CQ Mail Service]** 配置。 为 **[!UICONTROL SMTP服务器主机名]**, **[!UICONTROL SMTP服务器端口、]** 和 **[!UICONTROL “发件人”地址]** 字段。 单击“**[!UICONTROL 保存]**”。
   1. 打开 **[!UICONTROL Day CQ链接外部器]** 配置。 在 **[!UICONTROL 域]** 字段，为本地、创作和发布实例指定实际的主机名/IP地址和端口号。 单击“**[!UICONTROL 保存]**”。

1. 创建工作流阶段。 一个工作流可以具有多个阶段。 这些阶段会显示在AEM收件箱中并报告工作流进度。

   要定义舞台，请点按 ![信息圈](assets/info-circle.png) 图标以打开工作流模型属性，请打开 **[!UICONTROL 阶段]** ，为工作流模型添加阶段，然后点按 **[!UICONTROL 保存并关闭]**. 对于抵押申请示例，请创建阶段：贷款申请、贷款申请状态、待签文件、已签贷款文件。

1. 拖放 **[!UICONTROL 分配任务]** 步骤浏览到工作流模型。 将其设为模型的第一步。

   分配任务组件将工作流创建的任务分配给用户或组。 除了分配任务之外，您还可以使用组件为任务指定自适应表单或非交互式PDF。 自适应表单需要接受用户输入且非交互式PDF，或只读自适应表单仅用于审阅工作流。

   您还可以使用步骤来控制任务的行为。 例如，创建自动记录文档，将任务分配给特定用户或组、提交数据的路径、要预填充的数据路径以及默认操作。 有关分配任务步骤选项的详细信息，请参阅 [基于OSGi的以Forms为中心的工作流 — 步骤参考](/help/forms/using/aem-forms-workflow.md) 文档。

   ![工作流编辑器](assets/workflow-editor.png)

   对于抵押申请示例，请将分配任务步骤配置为在任务完成后使用只读自适应表单并显示PDF文档。 此外，选择允许批准贷款请求的用户组。 在 **[!UICONTROL 操作]** 选项卡，禁用 **[!UICONTROL 提交]** 选项。 指定 **[!UICONTROL 路由变量]**. 例如，actionTaked。 此外，添加批准和拒绝路由。 路由在AEM收件箱中显示为单独的操作（按钮）。 工作流会根据用户点按的操作（按钮）选择分支。

   您可以导入示例包（可从部分的开头下载），以获取为例如抵押申请配置的分配任务步骤的所有字段的完整值集。

1. 将OR拆分组件从步骤浏览器拖放到工作流模型。 “或拆分”(OR Split)在工作流中创建一个拆分，在该拆分之后，只有一个分支处于活动状态。 通过此步骤，您可以在工作流中引入条件处理路径。 您可以根据需要向每个分支添加工作流步骤。

   打开OR Split的属性，并将以下代码片段添加到Branch1和Branch2。 这些代码片段有助于根据AEM收件箱中的用户操作选择分支。

   **分支1的代码片段**

   用户点按 **[!UICONTROL 批准]** 在AEM收件箱中，将激活分支1。

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **分支2的代码片段**

   用户点按 **[!UICONTROL 拒绝]** 在AEM收件箱中，将激活分支2。

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. 添加其他工作流步骤以构建业务逻辑。

   对于抵押贷款示例，将生成的记录文档、两个分配任务步骤和一个签名文档步骤添加到模型的分支1，如下图所示。 一个分配任务步骤是显示和发送 **向申请人签署贷款文件** 另一个分配任务组件 **显示已签名文档**. 此外，将分配任务组件添加到分支2。 当用户点按AEM收件箱中的拒绝时，会激活该选项。

   对于为抵押申请配置的分配任务步骤、记录步骤文档和签名文档步骤的所有字段的完整值集，请导入示例包，该示例包可在本节的开头下载。

   工作流模型已准备就绪。 您可以通过各种方法启动工作流。 有关详细信息，请参阅 [在OSGi上启动以Forms为中心的工作流](#launch).

   ![workflow-editor-mortgage](assets/workflow-editor-mortgage.png)

## 创建以Forms为中心的工作流应用程序 {#create-a-forms-centric-workflow-application}

应用程序是与工作流关联的自适应表单。 当应用程序通过收件箱提交时，会启动关联的工作流。 要在AEM收件箱和AEM Forms应用程序中将Forms工作流作为应用程序提供，请执行以下操作以创建工作流应用程序：

>[!NOTE]
>
>您必须是fd-administrator组的成员才能创建和管理工作流应用程序。

1. 在您的AEM创作实例中，转到 ![工具](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL 管理工作流应用程序]** 和点按 **[!UICONTROL 创建]**.
1. 在创建工作流应用程序窗口中，为以下字段提供输入，然后点按 **[!UICONTROL 创建]**. 随即会创建新应用程序，该应用程序将列在“工作流应用程序”屏幕中。

<table> 
 <tbody> 
  <tr> 
   <td>字段</td> 
   <td>描述</td> 
  </tr> 
  <tr> 
   <td>标题</td> 
   <td>标题在AEM收件箱中可见，可帮助用户选择应用程序。 保持描述性。 例如，“储蓄帐户开立”应用程序。<br /> </td> 
  </tr> 
  <tr> 
   <td>名称 </td> 
   <td>指定应用程序的名称。 除字母、数字、连字符和下划线之外的所有其他字符都将替换为连字符。 </td> 
  </tr> 
  <tr> 
   <td>描述</td> 
   <td>描述显示在AEM收件箱中。 在描述字段中提供有关应用程序的详细信息。 例如，应用程序的用途。<br /> </td> 
  </tr> 
  <tr> 
   <td>自适应表单</td> 
   <td><p>指定自适应表单的路径。 当用户启动应用程序时，将显示指定的自适应表单。</p> <p><strong>注意</strong>:工作流应用程序不支持超过一页或需要在Apple iPad上滚动的表单和PDF文档。 当在Apple iPad上打开应用程序，并且自适应表单或PDF文档的长度超过某个页面时，来自第二页的表单字段和内容将丢失。</p> </td> 
  </tr> 
  <tr> 
   <td>访问组</td> 
   <td><p>选择群组。 该应用程序仅对选定组的成员显示在AEM收件箱中。 访问组选项可使工作流用户组的所有组可供选择。 </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>预填服务</td> 
   <td>选择 <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">预填充服务</a> ，用于自适应表单。<br /> </td> 
  </tr> 
  <tr> 
   <td>工作流模型</td> 
   <td>选择 <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">工作流模型</a> 中。 工作流模型由业务流程的逻辑和流程组成。 </td> 
  </tr> 
  <tr> 
   <td>数据文件路径</td> 
   <td>在crx-repository中指定数据文件的路径。 该路径与自适应表单有效负载相关，且包含数据文件的名称。 始终包含文件的完整名称（包括扩展名）（如果适用）。 例如，[有效负载]/data.xml。 </td> 
  </tr> 
  <tr> 
   <td>附件路径</td> 
   <td>在crx-repository中指定附件文件夹的路径。 附件路径相对于有效负载位置。 例如，[有效负载]/data.xml。 </td> 
  </tr> 
  <tr> 
   <td>记录文档路径</td> 
   <td>在crx-repository中指定记录文档文件的路径。 路径与自适应表单有效负载位置相关。 始终包含文件的完整名称（包括扩展名）（如果适用）。 例如，[有效负载]/DOR/creditcard.pdf。</td> 
  </tr> 
 </tbody> 
</table>

## 在OSGi上启动以Forms为中心的工作流 {#launch}

您可以通过以下方式启动或触发以Forms为中心的工作流：

* [从AEM收件箱提交应用程序](#inbox)
* [从AEM Forms应用程序提交应用程序](#afa)

* [提交自适应表单](#af)
* [使用监视文件夹](#watched)

* [提交交互式通信或信件](#letter)

### 从AEM收件箱提交应用程序 {#inbox}

您创建的工作流应用程序可作为收件箱中的应用程序使用。 属于工作流用户组的成员用户可以填写并提交触发关联工作流的应用程序。 有关使用AEM收件箱提交应用程序和管理任务的信息，请参阅 [在AEM收件箱中管理Forms应用程序和任务](/help/forms/using/manage-applications-inbox.md).

### 从AEM Forms应用程序提交应用程序 {#afa}

AEM Forms应用程序与AEM Forms服务器同步，允许您更改帐户中的表单数据、任务、工作流应用程序和保存的信息（草稿/模板）。 有关更多信息，请参阅 [AEM Forms应用程序](/help/forms/using/aem-forms-app.md) 和相关文章。

### 提交自适应表单 {#af}

您可以配置自适应表单的提交操作，以在提交自适应表单时启动工作流。 自适应表单提供 **[!UICONTROL 调用AEM工作流]** 提交操作以在提交自适应表单时启动工作流。 有关提交操作的详细信息，请参阅 [配置提交操作](/help/forms/using/configuring-submit-actions.md). 要通过AEM Forms应用程序提交自适应表单，请在自适应表单属性中启用与AEM Forms应用程序同步。

您可以配置自适应表单，以从AEM Forms应用程序同步、提交和触发工作流。 有关详细信息，请参阅 [使用表单](/help/forms/using/working-with-form.md).

### 使用监视文件夹 {#watched}

管理员（fd-administrators组的成员）可以将网络文件夹配置为在用户将文件(如PDF文件)放置到文件夹中时运行预配置的工作流。 工作流完成后，它可以将结果文件保存到指定的输出文件夹。 此类文件夹称为 [监视文件夹](/help/forms/using/watched-folder-in-aem-forms.md). 执行以下过程以配置已监视文件夹以启动工作流：

1. 在您的AEM创作实例中，转到 ![工具](assets/tools.png) **[!UICONTROL Forms >配置监视文件夹]**. 将显示已配置的监视文件夹列表。
1. 点按 **[!UICONTROL 新建]**. 将显示字段列表。 为以下字段指定值，以便为工作流配置监视文件夹：

<table> 
 <tbody> 
  <tr> 
   <td>字段</td> 
   <td>描述</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">名称</span></td> 
   <td>指定监视文件夹的名称。 此字段仅支持字母数字。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">路径</span></td> 
   <td>指定监视文件夹的物理位置。 在群集环境中，使用可从AEM群集节点访问的共享网络文件夹。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">文件处理方法</span></td> 
   <td>选择 <span class="uicontrol">工作流 </span>选项。 </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">工作流模型</span></td> 
   <td>选择工作流模型。<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">输出文件模式</span></td> 
   <td>指定输出文件和目录的目录结构。 您还可以指定 <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">输出文件和目录的模式</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. 点按 **[!UICONTROL 高级]**. 为以下字段指定值并点按 **[!UICONTROL 创建]**. 已将“监视文件夹”配置为启动工作流。 现在，每当将文件置于监视文件夹的输入目录中时，都会触发指定的工作流。

   | 字段 | 描述 |
   |---|---|
   | 有效负荷映射器过滤器 | 创建监视文件夹时，它会在crx-repository中创建文件夹结构。 文件夹结构可用作工作流的有效负荷。 您可以编写脚本以映射AEM工作流以接受来自监视文件夹结构的输入。 开箱即用的实施可用，并在有效负载映射器筛选器中列出。 如果您没有自定义实施，请选择默认实施。 |

   高级选项卡包含更多字段。 这些字段中的大多数都包含默认值。 要了解所有字段，请参阅 [创建或配置监视文件夹](/help/forms/using/creating-configure-watched-folder.md) 文章。

### 提交交互式通信或信件 {#letter}

在提交交互式通信或信件时，您可以在OSGi上关联和执行以Forms为中心的工作流。 在通信管理工作流中用于后处理交互式通信和信件。 例如，发送电子邮件、打印、传真或存档最终信件。 有关详细步骤，请参阅 [交互式通信和信件的后处理](/help/forms/using/submit-letter-topostprocess.md).

## 其他配置 {#additional-configurations}

### 配置电子邮件服务 {#configure-email-service}

您可以使用AEM工作流的“分配任务”和“发送电子邮件”步骤来发送电子邮件。 执行以下步骤以指定电子邮件服务器和发送电子邮件所需的其他配置：

1. 转到AEM配置管理器(位于 `https://[server]:[port]/system/console/configMgr`.
1. 打开 **[!UICONTROL Day CQ Mail Service]** 配置。 为 **[!UICONTROL SMTP服务器主机名]**, **[!UICONTROL SMTP服务器端口、]** 和 **[!UICONTROL “发件人”地址]** 字段。 单击“**[!UICONTROL 保存]**”。
1. 打开 **[!UICONTROL Day CQ链接外部器]** 配置。 在 **[!UICONTROL 域]** 字段，为本地、创作和发布实例指定实际的主机名/IP地址和端口号。 单击“**[!UICONTROL 保存]**”。

### 清除工作流实例 {#purge-workflow-instances}

最大限度地减少工作流实例的数量可以提高工作流引擎的性能，因此，您可以定期从存储库中清除已完成或正在运行的工作流实例。有关详细信息，请参阅 [定期清除工作流实例](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
