---
title: 配置提交操作
seo-title: 配置提交操作
description: AEM Forms允许您配置提交操作，以定义提交后如何处理自适应表单。 您可以使用内置提交操作，也可以从头开始编写自己的提交操作。
seo-description: AEM Forms允许您配置提交操作，以定义提交后如何处理自适应表单。 您可以使用内置提交操作，也可以从头开始编写自己的提交操作。
uuid: aa261e65-a1ec-402b-80de-0ba8a294e315
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: fea76f90-22d5-4836-9901-a35229401eb0
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 1%

---


# 配置提交操作{#configuring-the-submit-action}

## 提交操作简介{#introduction-to-submit-actions}

当用户单击自适应表单上的“提交”按钮时，将触发提交操作。 您可以在自适应表单上配置提交操作。 自适应表单提供了一些现成的提交操作。 您可以复制和扩展默认的提交操作，以创建您自己的提交操作。 但是，根据您的要求，您可以编写并注册您自己的提交操作以处理已提交表单中的数据。

预填或提交表单时，提交的数据将通过AEM传送，以按摩到中间格式。 除非自适应表单使用Adobe Sign、验证、表单门户草稿或提交或AEM工作流，否则数据不会保存在AEM实例中

您可以在提要栏中自适应表单容器属性的&#x200B;**[!UICONTROL 提交]**&#x200B;部分配置提交操作。

![配置提交](assets/thank-you-setting.png)
**操作图：** *配置提交操作*

自适应表单的默认提交操作包括：

* 提交到REST端点
* 发送电子邮件
* 通过电子邮件发送PDF
* 调用Forms Workflow
* 使用表单数据模型提交
* Forms Portal提交操作
* 调用AEM工作流

>[!NOTE]
>
>“通过电子邮件发送PDF”提交操作仅适用于使用XFA模板作为表单模型的自适应表单。

