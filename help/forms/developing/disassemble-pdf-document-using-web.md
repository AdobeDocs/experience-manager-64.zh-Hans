---
title: 使用Web服务API反汇编PDF文档
seo-title: 使用Web服务API反汇编PDF文档
description: 'null'
seo-description: 'null'
uuid: d6283dc5-e333-49d0-abde-1d390662f4fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 49584fb4-8c3a-4d73-acd6-0879a67f6093
translation-type: tm+mt
source-git-commit: 529b8c6556a7179a9169ff8250af6b5dc1251ef3
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---


# 使用Web服务API反汇编PDF文档 {#disassemble-a-pdf-document-usingthe-web-service-api}

使用Assembler Service API（Web服务）反汇编PDF文档:

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 请确保在设置服务引用时使用以下WSDL定义： `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替 `localhost` 换为承载AEM Forms的服务器的IP地址。

1. 创建PDF Assembler客户端。

   * 使用对象 `AssemblerServiceClient` 的默认构造函数创建对象。
   * 使用构 `AssemblerServiceClient.Endpoint.Address` 造函数创建 `System.ServiceModel.EndpointAddress` 对象。 将指定WSDL的字符串值传递给AEM Forms服务(例如 `http://localhost:8080/soap/services/AssemblerService?blob=mtom`)。 您无需使用该属 `lc_version` 性。 此属性在您创建服务引用时使用。
   * 通过获 `System.ServiceModel.BasicHttpBinding` 取字段的值创建对 `AssemblerServiceClient.Endpoint.Binding` 象。 将返回值转换为 `BasicHttpBinding`。
   * 将对 `System.ServiceModel.BasicHttpBinding` 象的字段 `MessageEncoding` 设置为 `WSMessageEncoding.Mtom`。 此值确保使用MTOM。
   * 通过执行以下任务启用基本HTTP身份验证：

      * 为字段指定AEM表单用户名 `AssemblerServiceClient.ClientCredentials.UserName.UserName`。
      * 为字段分配相应的口令值 `AssemblerServiceClient.ClientCredentials.UserName.Password`。
      * 为字段指 `HttpClientCredentialType.Basic` 定常量值 `BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 为字段指 `BasicHttpSecurityMode.TransportCredentialOnly` 定常量值 `BasicHttpBindingSecurity.Security.Mode`。

1. 引用现有DDX文档。

   * 使用对 `BLOB` 象的构造函数创建对象。 该 `BLOB` 对象用于存储DDX文档。
   * 通过调 `System.IO.FileStream` 用对象的构造函数创建对象。 传递一个字符串值，它表示DDX文档的文件位置以及打开文件的模式。
   * 创建存储对象内容的字节数 `System.IO.FileStream` 组。 您可以通过获取对象的属性来确定字 `System.IO.FileStream` 节数组的大 `Length` 小。
   * 通过调用对象的方法并传递要读取的 `System.IO.FileStream` 字节数 `Read` 组、开始位置和流长度，用流数据填充字节数组。
   * 通过 `BLOB` 将对象属性 `MTOM` 赋予字节数组的内容来填充对象。

1. 参考PDF文档进行反汇编。

   * 使用对 `BLOB` 象的构造函数创建对象。 该 `BLOB` 对象用于存储输入的PDF文档。 此 `BLOB` 对象作为参 `invokeOneDocument` 数传递给。
   * 通过调 `System.IO.FileStream` 用对象的构造函数并传递一个字符串值来创建对象，该字符串值表示输入PDF文档的文件位置以及打开文件的模式。
   * 创建存储对象内容的字节数 `System.IO.FileStream` 组。 您可以通过获取对象的属性来确定字 `System.IO.FileStream` 节数组的大 `Length` 小。
   * 通过调用对象的方法并传递要读取的 `System.IO.FileStream` 字节数 `Read` 组、开始位置和流长度，用流数据填充字节数组。
   * 通过 `BLOB` 为对象字段指 `MTOM` 定字节数组的内容来填充对象。
   * 创建对 `MyMapOf_xsd_string_To_xsd_anyType` 象。 此集合对象用于存储要反汇编的PDF。
   * 创建对 `MyMapOf_xsd_string_To_xsd_anyType_Item` 象。
   * 为对象的字段指定表示键名 `MyMapOf_xsd_string_To_xsd_anyType_Item` 的字符串 `key` 值。 此值必须与在DDX文档中指定的PDF源元素值匹配。
   * 将存 `BLOB` 储PDF文档的对象指 `MyMapOf_xsd_string_To_xsd_anyType_Item` 定到对象的字 `value` 段。
   * 将对 `MyMapOf_xsd_string_To_xsd_anyType_Item` 象添加到对 `MyMapOf_xsd_string_To_xsd_anyType` 象。 调用对 `MyMapOf_xsd_string_To_xsd_anyType` 象的方 `Add` 法并传递对 `MyMapOf_xsd_string_To_xsd_anyType` 象。

1. 设置运行时选项。

   * 使用 `AssemblerOptionSpec` 其构造函数创建存储运行时选项的对象。
   * 通过为属于该对象的数据成员分配一个值，设置运行时选项以满足您的业务 `AssemblerOptionSpec` 要求。 例如，要指示Assembler服务在出现错误时继续处理作业，请 `false` 指定 `AssemblerOptionSpec` 对象的字 `failOnError` 段。

1. 反汇编PDF文档。

   调用对 `AssemblerServiceClient` 象的方 `invokeDDX` 法并传递以下值：

   * 表示 `BLOB` 分解PDF文档的DDX文档的对象
   * 包含 `MyMapOf_xsd_string_To_xsd_anyType` 要反汇编的PDF文档的对象
   * 指定 `AssemblerOptionSpec` 运行时选项的对象

   该方 `invokeDDX` 法返回一个 `AssemblerResult` 对象，其中包含作业结果和发生的任何异常。

1. 保存已拆解的PDF文档。

   要获取新创建的PDF文档，请执行以下操作：

   * 访问对 `AssemblerResult` 象的字 `documents` 段，该字段是包含已 `Map` 拆解的PDF文档的对象。
   * 对对象进行 `Map` 迭代以获得每个生成文档。 然后，将该阵列成员 `value` 转换为 `BLOB`。
   * 通过访问PDF文档对象的属性提取表示PDF `BLOB` 的二进制 `MTOM` 数据。 这将返回可写入PDF文件的字节数组。

**另请参阅**

[以编程方式反汇编PDF文档](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
