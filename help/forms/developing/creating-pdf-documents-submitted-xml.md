---
title: 使用SubmittedXML文档创建PDF
seo-title: 使用SubmittedXML文档创建PDF
description: 'null'
seo-description: 'null'
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---


# 使用已提交的XML数据创建PDF文档 {#creating-pdf-documents-with-submittedxml-data}

## 使用已提交的XML数据创建PDF文档 {#creating-pdf-documents-with-submitted-xml-data}

使用户能够填写交互式表单的基于Web的应用程序需要将数据提交回服务器。 使用Forms服务，您可以检索用户在交互式表单中输入的表单数据。 然后，您可以将表单数据传递到另一个AEM Forms服务操作，并使用该数据创建PDF文档。

>[!NOTE]
>
>在阅读此内容之前，建议您对处理已提交表单有深入的了解。 表单设计与提交的XML数据之间的关系等概念在已提交的处理Forms中进行了介绍。

请考虑以下涉及三个AEM Forms服务的工作流：

* 用户从基于Web的应用程序向Forms服务提交XML数据。
* Forms服务用于处理提交的表单和提取表单字段。 可以处理表单数据。 例如，可以将数据提交到企业数据库。
* 表单数据将发送到输出服务以创建非交互式PDF文档。
* 非交互式PDF文档存储在Content Services（已弃用）中。

下图提供了此工作流的可视表示。

