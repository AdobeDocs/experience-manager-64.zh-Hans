---
title: 将文档传递到FormsService
seo-title: Passing Documents to the FormsService
description: 将包含表单设计的com.adobe.idp.Document对象传递到Forms服务。 Forms服务会呈现位于com.adobe.idp.Document对象中的表单设计。
seo-description: Pass a com.adobe.idp.Document object that contains the form design to the Forms service. The Forms service renders the form design located in the com.adobe.idp.Document object.
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
role: Developer
exl-id: fe19e9b3-d662-4df2-b372-5006b794cde8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# 将文档传递到Forms服务 {#passing-documents-to-the-formsservice}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM Forms服务可向客户端设备（通常是Web浏览器）提供交互式PDF forms，以从用户那里收集信息。 交互式PDF表单基于表单设计，通常另存为XDP文件并在Designer中创建。 从AEM Forms开始，您可以通过 `com.adobe.idp.Document` 包含表单设计到Forms服务的对象。 然后，Forms服务会呈现位于 `com.adobe.idp.Document` 对象。

传递 `com.adobe.idp.Document` 对Forms服务的对象是其他服务操作返回 `com.adobe.idp.Document` 实例。 也就是说，你可以 `com.adobe.idp.Document` 实例，并渲染。 例如，假定XDP文件存储在名为的Content Services（已弃用）节点中 `/Company Home/Form Designs`，如下图所示。

您可以以编程方式从Content Services（已弃用）中检索Loan.xdp，并将XDP文件传递到 `com.adobe.idp.Document` 对象。

>[!NOTE]
>
>有关Forms服务的更多信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

## 步骤摘要 {#summary-of-steps}

要将从Content Services（已弃用）获取的文档传递到Forms服务，请执行以下任务：

1. 包括项目文件。
1. 创建Forms和文档管理客户端API对象。
1. 从内容服务中检索表单设计（已弃用）。
1. 呈现交互式PDF表单。
1. 对表单数据流执行操作。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请包含代理文件。

**创建Forms和文档管理客户端API对象**

在以编程方式执行Forms服务API操作之前，请先创建Forms客户端API对象。 此外，由于此工作流从Content Services检索XDP文件（已弃用），因此请创建一个文档管理API对象。

**从内容服务中检索表单设计（已弃用）**

