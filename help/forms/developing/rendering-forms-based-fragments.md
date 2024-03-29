---
title: 基于片段渲染Forms
seo-title: Rendering Forms Based on Fragments
description: 使用Forms服务渲染基于使用Designer创建的片段的表单。
seo-description: Use the Forms service to render forms that are based on fragments created using Designer.
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
role: Developer
exl-id: 49c4af9a-5797-468c-b3ad-f3140d445ff2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2231'
ht-degree: 0%

---

# 基于片段渲染Forms {#rendering-forms-based-on-fragments}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 基于片段渲染Forms {#rendering-forms-based-on-fragments-inner}

Forms服务可以渲染基于您使用Designer创建的片段的表单。 A *片段* 是表单的可重用部分，并另存为可插入多个表单设计的单独XDP文件。 例如，片段可以包含地址块或法律文本。

使用片段可简化和加快大量表单的创建和维护。 创建新表单时，需要插入对所需片段的引用，该片段将显示在表单中。 片段引用包含指向物理XDP文件的子表单。 有关基于片段创建表单设计的信息，请参阅 [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_cn)

片段可以包括封装在选择子表单集中的多个子表单。 选择子表单集基于来自数据连接的数据流控制子表单的显示。 您可以使用条件语句确定集合中的哪个子表单显示在提交表单中。 例如，集合中的每个子表单可以包括关于特定地理位置的信息，并且所显示的子表单可以基于用户的位置来确定。

A *脚本片段* 包含可重用的JavaScript函数或值，这些函数或值与任何特定对象（如日期解析器或Web服务调用）分开存储。 这些片段包含一个脚本对象，该对象在“层级”面板中显示为变量的子项。 无法从属于其他对象属性的脚本（例如验证、计算或初始化等事件脚本）中创建片段。

以下是使用片段的优势：

* **内容重用**:您可以使用片段在多个表单设计中重复使用内容。 当您需要在多个表单中使用某些相同的内容时，使用片段比复制或重新创建内容速度更快、更简单。 使用片段还可确保表单设计中常用的部分在所有引用表单中具有一致的内容和外观。
* **全局更新**:您可以在一个文件中使用片段对多个表单仅进行一次全局更改。 您可以更改片段中的内容、脚本对象、数据绑定、布局或样式，引用片段的所有XDP表单都将反映更改。
* 例如，许多表单中的一个通用元素可能是一个地址块，其中包含国家/地区的下拉列表对象。 如果需要更新下拉列表对象的值，则必须打开多个表单才能进行更改。 如果在片段中包含地址块，则只需打开一个片段文件即可进行更改。
* 要更新PDF表单中的片段，必须在Designer中重新保存该表单。
* **共享表单创建**:您可以使用片段在多个资源之间共享表单的创建。 具有脚本或Designer其他高级功能专业知识的表单开发人员可以开发和共享利用脚本和动态属性的片段。 表单设计人员可以使用这些片段来布局表单设计，并确保表单的所有部分在由多人设计的多个表单中具有一致的外观和功能。

### 装配使用片段组装的表单设计 {#assembling-a-form-design-assembled-using-fragments}

您可以基于多个片段组合表单设计以传递到Forms服务。 要组合多个片段，请使用汇编程序服务。 要查看使用组合服务创建供其他Forms服务（输出服务）使用的表单设计的示例，请参阅 [使用片段创建PDF文档](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). 您可以使用Forms服务来执行相同的工作流，而不是使用输出服务。

使用汇编程序服务时，您将传递使用片段组合的表单设计。 创建的表单设计不引用其他片段。 相反，本主题讨论如何传递引用其他片段的表单设计到Forms服务。 但是，表单设计不是由汇编程序组装的。 它是在Designer中创建的。

>[!NOTE]
>
>有关Forms服务的更多信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>有关创建基于Web的应用程序以根据片段呈现表单的信息，请参阅 [创建可渲染Forms的Web应用程序](/help/forms/developing/creating-web-applications-renders-forms.md).

### 步骤摘要 {#summary-of-steps}

要根据片段渲染表单，请执行以下任务：

1. 包括项目文件。
1. 创建Forms客户端API对象。
1. 指定URI值。
1. 渲染表单。
1. 将表单数据流写入客户端Web浏览器。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建Forms客户端API对象**

您必须先创建Forms服务客户端，然后才能以编程方式执行Forms服务客户端API操作。

