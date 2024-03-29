---
title: 数字签名和认证文档
seo-title: Digitally Signing and Certifying Documents
description: 使用签名服务向PDF文档添加和删除数字签名字段，检索位于PDF文档中的签名字段的名称，修改签名字段，对PDF文档进行数字签名，对PDF文档进行数字签名，验证位于PDF文档中的数字签名，验证位于PDF文档中的所有数字签名，以及从签名字段中删除数字签名。
seo-description: Use the Signature service to add and delete digital signature fields to a PDF document, retrieve the names of signature fields located in a PDF document, modify signature fields, digitally sign PDF documents, certify PDF documents, validate digital signatures located in a PDF document, validate all digital signatures located in a PDF document, and remove a digital signature from a signature field.
uuid: 6331de8a-2a9c-45bf-89d2-29f1ad5cc856
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 42de04bf-25e4-4478-a411-38671ed871ae
role: Developer
exl-id: b8488a39-44dd-4e6c-b3f0-857d67c79385
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '17068'
ht-degree: 0%

---

# 数字签名和认证文档 {#digitally-signing-and-certifying-documents}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

**关于签名服务**

签名服务允许贵组织保护其分发和接收的Adobe PDF文档的安全和隐私。 此服务使用数字签名和认证来确保只有预期的收件人才能更改文档。 由于安全功能应用于文档本身，因此文档在其整个生命周期中保持安全并受到控制。 文档在防火墙之外、在离线下载以及提交回您的组织时，仍然是安全的。

>[!NOTE]
>
>您可以为签名服务创建自定义签名处理程序，在调用某些操作(如对PDF文档进行签名)时将调用该处理程序。

**签名字段名称**

某些签名服务操作要求您指定在其上执行操作的签名字段的名称。 例如，在对PDF文档进行签名时，您可以指定要签名字段的名称。 假定签名字段的全名为 `form1[0].Form1[0].SignatureField1[0]`. 您可以指定 `SignatureField1[0]` 而不是 `form1[0].Form1[0].SignatureField1[0]`.

有时，冲突会导致签名服务在错误的字段上签名（或执行需要签名字段名称的其他操作）。 此冲突是名称的结果 `SignatureField1[0]` 出现在同一PDF文档中的两个或多个位置。 例如，假定PDF文档包含两个名为的签名字段 `form1[0].Form1[0].SignatureField1[0]` 和 `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` 然后，指定 `SignatureField1[0]`. 在这种情况下，签名服务在迭代文档中的所有签名字段时对它找到的第一个签名字段进行签名。

如果PDF文档中有多个签名字段，建议您指定签名字段的全名。 即，指定 `form1[0].Form1[0].SignatureField1[0]`而不是 `SignatureField1[0]`.

您可以使用签名服务完成以下任务：

