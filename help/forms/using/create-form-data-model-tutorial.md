---
title: “教程：创建表单数据模型”
seo-title: Create form data model for Interactive Communication
description: 为交互式通信创建表单数据模型
seo-description: Create form data model for Interactive Communication
uuid: f7483d27-b468-4e6c-a849-f8e084f73e1e
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: ef873c07-be89-4cd0-8913-65765b989f90
feature: Interactive Communication
exl-id: f767e47c-f5a6-478c-ac56-00d519a627cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2760'
ht-degree: 0%

---

# 教程：创建表单数据模型 {#tutorial-create-form-data-model}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

为交互式通信创建表单数据模型

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

本教程是 [创建您的第一个交互式通信](/help/forms/using/create-your-first-interactive-communication.md) 系列。 建议按照时间顺序排列系列，以了解、执行和演示完整的教程用例。

## 关于教程 {#about-the-tutorial}

AEM Forms数据集成模块允许您从不同的后端数据源(如AEM用户配置文件、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库)创建表单数据模型。 您可以在表单数据模型中配置数据模型对象和服务，并将其与自适应表单相关联。 自适应表单字段绑定到数据模型对象属性。 利用这些服务，您可以预填自适应表单，并将提交的表单数据写回数据模型对象。

有关表单数据集成和表单数据模型的更多信息，请参阅 [AEM Forms数据集成](data-integration.md).

本教程将指导您完成准备、创建、配置表单数据模型并将其与交互式通信相关联的步骤。 在本教程结束时，您将能够：

