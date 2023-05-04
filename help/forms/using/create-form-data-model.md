---
title: “教程：创建表单数据模型“
seo-title: Create Form Data Model Tutorial
description: AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户配置文件、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 了解如何将MySQL数据库配置为数据源、创建、配置和测试表单数据模型。
seo-description: AEM Forms data integration module allows you to create a form data model from disparate backend data sources such as AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. Learn how to configure MySQL database as data source, create, configure, and test a form data model.
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: Adaptive Forms
exl-id: 2f83e853-2468-4ea2-85f6-8cf7fe9de6a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 1%

---

# 教程：创建表单数据模型  {#tutorial-create-form-data-model}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

本教程是 [创建您的第一个自适应表单](/help/forms/using/create-your-first-adaptive-form.md) 系列。 建议按照时间顺序排列系列，以了解、执行和演示完整的教程用例。

## 关于教程 {#about-the-tutorial}

AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户配置文件、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 您可以在表单数据模型中配置数据模型对象和服务，并将其与自适应表单相关联。 自适应表单字段绑定到数据模型对象属性。 利用这些服务，您可以预填自适应表单，并将提交的表单数据写回数据模型对象。

有关表单数据集成和表单数据模型的更多信息，请参阅 [AEM Forms数据集成](/help/forms/using/data-integration.md).

本教程将指导您完成准备、创建、配置表单数据模型并将其与自适应表单相关联的步骤。 在本教程结束时，您将能够：

