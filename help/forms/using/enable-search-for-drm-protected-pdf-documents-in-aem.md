---
title: 使AEM能够搜索文档安全保护的PDF文档
seo-title: 使AEM能够搜索文档安全保护的PDF文档
description: '了解如何启用本机AEM搜索以在受DRM保护的PDF文档上执行全文搜索。  '
seo-description: '了解如何启用本机AEM搜索以在受DRM保护的PDF文档上执行全文搜索。  '
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 1%

---


# 使AEM能够搜索文档安全保护的PDF文档{#enable-aem-to-search-document-security-protected-pdf-documents}

AEM搜索能够搜索和查找AEM资产，并对各种常用文档格式(如纯文本文件、Microsoft Office文档和PDF文档)执行文本搜索。 您还可以扩展本机搜索功能，对使用AEM文档安全性](/help/forms/using/admin-help/document-security.md)保护的[PDF文档执行全文搜索。 要使AEM能够对此类文档执行全文搜索，请执行以下步骤：

1. 建立安全连接
1. 索引受策略保护的示例PDF文档

## 前提条件 {#prerequisites}

* 如果您在OSGi上使用AEM Forms:

   * 在AEM Forms服务器上安装[AEM Forms文档安全索引器包](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html)。
   * 确保JEE服务器上的AEM Forms已启动并正在运行，并且JEE服务器上的相应AEM Forms上已安装文档安全。 JEE服务器上的AEM表单是索引受保护的文档的必需。

* 如果仅在JEE服务器上使用AEM Forms，则已安装索引器包。
* 确保所有捆绑包都已启动并运行。 如果所有捆绑包都未激活，请等待所有捆绑包都启动并运行。

   * 对于OSGi上的AEM Forms，这些包列在`https://[server]:[port]/system/console/bundles`。
   * 对于JEE上的AEM Forms，这些包列在`https://[server]:[port]/[context-path]/system/console/bundles`。 例如`http://localhost:8080/lc/system/console/bundles`。

* 将&#x200B;*sun.util.calendar*&#x200B;包添加到允许列表。 要将包添加到允许列表，请执行以下步骤：

   1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
   1. 找到并打开&#x200B;**反序列化防火墙配置**。
   1. 将sun.util.calendar包添加到白名单的类或包前缀字段，然后单击&#x200B;**保存**。

## 在AEM FormsJEE和OSGi堆栈{#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}之间建立安全连接

您可以使用以下方法之一建立安全连接：

* 在JEE管理员凭据上配置AdobeLiveCycle客户端SDK包和AEM Forms
* 使用相互身份验证配置AdobeLiveCycle客户端SDK包

### 在JEE管理员凭据{#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}上配置AdobeLiveCycle客户端SDK包和AEM Forms

1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
1. 找到并打开&#x200B;**AdobeLiveCycle客户端SDK Bundle**。 指定以下字段的值：

   * **服务器URL:** 指定JEE服务器上AEM Forms的HTTPS URL。要启用通过https的通信，请使用-Djavax.net.ssl.trustStore=&lt;JEE密钥库文件上的AEM Forms路径>参数重新启动服务器。
   * **服务名称**:将RightsManagementService添加到指定服务的列表。
   * **用户名：** 指定JEE帐户上用于从AEM服务器启动调用的AEM Forms的用户名。指定的帐户必须具有在JEE服务器上的AEM Forms上开始文档服务的权限。
   * **密码**:在“用户名”字段中提到的JEE帐户上指定AEM Forms的密码。

   单击&#x200B;**保存**。AEM可用于搜索受文档安全保护的PDF文档。

### 使用相互身份验证{#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}配置AdobeLiveCycle客户端SDK包

1. 在JEE上为AEM Forms启用相互身份验证。 有关详细信息，请参阅[CAC和相互身份验证](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html)。
1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
1. 找到并打开&#x200B;**AdobeLiveCycle客户端SDK**&#x200B;捆绑包。 指定以下属性的值：

   * **服务器URL**:在JEE服务器上指定AEM Forms的HTTPS URL。要启用通过https的通信，请使用-Djavax.net.ssl.trustStore=&lt;JEE密钥库文件上的AEM Forms路径>参数重新启动AEM服务器。
   * **启用双向SSL**:启用启用双向SSL选项。
   * **密钥存储文件URL**:指定密钥库文件的URL。
   * **TrustStore FIle URL**:指定信任存储文件的URL。
   * **密钥存储密码**:指定密钥库文件的口令。
   * **TrustStorePassword**:指定truststore文件的口令。
   * **服务名称**:将RightsManagementService添加到指定服务的列表。

   单击&#x200B;**保存**。AEM已启用以搜索受安全保护的文档PDF文档

## 索引受策略保护的示例PDF文档{#index-a-sample-policy-protected-pdf-document}

1. 以管理员身份登录AEM Assets。
1. 在AEM Digital Asset Manager中创建文件夹，并将受策略保护的PDF文档上传到新创建的文件夹。

   现在，您可以使用AEM搜索搜索搜索受策略保护的文档。

