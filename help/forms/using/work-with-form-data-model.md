---
title: 使用表单数据模型
seo-title: Work with form data model
description: 数据集成提供了表单数据模型编辑器，用于配置和使用表单数据模型。
seo-description: Data Integration provides form data model editor to configure and work with form data models.
uuid: cd123d42-f7cf-489d-8182-f3a01a2a4799
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 2ee45ac0-bc15-403a-93fc-c8592afb967d
feature: Form Data Model
exl-id: 2dcbc459-5fa3-4712-a72e-159bdbad0a61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3166'
ht-degree: 0%

---

# 使用表单数据模型 {#work-with-form-data-model}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

数据集成提供了表单数据模型编辑器，用于配置和使用表单数据模型。

![](do-not-localize/data-integeration.png)

表单数据模型编辑器提供了直观的用户界面和工具，用于编辑和配置表单数据模型。 使用编辑器，您可以在表单数据模型中添加和配置来自关联数据源的数据模型对象、属性和服务。 此外，它还允许您创建数据模型对象和属性，而不使用数据源，并在以后将它们与相应的数据模型对象和属性绑定。 您还可以为数据模型对象属性生成和编辑示例数据，在预览时，可以使用这些属性预填充自适应表单和交互式通信。 您可以测试在表单数据模型中配置的数据模型对象和服务，以确保它与数据源正确集成。

如果您是Forms数据集成的新用户，并且尚未配置数据源或创建表单数据模型，请参阅以下主题：

* [AEM Forms数据集成](/help/forms/using/data-integration.md)
* [配置数据源](/help/forms/using/configure-data-sources.md)
* [创建表单数据模型](/help/forms/using/create-form-data-models.md)

有关可以使用表单数据模型编辑器执行的各种任务和配置的详细信息，请阅读。

>[!NOTE]
>
>您必须是这两者的成员 **fdm-author** 和 **forms-user** 群组，以便能够创建和使用表单数据模型。 请联系您的AEM管理员以成为组的成员。

## 添加数据模型对象和服务 {#add-data-model-objects-and-services}

如果您使用数据源创建表单数据模型，则可以使用表单数据模型编辑器添加数据模型对象和服务，配置其属性，在数据模型对象之间构建关联，以及测试表单数据模型和服务。

您可以在表单数据模型中添加来自可用数据源的数据模型对象和服务。 添加的数据模型对象显示在“模型”选项卡中，添加的服务则显示在“服务”选项卡中。

要添加数据模型对象和服务，请执行以下操作：

