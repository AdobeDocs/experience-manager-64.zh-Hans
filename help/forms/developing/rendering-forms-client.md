---
title: 在客户端呈现Forms
seo-title: 在客户端呈现Forms
description: 'null'
seo-description: 'null'
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
translation-type: tm+mt
source-git-commit: a750aeb9f41347da93f1ceb16c5646bc94bee67b
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# 在客户端呈现Forms {#rendering-forms-at-the-client}

## 在客户端呈现Forms {#rendering-forms-at-the-client-inner}

您可以使用Acrobat或Adobe Reader的客户端渲染功能优化PDF内容的投放并提高Forms服务处理网络负载的能力。 此过程称为在客户端渲染表单。 要在客户端渲染表单，客户端设备（通常为Web浏览器）必须使用Acrobat 7.0或Adobe Reader7.0或更高版本。

服务器端脚本执行对表单所做的更改不会反映在客户端呈现的表单中，除非根子表单包含设置为 `restoreState` 的属性 `auto`。 有关此属性的详细信息，请参阅 [Forms设计器。](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>有关Forms服务的详细信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步骤摘要 {#summary-of-steps}

要在客户端渲染表单，请执行以下任务:

1. 包括项目文件。
1. 创建一个Forms客户端API对象。
1. 设置客户端渲染运行时选项。
1. 在客户端渲染表单。
1. 将表单写入客户端Web浏览器。

**包括项目文件**

将必要的文件包含在您的开发项目中。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建Forms客户端API对象**

在以编程方式执行Forms服务客户端API操作之前，必须创建Forms服务客户端。 如果您使用Java API，请创建一个 `FormsServiceClient` 对象。 如果您使用的是FormsWeb服务API，请创建一个 `FormsService` 对象。

**设置客户端渲染运行时选项**

必须通过将运行时选项设置为，将客户端渲染运行时选项设置为在客户端 `RenderAtClient` 渲染表单 `true`。 这会导致表单被传送到呈现表单的客户端设备。 如 `RenderAtClient` 果 `auto` 为（默认值），表单设计将确定表单是否在客户端呈现。 表单设计必须是具有可流动布局的表单设计。

可选的运行时选项可供您设 `SeedPDF` 置。 该选 `SeedPDF` 项将PDF容器(种子PDF文档)与表单设计和XML数据结合在一起。 表单设计和XML数据都交付到Acrobat或Adobe Reader，在那里可以呈现表单。 当客 `SeedPDF` 户端计算机没有表单中使用的字体时，可以使用此选项，例如当最终用户未获得使用表单所有者有权使用的字体的许可时。

您可以使用设计器创建简单的动态PDF文件以用作种子PDF文件。 执行此任务需要执行以下步骤：

1. 确定您是否需要在种子PDF文件中嵌入任何字体。 种子PDF文件需要包含呈现表单所需的其他字体。 在将字体嵌入到种子PDF文件中时，请确保您没有违反任何字体授权协议。 在Designer中，您可以确定是否可以合法嵌入字体。 保存时，如果有字体无法嵌入到表单中，设计器将显示一条消息，列出您无法嵌入的字体。 对于静态PDF文档，此消息不在Designer中显示。
1. 如果您是在Designer中创建种子PDF文件，建议您至少添加一个包含消息的文本字段。 该信息应针对Adobe Reader早期版本的用户，说明他们需要Acrobat 7.0或更高版本，或Adobe Reader7.0或更高版本来视图文档。
1. 将种子PDF文件另存为带有PDF文件扩展名的动态PDF文件。

>[!NOTE]
>
>您无需定义种子PDF运行时选项即可在客户端上渲染表单。 如果不指定种子PDF,Forms服务将创建一个外壳pdf，它将不包含COS对象，但将包含一个PDF包装器，实际XDP内容嵌入其中。 本节中的步骤不设置种子PDF运行时选项。 有关COS对象的信息，请参阅《Adobe PDF参考指南》。

**在客户端渲染表单**

要在客户端上呈现表单，必须确保在呈现表单的应用程序逻辑中包含客户端呈现运行时选项。

**将表单数据流写入客户端Web浏览器**

Forms服务创建一个表单数据流，您必须将其写入客户端Web浏览器。 当写入到客户端Web浏览器时，表单由Acrobat 7.0或Adobe Reader7.0或更高版本渲染，并且用户可见。

**另请参阅**

[使用Java API在客户端渲染表单](#render-a-form-at-the-client-using-the-java-api)

[使用Web服务API在客户端渲染表单](#render-a-form-at-the-client-using-the-web-service-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms服务API快速开始](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[将文档送至Forms](/help/forms/developing/passing-documents-forms-service.md)

[创建呈现Forms的Web 应用程序](/help/forms/developing/creating-web-applications-renders-forms.md)

### 使用Java API在客户端渲染表单 {#render-a-form-at-the-client-using-the-java-api}

使用FormsAPI(Java)在客户端渲染表单：

1. 包括项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-forms-client.jar。

1. 创建Forms客户端API对象

   * 创建包 `ServiceClientFactory` 含连接属性的对象。
   * 使用对 `FormsServiceClient` 象的构造函数并传递该对 `ServiceClientFactory` 象。

1. 设置客户端渲染运行时选项

   * 使用对 `PDFFormRenderSpec` 象的构造函数创建对象。
   * 通过 `RenderAtClient` 调用对象的方法并传 `PDFFormRenderSpec` 递枚举值 `setRenderAtClient` 来设置运行时选项 `RenderAtClient.Yes`。

1. 在客户端渲染表单

   调用对 `FormsServiceClient` 象的方 `renderPDFForm` 法并传递以下值：

   * 一个字符串值，它指定表单设计名称，包括文件扩展名。 如果您引用的表单设计是AEM Forms应用程序的一部分，请确保指定完整路径，如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`。
   * 包 `com.adobe.idp.Document` 含要与表单合并的数据的对象。 如果不想合并数据，请传递空对 `com.adobe.idp.Document` 象。
   * 存 `PDFFormRenderSpec` 储在客户端呈现表单所需的运行时选项的对象。
   * 包 `URLSpec` 含Forms服务渲染表单所需的URI值的对象。
   * 存储 `java.util.HashMap` 文件附件的对象。 这是可选参数，您可 `null` 以指定是否不想将文件附加到表单。

   该方 `renderPDFForm` 法返回 `FormsResult` 一个对象，该对象包含必须写入客户端Web浏览器的表单数据流。

1. 将表单数据流写入客户端Web浏览器

   * 通过 `com.adobe.idp.Document` 调用对象的 `FormsResult` 方法创建 `getOutputContent` 对象。
   * 通过调用对象的方 `com.adobe.idp.Document` 法获取对象的内容 `getContentType` 类型。
   * 通过调 `javax.servlet.http.HttpServletResponse` 用对象的方法并传递对 `setContentType` 象的内容类型来设置对象的内 `com.adobe.idp.Document` 容类型。
   * 创建一 `javax.servlet.ServletOutputStream` 个对象，该对象通过调用该对象的方法将表单数据流写 `javax.servlet.http.HttpServletResponse` 入客户端Web浏 `getOutputStream` 览器。
   * 通过 `java.io.InputStream` 调用对象的 `com.adobe.idp.Document` 方法创建 `getInputStream` 对象。
   * 通过调用对象的方法并将字节数组作为参数进行传递，创 `InputStream` 建一个字 `read` 节数组并用表单数据流填充它。
   * 调用对 `javax.servlet.ServletOutputStream` 象的方 `write` 法，将表单数据流发送到客户端Web浏览器。 将字节数组传递给 `write` 方法。

**另请参阅**

[快速开始（SOAP模式）: 使用Java API在客户端渲染表单](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API在客户端渲染表单 {#render-a-form-at-the-client-using-the-web-service-api}

使用FormsAPI（Web服务）在客户端渲染表单：

1. 包括项目文件

   * 创建使用Forms服务WSDL的Java代理类。
   * 将Java代理类包含到类路径中。

1. 创建Forms客户端API对象

   创建对 `FormsService` 象并设置身份验证值。

1. 设置客户端渲染运行时选项

   * 使用对 `PDFFormRenderSpec` 象的构造函数创建对象。
   * 通过 `RenderAtClient` 调用对象的方法并传 `PDFFormRenderSpec` 递字符串 `setRenderAtClient` 值来设置运行时选项 `RenderAtClient.Yes`。

1. 在客户端渲染表单

   调用对 `FormsService` 象的方 `renderPDFForm` 法并传递以下值：

   * 一个字符串值，它指定表单设计名称，包括文件扩展名。 如果您引用的表单设计是Forms应用程序的一部分，请确保指定完整路径，如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`。
   * 包 `BLOB` 含要与表单合并的数据的对象。 如果不想合并数据，请传递 `null`。 (请参阅 [使用可流动布局预填充Forms](/help/forms/developing/prepopulating-forms-flowable-layouts.md)。)
   * 存 `PDFFormRenderSpec` 储在客户端呈现表单所需的运行时选项的对象。
   * 包 `URLSpec` 含Forms服务所需的URI值的对象。
   * 存储 `java.util.HashMap` 文件附件的对象。 这是可选参数，您可 `null` 以指定是否不想将文件附加到表单。
   * 由方 `com.adobe.idp.services.holders.BLOBHolder` 法填充的空对象。 此参数用于存储呈现的PDF表单。
   * 由方 `javax.xml.rpc.holders.LongHolder` 法填充的空对象。 （此参数将存储表单中的页数）。
   * 由方 `javax.xml.rpc.holders.StringHolder` 法填充的空对象。 （此参数将存储区域设置值）。
   * 将包含 `com.adobe.idp.services.holders.FormsResultHolder` 此操作结果的空对象。

   该 `renderPDFForm` 方法使用 `com.adobe.idp.services.holders.FormsResultHolder` 表单数据流填充作为最后一个参数值传递的对象，该表单数据流必须写入客户端Web浏览器。

1. 将表单数据流写入客户端Web浏览器

   * 通过 `FormResult` 获取对象数据成 `com.adobe.idp.services.holders.FormsResultHolder` 员的值创 `value` 建对象。
   * 通过调 `BLOB` 用对象的方法创建包含表 `FormsResult` 单数据的 `getOutputContent` 对象。
   * 通过调用对象的方 `BLOB` 法获取对象的内容 `getContentType` 类型。
   * 通过调 `javax.servlet.http.HttpServletResponse` 用对象的方法并传递对 `setContentType` 象的内容类型来设置对象的内 `BLOB` 容类型。
   * 创建一 `javax.servlet.ServletOutputStream` 个对象，该对象通过调用该对象的方法将表单数据流写 `javax.servlet.http.HttpServletResponse` 入客户端Web浏 `getOutputStream` 览器。
   * 创建一个字节数组，并通过调用对 `BLOB` 象的方法来填 `getBinaryData` 充它。 此任务将对象的内 `FormsResult` 容分配给字节数组。
   * 调用对 `javax.servlet.http.HttpServletResponse` 象的方 `write` 法，将表单数据流发送到客户端Web浏览器。 将字节数组传递给 `write` 方法。

**另请参阅**

[在客户端呈现Forms](#rendering-forms-at-the-client)

[使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