* 向PDF文档添加和删除数字签名字段。 (请参阅 [添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields).)
* 检索位于PDF文档中的签名字段的名称。 (请参阅 [检索签名字段名称](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* 修改签名字段。 (请参阅 [修改签名字段](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* 对PDF文档进行数字签名。 (请参阅 [数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* 验证PDF文档。 (请参阅 [认证PDF文档](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* 验证位于PDF文档中的数字签名。 (请参阅 [验证数字签名](#unresolvedlink-lc-si).)
* 验证位于PDF文档中的所有数字签名。 (请参阅 [验证多个数字签名](#unresolvedlink-lc-si).)
* 从签名字段中删除数字签名。 (请参阅 [删除数字签名](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>有关签名服务的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

## 添加签名字段 {#adding-signature-fields}

数字签名显示在签名字段中，签名字段是包含签名图形表示的表单字段。 签名字段可以是可见的或不可见的。 签名者可以使用预先存在的签名字段，也可以以编程方式添加签名字段。 无论哪种情况，签名字段都必须存在，然后才能对PDF文档进行签名。

您可以使用签名服务Java API或签名Web服务API以编程方式添加签名字段。 可向PDF文档添加多个签名字段；但是，每个签名字段名称必须唯一。

>[!NOTE]
>
>某些PDF文档类型不允许您以编程方式添加签名字段。 有关签名服务和添加签名字段的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary-of-steps}

要向PDF文档添加签名字段，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取添加了签名字段的PDF文档。
1. 添加签名字段。
1. 将PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

**创建签名客户端**

在以编程方式执行签名服务操作之前，必须创建签名服务客户端。

**获取添加了签名字段的PDF文档**

您必须获取要添加签名字段的PDF文档。

**添加签名字段**

要成功将签名字段添加到PDF文档，请指定用于标识签名字段位置的坐标值。 （如果添加不可见的签名字段，则不需要这些值。） 此外，您还可以指定在将签名应用于签名字段后，PDF文档中的哪些字段会被锁定。

**将PDF文档另存为PDF文件**

在签名服务向PDF文档添加签名字段后，您可以将该文档另存为PDF文件，以便用户可以在Acrobat或Adobe Reader中打开它。

**另请参阅**

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### 使用Java API添加签名字段 {#add-signature-fields-using-the-java-api}

使用签名API(Java)添加签名字段：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取添加了签名字段的PDF文档

   * 创建 `java.io.FileInputStream` 对象，该对象表示将签名字段添加到的PDF文档使用其构造函数并传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 添加签名字段

   * 创建 `PositionRectangle` 使用其构造函数指定签名字段位置的对象。 在构造函数中，指定坐标值。
   * 如果需要，请创建 `FieldMDPOptions` 指定在数字签名应用于签名字段时锁定的字段的对象。
   * 通过调用 `SignatureServiceClient` 对象 `addSignatureField` 方法和传递以下值：

      * A `com.adobe.idp`. `Document` 表示将签名字段添加到的PDF文档的对象。
      * 指定签名字段名称的字符串值。
      * A `java.lang.Integer` 表示添加签名字段的页码的值。
      * A `PositionRectangle` 指定签名字段位置的对象。
      * A `FieldMDPOptions` 指定PDF文档中在将数字签名应用于签名字段后被锁定的字段的对象。 此参数值是可选的，您可以通过 `null`.
   * A `PDFSeedValueOptions` 指定各种运行时值的对象。 此参数值是可选的，您可以通过 `null`.

      的 `addSignatureField` 方法返回 `com.adobe.idp`. `Document` 表示包含签名字段的PDF文档的对象。
   >[!NOTE]
   >
   >您可以调用 `SignatureServiceClient` 对象 `addInvisibleSignatureField` 添加不可见签名字段的方法。

1. 将PDF文档另存为PDF文件

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp`. `Document` 对象 `copyToFile` 复制内容的方法 `Document` 对象。 确保使用 `com.adobe.idp`. `Document` 由返回的对象 `addSignatureField` 方法。

**另请参阅**

[签名服务API快速入门](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### 使用Web服务API添加签名字段 {#add-signature-fields-using-the-web-service-api}

要使用签名API（Web服务）添加签名字段，请执行以下操作：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取添加了签名字段的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储将包含签名字段的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性。

1. 添加签名字段

   通过调用 `SignatureServiceClient` 对象 `addSignatureField` 方法和传递以下值：

   * A `BLOB` 表示将签名字段添加到的PDF文档的对象。
   * 指定签名字段名称的字符串值。
   * 一个整数值，表示将签名字段添加到的页码。
   * A `PositionRect` 指定签名字段位置的对象。
   * A `FieldMDPOptions` 指定PDF文档中在将数字签名应用于签名字段后被锁定的字段的对象。 此参数值是可选的，您可以通过 `null`.
   * A `PDFSeedValueOptions` 指定各种运行时值的对象。 此参数值是可选的，您可以通过 `null`.

   的 `addSignatureField` 方法返回 `BLOB` 表示包含签名字段的PDF文档的对象。

1. 将PDF文档另存为PDF文件

   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示将包含签名字段的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 由返回的对象 `addSignatureField` 方法。 通过获取 `BLOB` 对象 `binaryData` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 检索签名字段名称 {#retrieving-signature-field-names}

您可以检索位于要签名或认证的PDF文档中的所有签名字段的名称。 如果您不确定位于PDF文档中的签名字段名称或要验证这些名称，则可以以编程方式检索它们。 签名服务返回签名字段的完全限定的名称，如 `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>有关签名服务的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)

### 步骤摘要 {#summary_of_steps-1}

要检索签名字段名称，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取包含签名字段的PDF文档。
1. 检索签名字段名称。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名服务操作之前，必须创建签名服务客户端。

**获取包含签名字段的PDF文档**

检索包含签名字段的PDF文档。

**检索签名字段名称**

在检索包含一个或多个签名字段的PDF文档后，可以检索签名字段名称。

**另请参阅**

[使用Java API检索签名字段名称](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[使用Web服务API检索签名字段](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields)

### 使用Java API检索签名字段名称 {#retrieve-signature-field-names-using-the-java-api}

使用签名API(Java)检索签名字段名称：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar文件。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取包含签名字段的PDF文档

   * 创建 `java.io.FileInputStream` 表示包含签名字段的PDF文档的对象(使用其构造函数并传递指定PDF文档位置的字符串值)。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 检索签名字段名称

   * 通过调用 `SignatureServiceClient` 对象 `getSignatureFieldList` 方法和通过 `com.adobe.idp.Document` 包含包含签名字段的PDF文档的对象。 此方法将返回 `java.util.List` 对象，其中每个元素都包含 `PDFSignatureField` 对象。 使用此对象，您可以获取有关签名字段的其他信息，如签名字段是否可见。
   * 循环访问 `java.util.List` 用于确定是否存在签名字段名称的对象。 对于PDF文档中的每个签名字段，您可以获取单独的 `PDFSignatureField` 对象。 要获取签名字段的名称，请调用 `PDFSignatureField` 对象 `getName` 方法。 此方法将返回一个指定签名字段名称的字符串值。

**另请参阅**

[检索签名字段名称](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[快速入门（SOAP模式）：使用Java API检索签名字段名称](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API检索签名字段 {#retrieve-signature-field-using-the-web-service-api}

使用签名API（Web服务）检索签名字段名称：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取包含签名字段的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储包含签名字段的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 字段字节数组内容。

1. 检索签名字段名称

   * 通过调用检索签名字段名称 `SignatureServiceClient` 对象 `getSignatureFieldList` 方法和通过 `BLOB` 包含包含签名字段的PDF文档的对象。 此方法将返回 `MyArrayOfPDFSignatureField` 每个元素包含的集合对象 `PDFSignatureField` 对象。
   * 循环访问 `MyArrayOfPDFSignatureField` 用于确定是否存在签名字段名称的对象。 对于PDF文档中的每个签名字段，您可以 `PDFSignatureField` 对象。 要获取签名字段的名称，请调用 `PDFSignatureField` 对象 `getName` 方法。 此方法将返回一个指定签名字段名称的字符串值。

**另请参阅**

[检索签名字段名称](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 修改签名字段 {#modifying-signature-fields}

您可以使用Java API和Web服务API修改位于PDF文档中的签名字段。 修改签名字段涉及处理其签名字段锁定字典值或种子值字典值。

A *字段锁词典* 指定签名字段时锁定的字段列表。 锁定的字段可阻止用户更改该字段。 A *种子值字典* 包含在应用签名时使用的约束信息。 例如，您可以更改权限，以控制可能发生的操作，而无需使签名失效。

通过修改现有签名字段，您可以更改PDF文档以反映不断变化的业务需求。 例如，新业务要求可能要求在文档签署后锁定所有文档字段。

本节介绍如何通过修改字段锁定词典和种子值词典值来修改签名字段。 对签名字段锁定词典所做的更改导致签名字段被签名时，PDF文档中的所有字段都被锁定。 对种子值字典所做的更改会禁止对文档进行特定类型的更改。

>[!NOTE]
>
>有关签名服务和修改签名字段的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary_of_steps-2}

要修改位于PDF文档中的签名字段，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取包含要修改的签名字段的PDF文档。
1. 设置字典值。
1. 修改签名字段。
1. 将PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包含LiveCycleJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名服务操作之前，必须创建签名服务客户端。

**获取包含要修改的签名字段的PDF文档**

检索包含要修改的签名字段的PDF文档。

**设置字典值**

要修改签名字段，请为其字段锁定字典或种子值字典分配值。 指定签名字段锁定词典值涉及指定签名字段时锁定的PDF文档字段。 （本节将讨论如何锁定所有字段。）

可以设置以下种子值字典值：

* **修订检查**:指定在将签名应用于签名字段时是否执行吊销检查。
* **证书选项**:为证书种子值字典分配值。 在指定证书选项之前，建议您熟悉证书种子值字典。 (请参阅 [PDF参考](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **摘要选项**:分配用于签名的摘要算法。 有效值为SHA1、SHA256、SHA384、SHA512和RIPEMD160。
* **过滤器**:指定与签名字段一起使用的过滤器。 例如，您可以使用Adobe.PPKLite过滤器。 (请参阅 [PDF参考](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **标记选项**:指定与此签名字段关联的标记值。 值1表示签名者必须仅为条目使用指定的值。 值0表示允许使用其他值。 以下是位位置：

   * **1（过滤器）：** 用于签名字段的签名处理程序
   * **2（子过滤器）：** 一个名称数组，指示在签名时使用的可接受编码
   * **3(V)**:用于签名字段的签名处理程序的最低所需版本号
   * **4（理由）：** 字符串数组，可指定签署文档的可能原因
   * **5(PDFLegalWarnings):** 一个字符串数组，可指定可能的合法证明

* **法律证明**:文档经认证后，会自动扫描特定类型的内容，这些内容可能会使文档的可见内容模糊或具有误导性。 例如，注释可能会掩盖对了解认证内容非常重要的文本。 扫描过程会生成指示存在此类内容的警告。 它还对可能生成警告的内容提供了额外说明。
* **权限**:指定可在PDF文档上使用的权限，而不使签名失效。
* **原因**:指定必须签署此文档的原因。
* **时间戳**:指定时间戳选项。 例如，您可以设置所用时间戳服务器的URL。
* **版本**:指定要用于签名字段的签名处理程序的最低版本号。

**修改签名字段**

在创建签名服务客户端后，检索包含要修改的签名字段的PDF文档，并设置字典值，您可以指示签名服务修改签名字段。 然后，签名服务返回包含修改后签名字段的PDF文档。 原始PDF文档不受影响。

**将PDF文档另存为PDF文件**

将包含已修改签名字段的PDF文档保存为PDF文件，以便用户可以在Acrobat或Adobe Reader中打开它。

**另请参阅**

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[签名服务API快速入门](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### 使用Java API修改签名字段 {#modify-signature-fields-using-the-java-api}

使用签名API(Java)修改签名字段：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar文件。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取包含要修改的签名字段的PDF文档

   * 创建 `java.io.FileInputStream` 表示包含要修改的签名字段的PDF文档的对象(使用其构造函数并传递指定PDF文档位置的字符串值)。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 设置字典值

   * 创建 `PDFSignatureFieldProperties` 对象。 A `PDFSignatureFieldProperties` 对象存储签名字段锁定字典和种子值字典信息。
   * 创建 `PDFSeedValueOptionSpec` 对象。 此对象允许您设置种子值字典值。
   * 通过调用 `PDFSeedValueOptionSpec` 对象 `setMdpValue` 方法和通过 `MDPPermissions.NoChanges` 枚举值。
   * 创建 `FieldMDPOptionSpec` 对象。 此对象允许您设置签名字段锁定词典值。
   * 通过调用 `FieldMDPOptionSpec` 对象 `setMdpValue` 方法和通过 `FieldMDPAction.ALL` 枚举值。
   * 通过调用 `PDFSignatureFieldProperties` 对象 `setSeedValue` 方法和通过 `PDFSeedValueOptionSpec` 对象。
   * 通过调用 `PDFSignatureFieldProperties`对象 `setFieldMDP` 方法和通过 `FieldMDPOptionSpec` 对象。

   >[!NOTE]
   >
   >要查看可设置的所有种子值字典值，请参阅 `PDFSeedValueOptionSpec` 类引用。 (请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. 修改签名字段

   通过调用 `SignatureServiceClient` 对象 `modifySignatureField` 方法和传递以下值：

   * 的 `com.adobe.idp.Document` 用于存储要修改的签名字段的PDF文档的对象
   * 指定签名字段名称的字符串值
   * 的 `PDFSignatureFieldProperties` 存储签名字段锁定字典和种子值字典信息的对象

   的 `modifySignatureField` 方法返回 `com.adobe.idp.Document` 用于存储包含修改的签名字段的PDF文档的对象。

1. 将PDF文档另存为PDF文件

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp.Document` 对象 `copyToFile` 复制内容的方法 `com.adobe.idp.Document` 对象。 确保使用 `com.adobe.idp.Document` 对象 `modifySignatureField` 方法返回。

### 使用Web服务API修改签名字段 {#modify-signature-fields-using-the-web-service-api}

使用签名API（Web服务）修改签名字段：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取包含要修改的签名字段的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储包含要修改的签名字段的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。

1. 设置字典值

   * 创建 `PDFSignatureFieldProperties` 对象。 此对象存储签名字段锁定字典和种子值字典信息。
   * 创建 `PDFSeedValueOptionSpec` 对象。 此对象允许您设置种子值字典值。
   * 通过分配 `MDPPermissions.NoChanges` 枚举值 `PDFSeedValueOptionSpec` 对象 `mdpValue` 数据成员。
   * 创建 `FieldMDPOptionSpec` 对象。 此对象允许您设置签名字段锁定词典值。
   * 通过指定 `FieldMDPAction.ALL` 枚举值 `FieldMDPOptionSpec` 对象 `mdpValue` 数据成员。
   * 通过分配 `PDFSeedValueOptionSpec` 对象 `PDFSignatureFieldProperties` 对象 `seedValue` 数据成员。
   * 通过分配 `FieldMDPOptionSpec` 对象 `PDFSignatureFieldProperties` 对象 `fieldMDP` 数据成员。

   >[!NOTE]
   >
   >要查看可设置的所有种子值字典值，请参阅 `PDFSeedValueOptionSpec` 类引用。 (请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en))。

1. 修改签名字段

   通过调用 `SignatureServiceClient` 对象 `modifySignatureField` 方法和传递以下值：

   * 的 `BLOB` 用于存储要修改的签名字段的PDF文档的对象
   * 指定签名字段名称的字符串值
   * 的 `PDFSignatureFieldProperties` 存储签名字段锁定字典和种子值字典信息的对象

   的 `modifySignatureField` 方法返回 `BLOB` 用于存储包含修改的签名字段的PDF文档的对象。

1. 将PDF文档另存为PDF文件

   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示将包含签名字段的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 对象 `addSignatureField` 方法会返回。 通过获取 `BLOB` 对象 `MTOM` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 数字签名PDF文档 {#digitally-signing-pdf-documents}

数字签名可应用于PDF文档以提供安全级别。 数字签名（如手写签名）提供了一种手段，使签名者能够识别自己并对文档进行陈述。 用于对文档进行数字签名的技术有助于确保签名者和收件人都清楚已签名的内容，并确信文档自签名后没有被更改。

PDF文件采用公钥技术进行签名。 签名者有两个密钥：公钥和私钥。 私钥存储在用户的凭据中，在签名时必须可用。 公钥存储在用户的证书中，收件人必须可以使用该证书来验证签名。 有关已吊销证书的信息可在由证书颁发机构(CA)分发的证书吊销列表(CRL)和在线证书状态协议(OCSP)响应中找到。 签名时间可以从称为时间戳颁发机构的可信来源获得。

>[!NOTE]
>
>在对PDF文档进行数字签名之前，必须确保将证书添加到AEM Forms。 证书是使用管理控制台添加的，或使用信任管理器API以编程方式添加的。 (请参阅 [使用信任管理器API导入凭据](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

您可以以编程方式对PDF文档进行数字签名。 对PDF文档进行数字签名时，必须引用AEM Forms中存在的安全凭据。 凭据是用于签名的私钥。

签名服务在签名PDF文档时执行以下步骤：

1. 签名服务通过传递请求中指定的别名从Truststore中检索凭据。
1. 信任存储会搜索指定的凭据。
1. 凭据将返回到签名服务，并用于对文档进行签名。 此外，还会根据将来请求的别名缓存凭据。

有关处理安全凭据的信息，请参阅*为应用程序服务器安装和部署AEM Forms*指南。

>[!NOTE]
>
>签名和认证文档之间存在差异。 (请参阅 [认证PDF文档](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>并非所有PDF文档都支持签名。 有关签名服务和数字签名文档的更多信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>签名服务不支持将嵌入PDF数据作为操作输入（如验证文档）的XDP文件。 此操作会导致签名服务引发 `PDFOperationException`. 要解决此问题，请使用PDF实用程序服务将XDP文件转换为PDF文件，然后将转换后的PDF文件传递到签名服务操作。 (请参阅 [使用PDF实用程序](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**nShield HSM凭据**

使用nCipher nShield HSM凭据对PDF文档进行签名或认证时，新凭据在重新启动部署AEM Forms的J2EE应用程序服务器之前无法使用。 但是，您可以设置一个配置值，从而在不重新启动J2EE应用程序服务器的情况下使用符号或验证操作。

您可以在cknfastrc文件中添加以下配置值，该文件位于/opt/nfast/cknfastrc(或c:\nfast\cknfastrc):

```as3
 CKNFAST_ASSUME_SINGLE_PROCESS=0
```

将此配置值添加到cknfastrc文件后，无需重新启动J2EE应用程序服务器即可使用新凭据。

**签名不受信任**

在验证和签署同一PDF文档时，如果验证签名不可信，则在Acrobat或Adobe Reader中打开PDF文档时，第一个签名会出现一个黄色三角形。 为避免这种情况，认证签名必须可信。

**对基于XFA的表单的文档进行签名**

如果您尝试使用签名服务API对基于XFA的表单进行签名，则数据可能会从 `View` `Signed` `Version` 位于Acrobat。 例如，请考虑以下工作流：

* 使用使用Designer创建的XDP文件，可以合并包含签名字段和包含表单数据的XML数据的表单设计。 您可以使用Forms服务生成交互式PDF文档。
* 您使用签名服务API对PDF文档进行签名。

### 步骤摘要 {#summary_of_steps-3}

要对PDF文档进行数字签名，请执行以下任务：

1. 包括项目文件。
1. 创建签名服务客户端。
1. 获取要签名的PDF文档。
1. 签署PDF文档。
1. 将签名的PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

**创建签名客户端**

在以编程方式执行签名服务操作之前，必须创建签名服务客户端。

**获取要签名的PDF文档**

要对PDF文档进行签名，必须获取包含签名字段的PDF文档。 如果PDF文档不包含签名字段，则无法对其进行签名。 可以使用Designer或以编程方式添加签名字段。

**签署PDF文档**

在对PDF文档进行签名时，您可以设置签名服务使用的运行时选项。 您可以设置以下选项：

* 外观选项
* 吊销检查
* 时间戳值

使用 `PDFSignatureAppearanceOptionSpec` 对象。 例如，您可以通过调用 `PDFSignatureAppearanceOptionSpec` 对象 `setShowDate` 方法和传递 `true`.

您还可以指定是否执行撤销检查，以确定用于对PDF文档进行数字签名的证书是否已被撤销。 要执行撤销检查，您可以指定以下值之一：

* **NoCheck**:不执行吊销检查。
* **BestEffort**:始终尝试检查是否吊销链中的所有证书。 如果检查中出现任何问题，则假定撤销有效。 如果发生任何失败，请假定证书未吊销。
* **CheckIfAvailable:** 如果吊销信息可用，请检查是否吊销链中的所有证书。 如果检查中出现任何问题，则假定撤销无效。 如果发生任何失败，请假定证书已吊销且无效。 （这是默认值。）
* **AlwaysCheck**:检查是否吊销链中的所有证书。 如果任何证书中不存在吊销信息，则假定吊销无效。

要对证书执行吊销检查，您可以使用 `CRLOptionSpec` 对象。 但是，如果要执行吊销检查，并且您没有指定到CRL服务器的URL，则签名服务将从证书中获取该URL。

在执行撤销检查时，您可以使用联机证书状态协议(OCSP)服务器，而不是使用CRL服务器。 通常，在与CRL服务器相对使用OCSP服务器时，会更快地执行撤销检查。 (请参阅 [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

您可以使用Adobe应用程序和服务设置签名服务使用的CRL和OCSP服务器顺序。 例如，如果首先在Adobe应用程序和服务中设置OCSP服务器，则检查OCSP服务器，然后检查CRL服务器。 （请参阅AAC帮助中的“使用信任存储管理证书和凭据”）。

如果您指定不执行吊销检查，则签名服务不会检查用于对文档进行签名或认证的证书是否已被吊销。 即，忽略CRL和OCSP服务器信息。

>[!NOTE]
>
>虽然可以在证书中指定CRL或OCSP服务器，但您可以使用 `CRLOptionSpec` 和 `OCSPOptionSpec` 对象。 例如，要覆盖CRL服务器，可以调用 `CRLOptionSpec` 对象 `setLocalURI` 方法。

时间戳是指跟踪修改已签名或已验证文档的时间的过程。 文档一旦签名，即使文档所有者也不应修改它。 时间戳有助于加强已签名或已认证文档的有效性。 您可以使用 `TSPOptionSpec` 对象。 例如，您可以指定时间戳提供程序(TSP)服务器的URL。

>[!NOTE]
>
>在Java和Web服务中浏览各个部分和相应的快速启动，使用撤销检查。 由于未指定CRL或OCSP服务器信息，因此服务器信息是从用于对PDF文档进行数字签名的证书中获取的。

要成功对PDF文档进行签名，您可以指定将包含数字签名的签名字段的完全限定名称，例如 `form1[0].#subform[1].SignatureField3[3]`. 使用XFA表单字段时，还可以使用签名字段的部分名称： `SignatureField3[3]`.

您还必须引用安全凭据才能对PDF文档进行数字签名。 要引用安全凭据，请指定别名。 别名是对实际凭据的引用，实际凭据可能位于PKCS#12文件（具有.pfx扩展名）或硬件安全模块(HSM)中。 有关安全凭据的信息，请参阅*为应用程序服务器安装和部署AEM Forms*指南。

**保存已签名的PDF文档**

签名服务对PDF文档进行数字签名后，您可以将其另存为PDF文件，以便用户在Acrobat或Adobe Reader中打开它。

**另请参阅**

[使用Java API对PDF文档进行数字签名](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[使用Web服务API对PDF文档进行数字签名](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields)

[检索签名字段名称](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### 使用Java API对PDF文档进行数字签名 {#digitally-sign-pdf-documents-using-the-java-api}

使用签名API(Java)对PDF文档进行数字签名：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取要签名的PDF文档

   * 创建 `java.io.FileInputStream` 表示PDF文档的对象，该文档要使用其构造函数进行数字签名，并传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 签署PDF文档

   通过调用 `SignatureServiceClient` 对象 `sign` 方法和传递以下值：

   * A `com.adobe.idp.Document` 表示要签名的PDF文档的对象。
   * 表示将包含数字签名的签名字段名称的字符串值。
   * A `Credential` 表示用于对PDF文档进行数字签名的凭据的对象。 创建 `Credential` 对象 `Credential` 对象的静态 `getInstance` 方法和传递指定与安全凭据对应的别名值的字符串值。
   * A `HashAlgorithm` 指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个字符串值，表示PDF文档进行数字签名的原因。
   * 表示签名者联系信息的字符串值。
   * A `PDFSignatureAppearanceOptions` 用于控制数字签名外观的对象。 例如，您可以使用此对象向数字签名添加自定义徽标。
   * A `java.lang.Boolean` 指定是否对签名者的证书执行吊销检查的对象。
   * 安 `OCSPOptionSpec` 用于存储联机证书状态协议(OCSP)支持首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 此参数是可选的，可以是 `null`. 有关更多信息，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   的 `sign` 方法返回 `com.adobe.idp.Document` 表示签名PDF文档的对象。

1. 保存已签名的PDF文档

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp.Document` 对象 `copyToFile` 方法和传递 `java.io.File`复制 `Document` 对象。 确保使用 `com.adobe.idp.Document` 由返回的对象 `sign` 方法。

**另请参阅**

[数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[快速入门（SOAP模式）：使用Java API对PDF文档进行数字签名](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API对PDF文档进行数字签名 {#digitally-signing-pdf-documents-using-the-web-service-api}

要使用签名API（Web服务）对PDF文档进行数字签名，请执行以下操作：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取要签名的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储已签名的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示要签名的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。

1. 签署PDF文档

   通过调用 `SignatureServiceClient` 对象 `sign` 方法和传递以下值：

   * A `BLOB` 表示要签名的PDF文档的对象。
   * 表示将包含数字签名的签名字段名称的字符串值。
   * A `Credential` 表示用于对PDF文档进行数字签名的凭据的对象。 创建 `Credential` 对象，并通过为别名分配值来指定别名 `Credential` 对象 `alias` 属性。
   * A `HashAlgorithm` 指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个布尔值，用于指定是否使用哈希算法。
   * 一个字符串值，表示PDF文档进行数字签名的原因。
   * 表示签名者位置的字符串值。
   * 表示签名者联系信息的字符串值。
   * A `PDFSignatureAppearanceOptions` 用于控制数字签名外观的对象。 例如，您可以使用此对象向数字签名添加自定义徽标。
   * A `System.Boolean` 指定是否对签名者的证书执行吊销检查的对象。 如果此撤销检查已完成，则会将其嵌入签名中。 默认为 `false`。
   * 安 `OCSPOptionSpec` 用于存储联机证书状态协议(OCSP)支持首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`. 有关此对象的信息，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 此参数是可选的，可以是 `null`.

   的 `sign` 方法返回 `BLOB` 表示签名PDF文档的对象。

1. 保存已签名的PDF文档

   * 创建 `System.IO.FileStream` 对象。 传递一个字符串值，该值表示已签名PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 由返回的对象 `sign` 方法。 通过获取 `BLOB` 对象 `MTOM` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 以数字方式签名交互式Forms {#digitally-signing-interactive-forms}

您可以签署由Forms服务创建的交互式表单。 例如，请考虑以下工作流：

* 您可以合并基于XFA的PDF表单（使用Designer创建），以及使用Forms服务将表单数据（位于XML文档中）。 Forms服务器呈现交互式表单。
* 您可以使用签名服务API对交互式表单进行签名。

结果会生成一个数字签名的交互式PDF表单。 对基于XFA表单的PDF表单进行签名时，请确保将PDF文件另存为Adobe静态PDF表单。 如果尝试对另存为PDF动态PDF表单的Adobe表单进行签名，则会出现异常。 由于您正在对从Forms服务返回的表单进行签名，因此请确保表单包含签名字段。

>[!NOTE]
>
>在对交互式表单进行数字签名之前，必须确保将证书添加到AEM Forms。 证书是使用管理控制台添加的，或使用信任管理器API以编程方式添加的。 (请参阅 [使用信任管理器API导入凭据](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

使用Forms服务API时，将 `GenerateServerAppearance` 运行时选项 `true`. 此运行时选项可确保在Acrobat或Adobe Reader中打开时，服务器上生成的表单的外观仍然有效。 建议在使用Forms API生成要签名的交互式表单时设置此运行时选项。

>[!NOTE]
>
>在阅读交互式Forms的数字签名之前，建议您熟悉PDF文档的签名。 (请参阅 [数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### 步骤摘要 {#summary_of_steps-4}

要对Forms服务返回的交互式表单进行数字签名，请执行以下任务：

1. 包括项目文件。
1. 创建Forms和签名客户端。
1. 使用Forms服务获取交互式表单。
1. 签署交互式表单。
1. 将签名的PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建Forms和签名客户端**

由于此工作流同时调用Forms和签名服务，因此请同时创建Forms服务客户端和签名服务客户端。

**使用Forms服务获取交互式表单**

您可以使用Forms服务获取要签名的交互式PDF表单。 从AEM Forms开始，您可以通过 `com.adobe.idp.Document` 对象到包含要呈现的表单的Forms服务。 此方法的名称为 `renderPDFForm2`. 此方法将返回 `com.adobe.idp.Document` 包含要签名的表单的对象。 你可以通过这个 `com.adobe.idp.Document` 实例添加到签名服务。

同样，如果您使用的是Web服务，则可以将 `BLOB` Forms服务返回到签名服务的实例。

>[!NOTE]
>
>与交互式Forms的数字签名关联的快速入门部分会调用 `renderPDFForm2` 方法。

**对交互式表单进行签名**

在对PDF文档进行签名时，您可以设置签名服务使用的运行时选项。 您可以设置以下选项：

* 外观选项
* 吊销检查
* 时间戳值

使用 `PDFSignatureAppearanceOptionSpec` 对象。 例如，您可以通过调用 `PDFSignatureAppearanceOptionSpec` 对象 `setShowDate` 方法和传递 `true`.

**保存已签名的PDF文档**

签名服务对PDF文档进行数字签名后，您可以将其另存为PDF文件。 PDF文件可在Acrobat或Adobe Reader中打开。

**另请参阅**

[使用Java API对交互式表单进行数字签名](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[使用Web服务API对交互式表单进行数字签名](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[数字签名PDF文档](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[呈现交互式PDF forms](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### 使用Java API对交互式表单进行数字签名 {#digitally-sign-an-interactive-form-using-the-java-api}

使用Forms和签名API(Java)对交互式表单进行数字签名：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar和adobe-forms-client.jar。

1. 创建Forms和签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。
   * 创建 `FormsServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 使用Forms服务获取交互式表单

   * 创建 `java.io.FileInputStream` 表示要使用其构造函数传递到Forms服务的PDF文档的对象。 传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。
   * 创建 `java.io.FileInputStream` 表示包含要使用其构造函数传递到Forms服务的表单数据的XML文档的对象。 传递指定XML文件位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。
   * 创建 `PDFFormRenderSpec` 用于设置运行时选项的对象。 调用 `PDFFormRenderSpec` 对象 `setGenerateServerAppearance` 方法和传递 `true`.
   * 调用 `FormsServiceClient` 对象 `renderPDFForm2` 方法并传递以下值：

      * A `com.adobe.idp.Document` 包含要呈现的PDF表单的对象。
      * A `com.adobe.idp.Document` 包含要与表单合并的数据的对象。
      * A `PDFFormRenderSpec` 用于存储运行时选项的对象。
      * A `URLSpec` 包含Forms服务所需URI值的对象。 您可以指定 `null` 的值。
      * A `java.util.HashMap` 用于存储文件附件的对象。 这是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。

      的 `renderPDFForm2` 方法返回 `FormsResult` 包含表单数据流的对象

   * 通过调用 `FormsResult` 对象 `getOutputContent` 方法。 此方法将返回 `com.adobe.idp.Document` 表示交互式表单的对象。


1. 对交互式表单进行签名

   通过调用 `SignatureServiceClient` 对象 `sign` 方法和传递以下值：

   * A `com.adobe.idp.Document` 表示要签名的PDF文档的对象。 确保此对象为 `com.adobe.idp.Document` 从Forms服务获取的对象。
   * 表示已签名的签名字段名称的字符串值。
   * A `Credential` 表示用于对PDF文档进行数字签名的凭据的对象。 创建 `Credential` 对象 `Credential` 对象的静态 `getInstance` 方法。 传递一个字符串值，以指定与安全凭据对应的别名值。
   * A `HashAlgorithm` 指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个字符串值，表示PDF文档进行数字签名的原因。
   * 表示签名者联系信息的字符串值。
   * A `PDFSignatureAppearanceOptions` 用于控制数字签名外观的对象。 例如，您可以使用此对象向数字签名添加自定义徽标。
   * A `java.lang.Boolean` 指定是否对签名者的证书执行吊销检查的对象。
   * 安 `OCSPPreferences` 用于存储联机证书状态协议(OCSP)支持首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 此参数是可选的，可以是 `null`.

   的 `sign` 方法返回 `com.adobe.idp.Document` 表示签名PDF文档的对象。

1. 保存已签名的PDF文档

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp.Document` 对象 `copyToFile` 方法和传递 `java.io.File`复制 `Document` 对象。 确保使用 `com.adobe.idp.Document` 对象 `sign` 方法返回。

**另请参阅**

[以数字方式签名交互式Forms](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[快速入门（SOAP模式）：使用Java API对PDF文档进行数字签名](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API对交互式表单进行数字签名 {#digitally-sign-an-interactive-form-using-the-web-service-api}

使用Forms和签名API（Web服务）对交互式表单进行数字签名：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 由于此客户端应用程序调用两个AEM Forms服务，因此请创建两个服务引用。 对与签名服务关联的服务引用使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   对与Forms服务关联的服务引用使用以下WSDL定义： `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   因为 `BLOB` 数据类型对于两个服务引用都是通用的，可完全限定 `BLOB` 数据类型。 在相应的Web服务快速启动中， `BLOB` 实例完全限定。

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建Forms和签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >为Forms服务客户端重复这些步骤。

1. 使用Forms服务获取交互式表单

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储已签名的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示要签名的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。
   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储表单数据。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示包含表单数据的XML文件的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。
   * 创建 `PDFFormRenderSpec` 用于设置运行时选项的对象。 分配值 `true` 到 `PDFFormRenderSpec` 对象 `generateServerAppearance` 字段。
   * 调用 `FormsServiceClient` 对象 `renderPDFForm2` 方法并传递以下值：

      * A `BLOB` 包含要呈现的PDF表单的对象。
      * A `BLOB` 包含要与表单合并的数据的对象。
      * A `PDFFormRenderSpec` 用于存储运行时选项的对象。
      * A `URLSpec` 包含Forms服务所需URI值的对象。 您可以指定 `null` 的值。
      * A `java.util.HashMap` 用于存储文件附件的对象。 这是一个可选参数，您可以指定 `null` 如果您不想将文件附加到表单。
      * 用于存储表单中页数的长输出参数。
      * 用于区域设置值的字符串输出参数。
      * A `FormResult` 用于存储交互式表单的输出参数的值。
   * 通过调用 `FormsResult` 对象 `outputContent` 字段。 此字段存储 `BLOB` 表示交互式表单的对象。


1. 对交互式表单进行签名

   通过调用 `SignatureServiceClient` 对象 `sign` 方法和传递以下值：

   * A `BLOB` 表示要签名的PDF文档的对象。 使用 `BLOB` 由Forms服务返回的实例。
   * 表示已签名的签名字段名称的字符串值。
   * A `Credential` 表示用于对PDF文档进行数字签名的凭据的对象。 创建 `Credential` 对象，并通过为别名分配值来指定别名 `Credential` 对象 `alias` 属性。
   * A `HashAlgorithm` 指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个布尔值，用于指定是否使用哈希算法。
   * 一个字符串值，表示PDF文档进行数字签名的原因。
   * 表示签名者位置的字符串值。
   * 表示签名者联系信息的字符串值。
   * A `PDFSignatureAppearanceOptions` 用于控制数字签名外观的对象。 例如，您可以使用此对象向数字签名添加自定义徽标。
   * A `System.Boolean` 指定是否对签名者的证书执行吊销检查的对象。 如果此撤销检查已完成，则会将其嵌入签名中。 默认为 `false`。
   * 安 `OCSPPreferences` 用于存储联机证书状态协议(OCSP)支持首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`. 有关此对象的信息，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 此参数是可选的，可以是 `null`.

   的 `sign` 方法返回 `BLOB` 表示签名PDF文档的对象。

1. 保存已签名的PDF文档

   * 创建 `System.IO.FileStream` 对象。 传递一个字符串值，该值表示已签名PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 由返回的对象 `sign` 方法。 通过获取 `BLOB` 对象 `MTOM` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[以数字方式签名交互式Forms](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## 认证PDF文档 {#certifying-pdf-documents}

您可以通过使用称为认证签名的特定类型的签名来验证PDF文档，从而保护文档的安全。 认证签名与数字签名在以下方面有所区别：

* 它必须是应用于PDF文档的第一个签名；也就是说，在应用经认证的签名时，文档中的任何其他签名字段都必须是无符号的。 在PDF文档中只允许一个经认证的签名。 如果要对PDF文档进行签名和认证，则必须在对其签名之前对其进行认证。 验证PDF文档后，您可以对其他签名字段进行数字签名。
* 文档的作者或创作者可以指定文档可以以某些方式修改，而不会使经认证的签名失效。 例如，文档可以允许填写表单或注释。 如果作者指定不允许进行某种修改，则Acrobat会限制用户以这种方式修改文档。 如果进行了此类修改（如使用其他应用程序），则经认证的签名无效，当用户打开文档时，Acrobat会发出警告。 （如果签名未经认证，则不会阻止修改，且常规编辑操作不会使原始签名失效。）
* 在签名时，将扫描文档以查找可能使文档内容含糊或具有误导性的特定类型的内容。 例如，注释可能会模糊页面上一些对于了解正在认证的内容非常重要的文本。 可以对此类内容提供说明（法律证明）。

您可以使用签名服务Java API或签名Web服务API以编程方式验证PDF文档。 验证PDF文档时，必须引用凭据服务中存在的安全凭据。 有关安全凭据的信息，请参阅 *安装和部署AEM Forms* 应用程序服务器指南。

>[!NOTE]
>
>在验证和签署同一PDF文档时，如果认证签名不受信任，则当您在Acrobat或Adobe Reader中打开PDF文档时，第一个签名旁边会显示一个黄色三角形。 必须信任认证签名才能避免这种情况。

>[!NOTE]
>
>使用nCipher nShield HSM凭据对PDF文档进行签名或认证时，新凭据只有在部署了AEM Forms的J2EE应用程序服务器重新启动后才能使用。 但是，您可以设置一个配置值，从而在不重新启动J2EE应用程序服务器的情况下使用符号或验证操作。

您可以在cknfastrc文件中添加以下配置值，该文件位于/opt/nfast/cknfastrc(或c:\nfast\cknfastrc):

```as3
             CKNFAST_ASSUME_SINGLE_PROCESS=0
```

将此配置值添加到cknfastrc文件后，无需重新启动J2EE应用程序服务器即可使用新凭据。

>[!NOTE]
>
>有关签名服务和文档验证的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary_of_steps-5}

要验证PDF文档，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取PDF文档以进行认证。
1. 验证PDF文档。
1. 将认证的PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名操作之前，必须创建签名客户端。

**获取PDF文档以进行认证**

要验证PDF文档，必须获取包含签名字段的PDF文档。 如果PDF文档不包含签名字段，则无法对其进行认证。 可以使用Designer或以编程方式添加签名字段。 有关以编程方式添加签名字段的信息，请参阅 [添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields).

**验证PDF文档**

要成功验证PDF文档，您需要签名服务使用的以下输入值来验证PDF文档：

* **PDF文档**:包含签名字段的PDF文档，该字段是包含经认证签名的图形表示的表单字段。 PDF文档必须包含签名字段才能进行认证。 可以使用Designer或以编程方式添加签名字段。 (请参阅 [添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **签名字段名称**:经认证的签名字段的完全限定名称。 以下值是一个示例： `form1[0].#subform[1].SignatureField3[3]`. 使用XFA表单字段时，还可以使用签名字段的部分名称： `SignatureField3[3]`. 如果为字段名称传递了空值，则会动态创建并验证不可见的签名字段。
* **安全凭据**:用于验证PDF文档的凭据。 此安全凭据包含密码和别名，该密码和别名必须与位于凭据服务内的凭据中显示的别名相匹配。 别名是对实际凭据的引用，实际凭据可能位于PKCS#12文件（具有.pfx扩展名）或硬件安全模块(HSM)中。
* **哈希算法**:用于摘要PDF文档的哈希算法。
* **签名原因**:一个值，显示在Acrobat或Adobe Reader中，以便其他用户了解PDF文档获得认证的原因。
* **签名者的位置**:由凭据指定的签名者的位置。
* **联系信息**:签名者的联系信息，如地址和电话号码。
* **权限信息**:控制最终用户可对文档执行的操作的权限，而不会导致认证签名无效。 例如，您可以设置权限，以便对PDF文档进行任何更改都会导致认证的签名无效。
* **法律解释**:文档经认证后，会自动扫描特定类型的内容，这些内容可能会使文档的内容含糊或具有误导性。 例如，注释可能会模糊页面上一些对于了解正在认证的内容非常重要的文本。 扫描过程会生成有关这些类型内容的警告。 此值对可能生成警告的内容提供了额外说明。
* **外观选项**:控制认证签名外观的选项。 例如，认证签名可显示日期信息。
* **吊销检查**:此值指定是否对签名者的证书执行吊销检查。 默认设置为 `false` 表示未完成吊销检查。
* **OCSP设置**:联机证书状态协议(OCSP)支持的设置，该设置提供有关用于验证PDF文档的凭据状态的信息。 例如，您可以指定服务器的URL，以提供有关您用于登录到PDF文档的凭据的信息。
* **CRL设置**:完成吊销检查时，证书吊销列表(CRL)首选项的设置。 例如，您可以指定始终检查凭据是否已吊销。
* **时间戳**:定义应用于认证签名的时间戳信息的设置。 时间戳表示特定数据是在特定时间之前建立的。 此知识有助于在签名者和验证者之间建立信任关系。

**将认证的PDF文档另存为PDF文件**

在签名服务对PDF文档进行认证后，您可以将其另存为PDF文件，以便用户在Acrobat或Adobe Reader中打开它。

**另请参阅**

[使用Java API验证PDF文档](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[使用Web服务API验证PDF文档](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields)

### 使用Java API验证PDF文档 {#certify-pdf-documents-using-the-java-api}

使用签名API(Java)验证PDF文档：

1. 包含项目文件

   将客户端JAR文件（如adobe-signatures-client.jar）包含在您Java项目的类路径中。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取PDF文档以进行认证

   * 创建 `java.io.FileInputStream` 表示PDF文档的对象，该文档将使用其构造函数并传递指定PDF文档位置的字符串值进行验证。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 验证PDF文档

   通过调用 `SignatureServiceClient` 对象 `certify` 方法和传递以下值：

   * 的 `com.adobe.idp.Document` 表示要认证的PDF文档的对象。
   * 表示将包含签名的签名字段名称的字符串值。
   * A `Credential` 表示用于验证PDF文档的凭据的对象。 创建 `Credential` 对象 `Credential` 对象的静态 `getInstance` 方法和传递指定与安全凭据对应的别名值的字符串值。
   * A `HashAlgorithm` 用于指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个字符串值，表示PDF文档被认证的原因。
   * 表示签名者联系信息的字符串值。
   * A `MDPPermissions` 对象，指定可对使签名失效的PDF文档执行的操作。
   * A `PDFSignatureAppearanceOptions` 控制认证签名外观的对象。 如果需要，可通过调用方法(例如 `setShowDate`.
   * 一个字符串值，用于解释使签名失效的操作。
   * A `java.lang.Boolean` 指定是否对签名者的证书执行吊销检查的对象。 如果此撤销检查已完成，则会将其嵌入签名中。 默认为 `false`。
   * A `java.lang.Boolean` 用于指定是否锁定正在认证的签名字段的对象。 如果字段已锁定，则签名字段将标记为只读，其属性将无法修改，并且没有所需权限的任何人都无法清除该字段。 默认为 `false`。
   * 安 `OCSPPreferences` 用于存储联机证书状态协议(OCSP)支持首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`. 有关此对象的信息，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 例如，在您创建 `TSPPreferences` 对象，可以通过调用 `TSPPreferences` 对象 `setTspServerURL` 方法。 此参数是可选的，可以是 `null`. 有关更多信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

   的 `certify` 方法返回 `com.adobe.idp.Document` 表示认证的PDF文档的对象。

1. 将认证的PDF文档另存为PDF文件

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp.Document` 对象 `copyToFile` 复制内容的方法 `com.adobe.idp.Document` 对象。

**另请参阅**

[认证PDF文档](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[快速入门（SOAP模式）：使用Java API验证PDF文档](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API验证PDF文档 {#certify-pdf-documents-using-the-web-service-api}

使用签名API（Web服务）验证PDF文档：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取PDF文档以进行认证

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储经过认证的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示要认证的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法及传递要读取的字节数组、起始位置及流长度。
   * 填充 `BLOB` 通过指定对象 `MTOM` 数据成员字节数组的内容。

1. 验证PDF文档

   通过调用 `SignatureServiceClient` 对象 `certify` 方法和传递以下值：

   * 的 `BLOB` 表示要认证的PDF文档的对象。
   * 表示将包含签名的签名字段名称的字符串值。
   * A `Credential` 表示用于验证PDF文档的凭据的对象。 创建 `Credential` 对象，并通过为别名分配值来指定别名 `Credential` 对象 `alias` 属性。
   * A `HashAlgorithm` 用于指定静态数据成员的对象，该静态数据成员表示用于摘要PDF文档的哈希算法。 例如，您可以指定 `HashAlgorithm.SHA1` 以使用SHA1算法。
   * 一个布尔值，用于指定是否使用哈希算法。
   * 一个字符串值，表示PDF文档被认证的原因。
   * 表示签名者位置的字符串值。
   * 表示签名者联系信息的字符串值。
   * 安 `MDPPermissions` 对象的静态数据成员，用于指定可对使签名失效的PDF文档执行的操作。
   * 一个布尔值，用于指定是否使用 `MDPPermissions` 作为上一个参数值传递的对象。
   * 一个字符串值，用于解释使签名失效的操作。
   * A `PDFSignatureAppearanceOptions` 控制认证签名外观的对象。 创建 `PDFSignatureAppearanceOptions` 对象。 您可以通过设置签名的一个数据成员来修改其外观。
   * A `System.Boolean` 指定是否对签名者的证书执行吊销检查的对象。 如果此撤销检查已完成，则会将其嵌入签名中。 默认为 `false`。
   * A `System.Boolean` 用于指定是否锁定正在认证的签名字段的对象。 如果字段已锁定，则签名字段将标记为只读，其属性将无法修改，并且没有所需权限的任何人都无法清除该字段。 默认为 `false`。
   * A `System.Boolean` 指定签名字段是否已锁定的对象。 也就是说，如果你通过 `true` 转到上一个参数，然后传递 `true` 到此参数。
   * 安 `OCSPPreferences` 用于存储在线证书状态协议(OCSP)支持首选项的对象，该首选项提供有关用于验证PDF文档的凭据状态的信息。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `CRLPreferences` 存储证书吊销列表(CRL)首选项的对象。 如果未完成吊销检查，则不使用此参数，您可以指定 `null`.
   * A `TSPPreferences` 用于存储时间戳提供程序(TSP)支持首选项的对象。 例如，在您创建 `TSPPreferences` 对象，则可以通过设置 `TSPPreferences` 对象 `tspServerURL` 数据成员。 此参数是可选的，可以是 `null`.

   的 `certify` 方法返回 `BLOB` 表示认证的PDF文档的对象。

1. 将认证的PDF文档另存为PDF文件

   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示将包含经认证的PDF文档的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 由返回的对象 `certify` 方法。 通过获取 `BLOB` 对象 `binaryData` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[认证PDF文档](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 验证数字签名 {#verifying-digital-signatures}

可以验证数字签名以确保签名的PDF文档未被修改且数字签名有效。 验证数字签名时，您可以检查签名的状态和签名的属性，如签名者的身份。 在信任数字签名之前，建议您验证数字签名。 验证数字签名时，请引用包含数字签名的PDF文档。

假设签名者的身份未知。 在Acrobat中打开PDF文档时，会出现一条警告消息，指出签名者的身份未知，如下图所示。

![vd_vd_verifsig](assets/vd_vd_verifysig.png)

同样，当您以编程方式验证数字签名时，您可以确定签名者身份的状态。 例如，如果验证上图所示文档中的数字签名，则结果是签名者的身份未知。

>[!NOTE]
>
>有关签名服务和验证数字签名的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary_of_steps-6}

要验证数字签名，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取包含要验证的签名的PDF文档。
1. 设置PKI运行时选项。
1. 验证数字签名。
1. 确定签名的状态。
1. 确定签名者的身份。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名服务操作之前，请创建签名服务客户端。

**获取包含要验证的签名的PDF文档**

要验证用于对PDF文档进行数字签名或认证的签名，请获取包含签名的PDF文档。

**设置PKI运行时选项**

设置签名服务在PDF文档中验证签名时使用的以下PKI运行时选项：

* 验证时间
* 吊销检查
* 时间戳值

在设置这些选项时，您可以指定验证时间。 例如，您可以选择当前时间（验证器计算机上的时间），该时间指示使用当前时间。 有关不同时间值的信息，请参阅 `VerificationTime` 枚举值 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

您还可以指定是否在验证过程中执行吊销检查。 例如，您可以执行吊销检查以确定证书是否被吊销。 有关吊销检查选项的信息，请参阅 `RevocationCheckStyle` 枚举值 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

要对证书执行吊销检查，请使用 `CRLOptionSpec` 对象。 但是，如果您没有指定到CRL服务器的URL，签名服务将从证书中获取该URL。

在执行撤销检查时，您可以使用联机证书状态协议(OCSP)服务器，而不是使用CRL服务器。 通常，与CRL服务器相比，使用OCSP服务器时，撤销检查的执行速度会更快。 (请参阅 [联机证书状态协议](https://tools.ietf.org/html/rfc2560).)

您可以使用Adobe应用程序和服务设置签名服务使用的CRL和OCSP服务器顺序。 例如，如果首先在Adobe应用程序和服务中设置OCSP服务器，则检查OCSP服务器，然后检查CRL服务器。

如果不执行吊销检查，则签名服务不检查证书是否被吊销。 即，忽略CRL和OCSP服务器信息。

>[!NOTE]
>
>您可以使用 `CRLOptionSpec` 和 `OCSPOptionSpec` 对象。 例如，要覆盖CRL服务器，可以调用 `CRLOptionSpec` 对象 `setLocalURI` 方法。

时间戳是跟踪修改已签名或已验证文档的时间的过程。 文档签名后，任何人都无法修改它。 时间戳有助于加强已签名或已认证文档的有效性。 您可以使用 `TSPOptionSpec` 对象。 例如，您可以指定时间戳提供程序(TSP)服务器的URL。

>[!NOTE]
>
>在Java和Web服务快速启动中，验证时间设置为 `VerificationTime.CURRENT_TIME` 和吊销检查设置为 `RevocationCheckStyle.BestEffort`. 由于未指定CRL或OCSP服务器信息，因此从证书中获取服务器信息。

**验证数字签名**

要成功验证签名，请指定包含签名的签名字段的完全限定名称，如 `form1[0].#subform[1].SignatureField3[3]`. 使用XFA表单字段时，您还可以使用签名字段的部分名称： `SignatureField3`.

默认情况下，签名服务将文档在验证后可签名的时间限制为65分钟。 如果用户尝试在当前时间验证签名，并且签名时间晚于当前时间并且在65分钟内，则签名服务不会创建验证错误。

>[!NOTE]
>
>有关验证签名时需要的其他值，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**确定签名的状态**

在验证数字签名时，您可以检查签名的状态。

**确定签名者的身份**

您可以确定签名者的身份，该身份可以是以下值之一：

* **未知**:此签名者未知，因为无法执行签名者验证。
* **受信任**:此签名者是可信的。
* **不受信任**:此签名者不可信。

**另请参阅**

[使用Java API验证数字签名](#unresolvedlink-lc-si)

[使用Web服务API验证数字签名](#unresolvedlink-lc-si)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Java API验证数字签名 {#verify-digital-signatures-using-the-java-api}

使用签名服务API(Java)验证数字签名：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar。

1. [创建签名客户端](#unresolvedlink-lc-si)

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取包含要验证的签名的PDF文档

   * 创建 `java.io.FileInputStream` 表示包含要使用其构造函数验证的签名的PDF文档的对象。 传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 设置PKI运行时选项

   * 创建 `PKIOptions` 对象。
   * 通过调用 `PKIOptions` 对象 `setVerificationTime` 方法和通过 `VerificationTime` 指定验证时间的枚举值。
   * 通过调用设置吊销检查选项 `PKIOptions` 对象 `setRevocationCheckStyle` 方法和通过 `RevocationCheckStyle` 指定是否执行吊销检查的枚举值。

1. 验证数字签名

   通过调用 `SignatureServiceClient` 对象 `verify2` 方法和传递以下值：

   * A `com.adobe.idp.Document` 包含经过数字签名或认证的PDF文档的对象。
   * 表示包含要验证的签名的签名字段名称的字符串值。
   * A `PKIOptions` 包含PKI运行时选项的对象。
   * A `VerifySPIOptions` 包含SPI信息的实例。 您可以指定 `null` 的值。

   的 `verify2` 方法返回 `PDFSignatureVerificationInfo` 包含可用于验证数字签名的信息的对象。

1. 确定签名的状态

   * 通过调用 `PDFSignatureVerificationInfo` 对象 `getStatus` 方法。 此方法将返回 `SignatureStatus` 指定签名状态的对象。 例如，如果未修改已签名的PDF文档，此方法将返回 `SignatureStatus.DocumentSigNoChanges`.

1. 确定签名者的身份

   * 通过调用 `PDFSignatureVerificationInfo` 对象 `getSigner` 方法。 此方法将返回 `IdentityInformation` 对象。
   * 调用 `IdentityInformation` 对象 `getStatus` 确定签名者身份的方法。 此方法将返回 `IdentityStatus` 指定标识的枚举值。 例如，如果签名者受信任，此方法将返回 `IdentityStatus.TRUSTED`.

**另请参阅**

[验证数字签名](#unresolvedlink-lc-si)

[快速入门（SOAP模式）：使用Java API验证数字签名](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API验证数字签名 {#verify-digital-signatures-using-the-web-service-api}

使用签名服务API（Web服务）验证数字签名：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取包含要验证的签名的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储包含要验证的数字或认证签名的PDF文档。
   * 创建 `System.IO.FileStream` 对象。 传递一个字符串值，该值表示已签名PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法。 传递字节数组、开始位置和流长度以读取。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。

1. 设置PKI运行时选项

   * 创建 `PKIOptions` 对象。
   * 通过分配 `PKIOptions` 对象 `verificationTime` 数据成员a `VerificationTime` 指定验证时间的枚举值。
   * 通过分配 `PKIOptions` 对象 `revocationCheckStyle` 数据成员a `RevocationCheckStyle` 指定是否执行吊销检查的枚举值。

1. 验证数字签名

   通过调用 `SignatureServiceClient` 对象 `verify2` 方法和传递以下值：

   * 的 `BLOB` 包含经过数字签名或认证的PDF文档的对象。
   * 表示包含要验证的签名的签名字段名称的字符串值。
   * A `PKIOptions` 包含PKI运行时选项的对象。
   * A `VerifySPIOptions` 包含SPI信息的实例。 您可以指定 `null` 的值。

   的 `verify2` 方法返回 `PDFSignatureVerificationInfo` 包含可用于验证数字签名的信息的对象。

1. 确定签名的状态

   通过获取 `PDFSignatureVerificationInfo` 对象 `status` 数据成员。 此数据成员存储 `SignatureStatus` 指定签名状态的对象。 例如，如果修改了已签名的PDF文档，则 `status` 数据成员存储值 `SignatureStatus.DocumentSigNoChanges`.

1. 确定签名者的身份

   * 通过检索 `PDFSignatureVerificationInfo` 对象 `signer` 数据成员。 此成员返回 `IdentityInformation` 对象。
   * 检索 `IdentityInformation` 对象 `status` 确定签名者身份的数据成员。 此数据成员返回 `IdentityStatus` 指定标识的枚举值。 例如，如果签名者受信任，则此成员将返回 `IdentityStatus.TRUSTED`.

**另请参阅**

[验证数字签名](#unresolvedlink-lc-si)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 验证多个数字签名 {#verifying-multiple-digital-signatures}

AEM Forms提供了验证位于PDF文档中的所有数字签名的方法。 假设PDF文档包含多个数字签名，因为业务流程需要多个签名者的签名。 例如，假设一项金融交易要求贷款官员和经理签名。 您可以使用签名服务Java API或Web服务API来验证PDF文档中的所有签名。 验证多个数字签名时，您可以检查每个签名的状态和属性。 在您信任数字签名之前，建议您对其进行验证。 建议您熟悉验证单个数字签名。

>[!NOTE]
>
>有关签名服务和验证数字签名的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary_of_steps-7}

要验证多个数字签名，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取包含要验证的签名的PDF文档。
1. 设置PKI运行时选项。
1. 检索所有数字签名。
1. 遍历所有签名。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名服务操作之前，请创建签名服务客户端。

**获取包含要验证的签名的PDF文档**

要验证用于对PDF文档进行数字签名或认证的签名，请获取包含签名的PDF文档。

**设置PKI运行时选项**

设置签名服务在验证PDF文档中的所有签名时使用的以下PKI运行时选项：

* 验证时间
* 吊销检查
* 时间戳值

在设置这些选项时，您可以指定验证时间。 例如，您可以选择当前时间（验证器计算机上的时间），该时间指示使用当前时间。 有关不同时间值的信息，请参阅 `VerificationTime` 枚举值 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

您还可以指定是否在验证过程中执行吊销检查。 例如，您可以执行吊销检查以确定证书是否被吊销。 有关吊销检查选项的信息，请参阅 `RevocationCheckStyle` 枚举值 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

要对证书执行吊销检查，请使用 `CRLOptionSpec` 对象。 但是，如果您没有指定指向CRL服务器的URL，则签名服务将从证书中获取该URL。

在执行撤销检查时，您可以使用联机证书状态协议(OCSP)服务器，而不是使用CRL服务器。 通常，使用OCSP服务器而不是CRL服务器时，执行撤销检查的速度会更快。 (请参阅 [联机证书状态协议](https://tools.ietf.org/html/rfc2560).)

您可以使用Adobe应用程序和服务设置签名服务使用的CRL和OCSP服务器顺序。 例如，如果OCSP服务器是在Adobe应用程序和服务中首先设置的，则检查OCSP服务器，然后检查CRL服务器。

如果不执行吊销检查，则签名服务不检查证书是否被吊销。 即，忽略CRL和OCSP服务器信息。

>[!NOTE]
>
>您可以使用 `CRLOptionSpec` 和 `OCSPOptionSpec` 对象。 例如，要覆盖CRL服务器，可以调用 `CRLOptionSpec` 对象 `setLocalURI` 方法。

时间戳是跟踪修改已签名或已验证文档的时间的过程。 文档签名后，任何人都无法修改它。 时间戳有助于加强已签名或已认证文档的有效性。 您可以使用 `TSPOptionSpec` 对象。 例如，您可以指定时间戳提供程序(TSP)服务器的URL。

>[!NOTE]
>
>在Java和Web服务快速启动中，验证时间设置为 `VerificationTime.CURRENT_TIME` 和吊销检查设置为 `RevocationCheckStyle.BestEffort`. 由于未指定CRL或OCSP服务器信息，因此从证书中获取服务器信息。

**检索所有数字签名**

要验证位于PDF文档中的所有数字签名，请从PDF文档中检索数字签名。 所有签名都将在列表中返回。 在验证数字签名时，请检查签名的状态。

>[!NOTE]
>
>与验证单个数字签名不同，验证多个签名时，您无需指定签名字段名称。

**遍历所有签名**

遍历每个签名。 即，对于每个签名，验证数字签名，并检查签名者的身份和每个签名的状态。 (请参阅 [验证数字签名](#unresolvedlink-lc-si).)

>[!NOTE]
>
>如果要求是整个文档，则无需遍历所有签名。

**另请参阅**

[使用Java API验证多个数字签名](#unresolvedlink-lc-si)

[使用Web服务API验证多个数字签名](#unresolvedlink-lc-si)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Java API验证多个数字签名 {#verify-multiple-digital-signatures-using-the-java-api}

使用签名服务API(Java)验证多个数字签名：

1. 包含项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-signatures-client.jar。

1. 创建签名客户端

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取包含要验证的签名的PDF文档

   * 创建 `java.io.FileInputStream` 表示包含多个数字签名的PDF文档的对象，要使用其构造函数进行验证。 传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 设置PKI运行时选项

   * 创建 `PKIOptions` 对象。
   * 通过调用 `PKIOptions` 对象 `setVerificationTime` 方法和通过 `VerificationTime` 指定验证时间的枚举值。
   * 通过调用设置吊销检查选项 `PKIOptions` 对象 `setRevocationCheckStyle` 方法和通过 `RevocationCheckStyle` 指定是否执行吊销检查的枚举值。

1. 检索所有数字签名

   调用 `SignatureServiceClient` 对象 `verifyPDFDocument` 方法并传递以下值：

   * A `com.adobe.idp.Document` 包含包含多个数字签名的PDF文档的对象。
   * A `PKIOptions` 包含PKI运行时选项的对象。
   * A `VerifySPIOptions` 包含SPI信息的实例。 您可以指定 `null` 的值。

   的 `verifyPDFDocument` 方法返回 `PDFDocumentVerificationInfo` 包含有关位于PDF文档中的所有数字签名的信息的对象。

1. 遍历所有签名

   * 通过调用 `PDFDocumentVerificationInfo` 对象 `getVerificationInfos` 方法。 此方法将返回 `java.util.List` 每个元素为 `PDFSignatureVerificationInfo` 对象。 使用 `java.util.Iterator` 用于遍历签名列表的对象。
   * 使用 `PDFSignatureVerificationInfo` 对象中，您可以通过调用来执行诸如确定签名状态之类的任务 `PDFSignatureVerificationInfo` 对象 `getStatus` 方法。 此方法将返回 `SignatureStatus` 静态数据成员通知您签名状态的对象。 例如，如果签名未知，则此方法将返回 `SignatureStatus.DocumentSignatureUnknown`.

**另请参阅**

[验证多个数字签名](#unresolvedlink-lc-si)

[快速入门（SOAP模式）：使用Java API验证多个数字签名](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[验证数字签名](#unresolvedlink-lc-si)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API验证多个数字签名 {#verifying-multiple-digital-signatures-using-the-web-service-api}

使用签名服务API（Web服务）验证多个数字签名：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取包含要验证的签名的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象存储包含多个数字签名的PDF文档以进行验证。
   * 创建 `System.IO.FileStream` 对象。 传递一个字符串值，该值表示PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法。 传递字节数组、开始位置和流长度以读取。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性字节数组的内容。

1. 设置PKI运行时选项

   * 创建 `PKIOptions` 对象。
   * 通过分配 `PKIOptions` 对象 `verificationTime` 数据成员a `VerificationTime` 指定验证时间的枚举值。
   * 通过分配 `PKIOptions` 对象 `revocationCheckStyle` 数据成员a `RevocationCheckStyle` 指定是否执行吊销检查的枚举值。

1. 检索所有数字签名

   调用 `SignatureServiceClient` 对象 `verifyPDFDocument` 方法并传递以下值：

   * A `BLOB` 包含包含多个数字签名的PDF文档的对象。
   * A `PKIOptions` 包含PKI运行时选项的对象。
   * A `VerifySPIOptions` 包含SPI信息的实例。 可以为此参数指定null。

   的 `verifyPDFDocument` 方法返回 `PDFDocumentVerificationInfo` 包含有关位于PDF文档中的所有数字签名的信息的对象。

1. 遍历所有签名

   * 通过获取 `PDFDocumentVerificationInfo` 对象 `verificationInfos` 数据成员。 此数据成员返回 `Object` 每个元素都是 `PDFSignatureVerificationInfo` 对象。
   * 使用 `PDFSignatureVerificationInfo` 对象，您可以通过获取 `PDFSignatureVerificationInfo` 对象 `status` 数据成员。 此数据成员返回 `SignatureStatus` 静态数据成员通知您签名状态的对象。 例如，如果签名未知，则此方法将返回 `SignatureStatus.DocumentSignatureUnknown`.

**另请参阅**

[验证多个数字签名](#unresolvedlink-lc-si)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 删除数字签名 {#removing-digital-signatures}

必须先从签名字段中删除数字签名，然后才能应用较新的数字签名。 数字签名无法覆盖。 如果尝试将数字签名应用于包含签名的签名字段，则会出现异常。

>[!NOTE]
>
>有关签名服务的详细信息，请参阅 [AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

### 步骤摘要 {#summary_of_steps-8}

要从签名字段中删除数字签名，请执行以下任务：

1. 包括项目文件。
1. 创建签名客户端。
1. 获取包含要删除的签名的PDF文档。
1. 从签名字段中删除数字签名。
1. 将PDF文档另存为PDF文件。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(如果在JBoss上部署了AEM Forms，则此变量为必需变量)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建签名客户端**

在以编程方式执行签名服务操作之前，必须创建签名服务客户端。

**获取包含要删除的签名的PDF文档**

要从PDF文档中删除签名，必须获取包含签名的PDF文档。

**从签名字段中删除数字签名**

要成功从PDF文档中删除数字签名，必须指定包含数字签名的签名字段的名称。 此外，您必须拥有删除数字签名的权限；否则，会出现异常。

**将PDF文档另存为PDF文件**

在签名服务从签名字段中删除数字签名后，您可以将PDF文档另存为PDF文件，以便用户可以在Acrobat或Adobe Reader中打开它。

**另请参阅**

[使用Java API删除数字签名](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[使用Web服务API删除数字签名](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加签名字段](digitally-signing-certifying-documents.md#adding-signature-fields)

### 使用Java API删除数字签名 {#remove-digital-signatures-using-the-java-api}

使用签名API(Java)删除数字签名：

1. 包含项目文件

   将客户端JAR文件（如adobe-signatures-client.jar）包含在您Java项目的类路径中。

1. 创建签名客户端。

   * 创建 `ServiceClientFactory` 包含连接属性的对象。
   * 创建 `SignatureServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 对象。

1. 获取包含要删除的签名的PDF文档

   * 创建 `java.io.FileInputStream` 表示包含要删除的签名的PDF文档的对象，方法是使用其构造函数并传递指定PDF文档位置的字符串值。
   * 创建 `com.adobe.idp.Document` 对象，并使用其构造函数进行传递 `java.io.FileInputStream` 对象。

1. 从签名字段中删除数字签名

   通过调用 `SignatureServiceClient` 对象 `clearSignatureField` 方法和传递以下值：

   * A `com.adobe.idp.Document` 表示包含要删除的签名的PDF文档的对象。
   * 一个字符串值，用于指定包含数字签名的签名字段的名称。

   的 `clearSignatureField` 方法返回 `com.adobe.idp.Document` 表示从中删除数字签名的PDF文档的对象。

1. 将PDF文档另存为PDF文件

   * 创建 `java.io.File` 对象，并确保文件扩展名为.pdf。
   * 调用 `com.adobe.idp.Document` 对象 `copyToFile` 方法。 传递 `java.io.File` 对象，以复制 `com.adobe.idp.Document` 对象。 确保使用 `Document` 由返回的对象 `clearSignatureField` 方法。

**另请参阅**

[删除数字签名](digitally-signing-certifying-documents.md#removing-digital-signatures)

[快速入门（SOAP模式）：使用Java API删除数字签名](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API删除数字签名 {#remove-digital-signatures-using-the-web-service-api}

使用签名API（Web服务）删除数字签名：

1. 包含项目文件

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建签名客户端

   * 创建 `SignatureServiceClient` 对象。
   * 创建 `SignatureServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/SignatureService?WSDL`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。)
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `SignatureServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 获取包含要删除的签名的PDF文档

   * 创建 `BLOB` 对象。 的 `BLOB` 对象用于存储包含要删除的数字签名的PDF文档。
   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示已签名PDF文档的文件位置和打开文件的模式。
   * 创建用于存储 `System.IO.FileStream` 对象。 您可以通过获取 `System.IO.FileStream` 对象 `Length` 属性。
   * 通过调用 `System.IO.FileStream` 对象 `Read` 方法。 传递字节数组、开始位置和流长度以读取。
   * 填充 `BLOB` 通过指定对象 `MTOM` 属性。

1. 从签名字段中删除数字签名

   通过调用 `SignatureServiceClient` 对象 `clearSignatureField` 方法和传递以下值：

   * A `BLOB` 包含签名PDF文档的对象。
   * 表示包含要删除的数字签名的签名字段名称的字符串值。

   的 `clearSignatureField` 方法返回 `BLOB` 表示从中删除数字签名的PDF文档的对象。

1. 将PDF文档另存为PDF文件

   * 创建 `System.IO.FileStream` 对象，方法是调用其构造函数并传递一个字符串值，该字符串值表示包含空签名字段的PDF文档的文件位置以及打开文件的模式。
   * 创建用于存储 `BLOB` 由返回的对象 `sign` 方法。 通过获取 `BLOB` 对象 `MTOM` 数据成员。
   * 创建 `System.IO.BinaryWriter` 对象，方法是调用其构造函数并传递 `System.IO.FileStream` 对象。
   * 通过调用 `System.IO.BinaryWriter` 对象 `Write` 方法和传递字节数组。

**另请参阅**

[删除数字签名](digitally-signing-certifying-documents.md#removing-digital-signatures)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
