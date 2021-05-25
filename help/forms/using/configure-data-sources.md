---
title: 配置数据源
seo-title: 配置数据源
description: 了解如何配置不同类型的数据源并利用它们创建表单数据模型。
seo-description: 了解如何配置不同类型的数据源并利用它们创建表单数据模型。
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: 表单数据模型
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 1%

---

# 配置数据源{#configure-data-sources}

了解如何配置不同类型的数据源并利用它们创建表单数据模型。

![](do-not-localize/data-integeration.png)

AEM Forms数据集成允许您配置不同的数据源并将其连接到不同的数据源。 支持开箱即用地使用以下类型。 但是，通过少量自定义，您也可以集成其他数据源。

* 关系数据库 — MySQL、Microsoft SQL Server、IBM DB2和OracleRDBMS。
* AEM用户配置文件
* RESTful Web服务
* 基于SOAP的Web服务
* OData服务

数据集成支持开箱即用的OAuth2.0、基本身份验证和API密钥身份验证类型，并允许实施自定义身份验证以访问Web服务。 虽然在AEM云服务中配置了RESTful、基于SOAP和OData服务，但在AEM Web控制台中配置了关系数据库的JDBC和AEM用户配置文件的连接器。

## 配置关系数据库{#configure-relational-database}

您可以使用AEM Web控制台配置来配置关系数据库。 执行以下操作：

1. 转到位于`https://[server]:[host]/system/console/configMgr`的AEM Web控制台。
1. 查找&#x200B;**[!UICONTROL Apache Sling连接池化数据源]**&#x200B;配置。 点按以在编辑模式下打开配置。
1. 在配置对话框中，指定要配置的数据库的详细信息，例如：

   * 数据源的名称
   * 存储数据源名称的数据源服务属性
   * JDBC驱动程序的Java类名称
   * JDBC连接URI
   * 与JDBC驱动程序建立连接的用户名和密码

   >[!NOTE]
   >
   >在配置数据源之前，请确保加密密码等敏感信息。 要加密：
   >
   >1. 转到 `https://[server]:[port]/system/console/crypto`.
   >1. 在&#x200B;**[!UICONTROL 纯文本]**&#x200B;字段中，指定要加密的密码或任何字符串，然后单击&#x200B;**[!UICONTROL Protect]**。

   >
   >加密文本显示在可在配置中指定的受保护文本字段中。

1. 启用&#x200B;**[!UICONTROL 在借入时测试]**&#x200B;或&#x200B;**[!UICONTROL 在返回时测试]**&#x200B;以分别指定在从池借用或返回到池之前对对象进行验证。
1. 在&#x200B;**[!UICONTROL 验证查询]**&#x200B;字段中指定SQL SELECT查询，以验证池中的连接。 查询必须至少返回一行。 根据您的数据库，指定以下任一项：

   * 选择1（MySQL和MS SQL）
   * 从双(Oracle)中选择1

1. 点按&#x200B;**[!UICONTROL Save]**&#x200B;以保存配置。

## 配置AEM用户配置文件{#configure-aem-user-profile}

您可以在AEM Web Console中使用用户配置文件连接器配置来配置AEM用户配置文件。 执行以下操作：

1. 转到位于`https://[server]:[host]/system/console/configMgr`的AEM Web控制台。
1. 查找&#x200B;**[!UICONTROL AEM Forms数据集成 — 用户配置文件连接器配置]** ，然后点按以在编辑模式下打开配置。
1. 在用户配置文件连接器配置对话框中，您可以添加、删除或更新用户配置文件属性。 指定的属性将可在表单数据模型中使用。 使用以下格式指定用户配置文件属性：

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   示例：

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >上例中的&#x200B;**&amp;ast;**&#x200B;表示CRXDE结构中AEM用户配置文件`profile/empLocation/`节点下的所有节点。 这意味着表单数据模型可以访问`profile/empLocation/`节点下任何节点中存在的`string`类型的`city`属性。 但是，包含指定属性的节点必须遵循一致的结构。

1. 点按&#x200B;**[!UICONTROL Save]**&#x200B;以保存配置。

## 为云服务配置配置文件夹{#cloud-folder}

>[!NOTE]
>
>为RESTful、SOAP和OData服务配置云服务时，需要配置云服务文件夹。

AEM中的所有云服务配置都整合在AEM存储库的`/conf`文件夹中。 默认情况下， `conf`文件夹包含可在其中创建云服务配置的`global`文件夹。 但是，您需要为云配置手动启用它。 您还可以在`conf`中创建其他文件夹，以创建和组织云服务配置。

要为云服务配置配置文件夹，请执行以下操作：

1. 转到&#x200B;**[!UICONTROL 工具>常规>配置浏览器]**。
   * 有关更多信息，请参阅[配置浏览器文档](/help/sites-administering/configurations.md)。
1. 执行以下操作可为云配置启用全局文件夹，或跳过此步骤以为云服务配置创建和配置其他文件夹。

   1. 在&#x200B;**[!UICONTROL 配置浏览器]**&#x200B;中，选择`global`文件夹，然后点按&#x200B;**[!UICONTROL 属性]**。
   1. 在&#x200B;**[!UICONTROL 配置属性]**&#x200B;对话框中，启用&#x200B;**[!UICONTROL 云配置]**。
   1. 点按&#x200B;**[!UICONTROL 保存并关闭]**&#x200B;以保存配置并退出对话框。

