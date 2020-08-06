---
title: 使用自定义CSS文件渲染HTMLForms
seo-title: 使用自定义CSS文件渲染HTMLForms
description: 'null'
seo-description: 'null'
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
translation-type: tm+mt
source-git-commit: e2a6f76d8fa34b2b97713aaef094a2df8164e746
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 0%

---


# 使用自定义CSS文件渲染HTMLForms {#rendering-html-forms-using-custom-css-files}

Forms服务响应来自Web浏览器的HTTP请求来呈现HTML表单。 呈现HTML表单时，Forms服务可引用自定义CSS文件。 您可以创建自定义CSS文件以满足您的业务要求，并在使用Forms服务渲染HTML表单时引用该CSS文件。

Forms服务以静默方式解析自定义CSS文件。 即，Forms服务不会报告在自定义CSS文件不符合CSS标准时可能遇到的错误。 在这种情况下，Forms服务将忽略该样式，并继续保留CSS文件中的其余样式。

以下列表指定自定义CSS文件中支持的样式：

* **类级选择器——样式对**: 如果自定义CSS文件中存在，则使用HTML表单中用作类样式的选择器。 将忽略未使用的类样式。
* **标识符级别选择器——样式对**: 如果在HTML表单中使用所有标识符样式，则会使用这些样式。
* **元素级选择器样式对**: 如果在HTML表单中使用所有元素样式，则会使用这些样式。
* **样式优先级**: 支持样式优先级（如重要内容），并可在自定义CSS文件中使用。
* **媒体类型**: 一个或多个选择器样式对可以打包在@media样式中以定义媒体类型。 Forms服务不检查是否支持指定的媒体类型。 在自定义CSS文件中指定的媒体类型将合并到HTML表单中。

您可以使用FormsIVS应用程序检索示例CSS文件。 上传表单，在“测试表单设计”页面中选择它，然后单击“生成CSS”。 单击按钮之前，无需设置HTML转换类型。 下一步选择保存。 您可以编辑此CSS文件以满足您的业务需求。

>[!NOTE]
>
>在渲染使用自定义CSS文件的HTML表单之前，您必须对渲染HTML表单有深入的了解。 (请参阅 [将Forms渲染为HTML](/help/forms/developing/rendering-forms-html.md)。)

>[!NOTE]
>
>有关Forms服务的详细信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

## 步骤摘要 {#summary-of-steps}

要渲染使用CSS文件的HTML表单，请执行以下任务:

1. 包括项目文件。
1. 创建一个FormsJava API对象。
1. 引用CSS文件。
1. 渲染HTML表单。
1. 将表单数据流写入客户端Web浏览器。

**包括项目文件**

在开发项目中包含必要的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建FormsJava API对象**

在以编程方式执行Forms服务支持的操作之前，必须创建Forms客户端对象。

**引用CSS文件**

要渲染使用自定义CSS文件的HTML表单，请确保引用现有CSS文件。

**渲染HTML表单**

要渲染HTML表单，必须指定在Designer中创建并另存为XDP文件的表单设计。 还必须选择HTML转换类型。 例如，可指定用于为Internet Explorer 5.0或更高版本渲染动态HTML的HTML转换类型。

渲染HTML表单还需要值，如渲染其他表单类型所需的URI值。

**将表单数据流写入客户端Web浏览器**

当Forms服务呈现HTML表单时，它返回一个表单数据流，您必须将该数据流写入客户端Web浏览器，以使用户可以看到该HTML表单。

**另请参阅**

