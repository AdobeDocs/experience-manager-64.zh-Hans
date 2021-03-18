---
title: “教程：创建表单数据模型“
seo-title: 创建表单数据模型教程
description: AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户用户档案、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 了解如何将MySQL数据库配置为数据源，创建、配置和测试表单数据模型。
seo-description: AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户用户档案、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 了解如何将MySQL数据库配置为数据源，创建、配置和测试表单数据模型。
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: 自适应表单
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 1%

---


# 教程：创建表单数据模型{#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

本教程是[创建您的第一个自适应表单](/help/forms/using/create-your-first-adaptive-form.md)系列中的一个步骤。 建议按照时间顺序按照该系列进行操作，以了解、执行和演示完整的教程用例。

## 关于教程{#about-the-tutorial}

AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户用户档案、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 您可以在表单数据模型中配置数据模型对象和服务，并将其与自适应表单关联。 自适应表单字段绑定到数据模型对象属性。 这些服务使您能够预填自适应表单并将提交的表单数据写入数据模型对象。

有关表单数据集成和表单数据模型的详细信息，请参阅[AEM Forms数据集成](/help/forms/using/data-integration.md)。

本教程将指导您完成准备、创建、配置表单数据模型以及将表单数据模型与自适应表单关联的步骤。 在本教程的结尾，您将能够：