1. 在&#x200B;**[!UICONTROL 配置浏览器]**&#x200B;中，点按&#x200B;**[!UICONTROL 创建]**。
1. 在&#x200B;**[!UICONTROL 创建配置]**&#x200B;对话框中，指定文件夹的标题并启用&#x200B;**[!UICONTROL 云配置]**。
1. 点按&#x200B;**[!UICONTROL 创建]** ，以创建为云服务配置启用的文件夹。

## 配置RESTful Web服务{#configure-restful-web-services}

RESTful Web服务可在Swagger定义文件中使用JSON或YAML格式的[Swagger规范](https://swagger.io/specification/)进行描述。 要在AEM云服务中配置RESTful Web服务，请确保您的文件系统上具有Swagger文件，或文件托管位置的URL。

请执行以下操作以配置RESTful服务：

1. 转到&#x200B;**[!UICONTROL 工具>Cloud Services>数据源]**。 点按以选择要在其中创建云配置的文件夹。

   请参阅[为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) ，以了解有关为云服务配置创建和配置文件夹的信息。

1. 点按&#x200B;**[!UICONTROL 创建]** ，以打开&#x200B;**[!UICONTROL 创建数据源配置对话框]**。 指定配置的名称和标题（可选），从&#x200B;**[!UICONTROL 服务类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL RESTful Service]**，选择浏览并选择配置的缩略图，然后点按&#x200B;**[!UICONTROL Next]**。
1. 为RESTful服务指定以下详细信息：

   * 从Swagger源下拉列表中选择URL或文件，并相应地指定Swagger URL到Swagger定义文件，或从本地文件系统上传Swagger文件。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证、API密钥或自定义身份验证）以访问RESTful服务，并相应地提供身份验证详细信息。

1. 点按&#x200B;**[!UICONTROL 创建]** ，为RESTful服务创建云配置。

## 配置SOAP Web服务{#configure-soap-web-services}

使用[Web服务描述语言(WSDL)规范](https://www.w3.org/TR/wsdl)描述基于SOAP的Web服务。 要在AEM云服务中配置基于SOAP的Web服务，请确保您具有Web服务的WSDL URL，然后执行以下操作：

1. 转到&#x200B;**[!UICONTROL 工具>Cloud Services>数据源]**。 点按以选择要在其中创建云配置的文件夹。

   请参阅[为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) ，以了解有关为云服务配置创建和配置文件夹的信息。

1. 点按&#x200B;**[!UICONTROL 创建]** ，以打开&#x200B;**[!UICONTROL 创建数据源配置对话框]**。 指定配置的名称和标题（可选），从&#x200B;**[!UICONTROL 服务类型]**&#x200B;下拉菜单中选择&#x200B;**[!UICONTROL SOAP Web服务]**，或者浏览并选择配置的缩略图，然后点按&#x200B;**[!UICONTROL Next]**。
1. 为SOAP Web服务指定以下内容：

   * Web服务的WSDL URL。
   * 服务端点. 在此字段中指定一个值，以覆盖WSDL中提到的服务端点。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证、自定义身份验证或X509令牌）以访问SOAP服务，并相应地提供身份验证的详细信息。

      如果选择X509令牌作为身份验证类型，请配置X509证书。 有关更多信息，请参阅[设置证书](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service)。
在**[!UICONTROL 密钥别名]**&#x200B;字段中为X509证书指定KeyStore别名。 在&#x200B;**[!UICONTROL Time To Live]**&#x200B;字段中，指定身份验证请求保持有效的时间（以秒为单位）。 （可选）选择对消息正文或时间戳标头进行签名，或选择两者。

1. 点按&#x200B;**[!UICONTROL 创建]** ，为SOAP Web服务创建云配置。

## 配置OData服务{#config-odata}

OData服务由其服务根URL标识。 要在AEM云服务中配置OData服务，请确保您具有该服务的服务根URL，然后执行以下操作：

>[!NOTE]
>
>有关配置Microsoft Dynamics 365（联机或本地）的分步指南，请参阅[Microsoft Dynamics OData配置](/help/forms/using/ms-dynamics-odata-configuration.md)。

1. 转到&#x200B;**[!UICONTROL 工具>Cloud Services>数据源]**。 点按以选择要在其中创建云配置的文件夹。

   请参阅[为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) ，以了解有关为云服务配置创建和配置文件夹的信息。

1. 点按&#x200B;**[!UICONTROL 创建]** ，以打开&#x200B;**[!UICONTROL 创建数据源配置对话框]**。 指定配置的名称和标题（可选），从&#x200B;**[!UICONTROL 服务类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL OData服务]**，选择浏览并选择配置的缩略图，然后点按&#x200B;**[!UICONTROL Next]**。
1. 为OData服务指定以下详细信息：

   * 要配置的OData服务的服务根URL。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证或自定义身份验证）以访问OData服务，并相应地提供身份验证的详细信息。

   >[!NOTE]
   >
   >必须选择OAuth 2.0身份验证类型，才能使用OData端点作为服务根连接到Microsoft Dynamics服务。

1. 点按&#x200B;**创建** ，为OData服务创建云配置。

## 下面的步骤 {#next-steps}

您已配置数据源。 接下来，您可以创建表单数据模型，或者如果已经创建了没有数据源的表单数据模型，则可以将其与您刚刚配置的数据源相关联。 有关详细信息，请参阅[创建表单数据模型](/help/forms/using/create-form-data-models.md)。