1. 登录AEM创作实例，导航到 **[!UICONTROL Forms >数据集成]**，然后打开要在其中添加数据模型对象的表单数据模型。
1. 在“数据源”窗格中，展开数据源以查看可用的数据模型对象和服务。
1. 选择要添加到表单数据模型的数据模型对象和服务，然后点按 **[!UICONTROL 添加选定项]**.

   ![选定对象](assets/selected-objects.png)

   “模型”(Model)选项卡显示所有数据模型对象及其添加到表单数据模型的属性的图形表示。 每个数据模型对象由表单数据模型中的一个框表示。

   ![模型选项卡](assets/model-tab.png)

   >[!NOTE]
   >
   >您可以按住并拖动数据模型对象框，以在内容区域中对其进行组织。 在表单数据模型中添加的所有数据模型对象在“数据源”窗格中都呈灰显状态。

   “服务”选项卡列出了添加的服务。

   ![services-tab](assets/services-tab.png)

   >[!NOTE]
   >
   >除了数据模型对象和服务之外，OData服务元数据文档还包括定义两个数据模型对象之间关联的导航属性。 有关更多信息，请参阅 [使用OData服务的导航属性](#work-with-navigation-properties-of-odata-services).

1. 点按 **[!UICONTROL 保存]** 保存表单模型对象。

   >[!NOTE]
   >
   >您可以使用自适应表单规则调用在表单数据模型的“服务”选项卡中配置的服务。 已配置的服务可在规则编辑器的调用服务操作中使用。有关在自适应表单规则中使用这些服务的详细信息，请参阅 [规则编辑器](/help/forms/using/rule-editor.md).

## 创建数据模型对象和子属性 {#create-data-model-objects-and-child-properties}

### 创建数据模型对象 {#create-data-model-objects}

虽然可以从配置的数据源添加数据模型对象，但也可以创建没有数据源的数据模型对象或实体。 当您未在表单数据模型中配置数据源时，此功能会特别有用。

要创建不含数据源的数据模型对象，请执行以下操作：

1. 登录AEM创作实例，导航到 **[!UICONTROL Forms >数据集成]**，然后打开要在其中创建数据模型对象或实体的表单数据模型。
1. 点按 **[!UICONTROL 创建实体]**.
1. 在创建数据模型对话框中，指定数据模型对象的名称，然后点按 **[!UICONTROL 添加]**. 数据模型对象被添加到表单数据模型中。 请注意，新添加的数据模型对象未绑定到数据源，并且没有如下图所示的任何属性。

   ![新实体](assets/new-entity.png)

接下来，可以在未绑定数据模型对象中添加子属性。

### 添加子属性 {#child-properties}

表单数据模型编辑器允许您在数据模型对象中创建子属性。 创建时的资产不会绑定到数据源中的任何资产。 您稍后可以将子属性与包含数据模型对象中的其他属性绑定。

要创建子属性，请执行以下操作：

1. 在表单数据模型中，选择数据模型对象并点按 **[!UICONTROL 创建子属性]**.
1. 在 **[!UICONTROL 创建子属性]** 对话框中，为属性指定名称和数据类型 **[!UICONTROL 名称]** 和 **[!UICONTROL 类型]** 字段。 您可以选择为属性指定标题和描述。
1. 如果属性是计算属性，则启用计算。 计算属性的值基于规则或表达式。 有关更多信息，请参阅 [编辑属性](#edit-properties).
1. 如果数据模型对象绑定到数据源，则添加的子属性将自动绑定到具有相同名称和数据类型的父数据模型对象的属性。

   要手动将子属性与数据模型对象属性绑定，请点按 **[!UICONTROL 绑定引用]** 字段。 的 **[!UICONTROL 选择对象]** 对话框列出了父数据模型对象中的所有属性。 选择要与绑定的属性，然后点按勾号图标。 请注意，您只能选择与子属性具有相同数据类型的属性。

1. 点按 **[!UICONTROL 完成]** 保存子属性并点按 **[!UICONTROL 保存]** 保存表单数据模型…… 子属性现已添加到数据模型对象。

创建数据模型对象和属性后，可以继续根据表单数据模型创建自适应表单和交互式通信。 之后，当您配置了可用的数据源后，您便可以将表单数据模型与数据源绑定。 绑定将在关联的自适应表单和交互式通信中自动更新。 有关使用表单数据模型创建自适应表单和交互式通信的更多信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md).

### 绑定数据模型对象和属性 {#bind-data-model-objects-and-properties}

当要与表单数据模型集成的数据源可用时，可以按照 [更新数据源](/help/forms/using/create-form-data-models.md#update). 然后，执行以下操作以绑定未绑定的数据模型对象和属性：

1. 在表单数据模型中，选择要与数据源绑定的未绑定数据源。
1. 点按 **[!UICONTROL 编辑属性]**.
1. 在 **[!UICONTROL 编辑属性]** 窗格，点按 **[!UICONTROL 绑定]** 字段。 它会打开 **[!UICONTROL 选择对象]** 对话框，其中列出了在表单数据模型中添加的数据源。

   ![select-object](assets/select-object.png)

1. 展开数据源树并选择要与其绑定的数据模型对象，然后点按勾号图标。
1. 点按 **[!UICONTROL 完成]** 保存属性，然后点按 **[!UICONTROL 保存]** 保存表单数据模型。 数据模型对象现在与数据源绑定。 请注意，数据模型对象不再标记为未绑定。

   ![绑定模型对象](assets/bound-model-object.png)

## 配置服务 {#configure-services}

要读取和写入数据模型对象的数据，请执行以下操作以配置读取和写入服务：

1. 选中数据模型对象顶部的复选框以将其选中并点按 **[!UICONTROL 编辑属性]**.

   ![edit-properties](assets/edit-properties.png)

   编辑属性以配置数据模型对象的读取和写入服务

   此时将打开编辑属性对话框。

   ![edit-properties-2](assets/edit-properties-2.png)

   编辑属性对话框

   >[!NOTE]
   >
   >除了数据模型对象和服务之外，OData服务元数据文档还包括定义两个数据模型对象之间关联的导航属性。 向表单数据模型添加OData服务数据源时，表单数据模型中有一项服务可用于数据模型对象中的所有导航属性。 您可以使用此服务读取相应数据模型对象的导航属性。
   >
   >有关使用该服务的详细信息，请参阅 [使用OData服务的导航属性](#work-with-navigation-properties-of-odata-services).

1. 切换 **[!UICONTROL 顶级对象]** 指定数据模型对象是否为顶级模型对象。

   在表单数据模型中配置的数据模型对象可用于基于表单数据模型的自适应表单内容浏览器的“数据模型对象”选项卡中。 在两个数据模型对象之间添加关联时，与之关联的数据模型对象将嵌套在“数据模型对象”(Data Model Objects)选项卡中与之关联的数据模型对象下。 如果嵌套数据模型是顶级对象，则它也将单独显示在“数据模型对象”(Data Model Objects)选项卡中。 因此，您将看到其两个条目，一个位于嵌套层次结构内部，另一个位于嵌套层次结构外部，这可能会令表单作者感到困惑。 要使关联的数据模型对象仅显示在嵌套层次结构中，请禁用顶级对象属性。

1. 为选定的数据模型对象选择读取和写入服务。 将显示服务的参数。

   ![读写服务](assets/read-write-services.png)

   为员工数据源配置的读写服务

1. 点按 ![aem_6_3_edit](assets/aem_6_3_edit.png) 用于将参数绑定到用户配置文件属性、请求属性或文字值的读取服务参数，并指定绑定值。 它将服务参数绑定到指定的绑定属性或文本值，该属性或文本值将作为参数传递给服务，以从数据源获取与指定值关联的详细信息。

   在本例中， `id` 参数将采用 `empid` 属性，并将其作为参数传递给读取服务。 它将从 `employee` 指定的数据模型对象 `empid`. 因此，如果您在 `empid` 字段中，读取服务将读取员工ID为00250的详细信息。

   此外，您还可以将参数设为必填或可选参数。

   ![edit-argument](assets/edit-argument.png)

   将id参数绑定到AEM用户配置文件的empid属性

1. 点按 **[!UICONTROL 完成]** 为了保存参数， **[!UICONTROL 完成]** 保存属性，然后 **[!UICONTROL 保存]** 保存表单数据模型。

## 添加关联 {#add-associations}

通常，数据源中的数据模型对象之间会构建关联。 关联可以是一对一或一对多。 例如，可以有多个与员工关联的依赖项。 它称为一对多关联，由 `1:n` 在连接关联数据模型对象的行上。 但是，如果关联返回给定员工ID的唯一员工名称，则它称为一对一关联。

将数据源中的关联数据模型对象添加到表单数据模型时，它们的关联将保留并显示为通过箭头线连接。 您可以在表单数据模型中跨不同数据源在数据模型对象之间添加关联。

>[!NOTE]
>
>JDBC数据源中的预定义关联不会保留在表单数据模型中。 您必须手动创建它们。

添加关联：

1. 选中数据模型对象顶部的复选框以将其选中并点按 **[!UICONTROL 添加关联]**. 将打开添加关联对话框。

   ![添加关联](assets/add-association.png)

   >[!NOTE]
   >
   >除了数据模型对象和服务之外，OData服务元数据文档还包括定义两个数据模型对象之间关联的导航属性。 在表单数据模型中添加关联时，可以使用这些导航属性。 有关更多信息，请参阅 [使用OData服务的导航属性](#work-with-navigation-properties-of-odata-services).

   将打开添加关联对话框。

   ![add-association-2](assets/add-association-2.png)

   “添加关联”对话框

1. 在添加关联窗格中：

   * 指定关联的标题。
   * 选择关联类型 — 一对一或一对多。
   * 选择要与其关联的数据模型对象。
   * 选择读取服务以从所选模型对象读取数据。 将显示读取服务参数。 编辑以根据需要更改参数，并将其绑定到要关联的数据模型对象的属性。

   在以下示例中，Dependents数据模型对象的读取服务的默认参数为 `dependentid`.

   ![add-association-example](assets/add-association-example.png)

   依赖项读取服务的默认参数为dependientd

   但是，参数必须是关联数据模型对象之间的通用属性，在本例中为 `Employeeid`. 因此， `Employeeid` 参数必须绑定到 `id` Employee数据模型对象的属性，以从Dependents数据模型对象中获取关联的依赖项详细信息。

   ![add-association-example-2](assets/add-association-example-2.png)

   更新了参数和绑定

   点按 **[!UICONTROL 完成]** 来保存参数。

1. 点按 **[!UICONTROL 完成]** 保存关联，然后 **[!UICONTROL 保存]** 保存表单数据模型。
1. 根据需要重复这些步骤以创建更多关联。

>[!NOTE]
>
>添加的关联将出现在数据模型对象框中，其中具有指定的标题和连接关联数据模型对象的线条。
>
>您可以通过选中对应的复选框并点按来编辑关联 **[!UICONTROL 编辑关联]**.

![添加关联](assets/added-association.png)

## 编辑属性 {#properties}

您可以编辑在表单数据模型中添加的数据模型对象的属性、其属性和服务。

要编辑属性，请执行以下操作：

1. 选中表单数据模型中的数据模型对象、属性或服务旁边的复选框。
1. 点按 **[!UICONTROL 编辑属性]**. 的 **[!UICONTROL 编辑属性]** 将打开所选模型对象、属性或服务的窗格。

   * **数据模型对象**:指定读写服务和编辑参数。
   * **属性**:指定属性的类型、子类型和格式。 您还可以指定所选属性是否是数据模型对象的主键。
   * **服务**:指定服务的输入模型对象、输出类型和参数。 对于Get服务，您可以指定它是否需要返回数组。

   ![edit-properties-service](assets/edit-properties-service.png)

   获取服务的“编辑属性”对话框

1. 点按 **[!UICONTROL 完成]** 保存属性，然后 **[!UICONTROL 保存]** 保存表单数据模型。

### 创建计算属性 {#computed}

computed属性是根据规则或表达式计算其值的属性。 使用规则，您可以将计算属性的值设置为文本字符串、数字、数学表达式的结果或表单数据模型中其他属性的值。

例如，您可以创建一个计算属性 **全名** 其值是现有 **名字** 和 **LastName** 属性。 为此，请执行以下操作：

1. 创建名为的新资产 `FullName` 其数据类型为字符串。
1. 启用 **[!UICONTROL 计算]** 点按 **[!UICONTROL 完成]** 创建资产。

   ![计算](assets/computed.png)

   将创建FullName计算属性。 请注意属性旁边的图标，以描述计算属性。

   ![computed-prop](assets/computed-prop.png)

1. 选择FullName属性并点按 **[!UICONTROL 编辑规则]**. 随即会打开规则编辑器窗口。
1. 在规则编辑器窗口中，点按 **[!UICONTROL 创建]**. A **[!UICONTROL 设置值]** 规则窗口打开。

   从选择选项下拉菜单中，选择 **[!UICONTROL 数学表达式]**. 其他可用选项包括 **[!UICONTROL 表单数据模型对象]** 和 **[!UICONTROL 字符串]**.

1. 在数学表达式中，选择 **[!UICONTROL 名字]** 和 **[!UICONTROL LastName]** 分别在第一和第二对象中。 选择 **[!UICONTROL plus]** 作为运算符。

   点按 **[!UICONTROL 完成]** 然后点按 **[!UICONTROL 关闭]** 以关闭规则编辑器窗口。 该规则类似于以下内容。

   ![规则](assets/rule.png)

1. 在表单数据模型上，点按 **[!UICONTROL 保存]**. 已配置计算属性。

## 使用OData服务的导航属性 {#work-with-navigation-properties-of-odata-services}

在OData服务中，导航属性用于定义两个数据模型对象之间的关联。 这些属性是在实体类型或复杂类型上定义的。 例如，在以下从示例的元数据文件提取的 [TripPin](https://www.odata.org/blog/trippin-new-odata-v4-sample-service/) OData示例服务中，人员实体包含三个导航属性 — 朋友、BestFriend和Trips。

有关导航属性的更多信息，请参阅 [OData文档](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part3-csdl/odata-v4.0-errata03-os-part3-csdl-complete.html#_Toc453752536).

```xml
<edmx:Edmx xmlns:edmx="https://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
<script/>
<edmx:DataServices>
<Schema xmlns="https://docs.oasis-open.org/odata/ns/edm" Namespace="Microsoft.OData.Service.Sample.TrippinInMemory.Models">
<EntityType Name="Person">
<Key>
<PropertyRef Name="UserName"/>
</Key>
<Property Name="UserName" Type="Edm.String" Nullable="false"/>
<Property Name="FirstName" Type="Edm.String" Nullable="false"/>
<Property Name="LastName" Type="Edm.String"/>
<Property Name="MiddleName" Type="Edm.String"/>
<Property Name="Gender" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.PersonGender" Nullable="false"/>
<Property Name="Age" Type="Edm.Int64"/>
<Property Name="Emails" Type="Collection(Edm.String)"/>
<Property Name="AddressInfo" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location)"/>
<Property Name="HomeAddress" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location"/>
<Property Name="FavoriteFeature" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature" Nullable="false"/>
<Property Name="Features" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature)" Nullable="false"/>
<NavigationProperty Name="Friends" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person)"/>
<NavigationProperty Name="BestFriend" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person"/>
<NavigationProperty Name="Trips" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Trip)"/>
</EntityType>
```

在表单数据模型中配置OData服务时，实体容器中的所有导航属性都可通过表单数据模型中的服务提供。 在此TripPin OData服务示例中， `Person` 实体容器可使用一个 `GET LINK` 服务。

以下重点介绍 `GET LINK of Person /People` 表单数据模型中的服务，它是 `Person` TripPin OData服务的实体。

![nav-prop-service](assets/nav-prop-service.png)

添加 `GET LINK` 服务到表单数据模型中的“服务”选项卡，您可以编辑属性以选择要在服务中使用的输出模型对象和导航属性。 例如，以下 `GET LINK of Person /People` 以下示例中的服务使用“行程”作为输出模型对象，导航属性使用“行程”。

![edit-prop-nav-prop](assets/edit-prop-nav-prop.png)

>[!NOTE]
>
>中的可用值 **[!UICONTROL 默认值]** 字段 **NavigationPropertyName** 参数取决于 **[!UICONTROL 返回数组？]** 切换按钮。 启用后，将显示“收藏集”类型的导航属性。

在此示例中，您还可以将输出模型对象选为“人员”，将导航属性参数选为“好友”或“BestFriend”(取决于 **[!UICONTROL 返回数组？]** 启用或禁用)。

![edit-prop-nav-prop2](assets/edit-prop-nav-prop2.png)

同样，您也可以选择 `GET LINK` 在表单数据模型中添加关联时，服务和配置其导航属性。 但是，要能够选择导航属性，请确保 **[!UICONTROL 绑定到字段]** 设置为 **[!UICONTROL 文字]**.

![add-association-nav-prop](assets/add-association-nav-prop.png)

## 生成和编辑示例数据 {#sample}

表单数据模型编辑器允许您为表单数据模型中的所有数据模型对象属性（包括计算属性）生成示例数据。 它是一组符合为每个属性配置的数据类型的随机值。 您还可以编辑和保存数据，即使重新生成示例数据，该数据也会保留。

执行以下操作以生成和编辑示例数据：

1. 打开表单数据模型并点按 **[!UICONTROL 编辑示例数据]**. 它会在“编辑示例数据”窗口中生成并显示示例数据。

   ![示例数据](assets/sample-data.png)

1. 在 **[!UICONTROL 编辑示例数据]** ，根据需要编辑数据，然后点按 **[!UICONTROL 保存]**.

接下来，您可以使用示例数据根据表单数据模型预填和测试交互式通信。 有关更多信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md).

## 测试数据模型对象和服务 {#test-data-model-objects-and-services}

您的表单数据模型已配置，但在投入使用之前，您可能希望测试配置的数据模型对象和服务是否按预期工作。 要测试数据模型对象和服务，请执行以下操作：

1. 在表单数据模型中选择数据模型对象或服务，然后点按 **[!UICONTROL 测试模型对象]** 或 **[!UICONTROL 测试服务]**，分别为。

   “测试表单数据模型”(Test Form Data Model)窗口打开。

   ![测试数据模型](assets/test-data-model.png)

1. 在“测试表单数据模型”窗口中，从“输入”窗格中选择要测试的数据模型对象或服务。

1. 在测试代码中指定参数值，然后点按 **[!UICONTROL 测试]**. 成功的测试会在“输出”窗格中返回输出。

   ![test-data-model-2](assets/test-data-model-2.png)

同样，您也可以测试表单数据模型中的其他数据模型对象和服务。

## 后续步骤 {#next-steps}

您有一个工作表单数据模型，该模型现已准备好在自适应表单和交互式通信工作流中使用。 有关更多信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md).
