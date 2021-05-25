---
title: 使AEM能够搜索文档安全保护的PDF文档
seo-title: 使AEM能够搜索文档安全保护的PDF文档
description: '了解如何启用本机AEM搜索功能，以对受DRM保护的PDF文档执行全文搜索。  '
seo-description: '了解如何启用本机AEM搜索功能，以对受DRM保护的PDF文档执行全文搜索。  '
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: 文档安全
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---

# 使AEM能够搜索文档安全保护的PDF文档{#enable-aem-to-search-document-security-protected-pdf-documents}

AEM搜索能够搜索和查找AEM资产，并对各种常用文档格式（如纯文本文件、Microsoft Office文档和PDF文档）执行文本搜索。 您还可以扩展本机搜索，以对受AEM Document security保护的PDF文档](/help/forms/using/admin-help/document-security.md)执行全文搜索。 [要使AEM能够对此类文档执行全文搜索，请执行以下步骤：

1. 建立安全连接
1. 索引受策略保护的PDF文档示例

## 前提条件 {#prerequisites}

* 如果您在OSGi上使用AEM Forms:

   * 在AEM Forms服务器上安装[AEM Forms Document Security Indexer包](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html)。
   * 确保JEE服务器上的AEM Forms已启动且正在运行，并且文档安全已安装在JEE服务器上相应的AEM Forms上。 需要JEE服务器上的AEM表单才能对受保护的文档进行索引。

* 如果您在JEE服务器上只使用AEM Forms，则索引器包已安装。
* 确保所有包都已启动并运行。 如果所有包都不处于活动状态，请等待所有包都启动并运行。

   * 对于OSGi上的AEM Forms，这些包列在`https://[server]:[port]/system/console/bundles`。
   * 对于JEE上的AEM Forms，这些包列在`https://[server]:[port]/[context-path]/system/console/bundles`中。 例如`http://localhost:8080/lc/system/console/bundles`。

* 将&#x200B;*sun.util.calendar*&#x200B;包添加到允许列表中。 要将包添加到允许列表，请执行以下步骤：

   1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
   1. 找到并打开&#x200B;**反序列化防火墙配置**。
   1. 将sun.util.calendar包添加到列入白名单的类或包前缀字段，然后单击&#x200B;**Save**。

## 在AEM Forms JEE和OSGi堆栈{#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}之间建立安全连接

您可以使用以下方法之一建立安全连接：

* 在JEE上使用AEM Forms配置AdobeLiveCycle客户端SDK包管理员凭据
* 使用相互身份验证配置AdobeLiveCycle客户端SDK包

### 在JEE管理员凭据{#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}上使用AEM Forms配置AdobeLiveCycle客户端SDK包

1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
1. 找到并打开&#x200B;**AdobeLiveCycle客户端SDK包**。 为以下字段指定值：

   * **服务器URL:** 指定JEE服务器上AEM Forms的HTTPS URL。要启用通过https的通信，请使用-Djavax.net.ssl.trustStore=&lt;JEE KeyStore文件上AEM Forms的路径>参数重新启动服务器。
   * **服务名称**:将RightsManagementService添加到指定服务的列表。
   * **用户名：** 指定JEE帐户上用于从AEM服务器启动调用的AEM Forms的用户名。指定的帐户必须具有在JEE服务器上的AEM Forms上启动文档服务的权限。
   * **密码**:在用户名字段中指定JEE帐户上AEM Forms的密码。

   单击&#x200B;**保存**。AEM可用于搜索文档安全保护的PDF文档。

### 使用双向身份验证{#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}配置AdobeLiveCycle客户端SDK包

1. 在JEE上为AEM Forms启用双向身份验证。 有关详细信息，请参阅[CAC和双向身份验证](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html)。
1. 打开AEM Web Console。 URL为`https://[server]:[port]/system/console/configMgr`。
1. 找到并打开&#x200B;**AdobeLiveCycle客户端SDK**&#x200B;包。 为以下属性指定值：

   * **服务器URL**:在JEE服务器上指定AEM Forms的HTTPS URL。要启用通过https的通信，请使用-Djavax.net.ssl.trustStore=&lt;JEE KeyStore文件上的AEM Forms路径>参数重新启动AEM服务器。
   * **启用双向SSL**:启用启用双向SSL选项。
   * **KeyStore文件URL**:指定KeyStore文件的URL。
   * **TrustStore FIle URL**:指定truststore文件的URL。
   * **KeyStore密码**:指定密钥库文件的密码。
   * **TrustStorePassword**:为truststore文件指定密码。
   * **服务名称**:将RightsManagementService添加到指定服务的列表。

   单击&#x200B;**保存**。AEM允许搜索文档安全保护的PDF文档

## 索引受策略保护的PDF文档示例{#index-a-sample-policy-protected-pdf-document}

1. 以管理员身份登录AEM Assets。
1. 在AEM Digital Asset Manager中创建文件夹，并将受策略保护的PDF文档上传到新创建的文件夹。

   现在，您可以使用AEM搜索来搜索受策略保护的文档。