使用Java或Web服务API从内容服务中检索XDP文件（已弃用）。 在 `com.adobe.idp.Document` 实例(或 `BLOB` 实例（如果您使用的是web服务）。 然后，您可以通过 `com.adobe.idp.Document` 实例到Forms服务。

**渲染交互式PDF表单**

要渲染交互式表单，请传递 `com.adobe.idp.Document` 从内容服务（已弃用）返回到Forms服务的实例。

>[!NOTE]
>
>您可以通过 `com.adobe.idp.Document` 包含表单设计到Forms服务的内容。 两种新方法名为 `renderPDFForm2` 和 `renderHTMLForm2` 接受 `com.adobe.idp.Document` 包含表单设计的对象。

**对表单数据流执行操作**

根据客户端应用程序的类型，您可以将表单写入客户端Web浏览器或将表单另存为PDF文件。 基于Web的应用程序通常将表单写入Web浏览器。 但是，桌面应用程序通常会将表单另存为PDF文件。

**另请参阅**

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API快速入门](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## 使用Java API将文档传递到Forms服务 {#pass-documents-to-the-forms-service-using-the-java-api}

传递使用Forms服务和内容服务（已弃用）API(Java)从Content Services（已弃用）获取的文档：

1. 包含项目文件

   将客户端JAR文件（如adobe-forms-client.jar和adobe-contentservices-client.jar）包含在您Java项目的类路径中。

1. 创建Forms和文档管理客户端API对象

   * 创建 `ServiceClientFactory` 包含连接属性的对象。 (请参阅 [设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * 创建 `FormsServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。
   * 创建 `DocumentManagementServiceClientImpl` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 从内容服务中检索表单设计（已弃用）

   调用 `DocumentManagementServiceClientImpl` 对象 `retrieveContent` 方法并传递以下值：

   * 一个字符串值，用于指定添加内容的商店。 默认存储区为 `SpacesStore`. 此值是必需参数。
   * 一个字符串值，用于指定要检索的内容的完全限定路径(例如， `/Company Home/Form Designs/Loan.xdp`)。 此值是必需参数。
   * 指定版本的字符串值。 此值是一个可选参数，您可以传递一个空字符串。 在这种情况下，将检索最新版本。

   的 `retrieveContent` 方法返回 `CRCResult` 包含XDP文件的对象。 获取 `com.adobe.idp.Document` 实例 `CRCResult` 对象 `getDocument` 方法。

1. 渲染交互式PDF表单

   调用 `FormsServiceClient` 对象 `renderPDFForm2` 方法并传递以下值：

   * A `com.adobe.idp.Document` 包含从内容服务中检索的表单设计的对象（已弃用）。
   * A `com.adobe.idp.Document` 包含要与表单合并的数据的对象。 如果不想合并数据，请传递一个空 `com.adobe.idp.Document` 对象。
   * A `PDFFormRenderSpec` 用于存储运行时选项的对象。 此值是一个可选参数，您可以指定 `null` 如果您不想指定运行时选项，请执行以下操作：
   * A `URLSpec` 包含URI值的对象。 此值是一个可选参数，您可以指定 `null`.
   * A `java.util.HashMap` 用于存储文件附件的对象。 此值是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。

   的 `renderPDFForm` 方法返回 `FormsResult` 包含必须写入客户端web浏览器的表单数据流的对象。

1. 对表单数据流执行操作

   * 创建 `com.adobe.idp.Document` 对象 `FormsResult` 对象s `getOutputContent` 方法。
   * 获取的内容类型 `com.adobe.idp.Document` 通过调用对象 `getContentType` 方法。
   * 设置 `javax.servlet.http.HttpServletResponse` 对象的内容类型(通过调用 `setContentType` 方法和传递 `com.adobe.idp.Document` 对象。
   * 创建 `javax.servlet.ServletOutputStream` 用于通过调用将表单数据流写入客户端web浏览器的对象 `javax.servlet.http.HttpServletResponse` 对象 `getOutputStream` 方法。
   * 创建 `java.io.InputStream` 对象 `com.adobe.idp.Document` 对象 `getInputStream` 方法。
   * 通过调用 `InputStream` 对象 `read` 方法。 将字节数组作为参数传递。
   * 调用 `javax.servlet.ServletOutputStream` 对象 `write` 将表单数据流发送到客户端web浏览器的方法。 将字节数组传递到 `write` 方法。

**另请参阅**

[快速入门（SOAP模式）：使用Java API将文档传递到Forms服务](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## 使用Web服务API将文档传递到Forms服务 {#pass-documents-to-the-forms-service-using-the-web-service-api}

传递使用Forms服务和内容服务（已弃用）API（Web服务）从Content Services获取的文档（已弃用）：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 由于此客户端应用程序调用两个AEM Forms服务，因此请创建两个服务引用。 对与Forms服务关联的服务引用使用以下WSDL定义： `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   对与文档管理服务关联的服务引用使用以下WSDL定义： `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   因为 `BLOB` 数据类型对于两个服务引用都是通用的，可完全限定 `BLOB` 数据类型。 在相应的Web服务快速启动中， `BLOB` 实例完全限定。

   >[!NOTE]
   >
   >替换 `localhost`*包含托管AEM Forms的服务器的IP地址。*

1. 创建Forms和文档管理客户端API对象

   * 创建 `FormsServiceClient` 对象。
   * 创建 `FormsServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/FormsService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `FormsServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `FormsServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >对 `DocumentManagementServiceClient`*服务客户端。*

1. 从内容服务中检索表单设计（已弃用）

   通过调用 `DocumentManagementServiceClient` 对象 `retrieveContent` 方法和传递以下值：

   * 一个字符串值，用于指定添加内容的商店。 默认存储区为 `SpacesStore`. 此值是必需参数。
   * 一个字符串值，用于指定要检索的内容的完全限定路径(例如， `/Company Home/Form Designs/Loan.xdp`)。 此值是必需参数。
   * 指定版本的字符串值。 此值是一个可选参数，您可以传递一个空字符串。 在这种情况下，将检索最新版本。
   * 用于存储浏览链接值的字符串输出参数。
   * A `BLOB` 用于存储内容的输出参数。 您可以使用此输出参数检索内容。
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` 用于存储内容属性的输出参数。
   * A `CRCResult` 输出参数。 您可以使用 `BLOB` 输出参数来获取内容。

1. 渲染交互式PDF表单

   调用 `FormsServiceClient` 对象 `renderPDFForm2` 方法并传递以下值：

   * A `BLOB` 包含从内容服务中检索的表单设计的对象（已弃用）。
   * A `BLOB` 包含要与表单合并的数据的对象。 如果不想合并数据，请传递一个空 `BLOB` 对象。
   * A `PDFFormRenderSpec` 用于存储运行时选项的对象。 此值是一个可选参数，您可以指定 `null` 如果您不想指定运行时选项，请执行以下操作：
   * A `URLSpec` 包含URI值的对象。 此值是一个可选参数，您可以指定 `null`.
   * A `Map` 用于存储文件附件的对象。 此值是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。
   * 用于存储页面计数的长输出参数。
   * 用于存储区域设置值的字符串输出参数。
   * A `FormsResult` 用于存储交互PDF表单的输出参数 `.`

   的 `renderPDFForm2` 方法返回 `FormsResult` 包含交互式PDF表单的对象。

1. 对表单数据流执行操作

   * 创建 `BLOB` 包含表单数据的对象，方法是通过获取 `FormsResult` 对象 `outputContent` 字段。
   * 创建 `System.IO.FileStream` 对象。 传递一个字符串值，以表示交互式PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 从检索的对象 `FormsResult` 对象。 通过获取 `BLOB` 对象 `MTOM` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