* [设置数据库](#step-set-up-the-database)
* [将MySQL数据库配置为数据源](#step-configure-mysql-database-as-data-source)
* [创建表单数据模型](#step-create-form-data-model)
* [配置表单数据模型](#step-configure-form-data-model)
* [测试表单数据模型](#step-test-form-data-model-and-services)

表单数据模型类似于以下内容：

![form_data_model_callouts](assets/form_data_model_callouts.png)

**A.** 配置的数据源 **B.** 数据源架构 **C.** 可用服务 **D.** 数据模型对象 **E.** 已配置的服务

## 前提条件 {#prerequisites}

在开始之前，请确保您具有以下功能：

* MySQL数据库，其中的示例数据在 [设置数据库](#step-set-up-the-database) 中。
* MySQL JDBC驱动程序的OSGi包，如 [捆绑JDBC数据库驱动程序](https://helpx.adobe.com/experience-manager/6-3/sites-developing/jdbc.html#bundling-the-jdbc-database-driver)

## 步骤1:设置数据库 {#step-set-up-the-database}

数据库对于创建交互式通信至关重要。 本教程使用数据库来显示交互式通信的表单数据模型和持久性功能。 设置包含客户、帐单和调用表的数据库。\
下图说明了客户表的示例数据：

![sample_data_cust](assets/sample_data_cust.png)

使用以下DDL语句创建 **客户** 表。

```sql
CREATE TABLE `customer` (
   `mobilenum` int(11) NOT NULL,
   `name` varchar(45) NOT NULL,
   `address` varchar(45) NOT NULL,
   `alternatemobilenumber` int(11) DEFAULT NULL,
   `relationshipnumber` int(11) DEFAULT NULL,
   `customerplan` varchar(45) DEFAULT NULL,
   PRIMARY KEY (`mobilenum`),
   UNIQUE KEY `mobilenum_UNIQUE` (`mobilenum`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

使用以下DDL语句创建 **票据** 表。

```sql
CREATE TABLE `bills` (
   `billplan` varchar(45) NOT NULL,
   `latepayment` decimal(4,2) NOT NULL,
   `monthlycharges` decimal(4,2) NOT NULL,
   `billdate` date NOT NULL,
   `billperiod` varchar(45) NOT NULL,
   `prevbal` decimal(4,2) NOT NULL,
   `callcharges` decimal(4,2) NOT NULL,
   `confcallcharges` decimal(4,2) NOT NULL,
   `smscharges` decimal(4,2) NOT NULL,
   `internetcharges` decimal(4,2) NOT NULL,
   `roamingnational` decimal(4,2) NOT NULL,
   `roamingintnl` decimal(4,2) NOT NULL,
   `vas` decimal(4,2) NOT NULL,
   `discounts` decimal(4,2) NOT NULL,
   `tax` decimal(4,2) NOT NULL,
   PRIMARY KEY (`billplan`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

使用以下DDL语句创建 **调用** 表。

```sql
CREATE TABLE `calls` (
   `mobilenum` int(11) DEFAULT NULL,
   `calldate` date DEFAULT NULL,
   `calltime` varchar(45) DEFAULT NULL,
   `callnumber` int(11) DEFAULT NULL,
   `callduration` varchar(45) DEFAULT NULL,
   `callcharges` decimal(4,2) DEFAULT NULL,
   `calltype` varchar(45) DEFAULT NULL
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

的 **调用** 表包含呼叫详细信息，如呼叫日期、呼叫时间、呼叫号码、呼叫持续时间和呼叫费用。 的 **客户** 表可使用移动设备号码(mobilenum)字段链接到调用表。 对于 **客户** 表中，有多个记录 **调用** 表。 例如，您可以检索 **1457892541** 通过引用 **调用** 表。

的 **票据** 表包括帐单详细信息，如帐单日期、帐单期间、月费和电话费。 的 **客户** 表链接到 **票据** 表。 在 **客户** 表。 的 **票据** 表包括所有现有计划的定价详细信息。 例如，您可以检索 **莎拉** 从 **客户** 表，并使用这些详细信息从中检索定价详细信息 **票据** 表。

## 步骤2:将MySQL数据库配置为数据源 {#step-configure-mysql-database-as-data-source}

您可以配置不同类型的数据源以创建表单数据模型。 在本教程中，您将配置已配置并填充示例数据的MySQL数据库。 有关其他受支持数据源及其配置方式的信息，请参阅 [AEM Forms数据集成](data-integration.md).

执行以下操作以配置MySQL数据库：

1. 将MySQL数据库的JDBC驱动程序安装为OSGi包：

   1. 以管理员身份登录AEM Forms创作实例，然后转到AEM Web控制台包。 默认URL为 [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
   1. 点按 **安装/更新**. 安 **上载/安装包** 对话框。
   1. 点按 **选择文件** 浏览并选择MySQL JDBC驱动程序OSGi包。 选择 **启动包** 和 **刷新包**，然后点按 **安装** 或 **更新**. 确保Oracle公司的MySQL JDBC驱动程序处于活动状态。 已安装驱动程序。

1. 将MySQL数据库配置为数据源：

   1. 转到AEM Web控制台(位于 [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. 定位 **Apache Sling连接池化数据源** 配置。 点按以在编辑模式下打开配置。
   1. 在配置对话框中，指定以下详细信息：

      * **数据源名称：** 您可以指定任何名称。 例如，指定 **MySQL**.
      * **数据源服务属性名称**:指定包含数据源名称的服务属性的名称。 在将数据源实例注册为OSGi服务时指定。 例如， **datasource.name**.
      * **JDBC驱动程序类**:指定JDBC驱动程序的Java类名称。 对于MySQL数据库，请指定 **com.mysql.jdbc.驱动程序**.
      * **JDBC连接URI**:指定数据库的连接URL。 对于在端口3306和模式电信上运行的MySQL数据库，URL为： `jdbc:mysql://[server]:3306/teleca?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **用户名：** 数据库的用户名。 需要启用JDBC驱动程序来建立与数据库的连接。
      * **密码：** 数据库的密码。 需要启用JDBC驱动程序来建立与数据库的连接。
      * **借用测试：** 启用 **借用测试** 选项。
      * **回访时测试：** 启用 **在返回时测试** 选项。
      * **验证查询：** 指定SQL SELECT查询以验证池中的连接。 查询必须至少返回一行。 例如， **选择&amp;ast;从客户**.
      * **事务隔离**:将值设置为 **READ_COMMITTED**.

   将其他属性保留为默认值 [值](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) 点按 **保存**.

   将创建与以下类似的配置。

   ![apache_configuration](assets/apache_configuration.png)

## 步骤3:创建表单数据模型 {#step-create-form-data-model}

AEM Forms为 [创建表单数据模式](data-integration.md)l来自配置的数据源。 您可以在表单数据模型中使用多个数据源。 对于本教程中的用例，您将使用MySQL作为数据源。

执行以下操作以创建表单数据模型：

1. 在AEM创作实例中，导航到 **Forms** >  **数据集成**.
1. 点按 **创建** >  **表单数据模型**.
1. 在“创建表单数据模型”向导中，指定 **name** ，以访问表单数据模型。 例如， **FDM_Create_First_IC**. 点按 **下一个**.
1. “选择数据源”屏幕列出了所有已配置的数据源。 选择 **MySQL** 数据源和点按 **创建**.

   ![fdm_mysql_data_source](assets/fdm_mysql_data_source.png)

1. 单击 **完成**. 的 **FDM_Create_First_IC** 表单数据模型已创建。

## 步骤4:配置表单数据模型 {#step-configure-form-data-model}

配置表单数据模型包括：

* [添加数据模型对象和服务](#add-data-model-objects-and-services)
* [为数据模型对象创建计算子属性](#create-computed-child-properties-for-data-model-object)
* [在数据模型对象之间添加关联](#add-associations-between-data-model-objects)
* [编辑数据模型对象属性](#edit-data-model-object-properties)
* [为数据模型对象配置服务](#configure-services)

### 添加数据模型对象和服务 {#add-data-model-objects-and-services}

1. 在AEM创作实例上，导航到 **Forms** > **数据集成**. 默认URL为 [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. 的 **FDM_Create_First_IC** 此处列出了您之前创建的表单数据模型。 选择它并点按 **编辑**.

   所选数据源 **MySQL** 显示在 **数据源** 中。

   ![mysql_fdm](assets/mysql_fdm.png)

1. 展开 **MySQL** 数据源树。 从中选择以下数据模型对象和服务 **电信** 架构：

   * **数据模型对象**:

      * 票据
      * 调用
      * 客户
   * **服务:**

      * get
      * 更新

   点按 **添加选定项** 将选定数据模型对象和服务添加到表单数据模型。

   ![select_data_model_objs_services](assets/select_data_model_objs_services.png)

   清单、调用和客户数据模型对象显示在 **模型** 选项卡。 获取和更新服务显示在 **服务** 选项卡。

   ![data_model_objects](assets/data_model_objects.png)

### 为数据模型对象创建计算子属性 {#create-computed-child-properties-for-data-model-object}

computed属性是根据规则或表达式计算其值的属性。 使用规则，您可以将计算属性的值设置为文本字符串、数字、数学表达式的结果或表单数据模型中其他属性的值。

根据用例，创建 **乌萨盖查尔** 子计算属性 **票据** 数据模型对象使用以下数学表达式：

* 使用费=通话费+电话会议费+短信费+移动互联网费+漫游国家+漫游国际+ VAS（所有这些属性都存在于帐单数据模型对象中）

   有关 **乌萨盖查尔** 子计算属性，请参阅 [规划交互式通信](/help/forms/using/planning-interactive-communications.md).

执行以下步骤，为清单数据模型对象创建计算的子属性：

1. 选中 **票据** 数据模型对象进行选择并点按 **创建子属性**.
1. 在 **创建子属性** 窗格：

   1. 输入 **乌萨盖查尔** 作为子属性的名称。
   1. 启用 **计算**.
   1. 选择 **浮动** 作为类型并点按 **完成** 将子属性添加到 **票据** 数据模型对象。

   ![create_child_property_float](assets/create_child_property_float.png)

1. 点按 **编辑规则** 以打开规则编辑器。
1. 点按 **创建**. 的 **设置值** 规则窗口打开。
1. 从选择选项下拉菜单中，选择 **数学表达式**.

   ![usage_carges_rule_editor](assets/usage_charges_rule_editor.png)

1. 在数学表达式中，选择 **催缴费** 和 **concallcharces** 分别作为第一和第二对象。 选择 **plus** 作为运算符。 在数学表达式中点按，然后点按 **扩展表达式** 添加 **smscharges**, **internetcarines**, **罗马尼亚**, **roamingintnl**&#x200B;和 **vas** 对象。

   下图描述了规则编辑器中的数学表达式：

   ![usage_charges_rule_all](assets/usage_charges_rule_all.png)

1. 点按 **完成**. 将在规则编辑器中创建规则。
1. 点按 **关闭** 以关闭规则编辑器窗口。

### 在数据模型对象之间添加关联 {#add-associations-between-data-model-objects}

定义数据模型对象后，即可在它们之间构建关联。 关联可以是一对一或一对多。 例如，可以有多个与员工关联的依赖项。 它称为一对多关联，由1:n在连接关联数据模型对象的线上描述。 但是，如果关联返回给定员工ID的唯一员工名称，则它称为一对一关联。

将数据源中的关联数据模型对象添加到表单数据模型时，它们的关联将保留并显示为通过箭头线连接。

根据用例，在数据模型对象之间创建以下关联：

| 关联 | 数据模型对象 |
|---|---|
| 1:n | customer:calls（在每月账单中，可以向客户关联多个调用） |
| 1:1 | 客户：帐单（一个账单与某个特定月份的客户关联） |

执行以下步骤以在数据模型对象之间创建关联：

1. 选中 **客户** 数据模型对象进行选择并点按 **添加关联**. 的 **添加关联** 属性窗格打开。
1. 在 **添加关联** 窗格：

   * 指定关联的标题。 它是一个可选字段。
   * 选择 **一对多** 从 **类型** 下拉列表。
   * 选择 **调用** 从 **模型对象** 下拉列表。
   * 选择 **get** 从 **服务** 下拉列表。
   * 点按 **添加** 链接 **客户** 数据模型对象到 **调用** 使用属性的数据模型对象。 根据用例，调用数据模型对象必须链接到客户数据模型对象中的移动号码属性。 的 **添加参数** 对话框。

   ![add_association](assets/add_association.png)

1. 在 **添加参数** 对话框：

   * 选择 **mobilenum** 从 **名称** 下拉列表。 移动号码属性是客户和调用数据模型对象中可用的通用属性。 因此，它用于在客户和调用数据模型对象之间创建关联。

      对于客户数据模型对象中可用的每个移动设备号码，调用表中有多个可用的调用记录。

   * 为参数指定可选标题和描述。
   * 选择 **客户** 从 **绑定到** 下拉列表。
   * 选择 **mobilenum** 从 **绑定值** 下拉列表。
   * 点按 **添加**.

   ![add_association_argument](assets/add_association_argument.png)

   mobilenum属性显示在 **参数** 中。

   ![add_argument_association](assets/add_argument_association.png)

1. 点按 **完成** 在客户和调用数据模型对象之间创建1:n关联。

   在客户和调用数据模型对象之间创建关联后，在客户和清单数据模型对象之间创建1:1关联。

1. 选中 **客户** 数据模型对象进行选择并点按 **添加关联**. 的 **添加关联** 属性窗格打开。
1. 在 **添加关联** 窗格：

   * 指定关联的标题。 它是一个可选字段。
   * 选择 **一对一** 从 **类型** 下拉列表。
   * 选择 **票据** 从 **模型对象** 下拉列表。
   * 选择 **get** 从 **服务** 下拉列表。 的 **计费计划** 资产（清单表的主要键）已在 **参数** 中。

      帐单和客户数据模型对象分别使用帐单计划（帐单）和客户计划（客户）属性进行链接。 在这些属性之间创建绑定，以检索MySQL数据库中任何可用客户的计划详细信息。

   * 选择 **客户** 从 **绑定到** 下拉列表。
   * 选择 **customerplan** 从 **绑定值** 下拉列表。
   * 点按 **完成** 以在计费计划属性和customerplan属性之间创建绑定。

   ![add_association_customer_bills](assets/add_association_customer_bills.png)

   下图描述了数据模型对象与用于在数据模型对象之间创建关联的属性之间的关联：

   ![fdm_associations](assets/fdm_associations.gif)

### 编辑数据模型对象属性 {#edit-data-model-object-properties}

在客户和其他数据模型对象之间创建关联后，编辑客户属性以定义属性，根据该属性从数据模型对象中检索数据。 根据用例，移动号码用作属性，从客户数据模型对象中检索数据。

1. 选中 **客户** 数据模型对象进行选择并点按 **编辑属性**. 的 **编辑属性** 窗格。
1. 指定 **客户** 作为 **顶级模型对象**.
1. 选择 **get** 从 **读取服务** 下拉列表。
1. 在 **参数** 部分：

   * 选择 **请求属性** 从 **绑定到** 下拉列表。
   * 指定 **mobilenum** 作为绑定值。

1. 选择 **更新** 从 **写入** 服务下拉列表。
1. 在 **参数** 部分：

   * 对于 **mobilenum** 属性，选择 **客户** 从 **绑定到** 下拉列表。
   * 选择 **mobilenum** 从 **绑定值** 下拉列表。

1. 点按 **完成** 以保存属性。

   ![configure_services_customer](assets/configure_services_customer.png)

1. 选中 **调用** 数据模型对象进行选择并点按 **编辑属性**. 的 **编辑属性** 窗格。
1. 禁用 **顶级模型对象** 表示 **调用** 数据模型对象。
1. 点按 **完成**.

   重复步骤8 - 10以配置 **票据** 数据模型对象。

### 配置服务 {#configure-services}

1. 转到 **服务** 选项卡。
1. 选择 **get** 服务和点按 **编辑属性**. 的 **编辑属性** 窗格。
1. 在 **编辑属性** 窗格：

   * 输入可选标题和描述。
   * 选择 **客户** 从 **输出模型对象** 下拉列表。
   * 点按 **完成** 以保存属性。

   ![edit_properties_get_details](assets/edit_properties_get_details.png)

1. 选择 **更新** 服务和点按 **编辑属性**. 的 **编辑属性** 窗格。
1. 在 **编辑属性** 窗格：

   * 输入可选标题和描述。
   * 选择 **客户** 从 **输入模型对象** 下拉列表。
   * 点按 **完成**.
   * 点按 **保存** 保存表单数据模型。

   ![update_service_properties](assets/update_service_properties.png)

## 步骤5:测试表单数据模型和服务 {#step-test-form-data-model-and-services}

您可以测试数据模型对象和服务，以验证表单数据模型是否配置正确。

执行以下操作以运行测试：

1. 转到 **模型** 选项卡，选择 **客户** 数据模型对象，然后点按 **测试模型对象**.
1. 在 **测试表单数据模型** 窗口，选择 **读取模型对象** 从 **选择模型/服务** 下拉列表。
1. 在 **输入** 部分，为 **mobilenum** 配置的MySQL数据库中存在的属性，然后点按 **测试**.

   将获取与指定的mobilenum属性关联的客户详细信息，并将其显示在“输出”部分中，如下所示。 关闭对话框。

   ![test_data_model](assets/test_data_model.png)

1. 转到 **服务** 选项卡。
1. 选择 **get** 服务和点按 **测试服务。**
1. 在 **输入** 部分，为 **mobilenum** 配置的MySQL数据库中存在的属性，然后点按 **测试**.

   将获取与指定的mobilenum属性关联的客户详细信息，并将其显示在“输出”部分中，如下所示。 关闭对话框。

   ![test_service](assets/test_service.png)

### 编辑和保存示例数据 {#edit-and-save-sample-data}

表单数据模型编辑器允许您为表单数据模型中的所有数据模型对象属性（包括计算属性）生成示例数据。 它是一组符合为每个属性配置的数据类型的随机值。 您还可以编辑和保存数据，即使重新生成示例数据，该数据也会保留。

执行以下操作以生成、编辑和保存示例数据：

1. 在表单数据模型页面上，点按 **编辑示例数据**. 它会在“编辑示例数据”窗口中生成并显示示例数据。

   ![edit_sample_data](assets/edit_sample_data.png)

1. 在 **编辑示例数据** ，根据需要编辑数据，然后点按 **保存**. 关闭窗口。
