---
title: 请勿发布，但不DELETE自定义内容片段模型
seo-title: Customizing Content Fragment Models
description: 可以自定义和扩展内容片段模型。
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---


# 请勿发布，但不DELETE自定义内容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

内容片段模型编辑器是一个基于 `Formbuilder`，继承自：

`granite/ui/components/foundation/form/formbuilder`

此组件具有渲染模型编辑器的拖放界面所必需的工具，以及每种编辑器的数据类型和属性。

## 位置 {#locations}

在下保存和创建模型 `/conf`，位于具有 [内容片段模型属性](/help/assets/content-fragments-models.md#enable-content-fragment-models) 已启用。 此设置也可以在 **配置属性**，可从访问 **[配置浏览器](/help/sites-administering/configurations.md)**.

1. 通过导航到浏览器 **工具**, **常规**, **配置浏览器**
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 在浏览器中，选择相应的配置，然后 **属性** 中。

   例如， `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中， **内容片段模型** 属性。 导航方式 **工具**, **资产**, **内容片段模型**;例如， `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

用户可以 [创建内容片段模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) 使用 **创建模型** 向导(使用 **创建** )。

>[!CAUTION]
>
>您 ***必须*** 不会更改 `/libs` 路径。
>
>这是因为 `/libs` 在下次升级实例时被覆盖（在应用修补程序或功能包时可能会被覆盖）。

## 模型的结构 {#structure-of-a-model}

向导将创建一个具有此结构的条目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此文件夹的子文件夹下。

* `jcr:content`

   每个模型都包含 `jcr:content` 节点：

   * 包含有关模型的信息属性，例如 `jcr:title`, `lastModified`, `lastModifiedBy`
   * 通常具有 `sling:ResourceType` of `dam/cfm/models/console/components/data/entity/default`,

      和 `sling:ResourceSuperType` of `dam/cfm/models/console/components/data/entity`

* `model`

   的 `model` 节点包含属性 `dataTypesConfig`，用于确定模型编辑器中使用的数据类型。

* `items`

   在 `items` 节点中，将保存添加到模型的所有数据类型（在模型编辑器中拖放）。 每个项目都有一个随机的节点名称，但是为了使内容片段编辑器能够使用此模型，每个项目必须具有 `name` 属性。 此外，在此节点上，还会保存特定数据类型的所有配置属性，包括呈现组件所需的默认属性。

>[!CAUTION]
>
>在模型编辑器中拖放的所有数据类型，因此进行了实例化， **必须** 拥有 `name` 用户输入的属性。
>
>这被视为 **属性名称&amp;ast;** 在 **属性** 选项卡。

## 模型编辑器的结构 {#structure-of-the-model-editor}

的 **内容片段模型编辑器** 包含两个部分：

* 左侧的预览或视图面板，您可以在其中放置项目。 此功能：

   * 显示 **数据类型** 实例化。
   * 允许在模型编辑器中进行排序。

* 的 **数据类型**/**属性** 选项卡。 此功能：

   * 显示可拖动和实例化的数据类型列表。
   * 对于现成的模型编辑器，列表位于：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有渲染的数据类型都有两个脚本标记，在实例化后，这些脚本标记将构成视图（呈现在左侧的组件）和 **属性** 选项卡，用于定义用户可为给定组件定义的属性。

>[!CAUTION]
>
>您 ***必须*** 不会更改 `/libs` 路径。
>
>这是因为 `/libs` 在下次升级实例时被覆盖（在应用修补程序或功能包时可能会被覆盖）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

实例化数据类型后，将为组件需要在内容片段中呈现的每个属性创建HTML输入。 例如，这些参数包括：

* **属性名称&amp;ast;** ( `name`) — 用作组件的标识符

* **渲染为** ( `metaType`) — 键入要呈现为

* **描述** ( `fieldDescription`) — 内容片段中组件的描述

* 等等。

