---
title: 配置数据源
seo-title: Configure data sources
description: 了解如何配置不同类型的数据源并利用它们创建表单数据模型。
seo-description: Learn how to configure different types of data sources and leverage to create form data models.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 1%

---

# 配置数据源 {#configure-data-sources}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

了解如何配置不同类型的数据源并利用它们创建表单数据模型。

![](do-not-localize/data-integeration.png)

AEM Forms数据集成允许您配置不同的数据源并将其连接到不同的数据源。 支持开箱即用地使用以下类型。 但是，通过少量自定义，您也可以集成其他数据源。

* 关系数据库 — MySQL、Microsoft SQL Server、IBM DB2和OracleRDBMS。
* AEM用户配置文件
* RESTful Web服务
* 基于SOAP的Web服务
* OData服务

数据集成支持开箱即用的OAuth2.0、基本身份验证和API密钥身份验证类型，并允许实施自定义身份验证以访问Web服务。 虽然在AEM云服务中配置了RESTful、基于SOAP和OData服务，但在AEM Web控制台中配置了关系数据库的JDBC和AEM用户配置文件的连接器。

## 配置关系数据库 {#configure-relational-database}

您可以使用AEM Web控制台配置来配置关系数据库。 执行以下操作：

1. 转到AEM Web控制台(位于 `https://[server]:[host]/system/console/configMgr`.
1. 查找 **[!UICONTROL Apache Sling连接池化数据源]** 配置。 点按以在编辑模式下打开配置。
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
   >1. 在 **[!UICONTROL 纯文本]** 字段中，指定要加密的密码或任何字符串，然后单击 **[!UICONTROL Protect]**.

   >
   >加密文本显示在可在配置中指定的受保护文本字段中。

1. 启用 **[!UICONTROL 借用测试]** 或 **[!UICONTROL 在返回时测试]** 指定在从和向池借用或返回对象之前，对这些对象进行验证。
1. 在 **[!UICONTROL 验证查询]** 字段来验证池中的连接。 查询必须至少返回一行。 根据您的数据库，指定以下任一项：

   * 选择1（MySQL和MS SQL）
   * 从双(Oracle)中选择1

1. 点按 **[!UICONTROL 保存]** 以保存配置。

## 配置AEM用户配置文件 {#configure-aem-user-profile}

您可以在AEM Web Console中使用用户配置文件连接器配置来配置AEM用户配置文件。 执行以下操作：

1. 转到AEM Web控制台(位于 `https://[server]:[host]/system/console/configMgr`.
1. 查找 **[!UICONTROL AEM Forms数据集成 — 用户配置文件连接器配置]** 然后点按以在编辑模式下打开配置。
1. 在用户配置文件连接器配置对话框中，您可以添加、删除或更新用户配置文件属性。 指定的属性将可在表单数据模型中使用。 使用以下格式指定用户配置文件属性：

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   示例：

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >的 **&amp;ast;** 在上例中，表示 `profile/empLocation/` 节点。 这意味着表单数据模型可以访问 `city` 类型属性 `string` 位于 `profile/empLocation/` 节点。 但是，包含指定属性的节点必须遵循一致的结构。

1. 点按 **[!UICONTROL 保存]** 以保存配置。

## 为云服务配置配置文件夹 {#cloud-folder}

>[!NOTE]
>
>为RESTful、SOAP和OData服务配置云服务时，需要配置云服务文件夹。

AEM中的所有云服务配置都整合在 `/conf` 文件夹。 默认情况下， `conf` 文件夹包含 `global` 您可以在其中创建云服务配置的文件夹。 但是，您需要为云配置手动启用它。 您还可以在 `conf` 创建和组织云服务配置。

要为云服务配置配置文件夹，请执行以下操作：

1. 转到 **[!UICONTROL 工具>常规>配置浏览器]**.
   * 请参阅 [配置浏览器文档](/help/sites-administering/configurations.md) 以了解更多信息。
1. 执行以下操作可为云配置启用全局文件夹，或跳过此步骤以为云服务配置创建和配置其他文件夹。

   1. 在 **[!UICONTROL 配置浏览器]**，选择 `global` 文件夹，然后点按 **[!UICONTROL 属性]**.
   1. 在 **[!UICONTROL 配置属性]** 对话框，启用 **[!UICONTROL 云配置]**.
   1. 点按 **[!UICONTROL 保存并关闭]** 保存配置并退出对话框。

1. 在 **[!UICONTROL 配置浏览器]**，点按 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL 创建配置]** 对话框中，为文件夹指定标题并启用 **[!UICONTROL 云配置]**.
1. 点按 **[!UICONTROL 创建]** 创建云服务配置启用的文件夹。

## 配置RESTful Web服务 {#configure-restful-web-services}

RESTful Web服务可使用 [Swagger规范](https://swagger.io/specification/) JSON或YAML格式。 要在AEM云服务中配置RESTful Web服务，请确保您的文件系统上具有Swagger文件，或文件托管位置的URL。

请执行以下操作以配置RESTful服务：

1. 转到 **[!UICONTROL 工具>Cloud Services>数据源]**. 点按以选择要在其中创建云配置的文件夹。

   请参阅 [为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) 有关为云服务配置创建和配置文件夹的信息。

1. 点按 **[!UICONTROL 创建]** 打开 **[!UICONTROL “创建数据源配置”对话框]**. 为配置指定名称和（可选）标题，选择 **[!UICONTROL RESTful服务]** 从 **[!UICONTROL 服务类型]** （可选）浏览并选择配置的缩略图，然后点按 **[!UICONTROL 下一个]**.
1. 为RESTful服务指定以下详细信息：

   * 从Swagger源下拉列表中选择URL或文件，并相应地指定Swagger URL到Swagger定义文件，或从本地文件系统上传Swagger文件。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证、API密钥或自定义身份验证）以访问RESTful服务，并相应地提供身份验证详细信息。

1. 点按 **[!UICONTROL 创建]** 为RESTful服务创建云配置。

## 配置SOAP Web服务 {#configure-soap-web-services}

使用 [Web服务描述语言(WSDL)规范](https://www.w3.org/TR/wsdl). 要在AEM云服务中配置基于SOAP的Web服务，请确保您具有Web服务的WSDL URL，然后执行以下操作：

1. 转到 **[!UICONTROL 工具>Cloud Services>数据源]**. 点按以选择要在其中创建云配置的文件夹。

   请参阅 [为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) 有关为云服务配置创建和配置文件夹的信息。

1. 点按 **[!UICONTROL 创建]** 打开 **[!UICONTROL “创建数据源配置”对话框]**. 为配置指定名称和（可选）标题，选择 **[!UICONTROL SOAP Web服务]** 从 **[!UICONTROL 服务类型]** （可选）浏览并选择配置的缩略图，然后点按 **[!UICONTROL 下一个]**.
1. 为SOAP Web服务指定以下内容：

   * Web服务的WSDL URL。
   * 服务端点. 在此字段中指定一个值，以覆盖WSDL中提到的服务端点。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证、自定义身份验证或X509令牌）以访问SOAP服务，并相应地提供身份验证的详细信息。

      如果选择X509令牌作为身份验证类型，请配置X509证书。 有关更多信息，请参阅 [设置证书](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
在 **[!UICONTROL 键别名]** 字段。 在 **[!UICONTROL 生存时间]** 字段。 （可选）选择对消息正文或时间戳标头进行签名，或选择两者。

1. 点按 **[!UICONTROL 创建]** 为SOAP web服务创建云配置。

## 配置OData服务 {#config-odata}

OData服务由其服务根URL标识。 要在AEM云服务中配置OData服务，请确保您具有该服务的服务根URL，然后执行以下操作：

>[!NOTE]
>
>有关配置Microsoft Dynamics 365的分步指南（在线或本地），请参阅 [Microsoft Dynamics OData配置](/help/forms/using/ms-dynamics-odata-configuration.md).

1. 转到 **[!UICONTROL 工具>Cloud Services>数据源]**. 点按以选择要在其中创建云配置的文件夹。

   请参阅 [为云服务配置配置文件夹](/help/forms/using/configure-data-sources.md#cloud-folder) 有关为云服务配置创建和配置文件夹的信息。

1. 点按 **[!UICONTROL 创建]** 打开 **[!UICONTROL “创建数据源配置”对话框]**. 为配置指定名称和（可选）标题，选择 **[!UICONTROL OData服务]** 从 **[!UICONTROL 服务类型]** （可选）浏览并选择配置的缩略图，然后点按 **[!UICONTROL 下一个]**.
1. 为OData服务指定以下详细信息：

   * 要配置的OData服务的服务根URL。
   * 选择身份验证类型（无、OAuth2.0、基本身份验证或自定义身份验证）以访问OData服务，并相应地提供身份验证的详细信息。

   >[!NOTE]
   >
   >必须选择OAuth 2.0身份验证类型，才能使用OData端点作为服务根连接到Microsoft Dynamics服务。

1. 点按 **创建** 为OData服务创建云配置。

## 后续步骤 {#next-steps}

您已配置数据源。 接下来，您可以创建表单数据模型，或者如果已经创建了没有数据源的表单数据模型，则可以将其与您刚刚配置的数据源相关联。 请参阅 [创建表单数据模型](/help/forms/using/create-form-data-models.md) 以了解详细信息。