![cd_cd_finsrv_architecte_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

用户从客户端Web浏览器提交表单后，非交互式PDF文档存储在Content Services（已弃用）中。 下图显示了存储在Content Services中的PDF文档（已弃用）。

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### 步骤摘要 {#summary-of-steps}

要使用提交的XML文档创建非交互式PDF文档并存储在Content Services的PDF中（已弃用），请执行以下任务:

1. 包括项目文件。
1. 创建Forms、输出和文档管理对象。
1. 使用Forms服务检索表单数据。
1. 使用“输出”服务创建非交互式PDF文档。
1. 使用文档管理服务将PDF表单存储在Content Services（已弃用）中。

**包括项目文件**

将必要的文件包含在您的开发项目中。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建Forms、输出和文档管理对象**

在以编程方式执行Forms服务API操作之前，请创建一个Forms客户端API对象。 同样，由于此工作流调用输出和文档管理服务，因此请创建输出客户端API对象和文档管理客户端API对象。

**使用Forms服务检索表单数据**

检索提交到Forms服务的表单数据。 您可以处理提交的数据以满足您的业务需求。 例如，您可以将表单数据存储在企业数据库中。 但是，要创建非交互式PDF文档，表单数据会传递到输出服务。

**使用“输出”服务创建非交互式PDF文档。**

使用“输出”服务创建基于表单设计和XML表单文档的非交互式PDF数据。 在工作流中，从Forms服务检索表单数据。

**使用文档管理服务将PDF表单存储在Content Services（已弃用）中**

使用文档管理服务API在Content Services中存储PDF文档（已弃用）。

**另请参阅**

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms服务API快速开始](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### 使用Java API使用提交的XML数据创建PDF文档 {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

使用Forms、输出和文档管理API(Java)创建带有已提交XML数据的PDF文档:

1. 包括项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-forms-client.jar、adobe-output-client.jar和adobe-contentservices-client.jar。

1. 创建Forms、输出和文档管理对象

   * 创建包 `ServiceClientFactory` 含连接属性的对象。
   * 使用对 `FormsServiceClient` 象的构造函数并传递该对 `ServiceClientFactory` 象。
   * 使用对 `OutputClient` 象的构造函数并传递该对 `ServiceClientFactory` 象。
   * 使用对 `DocumentManagementServiceClientImpl` 象的构造函数并传递该对 `ServiceClientFactory` 象。

1. 使用Forms服务检索表单数据

   * 调用对 `FormsServiceClient` 象的方 `processFormSubmission` 法并传递以下值：

      * 包 `com.adobe.idp.Document` 含表单数据的对象。
      * 一个字符串值，它指定环境变量，包括所有相关的HTTP头。 通过为环境变量指定一个或多个值，指定要处理的内 `CONTENT_TYPE` 容类型。 例如，要处理XML数据，请为此参数指定以下字符串值： `CONTENT_TYPE=text/xml`.
      * 一个字符串值，它指 `HTTP_USER_AGENT` 定标题值，如 `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`。
      * 存 `RenderOptionsSpec` 储运行时选项的对象。

      该方 `processFormSubmission` 法返回 `FormsResult` 包含表单提交结果的对象。

   * 确定Forms服务是否已通过调用对象的方法处理 `FormsResult` 表单数 `getAction` 据。 如果此方法返回 `0`值，则数据可以处理。
   * 通过调用对象的方 `com.adobe.idp.Document` 法创建对象来 `FormsResult` 检索表单 `getOutputContent` 数据。 （此对象包含可发送到Output服务的表单数据。）
   * 通过调 `java.io.InputStream` 用构造函数并传 `java.io.DataInputStream` 递对象来创建 `com.adobe.idp.Document` 对象。
   * 通过调 `org.w3c.dom.DocumentBuilderFactory` 用静态对象的方 `org.w3c.dom.DocumentBuilderFactory` 法创建 `newInstance` 对象。
   * 通过调 `org.w3c.dom.DocumentBuilder` 用对象的方 `org.w3c.dom.DocumentBuilderFactory` 法创建 `newDocumentBuilder` 对象。
   * 通过调 `org.w3c.dom.Document` 用对象的方 `org.w3c.dom.DocumentBuilder` 法并传递 `parse` 对象来创建 `java.io.InputStream` 对象。
   * 检索XML文档中每个节点的值。 实现此任务的一种方法是创建接受两个参数的自定义方法： 要 `org.w3c.dom.Document` 检索其值的对象和节点的名称。 此方法返回表示节点值的字符串值。 在此过程后面的代码示例中，调用此自定义方法 `getNodeText`。 本文给出了该方法的主体。


1. 使用“输出”服务创建非交互式PDF文档。

   通过调用对象的方法并 `OutputClient` 传递以 `generatePDFOutput` 下值，创建PDF文档:

   * 枚举 `TransformationFormat` 值。 要生成PDF文档，请指定 `TransformationFormat.PDF`。
   * 指定表单设计名称的字符串值。 确保表单设计与从Forms服务检索的表单数据兼容。
   * 一个字符串值，它指定表单设计所在的内容根目录。
   * 包 `PDFOutputOptionsSpec` 含PDF运行时选项的对象。
   * 包含 `RenderOptionsSpec` 渲染运行时选项的对象。
   * 包 `com.adobe.idp.Document` 含XML数据源的对象，该数据源包含要与表单设计合并的数据。 确保对象的方法 `FormsResult` 返回此对 `getOutputContent` 象。
   * 该 `generatePDFOutput` 方法返回 `OutputResult` 包含操作结果的对象。
   * 通过调用对象的方法检索非交 `OutputResult` 互式PDF文档 `getGeneratedDoc` 符。 此方法返回 `com.adobe.idp.Document` 一个表示非交互式PDF文档的实例。

1. 使用文档管理服务将PDF表单存储在Content Services（已弃用）中

   通过调用对象的方 `DocumentManagementServiceClientImpl` 法并传递 `storeContent` 以下值来添加内容：

   * 一个字符串值，它指定添加内容的存储。 默认存储为 `SpacesStore`。 此值是必需参数。
   * 一个字符串值，它指定添加内容的空间的完全限定路径(例如 `/Company Home/Test Directory`)。 此值是必需参数。
   * 表示新内容的节点名称(例如 `MortgageForm.pdf`)。 此值是必需参数。
   * 指定节点类型的字符串值。 要添加新内容，如PDF文件，请指定 `{https://www.alfresco.org/model/content/1.0}content`。 此值是必需参数。
   * 表 `com.adobe.idp.Document` 示内容的对象。 此值是必需参数。
   * 一个字符串值，它指定编码值(例如 `UTF-8`)。 此值是必需参数。
   * 一个 `UpdateVersionType` 明细列表值，它指定如何处理版本信息(例如， `UpdateVersionType.INCREMENT_MAJOR_VERSION` 增加内容版本)。 )此值是必需参数。
   * 指定 `java.util.List` 与内容相关的方面的实例。 此值是可选参数，您可以指定 `null`。
   * 存储 `java.util.Map` 内容属性的对象。

   该方 `storeContent` 法返回一 `CRCResult` 个描述内容的对象。 例如， `CRCResult` 使用对象，您可以获取内容的唯一标识符值。 要执行此任务，请调 `CRCResult` 用对象的 `getNodeUuid` 方法。

**另请参阅**

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
