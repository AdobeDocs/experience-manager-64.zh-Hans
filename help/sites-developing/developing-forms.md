---
title: 开发Forms（经典UI）
seo-title: Developing Forms (Classic UI)
description: 了解如何开发表单
seo-description: Learn how to develop forms
uuid: 124e63ba-8d87-4173-aa35-7809b39811d7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 0ef6a3b1-e7ce-4268-a5be-a565646ecc29
exl-id: 6d52babc-9477-4528-9c25-35cb729f5d78
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 1%

---

# 开发Forms（经典UI）{#developing-forms-classic-ui}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

表单的基本结构是：

* 表单开始
* 表单元素
* 表单结尾

所有这些都通过一系列默认设置来实现 [表单组件](/help/sites-authoring/default-components.md)，在标准AEM安装中可用。

除 [开发新组件](/help/sites-developing/developing-components-samples.md) 要在表单上使用，您还可以：

* [预载包含值的表单](#preloading-form-values)
* [预加载（某些）具有多个值的字段](#preloading-form-fields-with-multiple-values)
* [开发新操作](#developing-your-own-form-actions)
* [开发新限制](#developing-your-own-form-constraints)
* [显示或隐藏特定表单字段](#showing-and-hiding-form-components)

[使用脚本](#developing-scripts-for-use-with-forms) 以根据需要扩展功能。

>[!NOTE]
>
>本文档重点介绍如何使用 [基础组件](/help/sites-authoring/default-components-foundation.md) 在经典UI中。 Adobe建议利用 [核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hans) 和 [隐藏条件](/help/sites-developing/hide-conditions.md) 用于触屏UI中的表单开发。

## 预加载表单值 {#preloading-form-values}

表单开始组件为 **加载路径**，指向存储库中节点的可选路径。

Load Path是用于将预定义值加载到表单上多个字段中的节点属性的路径。

这是一个可选字段，用于指定存储库中节点的路径。 如果此节点具有与字段名称匹配的属性，则表单上的相应字段将预先加载这些属性的值。 如果不存在匹配项，则字段包含默认值。

>[!NOTE]
>
>A [表单操作](#developing-your-own-form-actions) 还可以设置加载初始值的资源。 这是使用完成的 `FormsHelper#setFormLoadResource` in `init.jsp`.
>
>仅当未设置时，作者才会从开始表单组件中设置的路径填充表单。

## 预加载具有多个值的表单字段 {#preloading-form-fields-with-multiple-values}

各种表单字段还具有 **项目加载路径**，也是指向存储库中节点的可选路径。

的 **项目加载路径** 是用于将预定义值加载到表单上特定字段的节点属性的路径，例如， [下拉列表](/help/sites-authoring/default-components-foundation.md#dropdown-list), [复选框组](/help/sites-authoring/default-components-foundation.md#checkbox-group) 或 [无线组](/help/sites-authoring/default-components-foundation.md#radio-group).

### 示例 — 预加载具有多个值的下拉列表 {#example-preloading-a-dropdown-list-with-multiple-values}

可以为下拉列表配置要选择的值范围。

的 **项目加载路径** 可用于从存储库的文件夹访问列表，并将这些列表预载到字段中：

1. 创建新Sling文件夹( `sling:Folder`)

   例如， `/etc/designs/<myDesign>/formlistvalues`

1. 添加新属性(例如， `myList`)类型为多值字符串( `String[]`)以包含下拉项目列表。 也可以使用脚本导入内容，例如使用JSP脚本或Shell脚本中的cURL。

1. 在 **项目加载路径** 字段：

   例如， `/etc/designs/geometrixx/formlistvalues/myList`

请注意，如果 `String[]` 格式如下：

* `AL=Alabama`
* `AK=Alaska`
* *以此类推。*

然后，AEM将生成列表，如下所示：

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

例如，此功能可在多语言设置中得到良好使用。

### 开发您自己的表单操作 {#developing-your-own-form-actions}

表单需要操作。 操作定义在随用户数据提交表单时执行的操作。

标准AEM安装提供了一系列操作，这些操作可在下面查看：

`/libs/foundation/components/form/actions`

和 **操作类型** 列表 **表单** 组件：

![chlimage_1-226](assets/chlimage_1-226.png)

本节介绍如何开发您自己的表单操作以包含在此列表中。

您可以在 `/apps` 如下所示：

1. 创建类型的节点 `sling:Folder`. 指定反映要实施的操作的名称。

   例如：

   `/apps/myProject/components/customFormAction`

1. 在此节点上，定义以下属性，然后单击 **全部保存** 要保留更改，请执行以下操作：

   * `sling:resourceType`  — 设置为 `foundation/components/form/action`
   * `componentGroup`  — 定义为 `.hidden`
   * （可选）：

      * `jcr:title`  — 指定您选择的标题，该标题将显示在下拉选择列表中。 如果未设置，则会显示节点名称
      * `jcr:description`  — 输入您选择的描述

1. 在文件夹中，创建一个对话框节点：

   1. 添加字段，以便作者在选择操作后可以编辑表单对话框。

1. 在文件夹中创建以下任一项：

   1. 帖子脚本。

      脚本的名称为 `post.POST.<extension>`，例如 `post.POST.jsp`

      提交表单以处理表单时，将调用post脚本，该脚本包含用于处理从表单到达的数据的代码 `POST`.

   1. 添加在提交表单时调用的转发脚本。

      脚本的名称为 `forward.<extension`>，例如 `forward.jsp`

      此脚本可定义路径。 然后，将当前请求转发到指定的路径。
   必要的调用是 `FormsHelper#setForwardPath` （2个变体）。 典型情况是执行一些验证或逻辑，以查找目标路径，然后转发到该路径，从而让默认的SlingPOSTServlet在JCR中执行实际存储。

   还可以有一个执行实际处理的Servlet，在这种情况下，表单操作和 `forward.jsp` 只能充当“胶”代码。 例如，在 `/libs/foundation/components/form/actions/mail`，将详细信息转发到 `<currentpath>.mail.html`其中，邮件Servlet位于。

   因此：

   * a `post.POST.jsp` 对于操作本身完全完成的小操作非常有用
   * 而 `forward.jsp` 仅在需要委派时很有用。

   脚本的执行顺序为：

   * 呈现表单时( `GET`):

      1. `init.jsp`
      1. 对于所有字段的约束： `clientvalidation.jsp`
      1. 表单的validationRT: `clientvalidation.jsp`
      1. 如果已设置，则通过加载资源加载表单
      1. `addfields.jsp` 在内部渲染 `<form></form>`
   * 处理表格 `POST`:

      1. `init.jsp`
      1. 对于所有字段的约束： `servervalidation.jsp`
      1. 表单的validationRT: `servervalidation.jsp`
      1. `forward.jsp`
      1. 如果设置了前进路径( `FormsHelper.setForwardPath`)，转发请求，然后调用 `cleanup.jsp`
      1. 如果未设置前进路径，则调用 `post.POST.jsp` (此处结束，否 `cleanup.jsp` 调用)




1. 在文件夹中再次选择添加：

   1. 用于添加字段的脚本。

      脚本的名称为 `addfields.<extension>`，例如 `addfields.jsp`

      在写入表单开始的HTML后，会立即调用addfields脚本。 这允许操作在表单中添加自定义输入字段或其他此类HTML。

   1. 初始化脚本。

      脚本的名称为 `init.<extension>`，例如 `init.jsp`

      在呈现表单时将调用此脚本。 它可用于初始化操作特定信息。 &quot;

   1. 清理脚本。

      脚本的名称为 `cleanup.<extension>`，例如 `cleanup.jsp`

      此脚本可用于执行清理。

1. 使用 **Forms** 组件。 的 **操作类型** 下拉菜单现在将包含您的新操作。

   >[!NOTE]
   >
   >要查看产品中的默认操作，请执行以下操作：
   >
   >`/libs/foundation/components/form/actions`

### 开发您自己的表单约束 {#developing-your-own-form-constraints}

可在两个级别施加限制：

* 对于 [单个字段（请参阅以下过程）](#constraints-for-individual-fields)
* 作为 [表单全局验证](#form-global-constraints)

#### 单个字段的限制 {#constraints-for-individual-fields}

您可以为单个字段添加自己的约束(在 `/apps`)，如下所示：

1. 创建类型的节点 `sling:Folder`. 指定反映要实施的约束的名称。

   例如：

   `/apps/myProject/components/customFormConstraint`

1. 在此节点上，定义以下属性，然后单击 **全部保存** 要保留更改，请执行以下操作：

   * `sling:resourceType`  — 设置为 `foundation/components/form/constraint`
   * `constraintMessage`  — 根据约束条件，在提交表单时，如果字段无效，将显示自定义消息
   * （可选）：

      * `jcr:title`  — 指定您选择的标题，该标题将显示在选择列表中。 如果未设置，则会显示节点名称
      * `hint`  — 有关如何使用字段的其他信息，请向用户提供

1. 在此文件夹中，您可以需要以下脚本：

   * 客户端验证脚本：

      脚本的名称为 `clientvalidation.<extension>`，例如 `clientvalidation.jsp`

      在呈现表单字段时，将调用此调用。 它可用于创建客户端javascript以验证客户端上的字段。

   * 服务器验证脚本：

      脚本的名称为 `servervalidation.<extension>`，例如 `servervalidation.jsp`

      在提交表单时，将调用此调用。 该字段可用于在提交后验证服务器上的字段。

>[!NOTE]
>
>示例约束可在以下位置查看：
>
>`/libs/foundation/components/form/constraints`

#### 表单 — 全局约束 {#form-global-constraints}

通过在开始表单组件( `validationRT`)。 例如：

`apps/myProject/components/form/validation`

然后，您可以定义：

* a `clientvalidation.jsp`  — 在字段的客户端验证脚本之后插入
* 和 `servervalidation.jsp`  — 在对 `POST`.

### 显示和隐藏表单组件 {#showing-and-hiding-form-components}

您可以配置表单，以根据表单中其他字段的值显示或隐藏表单组件。

仅当仅在特定条件下需要表单字段时，更改表单字段的可见性非常有用。 例如，在反馈表中，有一个问题询问客户是否希望通过电子邮件将产品信息发送给他们。 选择“是”后，会显示一个文本字段，使客户能够键入其电子邮件地址。

使用 **编辑显示/隐藏规则** 对话框以指定显示或隐藏表单组件的条件。

![showhideeditor](assets/showhideeditor.png)

使用对话框顶部的字段指定以下信息：

* 是否指定用于隐藏或显示组件的条件。
* 显示或隐藏组件是否需要满足任何或所有条件。

这些字段下会显示一个或多个条件。 条件会将另一个表单组件（在同一表单上）的值与值进行比较。 如果字段中的实际值满足条件，则该条件会计算为true。 条件包括以下信息：

* 测试的表单字段的标题。
* 运算符。
* 将比较针对的值与字段值。

例如，标题为的单选按钮组组件 `Receive email notifications?`*包含 `Yes` 和 `No` 单选按钮。 标题为 `Email Address` 会使用以下条件，以便在 `Yes` 已选中：

![肖美德](assets/showhidecondition.png)

在Javascript中，条件使用元素名称属性的值引用字段。 在上一个示例中，单选按钮组组件的Element Name属性为 `contact`. 以下代码与该示例的等效Javascript代码：

`((contact == "Yes"))`

**要显示或隐藏表单组件，请执行以下操作：**

1. 编辑特定的表单组件。

1. 选择 **显示/隐藏** 打开 **编辑显示/隐藏规则** 对话框：

   * 在第一个下拉列表中，选择 **显示** 或 **隐藏** 以指定条件确定是显示还是隐藏组件。
   * 在顶行末尾的下拉列表中，选择：

      * **全部**  — 如果所有条件都必须为true才能显示或隐藏组件
      * **any**  — 如果只有一个或多个条件必须为true才能显示或隐藏组件
   * 在条件行（一个显示为默认值）中，选择组件、运算符，然后指定一个值。
   * 根据需要，通过单击添加更多条件 **添加条件**.

   例如：

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. 单击 **确定** 以保存定义。

1. 保存定义后， **编辑规则** 链接在 **显示/隐藏** 选项。 单击此链接可打开 **编辑显示/隐藏规则** 对话框进行更改。

   单击 **确定** 以保存所有更改。

   ![chlimage_1-228](assets/chlimage_1-228.png)

   >[!CAUTION]
   >
   >可以查看和测试显示/隐藏定义的效果：
   >
   >* in **预览** 模式（首次切换到预览时需要重新加载页面）
   >* 在发布环境中


#### 处理损坏的组件引用 {#handling-broken-component-references}

显示/隐藏条件使用元素名称属性的值引用表单中的其他组件。 当任何条件引用的组件已删除或已更改Element Name属性时，显示/隐藏配置无效。 出现这种情况时，您需要手动更新条件，否则在表单加载时会出错。

当显示/隐藏配置无效时，该配置仅作为JavaScript代码提供。 编辑代码以更正问题。代码使用最初用于引用组件的元素名称属性。

### 开发用于Forms的脚本 {#developing-scripts-for-use-with-forms}

有关在编写脚本时可使用的API元素的更多信息，请参阅 [与表单相关的javaoc](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

您可以将此操作用于各种操作，例如在提交表单之前调用服务，并在表单失败时取消服务：

* 定义验证资源类型
* 包含验证脚本：

   * 在JSP中，调用Web服务并创建 `com.day.cq.wcm.foundation.forms.ValidationInfo` 包含错误消息的对象。 如果出现错误，将不会发布表单数据。