* [将MySQL数据库配置为数据源](#config-database)
* [使用MySQL数据库创建表单数据模型](#create-fdm)
* [配置表单数据模型](#config-fdm)
* [测试表单数据模型](#test-fdm)

表单数据模型将类似于以下内容：

![form-data-model_l](assets/form-data-model_l.png)

**A.** 配置的数据源 **B.** 数据源架构 **C.** 可用服务 **D.** 数据模型对象 **E.** 已配置的服务

## 前提条件 {#prerequisites}

在开始之前，请确保您具有以下功能：

* MySQL数据库，其示例数据在的“先决条件”部分中说明 [创建您的第一个自适应表单](/help/forms/using/create-your-first-adaptive-form.md)
* MySQL JDBC驱动程序的OSGi包，如 [捆绑JDBC数据库驱动程序](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* 自适应表单，如第一个教程中所述 [创建自适应表单](/help/forms/using/create-adaptive-form.md)

## 步骤1:将MySQL数据库配置为数据源 {#config-database}

您可以配置不同类型的数据源以创建表单数据模型。 在本教程中，我们将配置您配置并填充示例数据的MySQL数据库。 有关其他受支持数据源及其配置方式的信息，请参阅 [AEM Forms数据集成](/help/forms/using/data-integration.md).

执行以下操作以配置MySQL数据库：

1. 将MySQL数据库的JDBC驱动程序安装为OSGi包：

   1. 以管理员身份登录AEM Forms创作实例，然后转到AEM Web控制台包。 默认URL为 [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

   1. 点按 **安装/更新**. 安 **上载/安装包** 对话框。

   1. 点按 **选择文件** 浏览并选择MySQL JDBC驱动程序OSGi包。 选择 **启动包** 和 **刷新包**，然后点按 **安装或更新**. 确保Oracle公司的MySQL JDBC驱动程序处于活动状态。 已安装驱动程序。

1. 将MySQL数据库配置为数据源：

   1. 转到AEM Web控制台(位于 [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. 定位 **Apache Sling连接池化数据源** 配置。 点按以在编辑模式下打开配置。
   1. 在配置对话框中，指定以下详细信息：

      * **数据源名称：** 您可以指定任何名称。 例如，指定 **WeRetailMySQL**.
      * **数据源服务属性名称**:指定包含数据源名称的服务属性的名称。 在将数据源实例注册为OSGi服务时指定。 例如， **datasource.name**.
      * **JDBC驱动程序类**:指定JDBC驱动程序的Java类名称。 对于MySQL数据库，请指定 **com.mysql.jdbc.驱动程序**.
      * **JDBC连接URI**:指定数据库的连接URL。 对于在端口3306和模式weretail上运行的MySQL数据库，URL为： `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **用户名：** 数据库的用户名。 需要启用JDBC驱动程序来建立与数据库的连接。
      * **密码：** 数据库的密码。 需要启用JDBC驱动程序来建立与数据库的连接。
      * **借用测试：** 启用 **借用测试** 选项。
      * **回访时测试：** 启用 **在返回时测试** 选项。
      * **验证查询：** 指定SQL SELECT查询以验证池中的连接。 查询必须至少返回一行。 例如， **选择&amp;ast;从customerdetails**.
      * **事务隔离**:将值设置为 **READ_COMMITTED**.

      将其他属性保留为默认值 [值](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) 点按 **保存**.
   将创建与以下类似的配置。

   ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## 步骤2:创建表单数据模型 {#create-fdm}

AEM Forms为 [创建表单数据模型](data-integration.md) 从配置的数据源。 您可以在表单数据模型中使用多个数据源。 对于我们的用例，我们将使用配置的MySQL数据源。

执行以下操作以创建表单数据模型：

1. 在AEM创作实例中，导航到 **Forms** >  **数据集成** s.
1. 点按 **创建** >  **表单数据模型**.
1. 在创建表单数据模型对话框中，指定 **name** ，以访问表单数据模型。 例如， **customer-shipping-billing-details**. 点按 **下一个**.
1. “选择数据源”屏幕列出了所有已配置的数据源。 选择 **WeRetailMySQL** 数据源和点按 **创建**.

   ![数据源选择](assets/data-source-selection.png)

的 **customer-shipping-billing-details** 表单数据模型已创建。

## 步骤3:配置表单数据模型 {#config-fdm}

配置表单数据模型涉及：

* 添加数据模型对象和服务
* 为数据模型对象配置读写服务

执行以下操作以配置表单数据模型：

1. 在AEM创作实例上，导航到 **Forms >数据集成**. 默认URL为 [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. 的 **customer-shipping-billing-details** 此处列出了您之前创建的表单数据模型。 在编辑模式下将其打开。

   所选数据源 **WeRetailMySQL** 在表单数据模型中配置。

   ![default-fdm](assets/default-fdm.png)

1. 展开WeRailMySQL数据源树。 从中选择以下数据模型对象和服务 **weretail** >  **customerdetails** 用于形成数据模型的架构：

   * **数据模型对象**:

      * id
      * name
      * shippingAddress
      * 城市
      * 状态
      * 邮政编码
   * **服务:**

      * get
      * 更新

   点按 **添加选定项** 将选定数据模型对象和服务添加到表单数据模型。

   ![weretail-schema](assets/weretail-schema.png)

   >[!NOTE]
   >
   >JDBC数据源的默认获取、更新和插入服务是随表单数据模型一起提供的。

1. 为数据模型对象配置读和写服务。

   1. 选择 **customerdetails** 数据模型对象和点按 **编辑属性**.
   1. 选择 **get** 从“读取服务”下拉列表中。 的 **id** 参数（customerdetails数据模型对象中的主键）将自动添加。 点按 ![aem_6_3_edit](assets/aem_6_3_edit.png) 并按如下方式配置参数。

      ![读 — 默认](assets/read-default.png)

   1. 同样，选择 **更新** 作为写入服务。 的 **customerdetails** 对象会自动添加为参数。 参数的配置如下所示。

      ![write-default](assets/write-default.png)

      添加和配置 **id** 参数如下所示。

      ![id-arg](assets/id-arg.png)

   1. 点按 **完成** 保存数据模型对象属性。 然后，点按 **保存** 保存表单数据模型。

      的 **get** 和 **更新** 服务将作为数据模型对象的默认服务添加。

      ![数据模型 — 对象](assets/data-model-object.png)

1. 转到 **服务** 选项卡和配置 **get** 和 **更新** 服务。

   1. 选择 **get** 服务和点按 **编辑属性**. 此时将打开属性对话框。
   1. 在编辑属性对话框中指定以下内容：

      * **标题**:指定服务的标题。 例如：检索送货地址。
      * **描述**:指定包含服务详细功能的描述。 例如：

         此服务从MySQL数据库中检索送货地址和其他客户详细信息

      * **输出模型对象**:选择包含客户数据的架构。 例如：

         customerdetail架构
      * **返回数组**:禁用 **返回数组** 选项。
      * **参数**:选择名为的参数 **ID**.

      点按 **完成**. 已配置从MySQL数据库检索客户详细信息的服务。

      ![shiiping-address-retrieval](assets/shiiping-address-retrieval.png)

   1. 选择 **更新** 服务和点按 **编辑属性**. 此时将打开属性对话框。

   1. 在编辑属性对话框中指定以下内容：

      * **标题**:指定服务的标题。 例如，更新发运地址。

      * **描述**:指定包含服务详细功能的描述。 例如：

         此服务更新MySQL数据库中的送货地址和相关字段

      * **输入模型对象**:选择包含客户数据的架构。 例如：

         customerdetail架构

      * **输出类型**:选择 **布尔值**.
      * **参数**:选择名为的参数 **ID** 和 **customerdetails**.

      点按 **完成**. 的 **更新** 配置了更新MySQL数据库中客户详细信息的服务。

      ![shiiping-address-update](assets/shiiping-address-update.png)



配置表单数据模型中的数据模型对象和服务。 您现在可以测试表单数据模型。

## 步骤4:测试表单数据模型 {#test-fdm}

您可以测试数据模型对象和服务，以验证表单数据模型是否配置正确。

执行以下操作以运行测试：

1. 转到 **模型** 选项卡，选择 **customerdetails** 数据模型对象，然后点按 **测试模型对象**.
1. 在 **测试模型/服务** 窗口，选择 **读取模型对象** 从 **选择模型/服务** 下拉菜单。
1. 在 **customerdetails** 部分，为 **id** 已配置的MySQL数据库中存在的参数，然后点按 **测试**.

   将获取并显示在 **输出** 区域，如下所示。

   ![测试读取模型](assets/test-read-model.png)

1. 同样，您也可以测试Write模型对象和服务。

   在以下示例中，更新服务成功更新了数据库中ID 7102715的地址详细信息。

   ![测试 — 写入模型](assets/test-write-model.png)

   现在，如果您再次测试id 7107215的读取模型服务，它将获取并显示更新后的客户详细信息，如下所示。

   ![已读更新](assets/read-updated.png)
