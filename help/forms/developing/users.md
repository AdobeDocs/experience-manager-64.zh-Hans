---
title: 管理用户
seo-title: Managing Users
description: 使用用户管理API创建可管理角色、权限和主体（可以是用户或组）以及验证用户的客户端应用程序。
seo-description: Use the User Management API to create client applications that can manage roles, permissions, and principals (which can be users or groups), as well as authenticate users.
uuid: 68d8a0bc-6e3d-4286-ba5c-534dcf58cb84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 95804bff-9e6f-4807-aae4-790bd9e7cb57
role: Developer
exl-id: b03acdb5-e951-49d6-b63f-2df273fcb4c7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '6250'
ht-degree: 0%

---

# 管理用户 {#managing-users}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

**关于用户管理**

您可以使用用户管理API创建可管理角色、权限和承担者（可以是用户或组）以及验证用户的客户端应用程序。 用户管理API包含以下AEM Forms API:

* 目录管理器服务API
* Authentication Manager服务API
* 授权管理器服务API

用户管理允许您分配、删除和确定角色和权限。 它还允许您分配、删除和查询域、用户和组。 最后，您可以使用用户管理来验证用户。

在 [添加用户](users.md#adding-users) 您将了解如何以编程方式添加用户。 本节使用目录管理器服务API。

在 [删除用户](users.md#deleting-users) 您将了解如何以编程方式删除用户。 本节使用目录管理器服务API。

在 [管理用户和群组](users.md#managing-users-and-groups) 您将了解本地用户和目录用户之间的区别，并查看有关如何使用Java和web服务API以编程方式管理用户和组的示例。 本节使用目录管理器服务API。

在 [管理角色和权限](users.md#managing-roles-and-permissions) 您将了解系统角色和权限以及您可以以编程方式增强这些角色和权限的功能，并查看有关如何使用Java和web服务API以编程方式管理角色和权限的示例。 本节同时使用目录管理器服务API和授权管理器服务API。

在 [验证用户](users.md#authenticating-users) 您将看到如何使用Java和Web服务API以编程方式验证用户的示例。 本节使用授权管理器服务API。

**了解身份验证过程**

用户管理提供内置的身份验证功能，还允许您将其与您自己的身份验证提供程序连接。 当用户管理收到验证请求（例如，用户尝试登录）时，它会将用户信息传递给验证提供者以进行验证。 用户管理在验证用户后，会从验证提供程序接收结果。

下图显示了尝试登录的最终用户、用户管理和身份验证提供程序之间的交互。

![mu_mu_umauth_process](assets/mu_mu_umauth_process.png)

下表描述了身份验证过程的每个步骤。

<table> 
 <thead> 
  <tr> 
   <th><p>步骤</p></th> 
   <th><p>描述</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>用户尝试登录到调用用户管理的服务。 用户指定用户名和密码。 </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>用户管理会将用户名和密码以及配置信息发送给身份验证提供程序。</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>验证提供程序连接到用户存储并验证用户。</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>身份验证提供程序将结果返回给用户管理。</p></td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>用户管理允许用户登录或拒绝访问产品。</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>如果服务器时区与客户端时区不同，则在WebSphere应用程序服务器群集上使用.NET客户端在本机SOAP堆栈上使用AEM Forms的“生成PDF”服务时，可能会出现以下用户管理身份验证错误：

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**了解目录管理**

用户管理与支持与LDAP目录连接的目录服务提供程序(DirectoryManagerService)一起打包。 如果贵组织使用非LDAP存储库来存储用户记录，则可以创建您自己的目录服务提供程序，该程序可与您的存储库一起使用。

目录服务提供者应用户管理的请求从用户存储中检索记录。 用户管理会定期在数据库中缓存用户和组记录以提高性能。

目录服务提供程序可用于将用户管理数据库与用户存储同步。 此步骤可确保所有用户目录信息以及所有用户和组记录都是最新的。

此外， DirectoryManagerService还使您能够创建和管理域。 域定义不同的用户群。 域的边界通常根据组织的结构方式或用户存储的设置来定义。 用户管理域提供身份验证提供程序和目录服务提供程序使用的配置设置。

在用户管理导出的配置XML中，属性值为 `Domains` 包含为用户管理定义的每个域的XML元素。 这些元素中的每个元素都包含其他元素，这些元素定义与特定服务提供商关联的域的各个方面。

**了解objectSID值**

使用Active Directory时，请务必了解 `objectSID` 值不是跨多个域的唯一属性。 此值存储对象的安全标识符。 在多域环境（例如，域树）中， `objectSID` 值可以不同。

安 `objectSID` 如果对象从一个Active Directory域移动到另一个域，则值将发生更改。 某些对象具有相同的 `objectSID` 值。 例如，BUILDIN\Administrators、BUILDIN\Power Users等组将具有相同的 `objectSID` 值，而不考虑域。 这些 `objectSID` 值是众所周知的。

## 添加用户 {#adding-users}

您可以使用目录管理器服务API（Java和Web服务）以编程方式将用户添加到AEM Forms。 添加用户后，在执行需要用户的服务操作时，可以使用该用户。 例如，您可以为新用户分配任务。

### 步骤摘要 {#summary-of-steps}

要添加用户，请执行以下步骤：

1. 包括项目文件。
1. 创建DirectoryManagerService客户端。
1. 定义用户信息。
1. 将用户添加到AEM Forms。
1. 确认已添加用户。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请包含代理文件。

**创建DirectoryManagerService客户端**

在以编程方式执行目录管理器服务操作之前，请创建目录管理器服务API客户端。

**定义用户信息**

使用目录管理器服务API添加新用户时，请为该用户定义信息。 通常，在添加新用户时，需定义以下值：

* **域名**:用户所属的域(例如， `DefaultDom`)。
* **用户标识符值**:用户的标识符值(例如， `wblue`)。
* **主类型**:用户类型(例如，您可以指定 `USER)`.
* **给定名称**:用户的给定名称(例如， `Wendy`)。
* **姓氏**:用户的姓氏(例如， `Blue)`.
* **区域设置**:用户的区域设置信息。

**将用户添加到AEM Forms**

定义用户信息后，可以将用户添加到AEM Forms。 要添加用户，请调用 `DirectoryManagerServiceClient` 对象 `createLocalUser` 方法。

**确认已添加用户**

您可以验证是否已添加用户，以确保未出现任何问题。 使用用户标识符值查找新用户。

**另请参阅**

[使用Java API添加用户](users.md#add-users-using-the-java-api)

[使用Web服务API添加用户](users.md#add-users-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[删除用户](users.md#deleting-users)

### 使用Java API添加用户 {#add-users-using-the-java-api}

使用目录管理器服务API(Java)添加用户：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建DirectoryManagerServices客户端。

   创建 `DirectoryManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 定义用户信息。

   * 创建 `UserImpl` 对象。
   * 通过调用 `UserImpl` 对象 `setDomainName` 方法。 传递指定域名的字符串值。
   * 通过调用 `UserImpl` 对象 `setPrincipalType` 方法。 传递指定用户类型的字符串值。 例如，您可以指定 `USER`.
   * 通过调用 `UserImpl` 对象 `setUserid` 方法。 传递指定用户标识符值的字符串值。 例如，您可以指定 `wblue`.
   * 通过调用 `UserImpl` 对象 `setCanonicalName` 方法。 传递指定用户规范名称的字符串值。 例如，您可以指定 `wblue`.
   * 通过调用 `UserImpl` 对象 `setGivenName` 方法。 传递指定用户给定名称的字符串值。 例如，您可以指定 `Wendy`.
   * 通过调用 `UserImpl` 对象 `setFamilyName` 方法。 传递指定用户族名的字符串值。 例如，您可以指定 `Blue`.

   >[!NOTE]
   >
   >调用属于 `UserImpl` 对象来设置其他值。 例如，您可以通过调用 `UserImpl` 对象 `setLocale` 方法。

1. 将用户添加到AEM Forms。

   调用 `DirectoryManagerServiceClient` 对象 `createLocalUser` 方法并传递以下值：

   * 的 `UserImpl` 表示新用户的对象
   * 表示用户密码的字符串值

   的 `createLocalUser` 方法会返回一个指定本地用户标识符值的字符串值。

1. 确认已添加用户。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过调用 `PrincipalSearchFilter` 对象 `setUserId` 方法。 传递表示用户标识符值的字符串值。
   * 调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法和通过 `PrincipalSearchFilter` 对象。 此方法将返回 `java.util.List` 实例，其中每个元素是 `User` 对象。 循环访问 `java.util.List` 实例来查找用户。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[快速入门（SOAP模式）：使用Java API添加用户](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API添加用户 {#add-users-using-the-web-service-api}

使用目录管理器服务API（Web服务）添加用户：

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 确保为服务引用使用以下WSDL定义： `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建DirectoryManagerService客户端。

   * 创建 `DirectoryManagerServiceClient` 对象。
   * 创建 `DirectoryManagerServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。 确保指定 `?blob=mtom`.
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `DirectoryManagerServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 定义用户信息。

   * 创建 `UserImpl` 对象。
   * 通过为 `UserImpl` 对象 `domainName` 字段。
   * 通过为 `UserImpl` 对象 `principalType` 字段。 例如，您可以指定 `USER`.
   * 通过为 `UserImpl` 对象 `userid` 字段。
   * 通过为 `UserImpl` 对象 `canonicalName` 字段。
   * 通过为 `UserImpl` 对象 `givenName` 字段。
   * 通过为 `UserImpl` 对象 `familyName` 字段。

1. 将用户添加到AEM Forms。

   调用 `DirectoryManagerServiceClient` 对象 `createLocalUser` 方法并传递以下值：

   * 的 `UserImpl` 表示新用户的对象
   * 表示用户密码的字符串值

   的 `createLocalUser` 方法会返回一个指定本地用户标识符值的字符串值。

1. 确认已添加用户。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过为 `PrincipalSearchFilter` 对象 `userId` 字段。
   * 调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法和通过 `PrincipalSearchFilter` 对象。 此方法将返回 `MyArrayOfUser` 集合对象，其中每个元素都是 `User` 对象。 循环访问 `MyArrayOfUser` 收藏集来查找用户。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 删除用户 {#deleting-users}

您可以使用目录管理器服务API（Java和Web服务）以编程方式从AEM Forms中删除用户。 删除用户后，无法再使用该用户执行需要用户的服务操作。 例如，您无法将任务分配给已删除的用户。

### 步骤摘要 {#summary_of_steps-1}

要删除用户，请执行以下步骤：

1. 包括项目文件。
1. 创建DirectoryManagerService客户端。
1. 指定要删除的用户。
1. 从AEM Forms中删除用户。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。 如果您使用的是Web服务，请包含代理文件。

**创建DirectoryManagerService客户端**

在以编程方式执行目录管理器服务API操作之前，请创建目录管理器服务客户端。

**指定要删除的用户**

您可以使用用户的标识符值指定要删除的用户。

**从AEM Forms中删除用户**

要删除用户，请调用 `DirectoryManagerServiceClient` 对象 `deleteLocalUser` 方法。

**另请参阅**

[使用Java API删除用户](users.md#delete-users-using-the-java-api)

[使用Web服务API删除用户](users.md#delete-users-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加用户](users.md#adding-users)

### 使用Java API删除用户 {#delete-users-using-the-java-api}

使用目录管理器服务API(Java)删除用户：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建DirectoryManagerService客户端。

   创建 `DirectoryManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 指定要删除的用户。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过调用 `PrincipalSearchFilter` 对象 `setUserId` 方法。 传递表示用户标识符值的字符串值。
   * 调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法和通过 `PrincipalSearchFilter` 对象。 此方法将返回 `java.util.List` 实例，其中每个元素是 `User` 对象。 循环访问 `java.util.List` 实例来查找要删除的用户。

1. 从AEM Forms中删除用户。

   调用 `DirectoryManagerServiceClient` 对象 `deleteLocalUser` 方法，并传递 `User` 对象 `oid` 字段。 调用 `User` 对象 `getOid` 方法。 使用 `User` 从检索的对象 `java.util.List` 实例。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[快速启动（EJB模式）：使用Java API删除用户](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[快速入门（SOAP模式）：使用Java API删除用户](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API删除用户 {#delete-users-using-the-web-service-api}

使用目录管理器服务API（Web服务）删除用户：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建DirectoryManagerService客户端。

   * 创建 `DirectoryManagerServiceClient` 对象。
   * 创建 `DirectoryManagerServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`)。 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。 确保指定 `blob=mtom.`
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `DirectoryManagerServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 指定要删除的用户。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过为 `PrincipalSearchFilter` 对象 `userId` 字段。
   * 调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法和通过 `PrincipalSearchFilter` 对象。 此方法将返回 `MyArrayOfUser` 集合对象，其中每个元素都是 `User` 对象。 循环访问 `MyArrayOfUser` 收藏集来查找用户。 的 `User` 从检索的对象 `MyArrayOfUser` 集合对象用于删除用户。

1. 从AEM Forms中删除用户。

   通过传递 `User` 对象 `oid` 字段值 `DirectoryManagerServiceClient` 对象 `deleteLocalUser` 方法。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 创建群组 {#creating-groups}

您可以使用目录管理器服务API（Java和Web服务）以编程方式创建AEM Forms组。 创建组后，可以使用该组执行需要组的服务操作。 例如，您可以将用户分配给新群组。 (请参阅 [管理用户和群组](users.md#managing-users-and-groups).)

### 步骤摘要 {#summary_of_steps-2}

要创建组，请执行以下步骤：

1. 包括项目文件。
1. 创建DirectoryManagerService客户端。
1. 确定组不存在。
1. 创建群组。
1. 对组执行操作。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必需的JAR文件。

必须将以下JAR文件添加到项目的类路径中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar(在JBoss上部署AEM Forms时必需)
* jbossall-client.jar(在JBoss上部署AEM Forms时必需)

有关这些JAR文件的位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**创建DirectoryManagerService客户端**

在以编程方式执行目录管理器服务操作之前，请创建目录管理器服务API客户端。

**确定组是否存在**

创建群组时，请确保该群组不存在于同一域中。 也就是说，两个组不能在同一域中具有相同的名称。 要执行此任务，请执行搜索并根据两个值筛选搜索结果。 将主体类型设置为 `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` 以确保仅返回组。 另外，请确保指定域名。

**创建群组**

确定域中不存在群组后，请创建群组并指定以下属性：

* **CommonName**:组的名称。
* **域**:添加群组的域。
* **描述**:群组的描述。

**对组执行操作**

创建群组后，可以使用该群组执行操作。 例如，您可以将用户添加到群组。 要将用户添加到群组，请检索用户和群组的唯一标识符值。 将这些值传递给 `addPrincipalToLocalGroup` 方法。

**另请参阅**

[使用Java API创建组](users.md#create-groups-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[添加用户](users.md#adding-users)

[删除用户](users.md#deleting-users)

### 使用Java API创建组 {#create-groups-using-the-java-api}

使用目录管理器服务API(Java)创建组：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建DirectoryManagerService客户端。

   创建 `DirectoryManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 确定组是否存在。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过调用 `PrincipalSearchFilter` 对象 `setPrincipalType` 对象。 传递值 `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP`.
   * 通过调用 `PrincipalSearchFilter` 对象 `setSpecificDomainName` 对象。 传递指定域名的字符串值。
   * 要查找组，请调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法（主体可以是组）。 传递 `PrincipalSearchFilter` 指定主体类型和域名的对象。 此方法将返回 `java.util.List` 其中每个元素都是 `Group` 实例。 每个组实例都符合使用 `PrincipalSearchFilter` 对象。
   * 循环访问 `java.util.List` 实例。 对于每个元素，检索组名称。 确保组名称不等于新组名称。

1. 创建群组。

   * 如果组不存在，请调用 `Group` 对象 `setCommonName` 方法，并传递指定组名称的字符串值。
   * 调用 `Group` 对象 `setDescription` 方法，并传递指定组描述的字符串值。
   * 调用 `Group` 对象 `setDomainName` 方法，并传递指定域名的字符串值。
   * 调用 `DirectoryManagerServiceClient` 对象 `createLocalGroup` 方法和通过 `Group` 实例。

   的 `createLocalUser` 方法会返回一个指定本地用户标识符值的字符串值。

1. 对组执行操作。

   * 创建 `PrincipalSearchFilter` 对象。
   * 通过调用 `PrincipalSearchFilter` 对象 `setUserId` 方法。 传递表示用户标识符值的字符串值。
   * 调用 `DirectoryManagerServiceClient` 对象 `findPrincipals` 方法和通过 `PrincipalSearchFilter` 对象。 此方法将返回 `java.util.List` 实例，其中每个元素是 `User` 对象。 循环访问 `java.util.List` 实例来查找用户。
   * 通过调用 `DirectoryManagerServiceClient` 对象 `addPrincipalToLocalGroup` 方法。 传递的返回值 `User` 对象 `getOid` 方法。 传递的返回值 `Group` 对象 `getOid` 方法(使用 `Group` 表示新组的实例)。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## 管理用户和群组 {#managing-users-and-groups}

本主题介绍如何使用(Java)以编程方式分配、删除和查询域、用户和组。

>[!NOTE]
>
>配置域时，必须为组和用户设置唯一标识符。 所选属性不仅在LDAP环境中必须是唯一的，而且必须不可更改，并且不会在目录中发生更改。 此属性还必须是简单的字符串数据类型(Active Directory 2000/2003当前允许的唯一例外是 `"objectsid"`，这是二进制值)。 Novell eDirectory属性 `"GUID"`例如，不是简单的字符串数据类型，因此无法正常使用。

* 对于Active Directory，请使用 `"objectsid"`.
* 对于SunOne，请使用 `"nsuniqueid"`.

>[!NOTE]
>
>不支持在LDAP目录同步过程中创建多个本地用户和组。 尝试此进程可能会导致错误。

### 步骤摘要 {#summary_of_steps-3}

要管理用户和群组，请执行以下步骤：

1. 包括项目文件。
1. 创建DirectoryManagerService客户端。
1. 调用相应的用户或组操作。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建DirectoryManagerService客户端**

在以编程方式执行目录管理器服务操作之前，必须创建目录管理器服务客户端。 使用Java API，可通过创建 `DirectoryManagerServiceClient` 对象。 使用Web服务API，可通过创建 `DirectoryManagerServiceService` 对象。

**调用相应的用户或组操作**

创建服务客户端后，可以调用用户或组管理操作。 服务客户端允许您分配、删除和查询域、用户和组。 请注意，可以将目录主体或本地主体添加到本地组，但无法将本地主体添加到目录组。

**另请参阅**

[使用Java API管理用户和组](users.md#managing-users-and-groups-using-the-java-api)

[使用Web服务API管理用户和组](users.md#managing-users-and-groups-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[用户管理器API快速入门](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### 使用Java API管理用户和组 {#managing-users-and-groups-using-the-java-api}

要使用(Java)以编程方式管理用户、组和域，请执行以下任务：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。 有关这些文件位置的信息，请参阅 [包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. 创建DirectoryManagerService客户端。

   创建 `DirectoryManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。 有关信息，请参阅 [设置连接属性&#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. 调用相应的用户或组操作。

   要查找用户或组，请调用 `DirectoryManagerServiceClient` 对象查找主体的方法（因为主体可以是用户或组）。 在以下示例中， `findPrincipals` 方法(使用搜索过滤器 `PrincipalSearchFilter` 对象)。

   由于此例中的返回值是 `java.util.List` 包含 `Principal` 对象，遍历结果并转换 `Principal` 对象 `User` 或 `Group` 对象。

   使用结果 `User` 或 `Group` 对象(两者均继承自 `Principal` 界面)，检索您在工作流中需要的信息。 例如，域名和规范名称值组合在一起，可唯一标识主体。 调用 `Principal` 对象 `getDomainName` 和 `getCanonicalName` 方法。

   要删除本地用户，请调用 `DirectoryManagerServiceClient` 对象 `deleteLocalUser` 方法和传递用户的标识符。

   要删除本地组，请调用 `DirectoryManagerServiceClient` 对象 `deleteLocalGroup` 方法并传递组的标识符。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API管理用户和组 {#managing-users-and-groups-using-the-web-service-api}

要使用目录管理器服务API（Web服务）以编程方式管理用户、组和域，请执行以下任务：

1. 包括项目文件。

   * 创建使用目录管理器WSDL的Microsoft .NET客户端程序集。 (请参阅 [使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * 引用Microsoft .NET客户端程序集。 (请参阅 [创建使用Base64编码的.NET客户端程序集](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. 创建DirectoryManagerService客户端。

   创建 `DirectoryManagerServiceService` 对象。

1. 调用相应的用户或组操作。

   要查找用户或组，请调用 `DirectoryManagerServiceService` 对象查找主体的方法（因为主体可以是用户或组）。 在以下示例中， `findPrincipalsWithFilter` 方法(使用搜索过滤器 `PrincipalSearchFilter` 对象)。 使用 `PrincipalSearchFilter` 对象，仅当 `isLocal` 属性设置为 `true`. 此行为与Java API可能发生的行为不同。

   >[!NOTE]
   >
   >如果未在搜索筛选器中指定结果的最大数(通过 `PrincipalSearchFilter.resultsMax` 字段)，则最多将返回1000个结果。 这与使用Java API时发生的行为不同，Java API默认最大值为10个结果。 此外，搜索方法如 `findGroupMembers` 除非在搜索筛选器中指定了结果的最大数量(例如，通过 `GroupMembershipSearchFilter.resultsMax` 字段。 这适用于继承自 `GenericSearchFilter` 类。 有关更多信息，请参阅 [AEM Forms API参考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   由于此例中的返回值是 `object[]` 包含 `Principal` 对象，遍历结果并转换 `Principal` 对象 `User` 或 `Group` 对象。

   使用结果 `User` 或 `Group` 对象(两者均继承自 `Principal` 界面)，检索您在工作流中需要的信息。 例如，域名和规范名称值组合在一起，可唯一标识主体。 调用 `Principal` 对象 `domainName` 和 `canonicalName` 字段。

   要删除本地用户，请调用 `DirectoryManagerServiceService` 对象 `deleteLocalUser` 方法和传递用户的标识符。

   要删除本地组，请调用 `DirectoryManagerServiceService` 对象 `deleteLocalGroup` 方法并传递组的标识符。

**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## 管理角色和权限 {#managing-roles-and-permissions}

本主题介绍如何使用授权管理器服务API(Java)以编程方式分配、删除和确定角色和权限。

在AEM Forms, *角色* 是访问一个或多个系统级别资源的一组权限。 这些权限通过用户管理创建，并由服务组件强制执行。 例如，管理员可以将“策略集作者”角色分配给一组用户。 然后，Rights Management将允许具有该角色的组的用户通过管理控制台创建策略集。

角色有两种类型： *默认角色* 和 *自定义角色*. 默认角色(*系统角色)* 已经在AEM Forms居住了。 假定默认角色不能被管理员删除或修改，因此不可变。 因此，管理员创建的自定义角色可变，管理员随后可以修改或删除这些角色。

角色可简化权限管理。 当角色被分配给主体时，一组权限被自动地分配给该主体，并且主体的所有与访问相关的决策都基于被分配的总权限集。

### 步骤摘要 {#summary_of_steps-4}

要管理角色和权限，请执行以下步骤：

1. 包括项目文件。
1. 创建AuthorizationManagerService客户端。
1. 调用相应的角色或权限操作。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建AuthorizationManagerService客户端**

在以编程方式执行用户管理授权管理器服务操作之前，必须创建授权管理器服务客户端。 使用Java API，可通过创建 `AuthorizationManagerServiceClient` 对象。

**调用适当的角色或权限操作**

创建服务客户端后，可以调用角色或权限操作。 服务客户端允许您分配、删除和确定角色和权限。

**另请参阅**

[使用Java API管理角色和权限](users.md#managing-roles-and-permissions-using-the-java-api)

[使用Web服务API管理角色和权限](users.md#managing-roles-and-permissions-using-the-web-service-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[用户管理器API快速入门](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### 使用Java API管理角色和权限 {#managing-roles-and-permissions-using-the-java-api}

要使用授权管理器服务API(Java)管理角色和权限，请执行以下任务：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建AuthorizationManagerService客户端。

   创建 `AuthorizationManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 调用相应的角色或权限操作。

   要将角色分配给承担者，请调用 `AuthorizationManagerServiceClient` 对象 `assignRole` 方法并传递以下值：

   * A `java.lang.String` 包含角色标识符的对象
   * 数组 `java.lang.String` 包含主体标识符的对象。

   要从主体中删除角色，请调用 `AuthorizationManagerServiceClient` 对象 `unassignRole` 方法并传递以下值：

   * A `java.lang.String` 包含角色标识符的对象。
   * 数组 `java.lang.String` 包含主体标识符的对象。


**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[快速入门（SOAP模式）：使用Java API管理角色和权限](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服务API管理角色和权限 {#managing-roles-and-permissions-using-the-web-service-api}

使用授权管理器服务API（Web服务）管理角色和权限：

1. 包括项目文件。

   创建使用MTOM的Microsoft .NET项目。 确保使用以下WSDL定义： `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >替换 `localhost` 具有托管AEM Forms的服务器的IP地址。

1. 创建AuthorizationManagerService客户端。

   * 创建 `AuthorizationManagerServiceClient` 对象。
   * 创建 `AuthorizationManagerServiceClient.Endpoint.Address` 对象 `System.ServiceModel.EndpointAddress` 构造函数。 将指定WSDL的字符串值传递到AEM Forms服务(例如， `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`.) 您无需使用 `lc_version` 属性。 在创建服务引用时，会使用此属性。
   * 创建 `System.ServiceModel.BasicHttpBinding` 对象，方法是获取 `AuthorizationManagerServiceClient.Endpoint.Binding` 字段。 将返回值转换为 `BasicHttpBinding`.
   * 设置 `System.ServiceModel.BasicHttpBinding` 对象 `MessageEncoding` 字段 `WSMessageEncoding.Mtom`. 此值可确保使用MTOM。
   * 通过执行以下任务，启用基本HTTP身份验证：

      * 将AEM表单用户名分配给字段 `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName`.
      * 为字段分配相应的密码值 `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password`.
      * 指定常量值 `HttpClientCredentialType.Basic` 到字段 `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * 指定常量值 `BasicHttpSecurityMode.TransportCredentialOnly` 到字段 `BasicHttpBindingSecurity.Security.Mode`.

1. 调用相应的角色或权限操作。

   要将角色分配给承担者，请调用 `AuthorizationManagerServiceClient` 对象 `assignRole` 方法并传递以下值：

   * A `string` 包含角色标识符的对象
   * A `MyArrayOf_xsd_string` 包含主体标识符的对象。

   要从主体中删除角色，请调用 `AuthorizationManagerServiceService` 对象 `unassignRole` 方法并传递以下值：

   * A `string` 包含角色标识符的对象。
   * 数组 `string` 包含主体标识符的对象。


**另请参阅**

[步骤摘要](users.md#summary-of-steps)

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## 验证用户 {#authenticating-users}

本主题介绍如何使用身份验证管理器服务API(Java)来启用客户端应用程序以编程方式对用户进行身份验证。

可能需要用户身份验证才能与存储安全数据的企业数据库或其他企业存储库进行交互。

例如，假设用户在网页中输入用户名和密码，并将值提交到托管Forms的J2EE应用程序服务器。 Forms自定义应用程序可以使用身份验证管理器服务来验证用户。

如果身份验证成功，应用程序将访问安全的企业数据库。 否则，系统会向用户发送一条消息，说明用户不是授权用户。

下图显示了应用程序的逻辑流程。

![au_au_umauth_process](assets/au_au_umauth_process.png)

下表介绍了此图表中的步骤

<table> 
 <thead> 
  <tr> 
   <th><p>步骤</p></th> 
   <th><p>描述</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>用户访问网站并指定用户名和密码。 此信息将提交到托管AEM Forms的J2EE应用程序服务器。</p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>用户凭据通过Authentication Manager服务进行身份验证。 如果用户凭据有效，工作流将继续执行步骤3。 否则，系统会向用户发送一条消息，说明用户不是授权用户。</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>用户信息和表单设计从安全企业数据库中检索。 </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>用户信息将与表单设计合并，并且表单会呈现给用户。 </p></td> 
  </tr> 
 </tbody> 
</table>

### 步骤摘要 {#summary_of_steps-5}

要以编程方式验证用户，请执行以下步骤：

1. 包括项目文件。
1. 创建AuthenticationManagerService客户端。
1. 调用身份验证操作。
1. 如有必要，请检索上下文，以便客户端应用程序可以将其转发到其他AEM Forms服务进行身份验证。

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建AuthenticationManagerService客户端**

在以编程方式对用户进行身份验证之前，必须创建AuthenticationManagerService客户端。 使用Java API时，请创建 `AuthenticationManagerServiceClient` 对象。

**调用身份验证操作**

创建服务客户端后，即可调用身份验证操作。 此操作将需要有关用户的信息，如用户名和密码。 如果用户未进行身份验证，则会引发异常。

**检索身份验证上下文**

用户进行身份验证后，即可基于经过身份验证的用户创建上下文。 然后，您可以使用内容调用其他AEM Forms服务。 例如，您可以使用上下文创建 `EncryptionServiceClient` 并使用密码加密PDF文档。 确保已经过身份验证的用户具有名为的角色 `Services User` 调用AEM Forms服务所需的调用。

**另请参阅**

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[用户管理器API快速入门](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[使用密码加密PDF文档](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### 使用Java API验证用户身份 {#authenticate-a-user-using-the-java-api}

使用Authentication Manager Service API(Java)验证用户：

1. 包括项目文件。

   在Java项目的类路径中包含客户端JAR文件，如adobe-usermanager-client.jar。

1. 创建AuthenticationManagerServices客户端。

   创建 `AuthenticationManagerServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 调用身份验证操作。

   调用 `AuthenticationManagerServiceClient` 对象 `authenticate` 方法并传递以下值：

   * A `java.lang.String` 包含用户名称的对象。
   * 字节数组( `byte[]` 对象)。 您可以获取 `byte[]` 对象 `java.lang.String` 对象 `getBytes` 方法。

   身份验证方法会返回 `AuthResult` 对象，其中包含有关已验证用户的信息。

1. 检索身份验证上下文。

   调用 `ServiceClientFactory` 对象 `getContext` 方法，该方法将返回 `Context` 对象。

   然后调用 `Context` 对象 `initPrincipal` 方法和通过 `AuthResult`.

### 使用Web服务API验证用户 {#authenticate-a-user-using-the-web-service-api}

使用Authentication Manager Service API（Web服务）验证用户：

1. 包括项目文件。

   * 创建使用身份验证管理器WSDL的Microsoft .NET客户端程序集。 (请参阅 [使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * 引用Microsoft .NET客户端程序集。 (请参阅 [使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. 创建AuthenticationManagerService客户端。

   创建 `AuthenticationManagerServiceService` 对象。

1. 调用身份验证操作。

   调用 `AuthenticationManagerServiceClient` 对象 `authenticate` 方法并传递以下值：

   * A `string` 包含用户名称的对象
   * 字节数组( `byte[]` 对象)。 您可以获取 `byte[]` 对象 `string` 包含对 `byte[]` 数组。
   * 返回的值将为 `AuthResult` 对象，用于检索有关用户的信息。 在以下示例中，用户信息是通过首先获取 `AuthResult` 对象 `authenticatedUser` 字段，然后获取结果 `User` 对象 `canonicalName` 和 `domainName` 字段。

**另请参阅**

[使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 以编程方式同步用户 {#programmatically-synchronizing-users}

您可以使用用户管理API以编程方式同步用户。 同步用户时，您会使用位于用户存储库中的用户数据来更新AEM Forms。 例如，假定您向用户存储库中添加新用户。 执行同步操作后，新用户将成为AEM Forms用户。 此外，用户存储库中不再存在的用户也会从AEM Forms中删除。

下图显示了与用户存储库同步的AEM Forms。

![ps_ps_umauth_sync](assets/ps_ps_umauth_sync.png)

下表介绍了此图表中的步骤

<table> 
 <thead> 
  <tr> 
   <th><p>步骤</p></th> 
   <th><p>描述</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>客户端应用程序请求AEM Forms执行同步操作。</p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>AEM Forms执行同步操作。</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>用户信息已更新。</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>用户能够查看更新的用户信息。 </p></td> 
  </tr> 
 </tbody> 
</table>

### 步骤摘要 {#summary_of_steps-6}

要以编程方式同步用户，请执行以下步骤：

1. 包括项目文件。
1. 创建UserManagerUtilServiceClient客户端。
1. 指定企业域。
1. 调用身份验证操作。
1. 确定同步操作是否已完成

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建UserManagerUtilServiceClientclient**

在以编程方式同步用户之前，您必须先创建 `UserManagerUtilServiceClient` 对象。

**指定企业域**

在使用用户管理API执行同步操作之前，您需要指定用户所属的企业域。 您可以指定一个或多个企业域。 在以编程方式执行同步操作之前，您必须使用管理控制台设置一个企业域。 (请参阅 [管理帮助](https://www.adobe.com/go/learn_aemforms_admin_63).)

**调用同步操作**

指定一个或多个企业域后，可以执行同步操作。 执行此操作所花费的时间取决于位于用户存储库中的用户记录数。

**确定同步操作是否已完成**

以编程方式执行同步操作后，可以确定操作是否完成。

**另请参阅**

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[用户管理器API快速入门](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[使用密码加密PDF文档](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### 使用Java API以编程方式同步用户 {#programmatically-synchronizing-users-using-the-java-api}

使用用户管理API(Java)同步用户：

1. 包括项目文件。

   将客户端JAR文件（如adobe-usermanager-client.jar和adobe-usermanager-util-client.jar）包含在您Java项目的类路径中。

1. 创建UserManagerUtilServiceClient客户端。

   创建 `UserManagerUtilServiceClient` 对象，并使用其构造函数进行传递 `ServiceClientFactory` 包含连接属性的对象。

1. 指定企业域。

   * 调用 `UserManagerUtilServiceClient` 对象 `scheduleSynchronization` 方法启动用户同步操作。
   * 创建 `java.util.Set` 实例 `HashSet` 构造函数。 确保指定 `String` 类型。 此 `Java.util.Set` 实例存储应用同步操作的域名。
   * 对于要添加的每个域名，请调用 `java.util.Set` 对象的add方法并传递域名。

1. 调用同步操作。

   调用 `ServiceClientFactory` 对象 `getContext` 方法，该方法将返回 `Context` 对象。

   然后调用 `Context` 对象 `initPrincipal` 方法和通过 `AuthResult`.

**另请参阅**

[以编程方式同步用户](users.md#programmatically-synchronizing-users)

[包括AEM Forms Java库文件](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[设置连接属性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