[使用Java API渲染使用CSS文件的HTML表单](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms服务API快速开始](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[渲染交互式PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[将Forms渲染为HTML](/help/forms/developing/rendering-forms-html.md)

[创建呈现Forms的Web 应用程序](/help/forms/developing/creating-web-applications-renders-forms.md)

## 使用Java API渲染使用CSS文件的HTML表单 {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

使用FormsAPI(Java)渲染使用自定义CSS文件的HTML表单：

1. 包括项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-forms-client.jar。

1. 创建FormsJava API对象

   * 创建包 `ServiceClientFactory` 含连接属性的对象。
   * 使用对 `FormsServiceClient` 象的构造函数并传递该对 `ServiceClientFactory` 象。

1. 引用CSS文件

   * 使用对 `HTMLRenderSpec` 象的构造函数创建对象。
   * 要呈现使用自定义CSS文件的HTML表单，请调 `HTMLRenderSpec` 用对象 `setCustomCSSURI` 的方法并传递一个字符串值，它指定CSS文件的位置和名称。

1. 渲染HTML表单

   调用对 `FormsServiceClient` 象的方 `(Deprecated) (Deprecated) renderHTMLForm` 法并传递以下值：

   * 一个字符串值，它指定表单设计名称，包括文件扩展名。 如果您引用的表单设计是Forms应用程序的一部分，请确保指定完整路径，如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`。
   * 指定 `TransformTo` HTML首选项类型的枚举值。 例如，要渲染与Internet Explorer 5.0或更高版本的动态HTML兼容的HTML表单，请指定 `TransformTo.MSDHTML`。
   * 包 `com.adobe.idp.Document` 含要与表单合并的数据的对象。 如果不想合并数据，请传递空对 `com.adobe.idp.Document` 象。
   * 存 `HTMLRenderSpec` 储HTML运行时选项的对象。
   * 一个字符串值，它指 `HTTP_USER_AGENT` 定标题值，如 `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`。
   * 存储 `URLSpec` 呈现HTML表单所需的URI值的对象。
   * 存储 `java.util.HashMap` 文件附件的对象。 这是可选参数，您可以指 `null` 定是否不想将文件附加到表单。

   该方 `(Deprecated) renderHTMLForm` 法返回 `FormsResult` 一个对象，该对象包含必须写入客户端Web浏览器的表单数据流。

1. 将表单数据流写入客户端Web浏览器

   * 通过 `com.adobe.idp.Document` 调用对象的 `FormsResult` 方法创建 `getOutputContent` 对象。
   * 通过调用对象的方 `com.adobe.idp.Document` 法获取对象的内容 `getContentType` 类型。
   * 通过调 `javax.servlet.http.HttpServletResponse` 用对象的方法并传递对 `setContentType` 象的内容类型来设置对象的内 `com.adobe.idp.Document` 容类型。
   * 创建一 `javax.servlet.ServletOutputStream` 个对象，该对象通过调用该对象的方法将表单数据流写 `javax.servlet.h\ttp.HttpServletResponse` 入客户端Web浏 `getOutputStream` 览器。
   * 通过 `java.io.InputStream` 调用对象的 `com.adobe.idp.Document` 方法创建 `getInputStream` 对象。
   * 通过调用对象的方法并将字节数组作为参数进行传递，创 `InputStream` 建一个字 `read` 节数组并用表单数据流填充它。
   * 调用对 `javax.servlet.ServletOutputStream` 象的方 `write` 法，将表单数据流发送到客户端Web浏览器。 将字节数组传递给 `write` 方法。

**另请参阅**

[使用自定义CSS文件渲染HTMLForms](#rendering-html-forms-using-custom-css-files)

[快速开始（SOAP模式）: 使用Java API渲染使用CSS文件的HTML表单](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## 使用Web服务API渲染使用CSS文件的HTML表单 {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

使用FormsAPI（Web服务）渲染使用自定义CSS文件的HTML表单：

1. 包括项目文件

   * 创建使用Forms服务WSDL的Java代理类。
   * 在类路径中包含Java代理类。

1. 创建FormsJava API对象

   创建对 `FormsService` 象并设置身份验证值。

1. 引用CSS文件

   * 使用对 `HTMLRenderSpec` 象的构造函数创建对象。
   * 要呈现使用自定义CSS文件的HTML表单，请调 `HTMLRenderSpec` 用对象 `setCustomCSSURI` 的方法并传递一个字符串值，它指定CSS文件的位置和名称。

1. 渲染HTML表单

   调用对 `FormsService` 象的方 `(Deprecated) renderHTMLForm` 法并传递以下值：

   * 一个字符串值，它指定表单设计名称，包括文件扩展名。 如果您引用的表单设计是Forms应用程序的一部分，请确保指定完整路径，如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`。
   * 指定 `TransformTo` HTML首选项类型的枚举值。 例如，要渲染与Internet Explorer 5.0或更高版本的动态HTML兼容的HTML表单，请指定 `TransformTo.MSDHTML`。
   * 包 `BLOB` 含要与表单合并的数据的对象。 如果不想合并数据，请传递 `null`。 (请参阅 [使用可流动布局预填充Forms](/help/forms/developing/prepopulating-forms-flowable-layouts.md)。)
   * 存 `HTMLRenderSpec` 储HTML运行时选项的对象。
   * 一个字符串值，它指 `HTTP_USER_AGENT` 定标题值，如 `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`。 如果不想设置此值，可以传递空字符串。
   * 存储 `URLSpec` 呈现HTML表单所需的URI值的对象。
   * 存储 `java.util.HashMap` 文件附件的对象。 这是可选参数，您可以指 `null` 定是否不想将文件附加到表单。
   * 由方 `com.adobe.idp.services.holders.BLOBHolder` 法填充的空对 `(Deprecated) renderHTMLForm` 象。 此参数值存储呈现的表单。
   * 由方 `com.adobe.idp.services.holders.BLOBHolder` 法填充的空对 `(Deprecated) renderHTMLForm` 象。 此参数存储输出XML数据。
   * 由方 `javax.xml.rpc.holders.LongHolder` 法填充的空对 `(Deprecated) renderHTMLForm` 象。 此参数存储表单中的页数。
   * 由方 `javax.xml.rpc.holders.StringHolder` 法填充的空对 `(Deprecated) renderHTMLForm` 象。 此参数存储区域设置值。
   * 由方 `javax.xml.rpc.holders.StringHolder` 法填充的空对 `(Deprecated) renderHTMLForm` 象。 此参数存储所使用的HTML呈现值。
   * 将包含 `com.adobe.idp.services.holders.FormsResultHolder` 此操作结果的空对象。

   该 `(Deprecated) renderHTMLForm` 方法使用 `com.adobe.idp.services.holders.FormsResultHolder` 表单数据流填充作为最后一个参数值传递的对象，该表单数据流必须写入客户端Web浏览器。

1. 将表单数据流写入客户端Web浏览器

   * 通过 `FormResult` 获取对象数据成 `com.adobe.idp.services.holders.FormsResultHolder` 员的值创 `value` 建对象。
   * 通过调 `BLOB` 用对象的方法创建包含表 `FormsResult` 单数据的 `getOutputContent` 对象。
   * 通过调用对象的方 `BLOB` 法获取对象的内容 `getContentType` 类型。
   * 通过调 `javax.servlet.http.HttpServletResponse` 用对象的方法并传递对 `setContentType` 象的内容类型来设置对象的内 `BLOB` 容类型。
   * 创建一 `javax.servlet.ServletOutputStream` 个对象，该对象通过调用该对象的方法将表单数据流写 `javax.servlet.http.HttpServletResponse` 入客户端Web浏 `getOutputStream` 览器。
   * 创建一个字节数组，并通过调用对 `BLOB` 象的方法来填 `getBinaryData` 充它。 此任务将对象的内 `FormsResult` 容分配给字节数组。
   * 调用对 `javax.servlet.http.HttpServletResponse` 象的方 `write` 法，将表单数据流发送到客户端Web浏览器。 将字节数组传递给 `write` 方法。

**另请参阅**

[使用自定义CSS文件渲染HTMLForms](#rendering-html-forms-using-custom-css-files)

[使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
