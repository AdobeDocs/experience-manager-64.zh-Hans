---
title: 基于OSGi的以Forms为中心的工作流 — 步骤参考
seo-title: Forms-centric workflow on OSGi - Step Reference
description: 基于OSGi步骤的以Forms为中心的工作流允许您快速构建基于自适应表单的工作流。
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4673'
ht-degree: 0%

---

# 基于OSGi的以Forms为中心的工作流 — 步骤参考 {#forms-centric-workflow-on-osgi-step-reference}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## Forms Workflow步骤 {#forms-workflow-steps}

Forms工作流步骤在AEM工作流中执行特定于AEM Forms的操作。 这些步骤允许您在OSGi上快速构建基于以Forms为中心的自适应表单工作流。 这些工作流可用于开发基本的审核和批准工作流、内部和跨防火墙的业务流程。 您还可以使用Forms Workflow步骤来启动文档服务、与Acrobat Sign签名工作流集成，以及执行其他AEM Forms操作。 您需要 [AEM Forms附加组件](https://www.adobe.com/go/learn_aemforms_documentation_63) 以在工作流中使用这些步骤。

## 分配任务步骤 {#assign-task-step}

分配任务步骤将创建一个任务并将其分配给用户或组。 除了分配任务外，组件还为任务指定自适应表单或非交互式PDF。 自适应表单需要接受用户输入且非交互式PDF，或只读自适应表单仅用于审阅工作流。

您还可以使用组件来控制任务的行为。 例如，创建自动记录文档、将任务分配给特定用户或组、指定提交数据的路径、指定要预填充的数据路径以及指定默认操作。 “分配任务”步骤具有以下属性：

* **标题：** 任务的标题。 标题会显示在AEM收件箱中。
* **描述：** 任务中正在执行的操作说明。 当您在共享开发环境中工作时，此信息对于其他流程开发人员非常有用。

* **缩略图路径：** 任务缩略图的路径。 如果未指定路径，则会显示自适应表单默认缩略图，并且对于“记录文档”，会显示默认图标。
* **工作流阶段：** 一个工作流可以具有多个阶段。 这些阶段会显示在AEM收件箱中。 您可以在模型的属性（Sidekick >页面>页面属性>阶段）中定义这些阶段。
* **优先级：** 选定的优先级将显示在AEM收件箱中。 可用选项包括“高”、“中”和“低”。 默认值为“中”。
* **到期日期：** 指定任务标记为逾期的天数或小时数。 如果您选择 **关闭**，则任务永远不会被标记为过期。 您还可以指定超时处理程序，以在任务过期后执行特定任务。

* **天数：** 任务完成前的天数。 在将任务分配给用户后，将计为天数。 如果任务未完成，并且跨越“天”字段中指定的天数，则如果选中，将在到期日期后触发超时处理程序。
* **小时数：** 任务完成前的小时数。 在将任务分配给用户后，将计为小时数。 如果任务未完成，并跨越“小时”字段中指定的小时数，则如果选中，则会在到期小时后触发超时处理程序。
* **到期日期后超时：** 选择此选项可启用超时处理程序选择字段。
* **超时处理程序：** 选择要在分配任务步骤跨越到期日期时执行的脚本。 放置在CRX存储库(位于 [应用程序]/fd/dashboard/scripts/timeoutHandler可供选择。 crx-repository中不存在指定的路径。 管理员在使用路径之前会创建该路径。
* **在任务详细信息中突出显示最后一个任务中的操作和注释：** 选择此选项可显示上次执行的操作以及收到的对任务详细信息部分的评论。
* **类型：** 选择启动工作流时要填写的文档类型。 您可以选择自适应表单、只读自适应表单或非交互式PDF文档。
* **使用自适应表单：** 指定定位输入自适应表单的方法。 您可以使用绝对路径上提供的自适应表单作为有效负荷提交到工作流，或在使用变量计算的路径上提供。 您可以使用字符串类型的变量指定路径。
* **自适应表单路径**:指定自适应表单的路径。 当您在“类型”字段中使用自适应表单或只读自适应表单选项，同时使用“使用自适应表单”字段中的绝对路径选项时，该字段将可用。
* **PDF路径：** 指定非交互式PDF文档的路径。 在“类型”字段中选择非交互式PDF文档时，该字段将可用。 路径始终相对于有效负载。 例如， [Payload_Directory]/Workflow/PDF/credit-card.pdf。 crx-repository中不存在路径。 管理员在使用路径之前会创建该路径。 您需要启用“记录文档”选项或基于表单模板的自适应表单才能使用“PDF路径”选项。
* **对于已完成的任务，将自适应表单渲染为**:当任务标记完成时，您可以将自适应表单呈现为只读自适应表单或PDF文档。 您需要启用“记录文档”选项或基于表单模板的自适应表单，以将自适应表单渲染为“记录文档”。
* **要预填充的信息：** 下面列出的字段用作任务的输入：

   * **数据文件路径：** 输入数据文件(.json或.xml)的路径。 路径始终相对于有效负载。 例如，文件包含通过AEM收件箱应用程序为表单提交的数据。 示例路径为 [Payload_Directory]/workflow/data.
   * **附件路径：** 该位置可用的附件会附加到与任务关联的表单。 路径始终相对于有效负载。 示例路径为 [Payload_Directory]/attachments/

* **提交的信息：** 下面列出的字段用作任务的输出位置：

   * **数据文件路径：** 数据文件的路径(.json或.xml)。 数据文件包含通过关联表单提交的信息。 路径始终相对于有效负载。 例如， [Payload_Directory]/Workflow/data，其中数据是文件。
   * **附件路径：** 保存任务中提供的表单附件的路径。
   * **记录路径文档：** 保存记录文档的路径。 例如， [Payload_Directory]/DocumentofRecord/credit-card.pdf。 如果路径字段留空，则不会生成记录文档。 路径始终相对于有效负载。

* **分配选项：** 指定将任务分配给用户的方法。 您可以使用“参与者选择器”脚本将任务动态分配给用户或组，或将任务分配给特定的AEM用户或组。
* **参与者选择器：** 当 **动态发送给用户或组** 选项。 您可以使用ECMAScript或服务动态选择用户或组。 有关更多信息，请参阅 [动态地为用户分配工作流](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) 和 [创建自定义Adobe Experience Manager动态参与者步骤。](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **参与者：** 当 **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** 选项。 利用字段，可为RandomParticipantChooser选项选择用户或组。

* **参数：** 当在“参与者选择器”字段中选择RandomParticiantChoose脚本以外的脚本时，该字段将可用。 利用字段，可为在“参与者选择器”字段中选择的脚本提供以逗号分隔的参数列表。

* **用户或组：** 该任务被分配给选定的用户或组。 当 **到特定用户或群组选项** 的“指定选项”字段中，此列将被选中。 该字段列出了工作流用户组的所有用户和组。

* **通过电子邮件通知被分派人：** 选择此选项可向被分派人发送电子邮件通知。 将任务分配给用户后，将发送这些通知。 在使用选项之前，请从AEM Web Console中启用通知。 有关分步说明，请参阅 [为分配任务步骤配置电子邮件通知](/help/forms/using/aem-forms-workflow.md)

* **HTML电子邮件模板**:为通知电子邮件选择电子邮件模板。 要编辑模板，请修改crx-repository中位于/libs/fd/dashboard/templates/email/htmlEmailTemplate.txt的文件。
* **允许委派到：** AEM收件箱为已登录的用户提供了一个选项，用于将分配的工作流委派给其他用户。 允许您在同一组内委派给另一个组的工作流用户。 如果任务被分配给单个用户，并且 **允许委派给受让人组成员** 选项，则无法将任务委派给其他用户或组。

* **默认操作：** 现成可用的提交、保存和重置操作。 默认情况下，所有默认操作都处于启用状态。
* **路由变量：** 路由变量的名称。 route变量可捕获用户在AEM收件箱中选择的自定义操作。
* **路由：** 任务可以分支到不同的路由。 在AEM收件箱中选择该路由后，该路由将返回一个值，并根据选定的路由返回工作流分支。
* **标题**:指定路由的标题。 它显示在AEM收件箱中。
* **Coral图标**:指定珊瑚图标的HTML属性。 AdobeCorelUI库提供了大量的触屏优先图标。 您可以选择并使用路由的图标。 它与标题一起显示在AEM收件箱中。
* **允许被分派人添加评论**:选择此选项可为任务启用注释。 任务提交时，被分派人可以从AEM收件箱中添加评论。
* **允许被分派人向任务添加附件**:选择此选项可为任务启用附件。 任务提交时，被分派人可以从AEM收件箱中添加附件。
* **任务附件的输出路径**:指定附件文件夹的位置。 位置与有效负载相关。
* **使用自定义元数据：** 选择此选项可启用自定义元数据字段。 自定义元数据在电子邮件模板中使用。
* **自定义元数据：** 为电子邮件模板选择自定义元数据。 自定义元数据可在crx-repository中的apps/fd/dashboard/scripts/metadataScripts访问。 crx-repository中不存在指定的路径。 管理员在使用路径之前会创建该路径。 您还可以将服务用于自定义元数据。 您还可以扩展 `WorkitemUserMetadataService` 用于提供自定义元数据的界面。

* **显示前一步骤的数据**:选择此选项可使受分配人能够查看以前的受分配人、已对任务执行的操作、添加到任务的注释以及已完成任务的记录文档（如果可用）。
* **显示后续步骤的数据：** 选择此选项可使当前代理人能够查看由后续代理人执行的操作和添加到任务的注释。 它还允许当前受让人查看已完成任务的记录文档（如果可用）。
* **数据类型的可见性：** 默认情况下，代理人可以查看记录文档、受让人、已采取的操作以及先前和后续受让人已添加的注释。 使用数据类型的可见性选项限制受让人可见的数据类型。

## 发送电子邮件步骤 {#send-email-step}

使用电子邮件步骤发送电子邮件，例如，包含记录文档、自适应表单链接、交互式通信链接或附加PDF文档的电子邮件。 “发送电子邮件”步骤支持 [HTML电子邮件](https://en.wikipedia.org/wiki/HTML_email). HTML电子邮件是响应式的，可根据收件人的电子邮件客户端和屏幕大小进行调整。 您可以使用HTML电子邮件模板来定义电子邮件的外观、颜色方案和行为。

电子邮件步骤使用Day CQ Mail Service发送电子邮件。 在使用电子邮件步骤之前，请确保 [电子邮件服务](/help/forms/using/aem-forms-workflow.md) 已配置。 电子邮件步骤具有以下属性：

**标题：** 步骤的标题有助于在工作流编辑器中识别步骤。

**描述：** 当您在共享开发环境中工作时，此说明对于其他流程开发人员非常有用。

**电子邮件主题：** 主题可以从工作流元数据中检索或手动指定。 选择 **文字** 用于手动指定主题或选择 **从工作流元数据中检索** 用于从元数据属性中检索主题的选项。

**HTML电子邮件模板**:HTML电子邮件模板。 您可以在电子邮件模板中指定变量。 电子邮件步骤会提取并显示模板中包含的所有变量以用于输入。

**电子邮件模板元数据：** 电子邮件模板变量的值可以是用户指定的值、作者或发布服务器上资产的路径、图像或工作流元数据属性。

* **文字：** 当您知道要指定的确切值时，请使用选项。 例如， [example@example.com](mailto:example@example.com).

* **工作流元数据：** 将要使用的值保存在工作流元数据属性中时，请使用选项。 选择选项后，在工作流元数据选项下方的空文本框中输入元数据属性名称。 例如， emailAddress。
* **资产URL:** 使用选项可将交互式通信的Web链接嵌入到电子邮件。 选择选项后，浏览并选择要嵌入的交互式通信。 资产可以驻留在作者或发布服务器上。
* **图像：** 使用选项将图像嵌入到电子邮件中。 选择选项后，浏览并选择图像。 图像选项仅适用于电子邮件模板中可用的图像标记(&lt;img src=&quot;&amp;ast;&quot; />)。

**发件人/收件人的电子邮件地址：** 选择 **文字** 用于手动指定电子邮件地址或选择 **从工作流元数据中检索** 用于从元数据属性中检索电子邮件地址的选项。 您还可以为 **从工作流元数据中检索** 选项。

**文件附件路径：** 指定位置的可用资产会附加到电子邮件中。 资产的路径可以是相对于有效负载的路径，也可以是绝对路径。 示例路径为 [Payload_Directory]/attachments/

**文件名：** 电子邮件附件文件的名称。 电子邮件步骤将附件的原始文件名更改为指定的文件名。 可以手动指定名称或从工作流元数据属性中进行检索。 使用 **文字** 选项。 使用 **从工作流元数据中检索** 选项。

## 生成记录文档步骤 {#generate-document-of-record-step}

填写或提交表单后，您可以以打印或文档格式保留表单的记录。 这称为记录文档(DoR)。 您可以使用生成记录文档步骤创建自适应表单的只读或交互式PDF版本。 PDF版本包含填写到表单中的信息以及自适应表单的布局。

“记录文档”步骤具有以下属性：

**使用自适应表单**:指定定位输入自适应表单的方法。 您可以使用绝对路径上提供的自适应表单作为有效负荷提交到工作流，或在使用变量计算的路径上提供。 您可以使用字符串类型的变量指定路径。

**自适应表单路径**:指定自适应表单的路径。 当您在“类型”字段中使用自适应表单或只读自适应表单选项，同时使用“使用自适应表单”字段中的绝对路径选项时，该字段将可用。

**输入数据路径：** 自适应表单的输入数据路径。 您可以将数据保留在相对于有效负载的位置，或指定数据的绝对路径。 输入数据与自适应表单合并以创建记录文档。

**输入附件路径：** 输入附件路径：附件的路径。 这些附件包含在记录文档中。 您可以将附件保留在相对于有效负载的位置，或指定附件的绝对路径。

如果指定文件夹的路径（例如附件），则文件夹中直接可用的所有文件都将附加到记录文档。 如果任何文件在指定附件路径中直接可用的文件夹中可用，则这些文件将作为附件包含在记录文档中。 如果直接可用的文件夹中存在任何文件夹，则会跳过这些文件夹。

**生成的记录路径文档：** 指定保留记录文件文档的位置。 您可以选择覆盖有效负载文件夹，或将记录文档放置在有效负载目录中的某个位置。

**区域设置**:指定记录文档的语言。

## 调用表单数据模型服务步骤 {#invoke-form-data-model-service-step}

您可以使用 [AEM Forms数据集成](/help/forms/using/data-integration.md) 配置和连接到不同的数据源。 这些数据源可以是数据库、Web服务、REST服务、OData服务和CRM解决方案。 AEM Forms数据集成允许您创建包含各种服务的表单数据模型，以对配置的数据库执行数据检索、添加和更新操作。 您可以使用 **调用数据模型服务步骤** 要选择表单数据模型(FDM)，并使用FDM的服务来检索、更新或将数据添加到不同的数据源，请执行以下操作：

为了说明步骤字段的输入，以下数据库表和JSON文件作为示例：

**CustomerDetails表示例**

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>价值<br /> </td> 
  </tr> 
  <tr> 
   <td>名字<br /> </td> 
   <td>莎拉<br /> </td> 
  </tr> 
  <tr> 
   <td>姓氏</td> 
   <td>罗斯</td> 
  </tr> 
  <tr> 
   <td>客户ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>电子邮件地址<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**JSON文件示例**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

“调用表单数据模型服务”步骤包含以下列出的字段，以便于表单数据模型操作：

* **标题：** 步骤的标题。 它有助于在工作流编辑器中确定步骤。
* **描述：** 当您在共享开发环境中工作时，此说明对其他流程开发人员非常有用。

* **表单数据模型路径**:浏览并选择服务器上存在的表单数据模型。

* **服务**:所选表单数据模型提供的服务列表。
* **服务的输入>使用文字、工作流元数据和JSON文件提供输入数据**:一个服务可以有多个参数。 选择选项，以从工作流元数据属性（JSON对象）中获取服务参数的值，或直接在提供的文本框中输入值：

   * **文字：** 当您知道要指定的确切值时，请使用选项。 例如， srose@we.info。
   * **从工作流元数据中检索：** 将要使用的值保存在工作流元数据属性中时，请使用选项。 例如， emailAddress。
   * **JSON点表示法：** 当要使用的值位于JSON文件中时，请使用选项。 例如， insurance.customerDetails.emailAddress.只有在选择“映射输入JSON中的输入字段”选项时，“JSON点表示法”选项才可用。
   * **映射输入JSON中的输入字段：** 指定JSON文件的路径，以从JSON文件获取某些服务参数的输入值。 JSON文件的路径可以是相对于有效负载的路径，也可以是绝对路径。

* **服务输入>使用JSON文件提供输入数据：** 选择选项，以从JSON文件获取所有参数的值。
* **输入JSON文件路径**:包含所有服务参数值的JSON文件的路径。 JSON文件的路径可以是 **相对于有效载荷** 或 **绝对路径**.

* **JSON点表示法：** 将字段留空，以使用指定JSON文件的所有对象作为服务参数的输入。 要从指定的JSON文件中读取特定JSON对象作为服务参数的输入，请为JSON对象指定点表示法，例如，如果您的JSON与部分开头列出的JSON类似，请指定insurance.customerDetails，以提供作为服务输入的客户的所有详细信息。
* **服务输出>将输出值映射并写入元数据：** 选择选项，将输出值另存为crx-repository中工作流实例元数据节点的属性。 指定元数据属性的名称并选择要映射为元数据属性的相应服务输出属性，例如，将输出服务返回的phone_number映射为工作流元数据的phone_number属性。
* **服务输出>将输出另存为JSON:** 选择选项以将输出值保存在JSON文件中。
* **输出JSON文件路径：** 保存输出JSON文件的路径。 输出JSON文件的路径可以是相对于有效负载的路径，也可以是绝对路径。

## “签名文档”步骤 {#sign-document-step}

通过“签名文档”步骤，您可以使用Acrobat Sign来签署文档。 “签名文档”步骤具有以下属性：

* **协议名称：** 指定协议的标题。 协议名称将成为发送给签名者的电子邮件的主题和正文文本的一部分。
* **区域设置：** 指定电子邮件和验证选项的语言。
* **Acrobat Sign云配置**:选择Acrobat Sign云配置。 如果尚未为AEM Forms配置Acrobat Sign，请参阅 [将Acrobat Sign与AEM Forms集成](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **待签名文档：** 您可以从相对于有效负荷的位置选择文档，使用有效负荷作为文档，或指定文档的绝对路径。
* **输入附件路径：** 选择附件。 这些附件包含在签名文档中。 您可以将附件保留在相对于有效负载的位置，或指定附件的绝对路径。

   如果指定文件夹的路径（例如附件），则文件夹中直接可用的所有文件都将附加到记录文档。 如果任何文件位于指定附件路径中直接可用的文件夹中，则这些文件将作为附件包含在“签名文档”中。 如果直接可用的文件夹中存在任何文件夹，则会跳过这些文件夹。
* **截止日期前的天数：** 在中指定的天数内，任务上没有活动，则文档会标记为到期（已过期） **截止时间前的天数** 字段。 在将记录的分配给用户进行签名后，将计为天数。

* **提醒电子邮件频度：** 您可以以每日或每周间隔发送提醒电子邮件。 该周将从记录的被分配给用户进行签名的当天开始计数。
* **签名过程：** 您可以选择按顺序或并行顺序对文档进行签名。 按顺序，一个签名者每次接收文档以进行签名。 在第一个签名者完成对文档的签名后，将该文档发送给第二个签名者，依此类推。 同时，多个签名者可以一次对文档进行签名。

* **重定向URL:** 指定重定向URL。 在文档签名后，您可以将代理人重定向到一个URL。 通常，此URL包含感谢信或进一步说明。
* **工作流阶段：** 一个工作流可以具有多个阶段。 这些阶段会显示在AEM收件箱中。 您可以在模型的属性（Sidekick >页面>页面属性>阶段）中定义这些阶段。
* **选择签名者：** 指定为文档选择签名者的方法。 您可以动态地将工作流分配给用户或组，或手动添加签名者的详细信息。
* **用于选择签名者的脚本或服务：** 仅当在选择签名者字段中选择了动态选项时，该选项才可用。 您可以指定ECMAScript或服务来为文档选择签名者和验证选项。

* **签名者详细信息：** 仅当在选择签名者字段中选择了手动选项时，该选项才可用。 指定电子邮件地址并选择可选的验证机制。 在选择两步验证机制之前，请确保为已配置的Acrobat Sign帐户启用相应的验证选项。
* **状态变量：** 启用Acrobat Sign的文档将文档的签名状态存储在变量中。 指定状态变量的名称(adobeSignStatus)。 在CRXDE中，可以在/etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData包含变量的状态。
* **签名文档路径：** 指定保留已签名文档的位置。 您可以选择覆盖有效负载文件，或将已签名文档放置在有效负载目录中的某个位置。

## 文档服务步骤 {#document-services-steps}

AEM文档服务是一组用于创建、组合和保护PDF文档的服务。 AEM Forms为每个文档服务提供了单独的AEM工作流步骤：

### 应用文档时间戳步骤 {#apply-document-time-stamp-step}

向文档添加时间戳。 提供文档详细信息，如输入文档路径、输入文档名称、用于存储导出数据的位置。 您可以选择覆盖现有的有效负载文件，或选择其他文件名以将数据存储在有效负载文件夹下的其他文件中。

### 转换为图像步骤 {#convert-to-image-step}

将PDF文档转换为图像文件。 支持的图像格式包括JPEG、JPEG2000、PNG和TIFF。 以下信息适用于TIFF图像的转化：

* 将生成多页TIFF文件。
* 某些注释未包含在TIFF图像中。 不包含要求Acrobat生成其外观的注释。

### 转换为PDF/步骤 {#convert-to-pdf-a-step}

使用提供的选项将PDF文档转换为PDF/A格式。 PDF/A版本的可移植文档格式(PDF)专门用于文档的归档和长期保存。

### 转换为PS步骤 {#convert-to-ps-step}

将PDF文档转换为PostScript。 转换为PostScript时，可以使用转换操作指定源文档以及是转换为PostScript 2级还是3级。 您转换为PostScript文件的PDF文档必须是非交互式的。

### 从指定的类型步骤创建PDF {#create-pdf-from-specified-type-step}

从输入文件生成PDF文档。 输入文档可以是相对于有效负载的，具有绝对路径，或者可以是有效负载本身。

### 通过URL/PDF/邮政编码步骤创建HTML {#create-pdf-from-url-html-zip-step}

根据提供的URL、PDF和ZIP文件生成HTML文档。

### 导出数据步骤 {#export-data-step}

从PDF forms或XDP文件导出数据。 它要求您输入“输入文档”和“导出数据格式”的文件路径。 “导出数据格式”的选项包括“自动”、“XDP”和“XmlData”。

### Export PDF到指定类型步骤 {#export-pdf-to-specified-type-step}

将PDF文档转换为所选格式。

### 生成非交互式PDF步骤 {#generate-non-interactive-pdf-step}

生成非交互式PDF。 它提供了各种自定义选项。

### 导入数据步骤 {#import-data-step}

将表单数据合并到PDF表单。 您可以将表单数据导入PDF表单。

### 调用DDX步骤 {#invoke-ddx-step}

在指定的输入文档映射上执行DDX文件并返回操作的PDF文档。

### Optimize PDF步骤 {#optimize-pdf-step}

通过减小PDF文件的大小来优化文件。 此转换的结果是PDF文件可能小于其原始版本。 此操作还会将PDF文档转换为优化参数中指定的PDF版本。

优化设置指定如何优化文件。 以下是设置示例：

* TargetPDF版本
* 放弃对象（如JavaScript操作和嵌入的页面缩略图）
* 放弃用户数据（如注释和文件附件）
* 放弃无效或未使用的设置
* 压缩未压缩数据或使用更高效的压缩算法
* 删除嵌入字体
* 设置透明度值

### 渲染PDF表单步骤 {#render-pdf-form-step}

将在表单设计器(XDP)中创建的表单渲染到PDF表单。

### 安全文档步骤 {#secure-document-step}

加密、签名和验证文档。 AEM Forms支持基于密码的加密和基于证书的加密。 您还可以在各种文档签名算法之间进行选择。 例如， SHA-256和SH-512。 您还可以使用工作流步骤来读取器扩展PDF文档。 工作流步骤提供了用于启用条形码解码、数字签名、导入和导出PDF数据的选项，以及其他选项。

### 发送到打印机步骤 {#send-to-printer-step}

将文档直接发送到打印机。 它支持以下打印访问机制：

* **可直接访问的打印机**:安装在同一台计算机上的打印机称为直接可访问的打印机，该计算机名为打印机主机。 此类打印机可以是直接连接到计算机的本地打印机。
* **间接可访问的打印机**:安装在打印服务器上的打印机可从其他计算机访问。 通用的UNIX®打印系统(CUPS)和线式打印机守护程序(LPD)协议等技术可用于连接到网络打印机。 要访问间接可访问的打印机，请指定打印服务器的IP或主机名。 使用此机制，当网络运行LPD时，您可以将文档发送到LPD URI。 该机制允许您将文档路由到任何连接到运行LPD的网络的打印机。