**指定URI值**

要成功渲染基于片段的表单，您必须确保Forms服务能够找到表单设计引用的表单和片段（XDP文件）。 例如，假定表单名为PO.xdp，并且此表单使用名为FooterUS.xdp和FooterCanada.xdp的两个片段。 在这种情况下，Forms服务必须能够找到所有三个XDP文件。

您可以将表单及其片段放置在一个位置，将片段放置在另一个位置，或将所有XDP文件放置在同一位置，从而组织表单及其片段。 就本节而言，假定所有XDP文件都位于AEM Forms存储库中。 有关将XDP文件放置到AEM Forms存储库的信息，请参阅 [编写资源](/help/forms/developing/aem-forms-repository.md#writing-resources).

在基于片段呈现表单时，必须仅引用表单本身，而不引用片段。 例如，您必须引用PO.xdp，而不是FooterUS.xdp或FooterCanada.xdp。 确保将片段放置在Forms服务可以找到它们的位置。

**渲染表单**

基于片段的表单可以以与非碎片表单相同的方式呈现。 即，您可以将表单呈现为PDF、HTML或表单指南（已弃用）。 本节中的示例将基于片段的表单呈现为交互式PDF表单。 (请参阅 [呈现交互式PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**将表单数据流写入客户端Web浏览器**

当Forms服务呈现表单时，它会返回一个必须写入客户端Web浏览器的表单数据流。 写入客户端Web浏览器时，用户可以看到该表单。

**另请参阅**

[使用Java API根据片段渲染表单](#render-forms-based-on-fragments-using-the-java-api)

[使用Web服务API根据片段渲染表单](#render-forms-based-on-fragments-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API快速入门](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[呈现交互式PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[创建可渲染Forms的Web应用程序](/help/forms/developing/creating-web-applications-renders-forms.md)

### 使用Java API根据片段渲染表单 {#render-forms-based-on-fragments-using-the-java-api}

使用Forms API(Java)渲染基于片段的表单：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-forms-client.jar。

1. 创建Forms客户端API对象

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `FormsServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 指定URI值

   * 创建 `URLSpec` 使用其构造函数存储URI值的对象。
   * 调用 `URLSpec` 对象 `setApplicationWebRoot` 方法，并传递表示应用程序web根的字符串值。
   * 调用 `URLSpec` 对象 `setContentRootURI` 方法，并传递指定内容根URI值的字符串值。 确保表单设计和片段位于内容根URI中。 如果没有，则Forms服务会引发异常。 要引用存储库，请指定 `repository://`.
   * 调用 `URLSpec` 对象 `setTargetURL` 方法，并传递一个字符串值，该值指定将表单数据发布到的目标URL值。 如果在表单设计中定义目标URL，则可以传递一个空字符串。 您还可以指定将表单发送到的URL，以执行计算。

1. 渲染表单

   调用 `FormsServiceClient` 对象 `renderPDFForm` 方法并传递以下值：

   * 指定表单设计名称（包括文件扩展名）的字符串值。 如果您引用的表单设计是Forms应用程序的一部分，请确保指定完整路径，例如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` 包含要与表单合并的数据的对象。 如果不想合并数据，请传递一个空 `com.adobe.idp.Document` 对象。
   * A `PDFFormRenderSpec` 用于存储运行时选项的对象。
   * A `URLSpec` 包含Forms服务根据片段渲染表单所需URI值的对象。
   * A `java.util.HashMap` 用于存储文件附件的对象。 这是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。

   的 `renderPDFForm` 方法返回 `FormsResult` 包含必须写入客户端web浏览器的表单数据流的对象。

1. 将表单数据流写入客户端Web浏览器

   * 创建 `com.adobe.idp.Document` 对象 `FormsResult` 对象s `getOutputContent` 方法。
   * 获取的内容类型 `com.adobe.idp.Document` 通过调用对象 `getContentType` 方法。
   * 设置 `javax.servlet.http.HttpServletResponse` 对象的内容类型(通过调用 `setContentType` 方法和传递 `com.adobe.idp.Document` 对象。
   * 创建 `javax.servlet.ServletOutputStream` 用于通过调用将表单数据流写入客户端web浏览器的对象 `javax.servlet.http.HttpServletResponse` 对象 `getOutputStream` 方法。
   * 创建 `java.io.InputStream` 对象 `com.adobe.idp.Document` 对象 `getInputStream` 方法。
   * 通过调用 `InputStream` 对象 `read`方法并将字节数组作为参数进行传递。
   * 调用 `javax.servlet.ServletOutputStream` 对象 `write` 将表单数据流发送到客户端web浏览器的方法。 将字节数组传递到 `write` 方法。

**另请参阅**

[基于片段渲染Forms](#rendering-forms-based-on-fragments)

[快速入门（SOAP模式）：使用Java API根据片段渲染表单](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API根据片段渲染表单 {#render-forms-based-on-fragments-using-the-web-service-api}

使用Forms API（Web服务）渲染基于片段的表单：

1. 包含项目文件

   * 创建使用Forms服务WSDL的Java代理类。
   * 将Java代理类包含到类路径中。

1. 创建Forms客户端API对象

   创建 `FormsService` 对象，并设置身份验证值。

1. 指定URI值

   * 创建 `URLSpec` 使用其构造函数存储URI值的对象。
   * 调用 `URLSpec` 对象 `setApplicationWebRoot` 方法，并传递表示应用程序web根的字符串值。
   * 调用 `URLSpec` 对象 `setContentRootURI` 方法，并传递指定内容根URI值的字符串值。 确保表单设计位于内容根URI中。 如果没有，则Forms服务会引发异常。 要引用存储库，请指定 `repository://`.
   * 调用 `URLSpec` 对象 `setTargetURL` 方法，并传递一个字符串值，该值指定将表单数据发布到的目标URL值。 如果在表单设计中定义目标URL，则可以传递一个空字符串。 您还可以指定将表单发送到的URL，以执行计算。

1. 渲染表单

   调用 `FormsService` 对象 `renderPDFForm` 方法并传递以下值：

   * 指定表单设计名称（包括文件扩展名）的字符串值。 如果您引用的表单设计是Forms应用程序的一部分，请确保指定完整路径，例如 `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` 包含要与表单合并的数据的对象。 如果不想合并数据，请传递 `null`.
   * A `PDFFormRenderSpec` 用于存储运行时选项的对象。 请注意，如果输入文档是PDF文档，则无法设置标记的PDF选项。 如果输入文件是XDP文件，则可以设置标记的PDF选项。
   * A `URLSpec` 包含Forms服务所需URI值的对象。
   * A `java.util.HashMap` 用于存储文件附件的对象。 这是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。
   * 空 `com.adobe.idp.services.holders.BLOBHolder` 由方法填充的对象。 此参数用于存储渲染的表单。
   * 空 `javax.xml.rpc.holders.LongHolder` 由方法填充的对象。 此参数将以表单存储页数。
   * 空 `javax.xml.rpc.holders.StringHolder` 由方法填充的对象。 此参数将存储区域设置值。
   * 空 `com.adobe.idp.services.holders.FormsResultHolder` 包含此操作结果的对象。

   的 `renderPDFForm` 方法填充 `com.adobe.idp.services.holders.FormsResultHolder` 作为最后一个参数值传递的对象，表单数据流必须写入客户端web浏览器。

1. 将表单数据流写入客户端Web浏览器

   * 创建 `FormResult` 对象，方法是获取 `com.adobe.idp.services.holders.FormsResultHolder` 对象 `value` 数据成员。
   * 创建 `BLOB` 通过调用包含表单数据的对象 `FormsResult` 对象 `getOutputContent` 方法。
   * 获取的内容类型 `BLOB` 通过调用对象 `getContentType` 方法。
   * 设置 `javax.servlet.http.HttpServletResponse` 对象的内容类型(通过调用 `setContentType` 方法和传递 `BLOB` 对象。
   * 创建 `javax.servlet.ServletOutputStream` 用于通过调用将表单数据流写入客户端web浏览器的对象 `javax.servlet.http.HttpServletResponse` 对象 `getOutputStream` 方法。
   * 创建一个字节数组，并通过调用 `BLOB` 对象 `getBinaryData` 方法。 此任务分配 `FormsResult` 对象。
   * 调用 `javax.servlet.http.HttpServletResponse` 对象 `write` 将表单数据流发送到客户端web浏览器的方法。 将字节数组传递到 `write` 方法。

**另请参阅**

[基于片段渲染Forms](#rendering-forms-based-on-fragments)

[使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
