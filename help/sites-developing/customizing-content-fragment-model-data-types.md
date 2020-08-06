---
title: 请勿发布，但不DELETE为内容片段模型自定义数据类型
seo-title: 为内容片段模型自定义数据类型
description: 可以自定义内容片段模型中使用的数据类型。
seo-description: 可以自定义内容片段模型中使用的数据类型。
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# 请勿发布，但不DELETE为内容片段模型自定义数据类型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[内容片段](/help/assets/content-fragments.md) ，基于内 [容片段模型](/help/assets/content-fragments-models.md)。 这些模型由不同数 [据类型](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 的元素构建。

各种数据类型现成可用，包括单行文本、多行富文本、数字字段、布尔选择器、下拉菜单选项、日期和时间等。 AEM用户可以根据相应片段的编辑意图选择数据类型。 这使您能够满足简单文本模型到具有各种不同内容的复杂模型以及相关的片段创作体验的需要。

数据类型由存储库中 [特定位置中](#properties)[保存的节点属性组合定义](#locations-in-the-repository)。 您还可以创建自己的 [数据类型](#creating-your-data-type)[和fieldProperties](#creating-your-own-fieldproperties-property)。

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 存储库中的位置 {#locations-in-the-repository}

所有现成数据类型均在以下位置声明：

`/libs/settings`

您可以通过覆盖节点结构来添加新数据类型，如下所示 `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>您不得更改路径中的任 `/libs` 何内容。
>
>任何内容在下次升级或安装服务或修复包时都可能发生更改。

## 属性 {#properties}

节点属性用于定义数据类型：

* [数据类型属性](#data-type-properties)
* 和在这些字 [段属性](#fieldproperties)

### 数据类型属性 {#data-type-properties}

所有数据类型都在节点结构中表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

下面的每个节 `/items` 点都具有一些属性，这些属性定义了模型编辑器中数据类型的表示方式。

要使数据类型在模型编辑器中存在，必须存在以下所有属性：

* `fieldIcon`

   [CoralUI图标](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) ，用于表示模型编辑器UI中的数据类型。

* ` [fieldProperties](#fieldproperties)`

   表示每个数据类型的配置属性的数组。

* `fieldResourceType`

   用于在内容片段中呈现数据类型的Sling资源类型。 对于能以不同方式呈现的数据类型（例如，作为简单文本输入和／或多行文本输入），必须将此属性创建为数组，包含所有资源类型。 该 `renderasfield` 属性将自动添加 `fieldProperties` ，以便用户选择需要添加到模型的资源类型，

* `fieldPropResourceType`

   用于呈现数据类型默认属性的Sling资源类型。

   例如，对于数据类型：

   * 单行文本， `fieldPropResourceType` 将是组 `textfield` 件
   * 布尔值， `fieldPropResourceType` 它将是一个 `checkbox` 组件

* `fieldViewResourceType`

   在构建模型时，用于在预览中呈现数据类型的Sling资源类型。 当用户将数据类型拖动到模型编辑器的左侧时，该属 `fieldViewResourceType` 性表示呈现在该处的组件。 这用于不希望渲染完整组件，但只希望渲染替代，以最小化模型编辑器的开销的情况。

* `fieldTitle`

   定义此数据类型标题的属性。 例如，组 **件的单行文本** , `textfield` 多字段组 **件的多行文** 本。

* `valueType`

   这是数据类型在内部存储时返回的值类型。 请参 [阅映射](#mappings)。

* `renderType`

   这是数据类型的内部表示形式。 它将连接 `valueType` 到UI组件。 请参 [阅映射](#mappings)。

* `listOrder`

   每个数据类型都需要一个值来表示其在列表中的顺序。 这用于确保保存模型编辑器时各个字段（通过拖放添加／移动）的正确顺序。 此值必须为整数，建议以升序、有序的方式分配该数字。 创建新数据类型时，最好根据列表中的最后一个数据类型(数据类型中存在的最 `listOrder` 高值)分配值。

#### 映射 {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>数据类型<br /> </td> 
   <td>值类型<br /> </td> 
   <td>呈现类型</td> 
  </tr> 
  <tr> 
   <td>单行文本</td> 
   <td>字符串</td> 
   <td>文本单一</td> 
  </tr> 
  <tr> 
   <td>多行文本</td> 
   <td>字符串，内容类型<br /> </td> 
   <td>文本——多</td> 
  </tr> 
  <tr> 
   <td>数字（整数／长）<br /> </td> 
   <td>长</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>数字(多次/浮点)</td> 
   <td>多次</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>布尔型</td> 
   <td>布尔型</td> 
   <td>布尔型</td> 
  </tr> 
  <tr> 
   <td>日期和时间</td> 
   <td>日历</td> 
   <td>次</td> 
  </tr> 
  <tr> 
   <td>枚举</td> 
   <td>string/long</td> 
   <td>明细列表</td> 
  </tr> 
  <tr> 
   <td>标记</td> 
   <td>字符串</td> 
   <td>标记</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>某些类型(例如 `string`, `long`等等)可能具有多值。 在这种情况下，用于渲染和编辑的组件通常由多字段组件( `granite/ui/components/coral/foundation/form/multifield`)包装。 标记除外，在标记中，编辑组件负责正确呈现它。

### fieldProperties {#fieldproperties}

每个数据类型的配置属性。 以下项的 `fieldProperties`值：

* `base`

   这是所有组件的 `fieldProperties` 基础。 定义位于 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`。

   它包含变量， `fieldRoot`随后在创 `fieldProperties` 建输入以检索正确路径时可以使用该变量。

   示例： 要获取字段标签的 **正确路径** ，您需要使用键来标识此标签所属的组件，此字段的输入应 `fieldRoot` 为+ `<*fieldLabel*>`

* `checkboxfields`

   此组件为数据类型以及 `Boolean` Sling参数和添加默认复选框 `checked@Delete``checked@TypeHint`。

* `datepickerfields`

   用于添加日期选取器组件所需的隐藏输入的组件。 包括创建 `defaultDateField`属性 `displayedFormat`、 `emptyText`、 `valueFormat``minDate` 和 `maxDate`。

* `datetimepickerfields`

   这会为数据类型添加一 `Date&Time` 个选择字段，以区分 `Date` 和选 `Date&Time` 项。

* `datevaluefield`

   这会向属性添加日期选取器，以便用户可以为数据类型选择 `Date&Time` 默认值。

* `descriptionfield`

   此组件会添加一个多行文本字段，该字段表示多行编辑器中当前选定组件的说明。 它由模型编辑器渲染器自动添加到每个数据类型属性的末尾。

* `labelfield`

   添加输入的组 `textfield` 件，该输入为具有字段标签的数据类型添加字段标签。

* `maptopropertyfield`

   此组件在属 `Name` 性中添加字段，为数据类型的选定组件提供标识符。 它应存在于所有数据类型中。

* `maxlengthfield`

   它用于添加属性， `maxLength` 以便与接受此属性的数据类型一起使用。 例如，使用 **单行文本****、**&#x200B;数字等。

* `multieditorfield`

   这将添加多行编辑器工作所需的所有隐藏字段，该字段由多行文本数 **据类型表示** 。

* `mvfields`

   添加多字段组件工作所需的所有隐藏字段的组件。 例如，对于“单行文本”数据 **类型的第二个选** 项。 对于呈现为多字段的任何组件，都应添加此项。

* `numbertypefield`

   为Number数据类型选 **择选** 项，该数据类型在Integer或Fraction之间 **选择** Number数 **据类型的****** 数据类型。

* `numbervaluefield`

   数字 `numberfield` 的默认值选 **择器** 。这将添加为明细列表 `type.options` 类型输入的选项 **** ，该选项用于确定选择框组件的值。

* `placeholderfield`

   这是一个用作组件属性输入 `emptyText` 的文本字段。 所有接受占位符的数据类型都应使用该占位符(这并非非常复杂； 例如， **单行文本**、 **数字**&#x200B;等)。

* `renderasfield`

   这是当数据类型节点的属性中存 `fieldResourceTypes` 在多个组件时自动呈现的组件。

* `requiredfield`

   此复选框表示组件 `required` 的属性。 由于大多数组件接 `required` 受该字段，因此此字段可用于大多数数据类型。

* `tagsfields`

   添加要呈现的组件所 `tagfield` 需输入的组件，由“标记” **数据** 类型使用。

* `tagsroot`

   Tags数据类型用来设 **置组件** 根路径的路径选 `tagsfield` 取器。

* `textfield`

   由数据类 `Boolean` 型用来设置由此数据类型定义的复选框的字段标签。

* `textvaluefield`

   单行文本数据 **类型的默认** 值属性。

## 创建数据类型 {#creating-your-data-type}

要创建您自己的数据类型，您需要：

* [创建节点结构](#creating-the-node-structure)
* [定义数据类型的属性](#defining-the-properties-for-your-data-type)

然后，您可 [以使用数据类型](#using-your-data-type)。

您还可以 [创建自己的 `fieldProperties`](#creating-your-own-fieldproperties-property)。

### 创建节点结构 {#creating-the-node-structure}

必须在下面创建节 `/apps` 点结构，才能覆盖数据类型。 如果它不存在，您必须创建：

1. 如果它不存在，您必须创建：

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` 应该已存在。
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` 可能需要使用指定的nodetypes创建。

1. 在 `/items` 下，您可以添加新节点以表示新的数据类型：

   * 节点类型： `nt:unstructured`
   * “属性： 请参 [阅定义数据类型的属性](#defining-the-properties-for-your-data-type)

### 定义数据类型的属性 {#defining-the-properties-for-your-data-type}

1. 确定数据类型 [所需的以](#data-type-properties) 下数据类型属性的值：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   这些定义了数据类型的组件的呈现方式。 它们可以是任何组件； 包括您自己的自定义组件(需要一组匹配的 ` [fieldProperties](#fieldproperties)`组件)。

   在数据类型的节点上定义这些属性以及相应的值。

1. 确定要 ` [fieldProperties](#fieldproperties)` 使用的内容。 这取决于您需要的属性或 `fieldResourceType` 属性。

   例如，应 `granite/ui/components/coral/foundation/form/textfield`具有标 **签名称**、最大长 **度、占位符文**&#x200B;本 **和默认值****** 属性。

   您可以从现成的字段Properties中进 [行选择](#fieldproperties)，或 [创建您自己的属性](#creating-your-own-fieldproperties-property)。

   在数据类型的节点上定义这些属性以及相应的值。

1. 确定以下数据类 [型属性的值](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在数据类型的节点上定义这些属性以及相应的值。

### 使用数据类型 {#using-your-data-type}

保存此节点结构并应用所有属性后，您可以使用模型编辑器打开任何模型，查看和使用新的数据类型。

## 创建您自己的字段属性属性 {#creating-your-own-fieldproperties-property}

您可以从现成的字段Properties中进行选 [择](#fieldproperties)，或创建您自己的：

1. 在以下位置创建组件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路径不存在，则可以使用节点创建 `nt:folder` 它。

   1. 要访问变量，此组件应扩展：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 组件应能够通过以下方式包含：

      `sling:include`

   1. 此组件应呈现一个字段（如果用户需要引入数据）或一个隐藏输入，其中包含数据类型所需的属性。 例如，多字段组件需要具有它应重复的字段类型的子节点，因此应该有一个可创建(通过slingPOST机制)特定类型的子节点的输入。

1. 此组件的基本名称应添加到 `fieldProperties`。
1. 对您需要的所有属性重复上述步骤。