* [将MySQL数据库配置为数据源](#config-database)
* [使用MySQL数据库创建表单数据模型](#create-fdm)
* [配置表单数据模型](#config-fdm)
* [测试表单数据模型](#test-fdm)

表单数据模型将类似于：

![form-data-model_l](assets/form-data-model_l.png)

**A.配** 置的数 **据源B.** 数据源 **模式** C.Available  **services** D.D.Data  **** model对象E.C.Configured Services

## 前提条件 {#prerequisites}

在开始之前，请确保您具备以下各项：

* MySQL数据库，其示例数据在[的“入门项目”部分中说明创建您的第一个自适应表单](/help/forms/using/create-your-first-adaptive-form.md)
* [捆绑JDBC数据库驱动程序](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)中说明的MySQL JDBC驱动程序的OSGi捆绑
* 如第一个教程[创建自适应表单](/help/forms/using/create-adaptive-form.md)中所述

## 第1步：将MySQL数据库配置为数据源{#config-database}

您可以配置不同类型的数据源以创建表单数据模型。 在本教程中，我们将配置您配置并填充示例数据的MySQL数据库。 有关其他受支持数据源以及如何配置数据源的信息，请参阅[AEM Forms数据集成](/help/forms/using/data-integration.md)。

执行以下操作以配置MySQL数据库：

1. 将MySQL数据库的JDBC驱动程序作为OSGi包安装：

   1. 以管理员身份登录到AEM Forms作者实例，然后转到AEM Web控制台包。 默认URL为[http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)。

   1. 点按&#x200B;**安装/更新**。 将显示&#x200B;**上载/安装包**&#x200B;对话框。

   1. 点按&#x200B;**选择文件**&#x200B;以浏览并选择MySQL JDBC驱动程序OSGi包。 选择&#x200B;**开始包**&#x200B;和&#x200B;**刷新包**，然后点按&#x200B;**安装或更新**。 确保Oracle Corporation的MySQL JDBC驱动程序处于活动状态。 已安装驱动程序。

1. 将MySQL数据库配置为数据源：

   1. 转到位于[http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)的AEM Web控制台。
   1. 找到&#x200B;**Apache Sling Connection Pooled DataSource**&#x200B;配置。 点按可在编辑模式下打开配置。
   1. 在配置对话框中，指定以下详细信息：

      * **数据源名称：** 您可以指定任何名称。例如，指定&#x200B;**WeRetailMySQL**。
      * **DataSource服务属性名称**:指定包含DataSource名称的服务属性的名称。将数据源实例注册为OSGi服务时指定。 例如，**datasource.name**。
      * **JDBC驱动程序类**:指定JDBC驱动程序的Java类名。对于MySQL数据库，请指定&#x200B;**com.mysql.jdbc.Driver**。
      * **JDBC连接URI**:指定数据库的连接URL。对于在端口3306和模式 weretail上运行的MySQL数据库，URL为：`jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **用户名：** 数据库的用户名。需要启用JDBC驱动程序以与数据库建立连接。
      * **口令：** 数据库的口令。需要启用JDBC驱动程序以与数据库建立连接。
      * **借阅时测试：** 启用 **借阅** 测试。
      * **返回时测试：** 启用 **返回** 时测试。
      * **验证查询:** 指定SQL SELECT查询以验证池中的连接。查询必须至少返回一行。 例如，**选择&amp;ast;自customerdetails**。
      * **事务隔离**:将值设置 **为READ_COMMITTED**。

      将其他属性保留为默认值[值](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html)，然后点按&#x200B;**保存**。
   将创建与以下内容类似的配置。

   ![关系型数据库 — 数据源配置](assets/relational-database-data-source-configuration.png)

## 第2步：创建表单数据模型{#create-fdm}

AEM Forms为[从配置的数据源创建表单数据模型](data-integration.md)提供了直观的用户界面。 您可以在表单数据模型中使用多个数据源。 对于我们的用例，我们将使用已配置的MySQL数据源。

执行以下操作以创建表单数据模型：

1. 在AEM创作实例中，导航到&#x200B;**Forms** > **数据集成**。
1. 点按&#x200B;**创建** > **表单数据模型**。
1. 在“创建表单数据模型”对话框中，为表单数据模型指定&#x200B;**名称**。 例如，**customer-shipping-billing-details**。 点按&#x200B;**下一步**。
1. 选择数据源屏幕会列表所有配置的数据源。 选择&#x200B;**WeRetailMySQL**&#x200B;数据源，然后点按&#x200B;**创建**。

   ![数据源选择](assets/data-source-selection.png)

将创建&#x200B;**customer-shipping-billing-details**&#x200B;表单数据模型。

## 第3步：配置表单数据模型{#config-fdm}

配置表单数据模型涉及：

* 添加数据模型对象和服务
* 为数据模型对象配置读写服务

执行以下操作以配置表单数据模型：

1. 在AEM作者实例上，导航到&#x200B;**Forms >数据集成**。 默认URL为[http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm)。
1. 此处列出了您之前创建的&#x200B;**customer-shipping-billing-details**&#x200B;表单数据模型。 在编辑模式下打开它。

   所选数据源&#x200B;**WeRetailMySQL**&#x200B;是在表单数据模型中配置的。

   ![default-fdm](assets/default-fdm.png)

1. 展开WeRailMySQL数据源树。 从&#x200B;**weretail** > **customerdetails**&#x200B;模式中选择以下数据模型对象和服务以形成数据模型：

   * **数据模型对象**:

      * id
      * name
      * shippingAddress
      * 城市
      * 状态
      * zipcode
   * **服务:**

      * 获取
      * 更新

   点按&#x200B;**添加选定**，将选定的数据模型对象和服务添加到表单数据模型。

   ![weretail-模式](assets/weretail-schema.png)

   >[!NOTE]
   >
   >JDBC数据源的默认get、update和insert服务是随表单数据模型提供的。

1. 为数据模型对象配置读和写服务。

   1. 选择&#x200B;**customerdetails**&#x200B;数据模型对象，然后点按&#x200B;**编辑属性**。
   1. 从“读取服务”下拉菜单中选择&#x200B;**get**。 将自动添加&#x200B;**id**&#x200B;参数，该参数是customerdetails数据模型对象中的主键。 点按![aem_6_3_edit](assets/aem_6_3_edit.png)并配置参数，如下所示。

      ![read-default](assets/read-default.png)

   1. 同样，选择&#x200B;**update**&#x200B;作为写入服务。 **customerdetails**&#x200B;对象将自动添加为参数。 参数的配置如下所示。

      ![write-default](assets/write-default.png)

      按如下添加和配置&#x200B;**id**&#x200B;参数。

      ![id-arg](assets/id-arg.png)

   1. 点按&#x200B;**完成**&#x200B;以保存数据模型对象属性。 然后，点按&#x200B;**保存**&#x200B;以保存表单数据模型。

      将&#x200B;**get**&#x200B;和&#x200B;**update**&#x200B;服务添加为数据模型对象的默认服务。

      ![数据模型对象](assets/data-model-object.png)

1. 转到&#x200B;**服务**&#x200B;选项卡并配置&#x200B;**get**&#x200B;和&#x200B;**update**&#x200B;服务。

   1. 选择&#x200B;**get**&#x200B;服务，然后点按&#x200B;**编辑属性**。 属性对话框打开。
   1. 在“编辑属性”对话框中指定以下内容：

      * **标题**:指定服务的标题。例如：检索发运地址。
      * **描述**:指定包含服务详细功能的说明。例如：

         此服务从MySQL数据库检索发运地址和其他客户详细信息

      * **输出模型对象**:选择包含模式数据的客户。例如：

         customerdetail模式
      * **返回数组**:禁用“ **返回** 图形”选项。
      * **参数**:选择名为 **ID的参数**。

      点按&#x200B;**完成**。已配置从MySQL数据库检索客户详细信息的服务。

      ![shiiping-address-retrieval](assets/shiiping-address-retrieval.png)

   1. 选择&#x200B;**update**&#x200B;服务，然后点按&#x200B;**编辑属性**。 属性对话框打开。

   1. 在“编辑属性”对话框中指定以下内容：

      * **标题**:指定服务的标题。例如，更新发货地址。

      * **描述**:指定包含服务详细功能的说明。例如：

         此服务更新MySQL数据库中的发运地址和相关字段

      * **输入模型对象**:选择包含模式数据的客户。例如：

         customerdetail模式

      * **输出类型**:选 **择BOOLEAN**。
      * **参数**:选择名为ID和 **** customerdetails **的参数**。

      点按&#x200B;**完成**。已配置用于更新MySQL数据库中客户详细信息的&#x200B;**update**&#x200B;服务。

      ![shiiping-address-update](assets/shiiping-address-update.png)



配置表单数据模型中的数据模型对象和服务。 您现在可以测试表单数据模型。

## 第4步：测试表单数据模型{#test-fdm}

您可以测试数据模型对象和服务，以验证表单数据模型配置是否正确。

执行以下操作以运行测试：

1. 转到&#x200B;**Model**&#x200B;选项卡，选择&#x200B;**customerdetails**&#x200B;数据模型对象，然后点按&#x200B;**测试模型对象**。
1. 在&#x200B;**测试模型/服务**&#x200B;窗口中，从&#x200B;**选择模型/服务**&#x200B;下拉菜单中选择&#x200B;**读取模型对象**。
1. 在&#x200B;**customerdetails**&#x200B;部分中，为配置的MySQL数据库中存在的&#x200B;**id**&#x200B;参数指定一个值，然后点按&#x200B;**Test**。

   将获取与指定ID关联的客户详细信息并在&#x200B;**Output**&#x200B;部分中显示，如下所示。

   ![测试读模型](assets/test-read-model.png)

1. 同样，您也可以测试Write模型对象和服务。

   在以下示例中，更新服务成功更新了数据库中id 7102715的地址详细信息。

   ![测写模型](assets/test-write-model.png)

   现在，如果您再次测试id 7107215的读取模型服务，它将获取并显示更新的客户详细信息，如下所示。

   ![read-updated](assets/read-updated.png)

