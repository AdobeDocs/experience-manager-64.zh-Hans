---
title: 请勿发布，但不DELETE为内容片段模型自定义数据类型
seo-title: Customizing Data Types for Content Fragment Models
description: 可以自定义内容片段模型中使用的数据类型。
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 2%

---


# 请勿发布，但不DELETE为内容片段模型自定义数据类型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[内容片段](/help/assets/content-fragments.md) 基于 [内容片段模型](/help/assets/content-fragments-models.md). 这些模型是从 [元素](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 不同数据类型。

提供了各种现成的数据类型，包括单行文本、多行富文本、数字字段、布尔选择器、下拉菜单选项、日期和时间等。 AEM用户可以根据相应片段的编辑意图选择数据类型。 这允许您通过包含各种不同内容的复杂模型以及相关的片段创作体验来满足简单文本模型的需求。

数据类型由 [节点属性组合](#properties) 持有 [存储库中的特定位置](#locations-in-the-repository). 您还可以创建自己的 [数据类型](#creating-your-data-type) 和 [fieldProperties](#creating-your-own-fieldproperties-property).

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
>您不得在 `/libs` 路径。
>
>任何内容在下次升级或安装服务或修复包时都可能发生更改。

## 属性 {#properties}

节点属性用于定义数据类型：

* [数据类型属性](#data-type-properties)
* 和 [fieldProperties](#fieldproperties)

### 数据类型属性 {#data-type-properties}

所有数据类型都在节点结构中表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

下的每个节点 `/items` 具有一些属性，这些属性定义数据类型在模型编辑器中的显示方式。

要使数据类型在模型编辑器中存在，必须存在以下所有属性：

* `fieldIcon`

   [CoralUI图标](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) 以在模型编辑器UI中表示数据类型。

* ` [fieldProperties](#fieldproperties)`

   表示每种数据类型的配置属性的数组。

* `fieldResourceType`

   用于在内容片段中呈现数据类型的Sling资源类型。 对于可以以不同方式呈现的数据类型（例如，作为简单文本输入和/或多行文本输入），此属性必须创建为包含所有资源类型的数组。 的 `renderasfield` 属性会自动添加到 `fieldProperties` 允许用户选择需要添加到模型中的资源类型，

* `fieldPropResourceType`

   用于呈现数据类型默认属性的Sling资源类型。

   例如，对于数据类型：

   * 单行文本， `fieldPropResourceType` 会是 `textfield` 组件
   * 布尔值， `fieldPropResourceType` 会是 `checkbox` 组件

* `fieldViewResourceType`

   构建模型时用于在预览中呈现数据类型的Sling资源类型。 当用户将数据类型拖动到模型编辑器的左侧时， `fieldViewResourceType` 属性表示呈现在该组件中的组件。 当您不想渲染完整组件，而只想渲染替代，以最大限度地减少模型编辑器的开销时，可使用此方法。

* `fieldTitle`

   定义此数据类型标题的属性。 例如， **单行文本** a `textfield` 组件， **多行文本** 的子域。

* `valueType`

   这是数据类型在内部存储时返回的值类型。 请参阅 [映射](#mappings).

* `renderType`

   这是数据类型的内部表示形式。 它连接 `valueType` 到UI组件。 请参阅 [映射](#mappings).

* `listOrder`

   每个数据类型都需要一个值来表示其在列表中的顺序。 用于确保在保存模型编辑器时各个字段（通过拖放添加/移动）的正确顺序。 此值必须是整数，建议以升序、有序的方式分配该数字。 创建新数据类型时，最好根据列表中的最后一个数据类型( `listOrder` 值)。

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
   <td>文本 — 单个</td> 
  </tr> 
  <tr> 
   <td>多行文本</td> 
   <td>字符串，内容类型<br /> </td> 
   <td>文本 — 多</td> 
  </tr> 
  <tr> 
   <td>数字（整数/长）<br /> </td> 
   <td>long</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>数字（双重/浮动）</td> 
   <td>多次</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>布尔值</td> 
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
   <td>字符串/长</td> 
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
>某些类型(例如， `string`, `long`（其中包括）可能具有多重价值。 在这种情况下，用于渲染和编辑的组件通常由多字段组件( `granite/ui/components/coral/foundation/form/multifield`)。 标记除外，编辑组件负责正确呈现标记。

### fieldProperties {#fieldproperties}

每个数据类型的配置属性。 的值 `fieldProperties`:

* `base`

   这是所有人的基础 `fieldProperties` 组件。 定义位于 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   它包含变量 `fieldRoot`，后续 `fieldProperties` 可在创建输入时使用，以检索正确的路径。

   示例：为 **字段标签** 您将需要键来标识此组件所属的组件，此字段的输入应为 `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   此组件会为 `Boolean` 数据类型以及Sling参数 `checked@Delete` 和 `checked@TypeHint`.

* `datepickerfields`

   用于添加日期选取器组件正常运行所需的隐藏输入的组件。 包括创建属性 `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` 和 `maxDate`.

* `datetimepickerfields`

   这会为 `Date&Time` 数据类型，用于区分 `Date` 和 `Date&Time` 选项。

* `datevaluefield`

   这会将日期选取器添加到属性中，以便用户可以为 `Date&Time` 数据类型。

* `descriptionfield`

   此组件会添加一个多行文本字段，用于表示多行编辑器中当前选定组件的描述。 它由模型编辑器渲染器在每个数据类型属性的末尾自动添加。

* `labelfield`

   添加 `textfield` 可为具有字段标签的数据类型添加字段标签的输入。

* `maptopropertyfield`

   此组件会将 `Name` 字段，为数据类型的选定组件提供标识符。 它应存在于所有数据类型中。

* `maxlengthfield`

   用于添加 `maxLength` 属性，以与接受此属性的数据类型一起使用。 例如，使用 **单行文本**, **数值**&#x200B;等。

* `multieditorfield`

   这会添加多行编辑器工作所需的所有隐藏字段，该字段由 **多行文本** 数据类型。

* `mvfields`

   组件，可添加多字段组件工作所需的所有隐藏字段。 例如，对于 **单行文本** 数据类型。 应当为呈现为多字段的任何组件添加此选项。

* `numbertypefield`

   选择 **数值** 数据类型，在 **整数** 或 **分数** 对于 **数值** 数据类型。

* `numbervaluefield`

   A `numberfield` 默认值选择器 **数值** `type.options` 这会添加 **明细列表** 数据类型，用于确定选择框组件的值。

* `placeholderfield`

   这是一个用作 `emptyText` 组件的属性。 所有接受占位符的数据类型都应使用此插件(不太复杂；例如 **单行文本**, **数值**&#x200B;等)。

* `renderasfield`

   这是当 `fieldResourceTypes` 数据类型节点的属性中存在。

* `requiredfield`

   这是一个复选框，表示 `required` 属性。 因为大多数组件接受 `required` 字段，此字段可用于大多数数据类型。

* `tagsfields`

   添加 `tagfield` 要呈现的组件，由 **标记** 数据类型。

* `tagsroot`

   使用的路径选取器 **标记** 用于设置根路径的数据类型 `tagsfield` 组件。

* `textfield`

   由 `Boolean` 数据类型，以设置由此数据类型定义的复选框的字段标签。

* `textvaluefield`

   的默认值属性 **单行文本** 数据类型。

## 创建数据类型 {#creating-your-data-type}

要创建您自己的数据类型，您需要：

* [创建节点结构](#creating-the-node-structure)
* [为数据类型定义属性](#defining-the-properties-for-your-data-type)

然后，您可以 [使用您的数据类型](#using-your-data-type).

您还可以 [创建您自己的 `fieldProperties`](#creating-your-own-fieldproperties-property).

### 创建节点结构 {#creating-the-node-structure}

必须在下创建节点结构 `/apps` 以覆盖数据类型。 如果它不存在，则必须创建：

1. 如果它不存在，则必须创建：

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
   >`/apps/settings/dam` 应该已经存在。
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` 可能需要使用指定的nodetypes创建。

1. 在 `/items` 您可以添加新节点以表示新的数据类型：

   * 节点类型： `nt:unstructured`
   * “资产：请参阅 [为数据类型定义属性](#defining-the-properties-for-your-data-type)

### 为数据类型定义属性 {#defining-the-properties-for-your-data-type}

1. 确定以下值 [数据类型属性](#data-type-properties) 数据类型所需的参数：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   这些定义了数据类型的组件的呈现方式。 它们可以是任何组件；包括您自己的自定义组件(需要 ` [fieldProperties](#fieldproperties)`)。

   在数据类型的节点上定义这些属性（包含相应的值）。

1. 确定 ` [fieldProperties](#fieldproperties)` 。 这取决于您的 `fieldResourceType` 需要。

   例如， `granite/ui/components/coral/foundation/form/textfield`应该有 **标签名称**, a **最大长度**, a **占位符文本** 和 **默认值** 属性。

   您可以从现成的环境中进行选择 [fieldProperties](#fieldproperties)或 [创建您自己的资产](#creating-your-own-fieldproperties-property).

   在数据类型的节点上定义这些属性（包含相应的值）。

1. 确定以下值 [数据类型属性](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在数据类型的节点上定义这些属性（包含相应的值）。

### 使用您的数据类型 {#using-your-data-type}

保存此节点结构并应用所有属性后，可以使用模型编辑器打开任何模型，查看和使用新的数据类型。

## 创建您自己的字段Properties资产 {#creating-your-own-fieldproperties-property}

您可以从现成的环境中进行选择 [fieldProperties](#fieldproperties)，或创建您自己的：

1. 在下创建组件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路径不存在，您可以使用 `nt:folder` 节点。

   1. 要访问变量，此组件应扩展：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 该组件应能够通过以下方式包含：

      `sling:include`

   1. 此组件应呈现字段（如果用户需要引入数据）或包含数据类型所需属性的隐藏输入。 例如，多字段组件需要一个子节点，其类型应该与其重复的字段，因此应该有一个输入，该输入可以创建(通过slingPOST机制)特定类型的子节点。

1. 此组件的基本名称应添加到 `fieldProperties`.
1. 重复执行上述步骤以获取您需要的所有资产。

