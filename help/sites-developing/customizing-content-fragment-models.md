---
title: 请勿发布，但不DELETE自定义内容片段模型
seo-title: 自定义内容片段模型
description: 可以自定义和扩展内容片段模型。
seo-description: 可以自定义和扩展内容片段模型。
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 请勿发布，但不DELETE自定义内容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

内容片段模型编辑器是基于`Formbuilder`的向导，继承自：

`granite/ui/components/foundation/form/formbuilder`

此组件具有渲染模型编辑器的拖放界面所必需的工具，以及每种编辑器的数据类型和属性。

## 位置 {#locations}

模型在`/conf`下保存并创建，在启用了[内容片段模型属性](/help/assets/content-fragments-models.md#enable-content-fragment-models)的文件夹下。 此设置也可在&#x200B;**配置属性**&#x200B;中查看，可从&#x200B;**[配置浏览器](/help/sites-administering/configurations.md)**&#x200B;访问。

1. 通过&#x200B;**Tools**、**General**、**Configuration Browser**导航到浏览器
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 从浏览器中，选择相应的配置，然后从工具栏中选择&#x200B;**属性**。

   例如，`global`的属性：`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中，将显示具有&#x200B;**内容片段模型**&#x200B;属性的所有文件夹。 通过&#x200B;**工具**、**资产**、**内容片段模型**&#x200B;进行导航；例如，`http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`。

用户可以使用&#x200B;**创建模型**&#x200B;向导（使用控制台中的&#x200B;**创建**）创建内容片段模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)。[

>[!CAUTION]
>
>***必须***&#x200B;不更改`/libs`路径中的任何内容。
>
>这是因为下次升级实例时，`/libs`的内容会被覆盖（应用修补程序或功能包时，可能会被覆盖）。

## 模型{#structure-of-a-model}的结构

向导将创建一个具有此结构的条目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此文件夹的子文件夹下。

* `jcr:content`

   每个模型都包含一个`jcr:content`节点，该节点：

   * 包含有关模型的信息属性，例如`jcr:title`、`lastModified`、`lastModifiedBy`
   * 通常具有`dam/cfm/models/console/components/data/entity/default`的`sling:ResourceType`,

      `dam/cfm/models/console/components/data/entity`的`sling:ResourceSuperType`

* `model`

   `model`节点包含属性`dataTypesConfig`，用于确定模型编辑器中使用的数据类型。

* `items`

   在`items`节点下，将保存添加到模型的所有数据类型（在模型编辑器中拖放）。 每个项目都有一个随机的节点名称，但为了使内容片段编辑器能够与此模型一起使用，每个项目必须具有`name`属性。 此外，在此节点上，还会保存特定数据类型的所有配置属性，包括呈现组件所需的默认属性。

>[!CAUTION]
>
>在模型编辑器中拖放的所有数据类型，因此实例化后，**必须**&#x200B;具有用户输入的`name`属性。
>
>在模型编辑器的&#x200B;**Properties**&#x200B;选项卡中，此参数被视为&#x200B;**属性名称&amp;ast;**。

## 模型编辑器的结构{#structure-of-the-model-editor}

**内容片段模型编辑器**&#x200B;包含两个部分：

* 左侧的预览或视图面板，您可以在其中放置项目。 此功能：

   * 显示已实例化的&#x200B;**数据类型**&#x200B;的预览。
   * 允许在模型编辑器中进行排序。

* 右侧面板中的&#x200B;**数据类型**/**属性**&#x200B;选项卡。 此功能：

   * 显示可拖动和实例化的数据类型列表。
   * 对于现成的模型编辑器，列表位于：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有渲染的数据类型都具有两个脚本标记，在实例化后，这些脚本标记将构成视图（左侧渲染的组件），以及&#x200B;**Properties**&#x200B;选项卡，该选项卡定义用户可以为给定组件定义的属性。

>[!CAUTION]
>
>***必须***&#x200B;不更改`/libs`路径中的任何内容。
>
>这是因为下次升级实例时，`/libs`的内容会被覆盖（应用修补程序或功能包时，可能会被覆盖）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

实例化数据类型后，将为组件需要在内容片段中呈现的每个属性创建HTML输入。 例如，这些参数包括：

* **属性名称(&amp;A);** ( `name`) — 用作组件的标识符

* **呈现方式** ( `metaType`) — 键入要呈现为的组件

* **描述** ( `fieldDescription`) — 内容片段中组件的描述

* 等等。

