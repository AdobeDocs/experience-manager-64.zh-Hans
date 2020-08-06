---
title: 分配使用权限
seo-title: 分配使用权限
description: 'null'
seo-description: 'null'
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
translation-type: tm+mt
source-git-commit: ba04fe705a91717f1d9658d436056ebddda6be3a
workflow-type: tm+mt
source-wordcount: '3895'
ht-degree: 0%

---


# 分配使用权限 {#assigning-usage-rights}

## 关于Acrobat Reader DC扩展服务 {#about-the-acrobat-reader-dc-extensions-service}

Acrobat Reader DC扩展服务通过扩展Adobe Reader的功能使您的组织能够轻松共享交互式PDF文档。 Acrobat Reader DC扩展服务完全支持任何PDF文档，最高包括PDF 1.7。它可与Adobe Reader7.0及更高版本一起使用。 本服务向PDF文档添加使用权限，激活使用Adobe Reader打开PDF文档时通常不可用的功能。 第三方用户不需要额外的软件或插件即可与启用权限的文档配合使用。

您可以使用Acrobat Reader DC扩展服务完成以下任务:

* 将使用权限应用于PDF文档。 有关信息，请参 [阅将使用权限应用于PDF文档](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)。
* 从PDF文档中删除使用权限。 有关信息，请参 [阅从PDF文档删除使用权限](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)。
* 检索凭据详细信息。 有关信息，请参阅 [检索凭据信息](assigning-usage-rights.md#retrieving-credential-information)。

>[!NOTE]
>
>有关Acrobat Reader DC扩展服务的更多信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

## 将使用权限应用于PDF文档 {#applying-usage-rights-to-pdf-documents}

您可以使用Acrobat Reader DC扩展Java客户端API和Web服务将使用权限应用于PDF文档。 使用权限与默认在Acrobat但在Adobe Reader不可用的功能有关，如向表单添加注释或填写表单字段并保存表单的功能。 对其应用了使用权限的PDF文档称为启用权限的文档。 在Adobe Reader打开启用权限的文档的用户可以执行为该特定文档启用的操作。

>[!NOTE]
>
>当使用Java API中的方 `applyUsageRights` 法将使用权限应用于PDF文档时，可以将对 `isModeFinal` 象的参数 `ReaderExtensionsOptionSpec` 设置为 `false`。 这会导致表单处理计数器不被更新，并且性能得到改进。 如果您不担心更新已处理的表单计数器，建议将参数 `isModeFinal` 设置为 `false`。

>[!NOTE]
>
>有关Acrobat Reader DC扩展服务的更多信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步骤摘要 {#summary-of-steps}

要对PDF文档应用使用权限，请执行以下步骤：

1. 包括项目文件。
1. 创建一个Acrobat Reader DC扩展Client对象。
1. 检索PDF文档。
1. 指定要应用的使用权限。
1. 将使用权限应用于PDF文档。
1. 保存启用权限的PDF文档。

**包括项目文件**

将必要的文件包含在您的开发项目中。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建Acrobat Reader DC扩展客户端对象**

要以编程方式执行Acrobat Reader DC扩展服务操作，必须创建Acrobat Reader DC扩展服务客户端对象。 如果您使用Acrobat Reader DC扩展Java API，请创建一个 `ReaderExtensionsServiceClient` 对象。 如果您使用Acrobat Reader DC扩展Web服务API，请创建一个 `ReaderExtensionsServiceService` 对象。

**检索PDF文档**

您必须检索PDF文档才能应用使用权限。 支持权限的PDF文档包含使用权限词典。 当Adobe Reader打开包含此类词典的文档时，它将启用字典中指定的仅用于该文档的使用权限。 如果文档不包含使用权词典，Acrobat Reader DC扩展服务将创建一个。 如果它已包含词典，则Acrobat Reader DC扩展服务会用您指定的词典覆盖现有的使用权限。 词典指定启用哪些使用权限。 当用户在Adobe Reader打开文档时，仅允许在词典中指定的使用权限。

**指定要应用的使用权限**

您可以设置的使用权限由您从Adobe Systems Incorporated购买的凭证决定。 凭据通常提供设置一组相关使用权限的权限，如与交互式表单相关的权限。 每个凭据都提供创建特定数量的启用权限的PDF文档的权利。 评估凭据赋予您创建不限数量的草稿文档的权利。

>[!NOTE]
>
>如果尝试分配凭据不允许的使用权，将导致异常。

**将使用权限应用于PDF文档**

要对PDF文档应用使用权限，请引用您用于应用使用权限的凭据的别名(通常在AEM Forms安装过程中会安装凭据)。 此外，还必须指定应用使用权限的PDF文档。 有关配置凭据的信息，请参阅应用程序服务器的安装和部署指南。

**保存启用权限的PDF文档**

在Acrobat Reader DC扩展服务将使用权限应用于PDF文档后，您可以将启用权限的PDF文档另存为PDF文件。

**另请参阅**

[使用Java API应用使用权限](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[使用Web服务API应用使用权限](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC扩展服务API快速开始](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### 使用Java API应用使用权限 {#apply-usage-rights-using-the-java-api}

使用Acrobat Reader DC扩展API(Java)将使用权限应用于PDF文档:

1. 包括项目文件

   在Java项目的类路径中包含客户端JAR文件，如adobe-reader-extensions-client.jar。

1. 创建一个Acrobat Reader DC扩展Client对象。

   * 创建包 `ServiceClientFactory` 含连接属性的对象。
   * 使用对 `ReaderExtensionsServiceClient` 象的构造函数并传递该对 `ServiceClientFactory` 象。

1. 检索PDF文档。

   * 通过 `java.io.FileInputStream` 使用PDF文档的构造函数并传递一个指定PDF文档位置的字符串值，创建一个表示PDF的对象。
   * 使用对 `com.adobe.idp.Document` 象的构造函数并传递该对 `java.io.FileInputStream` 象。

1. 指定要应用的使用权限。

   * 使用其 `UsageRights` 构造函数创建表示使用权限的对象。
   * 对于要应用的每个使用权，调用属于该对象的相应方 `UsageRights` 法。 例如，要添加使 `enableFormFillIn` 用权，请调用 `UsageRights` 对象的方 `enableFormFillIn` 法并传递 `true`。 （对要应用的每个使用权限重复此步骤）。

1. 将使用权限应用于PDF文档。

   * 使用对 `ReaderExtensionsOptionSpec` 象的构造函数创建对象。 此对象包含Acrobat Reader DC扩展服务所需的运行时选项。 调用此构造函数时，必须指定以下值：

      * 包含 `UsageRights` 要应用于文档的使用权限的对象。
      * 一个字符串值，它指定用户在Adobe Reader7.x中打开启用权限的PDF文档时看到的消息。 此消息未在Adobe Reader8.0中显示。
   * 通过调用对象的方法并传递以 `ReaderExtensionsServiceClient` 下值，将使 `applyUsageRights` 用权限应用于PDF文档:

      * 包 `com.adobe.idp.Document` 含应用了使用权限的PDF文档的对象。
      * 一个字符串值，它指定用于应用使用权限的凭据的别名。
      * 一个字符串值，它指定相应的密码值。 (当前忽略此参数。 你可以 `null`通过。)
   * 包 `ReaderExtensionsOptionSpec` 含运行时选项的对象。

   该方 `applyUsageRights` 法返回 `com.adobe.idp.Document` 一个对象，其中包含启用权限的PDF文档。

1. 保存启用权限的PDF文档。

   * 创建对 `java.io.File` 象并确保文件扩展名为。pdf。
   * 调用 `com.adobe.idp.Document` 对象的方 `copyToFile` 法，将对象的内容复制到文件 `com.adobe.idp.Document` 中(确保使用该方 `com.adobe.idp.Document` 法返回的 `applyUsageRights` 对象)。

**另请参阅**

[将使用权限应用于PDF文档](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[快速开始（SOAP模式）：使用Java API应用使用权限](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API应用使用权限 {#apply-usage-rights-using-the-web-service-api}

使用Acrobat Reader DC扩展API（Web服务）将使用权限应用于PDF文档:

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替 `localhost` 换为承载AEM Forms的服务器的IP地址。

1. 创建一个Acrobat Reader DC扩展Client对象。

   * 使用对象 `ReaderExtensionsServiceClient` 的默认构造函数创建对象。
   * 使用构 `ReaderExtensionsServiceClient.Endpoint.Address` 造函数创建 `System.ServiceModel.EndpointAddress` 对象。 将指定WSDL的字符串值传递给AEM Forms服务(例如 `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`。 确保您指 `?blob=mtom`定。)
   * 通过获 `System.ServiceModel.BasicHttpBinding` 取字段的值创建对 `ReaderExtensionsServiceClient.Endpoint.Binding` 象。 将返回值转换为 `BasicHttpBinding`。
   * 将对 `System.ServiceModel.BasicHttpBinding` 象的字段 `MessageEncoding` 设置为 `WSMessageEncoding.Mtom`。 此值确保使用MTOM。
   * 通过执行以下任务启用基本HTTP身份验证：

      * 为字段指定AEM表单用户名 `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`。
      * 为字段分配相应的口令值 `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`。
      * 为字段指 `HttpClientCredentialType.Basic` 定常量值 `BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 为字段指 `BasicHttpSecurityMode.TransportCredentialOnly` 定常量值 `BasicHttpBindingSecurity.Security.Mode`。

1. 检索PDF文档。

   * 使用对 `BLOB` 象的构造函数创建对象。 该 `BLOB` 对象用于存储应用了使用权限的PDF文档。
   * 通过调 `System.IO.FileStream` 用对象的构造函数并传递一个字符串值来创建对象，该字符串值表示PDF文档的文件位置以及打开文件的模式。
   * 创建存储对象内容的字节数 `System.IO.FileStream` 组。 您可以通过获取对象的属性来确定字 `System.IO.FileStream` 节数组的大 `Length` 小。
   * 通过调用对象的方法，用流数 `System.IO.FileStream` 据填充字节 `Read` 数组。 传递要读取的字节数组、开始位置和流长度。
   * 通过 `BLOB` 将对象属性 `MTOM` 赋予字节数组的内容来填充对象。

1. 指定要应用的使用权限。

   * 使用其 `UsageRights` 构造函数创建表示使用权限的对象。
   * 对于要应用的每个使用权，将值 `true` 分配给属于该对象的相应数据 `UsageRights` 成员。 例如，要添加使 `enableFormFillIn` 用权，请 `true` 指定 `UsageRights` 对象的数据 `enableFormFillIn` 成员。 （对要应用的每个使用权限重复此步骤）。

1. 将使用权限应用于PDF文档。

   * 使用对 `ReaderExtensionsOptionSpec` 象的构造函数创建对象。 此对象包含Acrobat Reader DC扩展服务所需的运行时选项。
   * 将对 `UsageRights` 象指定 `ReaderExtensionsOptionSpec` 给对象的数 `usageRights` 据成员。
   * 将一个字符串值指定用户在Adobe Reader打开启用权限的PDF文档时看到的消息，指 `ReaderExtensionsOptionSpec` 定给对象的数 `message` 据成员。
   * 通过调用对象的方法并传递以 `ReaderExtensionsServiceClient` 下值，将使 `applyUsageRights` 用权限应用于PDF文档:

      * 包 `BLOB` 含应用了使用权限的PDF文档的对象。
      * 一个字符串值，它指定用于应用使用权限的凭据的别名。
      * 一个字符串值，它指定相应的密码值。 (当前忽略此参数。 你可以 `null`通过。)
   * 包 `ReaderExtensionsOptionSpec` 含运行时选项的对象。

   该方 `applyUsageRights` 法返回 `BLOB` 一个对象，其中包含启用权限的PDF文档。

1. 保存启用权限的PDF文档。

   * 通过调 `System.IO.FileStream` 用对象的构造函数创建对象。 传递一个字符串值，它表示启用权限的PDF文档的文件位置。
   * 创建一个字节数组，它存储由方 `BLOB` 法返回的对象的数据 `applyUsageRights` 内容。 通过获取对象数据成员的值 `BLOB` 填充字节 `MTOM` 数组。
   * 通过调 `System.IO.BinaryWriter` 用对象的构造函数并传递该对 `System.IO.FileStream` 象来创建。
   * 通过调用对象的方法并传递字节数组，将字 `System.IO.BinaryWriter` 节数组的 `Write` 内容写入PDF文件。

**另请参阅**

[将使用权限应用于PDF文档](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 从PDF文档删除使用权限 {#removing-usage-rights-from-pdf-documents}

您可以从启用权限的文档中删除使用权限。 要对启用权限的PDF文档执行其他AEM Forms操作，还必须从其中删除使用权限。 例如，在设置使用权限之前，您必须对PDF文档进行数字签名（或验证）。 因此，如果要对启用权限的文档执行操作，则必须从PDF文档中删除使用权限，执行其他操作，如对文档进行数字签名，然后重新对文档应用使用权限。

>[!NOTE]
>
>有关Acrobat Reader DC扩展服务的更多信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步骤摘要 {#summary_of_steps-1}

要从启用权限的PDF文档中删除使用权限，请执行以下步骤：

1. 包括项目文件。
1. 创建一个Acrobat Reader DC扩展Client对象。
1. 检索启用权限的PDF文档。
1. 从PDF文档中删除使用权限。
1. 保存PDF文档。

**包括项目文件**

将必要的文件包含在您的开发项目中。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建Acrobat Reader DC扩展客户端对象**

在以编程方式执行Acrobat Reader DC扩展服务操作之前，必须创建Acrobat Reader DC扩展服务客户端对象。 如果您使用Java API，请创建一个 `ReaderExtensionsServiceClient` 对象。 如果您使用Acrobat Reader DC扩展Web服务API，请创建一个 `ReaderExtensionsServiceService` 对象。

**检索启用权限的PDF文档**

检索启用权限的PDF文档以删除使用权限。

**从PDF文档中删除使用权限**

检索启用权限的PDF文档后，您可以删除使用权限。 删除使用权限后，在Adobe Reader内查看PDF文档时，将没有任何其他功能。

**保存PDF文档**

可将不再包含使用权限的PDF文档另存为PDF文件。 保存为PDF文件后，可在Adobe Reader或Acrobat查看PDF文档。

**另请参阅**

[使用Java API删除使用权限](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[使用Web服务API删除使用权限](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC扩展服务API快速开始](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[将使用权限应用于PDF文档](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### 使用Java API删除使用权限 {#remove-usage-rights-using-the-java-api}

使用Acrobat Reader DC扩展API(Java)从启用权限的PDF文档中删除使用权限：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-reader-extensions-client.jar。

1. 创建一个Acrobat Reader DC扩展Client对象。

   使用对 `ReaderExtensionsServiceClient` 象的构造函数并传递包含连接属 `ServiceClientFactory` 性的对象，创建对象。

1. 检索PDF文档。

   * 使用 `java.io.FileInputStream` 其构造函数并传递一个指定PDF文档位置的字符串值，创建一个表示启用权限的PDF文档的对象。
   * 使用对 `com.adobe.idp.Document` 象的构造函数并传递该对 `java.io.FileInputStream` 象。

1. 从PDF文档中删除使用权限。

   通过调用对象的方法并传递包含启 `ReaderExtensionsServiceClient` 用权限的 `removeUsageRights` PDF文档的 `com.adobe.idp.Document` 对象，从PDF文档中删除使用权限。 此方法返回 `com.adobe.idp.Document` 一个对象，其中包含没有使用权限的PDF文档。

1. 将使用权限应用于PDF文档。

   * 创建一 `java.io.File` 个对象，并确保文件扩展名为。PDF。
   * 调用 `Document` 对象的方 `copyToFile` 法，将对象的内容复制到文件 `Document` 中(确保使用该方 `Document` 法返回的 `removeUsageRights` 对象)。

**另请参阅**

[从PDF文档删除使用权限](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[快速开始（SOAP模式）: 使用Java API从PDF文档删除使用权限](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API删除使用权限 {#remove-usage-rights-using-the-web-service-api}

使用Acrobat Reader DC扩展API（Web服务）从启用权限的PDF文档中删除使用权限：

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替 `localhost` 换为承载AEM Forms的服务器的IP地址。

1. 创建一个Acrobat Reader DC扩展Client对象。

   * 使用对象 `ReaderExtensionsServiceClient` 的默认构造函数创建对象。
   * 使用构 `ReaderExtensionsServiceClient.Endpoint.Address` 造函数创建 `System.ServiceModel.EndpointAddress` 对象。 将指定WSDL的字符串值传递给AEM Forms服务(例如 `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`。 确保您指 `?blob=mtom`定。)
   * 通过获 `System.ServiceModel.BasicHttpBinding` 取字段的值创建对 `ReaderExtensionsServiceClient.Endpoint.Binding` 象。 将返回值转换为 `BasicHttpBinding`。
   * 将对 `System.ServiceModel.BasicHttpBinding` 象的字段 `MessageEncoding` 设置为 `WSMessageEncoding.Mtom`。 此值确保使用MTOM。
   * 通过执行以下任务启用基本HTTP身份验证：

      * 为字段指定AEM表单用户名 `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`。
      * 为字段分配相应的口令值 `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`。
      * 为字段指 `HttpClientCredentialType.Basic` 定常量值 `BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 为字段指 `BasicHttpSecurityMode.TransportCredentialOnly` 定常量值 `BasicHttpBindingSecurity.Security.Mode`。

1. 检索PDF文档。

   * 使用对 `BLOB` 象的构造函数创建对象。 该 `BLOB` 对象用于存储启用权限的PDF文档，从中删除使用权限。
   * 通过调 `System.IO.FileStream` 用对象的构造函数并传递一个字符串值来创建对象，该字符串值表示PDF文档的文件位置以及打开文件的模式。
   * 创建存储对象内容的字节数 `System.IO.FileStream` 组。 您可以通过获取对象的属性来确定字 `System.IO.FileStream` 节数组的大 `Length` 小。
   * 通过调用对象的方法并传递要读取的 `System.IO.FileStream` 字节数 `Read` 组、开始位置和流长度，用流数据填充字节数组。
   * 通过 `BLOB` 将对象属性 `MTOM` 赋予字节数组的内容来填充对象。

1. 从PDF文档中删除使用权限。

   通过调用对象的方法并传递包含启 `ReaderExtensionsServiceClient` 用权限的 `removeUsageRights` PDF文档的 `BLOB` 对象，从PDF文档中删除使用权限。 此方法返回 `BLOB` 一个对象，其中包含没有使用权限的PDF文档。

1. 将使用权限应用于PDF文档。

   * 通过调 `System.IO.FileStream` 用对象的构造函数并传递表示PDF文件位置的字符串值来创建对象。
   * 创建一个字节数组，它存储由方 `BLOB` 法返回的对象的数据 `removeUsageRights` 内容。 通过获取对象数据成员的值 `BLOB` 填充字节 `MTOM` 数组。
   * 通过调 `System.IO.BinaryWriter` 用对象的构造函数并传递该对 `System.IO.FileStream` 象来创建。

**另请参阅**

[从PDF文档删除使用权限](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 检索凭据信息 {#retrieving-credential-information}

您可以检索有关用于将使用权限应用于启用权限的PDF文档的凭据的信息。 通过检索有关凭据的信息，您可以获取诸如证书失效日期等信息。

>[!NOTE]
>
>有关Acrobat Reader DC扩展服务的更多信息，请参 [阅AEM Forms服务参考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步骤摘要 {#summary_of_steps-2}

要检索有关用于将使用权限应用于PDF文档的凭据的信息，请执行以下步骤：

1. 包括项目文件。
1. 创建一个Acrobat Reader DC扩展Client对象。
1. 检索启用权限的PDF文档。
1. 检索有关凭据的信息。

**包括项目文件**

将必要的文件包含在您的开发项目中。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用Web服务，请确保包含代理文件。

**创建Acrobat Reader DC扩展客户端对象**

在以编程方式执行Acrobat Reader DC扩展服务操作之前，必须创建Acrobat Reader DC扩展服务客户端对象。 如果您使用Java API，请创建一个 `ReaderExtensionsServiceClient` 对象。 如果您使用Acrobat Reader DC扩展Web服务API，请创建一个 `ReaderExtensionsServiceService` 对象。

**检索启用权限的PDF文档**

您必须检索启用权限的PDF文档才能检索有关凭据的信息。 您还可以通过指定凭据的别名来检索有关凭据的信息； 但是，如果要检索有关用于将使用权限应用于启用特定权限的PDF文档的凭据的信息，则必须检索该文档。

**检索有关凭据的信息**

在检索启用权限的PDF文档后，您可以获取有关用于向其应用使用权限的凭证的信息。 您可以获取有关凭据的以下信息：

* 在启用权限的PDF文档打开时在Adobe Reader内显示的消息。
* 此凭据失效的日期。
* 此凭据无效的日期。
* 为此启用权限的PDF文档设置的使用权限。
* 凭据的使用次数。

**另请参阅**

[使用Java API删除使用权限](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[使用Web服务API删除使用权限](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC扩展服务API快速开始](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### 使用Java API检索凭据信息 {#retrieve-credential-information-using-the-java-api}

使用Acrobat Reader DC扩展API(Java)检索凭据信息：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-reader-extensions-client.jar。

1. 创建一个Acrobat Reader DC扩展Client对象。

   使用对 `ReaderExtensionsServiceClient` 象的构造函数并传递包含连接属 `ServiceClientFactory` 性的对象，创建对象。

1. 检索PDF文档。

   * 通过 `java.io.FileInputStream` 使用其构造函数并传递一个字符串值来创建表示启用权限的PDF文档的对象，该字符串值指定启用权限的PDF文档的位置。
   * 使用对 `com.adobe.idp.Document` 象的构造函数并传递该对 `java.io.FileInputStream` 象。

1. 从PDF文档中删除使用权限。

   * 通过调用对象的方法并传递包含启用权限的PDF文档的对 `ReaderExtensionsServiceClient` 象，检 `getDocumentUsageRights` 索用于将使用权 `com.adobe.idp.Document` 限应用到PDF文档的凭据信息。 此方法返回包 `GetUsageRightsResult` 含凭据信息的对象。
   * 通过调用对象的方法检索此凭据不再有效 `GetUsageRightsResult` 的日 `getNotAfter` 期。 此方法返回一 `java.util.Date` 个对象，该对象表示凭据不再有效的日期。
   * 检索在启用权限的PDF文档打开时在Adobe Reader显示的消息，方法是 `GetUsageRightsResult` 调用对象的方 `getMessage` 法。 此方法返回表示消息的字符串值。

**另请参阅**

[检索凭据信息](assigning-usage-rights.md#retrieving-credential-information)

[快速开始（SOAP模式）: 使用Java API检索凭据信息](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[包括AEM FormsJava库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API检索凭据信息 {#retrieve-credential-information-using-the-web-service-api}

使用Acrobat Reader DC扩展API（Web服务）检索凭据信息：

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替 `localhost` 换为承载AEM Forms的服务器的IP地址。

1. 创建一个Acrobat Reader DC扩展Client对象。

   * 使用对象 `ReaderExtensionsServiceClient` 的默认构造函数创建对象。
   * 使用构 `ReaderExtensionsServiceClient.Endpoint.Address` 造函数创建 `System.ServiceModel.EndpointAddress` 对象。 将指定WSDL的字符串值传递给AEM Forms服务(例如 `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`。 确保您指 `?blob=mtom`定。)
   * 通过获 `System.ServiceModel.BasicHttpBinding` 取字段的值创建对 `ReaderExtensionsServiceClient.Endpoint.Binding` 象。 将返回值转换为 `BasicHttpBinding`。
   * 将对 `System.ServiceModel.BasicHttpBinding` 象的字段 `MessageEncoding` 设置为 `WSMessageEncoding.Mtom`。 此值确保使用MTOM。
   * 通过执行以下任务启用基本HTTP身份验证：

      * 为字段指定AEM表单用户名 `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`。
      * 为字段分配相应的口令值 `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`。
      * 为字段指 `HttpClientCredentialType.Basic` 定常量值 `BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 为字段指 `BasicHttpSecurityMode.TransportCredentialOnly` 定常量值 `BasicHttpBindingSecurity.Security.Mode`。

1. 检索PDF文档。

   * 使用对 `BLOB` 象的构造函数创建对象。 该 `BLOB` 对象用于存储启用权限的PDF文档。
   * 通过调 `System.IO.FileStream` 用其构造函数并传递一个字符串值来创建对象，该字符串值表示启用权限的PDF文档的文件位置以及打开文件的模式。
   * 创建存储对象内容的字节数 `System.IO.FileStream` 组。 您可以通过获取对象的属性来确定字 `System.IO.FileStream` 节数组的大 `Length` 小。
   * 通过调用对象的方法并传递要读取的 `System.IO.FileStream` 字节数 `Read` 组、开始位置和流长度，用流数据填充字节数组。
   * 通过 `BLOB` 将对象属性 `MTOM` 赋予字节数组的内容来填充对象。

1. 从PDF文档中删除使用权限。

   * 通过调用对象的方法并传递包含启用权限的PDF文档的对 `ReaderExtensionsServiceClient` 象，检 `getDocumentUsageRights` 索用于将使用权 `com.adobe.idp.Document` 限应用到PDF文档的凭据信息。 此方法返回包 `GetUsageRightsResult` 含凭据信息的对象。
   * 通过获取对象数据成员的值，检索此凭据不再 `GetUsageRightsResult` 有效的 `notAfter` 日期。 此数据成员的数据类型为 `System.DateTime`。
   * 通过获取对象文档成员的值，检索在Adobe Reader打开启用权限的PDF时 `GetUsageRightsResult` 显示的 `message` 消息。 此数据成员的数据类型是字符串。
   * 获取对象数据成员的值，检索凭据 `GetUsageRightsResult` 的使 `useCount` 用次数。 此数据成员的数据类型是整数。

**另请参阅**

[检索凭据信息](assigning-usage-rights.md#retrieving-credential-information)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