>[!NOTE]
>
>确保[AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder exists。 临时存储附件时需要该目录。 如果目录不存在，请创建它。

>[!CAUTION]
>
>如果[预填](/help/forms/using/prepopulate-adaptive-form-fields.md)表单模板、表单数据模型或基于模式的自适应表单（XML或JSON数据）向模式(XML模式、JSON模式、表单模板或表单数据模型)投诉，该数据不包含&lt;afData>、&lt;afBoundData>和&lt;/AfUnboundData>标签，然后，自适应表单的无界字段（无界字段是没有[bindref](/help/forms/using/prepopulate-adaptive-form-fields.md)属性的自适应表单字段）的数据丢失。

您可以为自适应表单编写自定义提交操作，以满足您的使用案例。 有关详细信息，请参阅[编写自适应表单的自定义提交操作](/help/forms/using/custom-submit-action-form.md)。

## 提交到REST端点{#submit-to-rest-endpoint}

**[!UICONTROL 提交到REST端点]**&#x200B;提交选项将表单中填写的数据传递到配置的确认页，作为HTTPGET请求的一部分。 您可以添加要请求的字段的名称。 请求的格式为：

`{fieldName}={request parameter name}`

如下图所示，`param1`和`param2`作为参数传递，这些参数的值从&#x200B;**[!UICONTROL textbox]**&#x200B;和&#x200B;**[!UICONTROL numericbox]**&#x200B;字段中复制，以用于下一个操作。

您还可以&#x200B;**[!UICONTROL 启用POST请求]**&#x200B;并提供用于发布请求的URL。 要向托管表单的AEM服务器提交数据，请使用与AEM服务器的根路径对应的相对路径。 例如，/content/forms/af/SampleForm.html。 要向任何其他服务器提交数据，请使用绝对路径。

![配置Rest端点提交操作](assets/action-config.png)

配置Rest端点提交操作

>[!NOTE]
要将字段作为参数传递到REST URL，所有字段必须具有不同的元素名称，即使这些字段位于不同的面板上也是如此。

### 将提交的数据发布到资源或外部休息端点  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

使用&#x200B;**[!UICONTROL 提交到REST Endpoint]**&#x200B;动作将提交的数据发布到REST。 URL可以是内部（表单所在的服务器）或外部服务器。

要将数据发布到内部服务器，请提供资源的路径。 数据将发布在资源的路径中。 例如，/content/restEndPoint。 对于这种帖子请求，使用提交请求的验证信息。

要向外部服务器发布数据，请提供URL。 URL的格式为https:// host:port/path_to_rest_end_point。 确保配置路径以匿名处理POST请求。

![作为感谢页面参数传递的字段值的映射](assets/post-enabled-actionconfig.png)

在上面的示例中，用户在`textbox`中输入的信息是使用参数`param1`捕获的。 用于发布使用`param1`捕获的数据的语法为：

`String data=request.getParameter("param1");`

同样，用于发布XML数据和附件的参数是`dataXml`和`attachments`。

例如，您在脚本中使用这两个参数将数据解析到一个静止点。 使用以下语法存储和分析数据：

`String data=request.getParameter("dataXml");`\
`String att=request.getParameter("attachments");`

在此示例中，`data`存储XML数据，而`att`存储附件数据。

## 发送电子邮件 {#send-email}

**[!UICONTROL 发送电子邮件]**&#x200B;提交操作会在表单成功提交时向一个或多个收件人发送电子邮件。 生成的电子邮件可以包含预定义格式的表单数据。

>[!NOTE]
所有表单域必须具有不同的元素名称（即使它们位于不同的面板中），以便在电子邮件中包含表单数据。

## 通过电子邮件{#send-pdf-via-email}发送PDF

**[!UICONTROL 通过电子邮件]**&#x200B;发送PDF的提交操作在成功提交表单时向一个或多个收件人发送一封包含表单数据的PDF的电子邮件。

**注意：** *此提交操作适用于具有“记录”模板文档的基于XFA的自适应表单和基于XSD的自适应表单。*

## 调用表单工作流{#invoke-a-forms-workflow}

**[!UICONTROL 提交到Forms工作流]**&#x200B;提交选项会向JEE进程上的现有AdobeLiveCycle或AEM Forms发送数据xml和文件附件（如果有）。

有关如何配置“提交到表单”工作流提交操作的信息，请参阅[使用表单工作流](/help/forms/using/submit-form-data-livecycle-process.md)提交和处理表单数据。

## 使用表单数据模型提交 {#submit-using-form-data-model}

**[!UICONTROL 使用表单数据模型提交操作]**&#x200B;将指定数据模型对象的已提交的自适应表单数据写入其数据源。 配置提交操作时，您可以选择一个数据模型对象，其提交的数据要写回其数据源。

此外，您可以使用表单数据模型和记录文档(DoR)向数据源提交表单附件。

有关表单数据模型的信息，请参阅[AEM Forms Data Integration](/help/forms/using/data-integration.md)。

## Forms Portal提交操作{#forms-portal-submit-action}

**[!UICONTROL Forms Portal提交操作]**&#x200B;选项使表单数据可通过AEM Forms门户访问。

有关Forms门户和提交操作的详细信息，请参阅[草稿和提交组件](/help/forms/using/draft-submission-component.md)。

## 调用AEM Workflow {#invoke-an-aem-workflow}

**[!UICONTROL 调用AEM工作流]**&#x200B;提交操作将自适应表单与AEM工作流关联。 提交表单后，关联的工作流会自动开始到处理节点。 此外，它还会将数据文件、附件和记录文档（如果适用）放在工作流的有效负荷位置。

在使用&#x200B;**[!UICONTROL 调用AEM Workflow]**&#x200B;提交操作之前，[配置AEM DS设置](/help/forms/using/configuring-the-processing-server-url-.md)。 有关创建AEM工作流的信息，请参阅OSGi](/help/forms/using/aem-forms-workflow.md)上的[以表单为中心的工作流。

## Adaptive Form {#server-side-revalidation-in-adaptive-form}中的服务器端重新验证

通常，在任何在线数据捕获系统中，开发人员都会在客户端放置一些JavaScript验证，以强制实施一些业务规则。 但在现代浏览器中，最终用户可以绕过这些验证，使用各种技术（如Web浏览器开发工具控制台）手动执行提交。 这种技术也适用于自适应表单。 表单开发者可以创建各种验证逻辑，但从技术上讲，最终用户可以绕过那些验证逻辑，将无效数据提交到服务器。 无效数据将破坏表单作者强制实施的业务规则。

服务器端重新验证功能还提供了在服务器上设计自适应表单时运行自适应表单作者提供的验证功能的功能。 它防止了在表单验证方面所表示的数据提交和业务规则违规的任何可能危害。

### 在服务器上验证什么？{#what-to-validate-on-server-br}

服务器上重新运行的自适应表单的开箱即用(OOTB)字段验证包括：

* 必填
* 验证图片子句
* 验证表达式

### 启用服务器端验证{#enabling-server-side-validation-br}

使用提要栏中“自适应表单”容器下的&#x200B;**在服务器**&#x200B;上重新验证，启用或禁用当前表单的服务器端验证。

![启用服务器端](assets/revalidate-on-server.png)
**验证图：** *启用服务器端验证*

如果最终用户绕过这些验证并提交表单，服务器将再次执行验证。 如果验证在服务器端失败，则会停止提交事务。 最终用户再次呈现原始形式。 捕获的数据和提交的数据作为错误呈现给用户。

### 支持验证表达式{#supporting-custom-functions-in-validation-expressions-br}中的自定义函数

有时，对于&#x200B;**复杂验证规则**，确切验证脚本驻留在自定义函数中，作者从字段验证表达式调用这些自定义函数。 要在执行服务器端验证时使此自定义函数库已知并可用，表单作者可以在自适应表单容器属性的&#x200B;**[!UICONTROL 基本]**&#x200B;选项卡下配置AEM客户端库的名称，如下所示。

![在验证表达式中支持自](assets/clientlib-cat.png)
**定义函数图：** *在验证表达式中支持自定义函数*

作者可以根据自适应表单配置自定义javascript库。 在库中，只保留可重用函数，这些函数依赖于jquery和endrower.js第三方库。

## 提交操作{#error-handling-on-submit-action}时出错处理

作为AEM安全和强化准则的一部分，请配置自定义错误页，如404.jsp和500.jsp。 提交表单时，将调用这些处理函数，出现404或500个错误。 当在“发布”节点上触发这些错误代码时，也会调用处理函数。

有关详细信息，请参阅[自定义由错误处理程序](/help/sites-developing/customizing-errorhandler-pages.md)显示的页面。
