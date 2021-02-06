---
title: 请勿发布，但请勿DELETE自定义内容片段模型
seo-title: 自定义内容片段模型
description: 可以自定义和扩展内容片段模型。
seo-description: 可以自定义和扩展内容片段模型。
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 请勿发布，但不DELETE自定义内容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

内容片段模型编辑器是基于`Formbuilder`的向导，继承自：

`granite/ui/components/foundation/form/formbuilder`

此组件具有渲染模型编辑器的拖放界面所需的工具，并包含每种工具的数据类型和属性。

## 位置 {#locations}

模型在`/conf`下保存并创建，位于启用了[内容片段模型属性](/help/assets/content-fragments-models.md#enable-content-fragment-models)的文件夹下。 此设置也可在&#x200B;**配置属性**&#x200B;中查看，可从&#x200B;**[配置浏览器](/help/sites-administering/configurations.md)**&#x200B;访问。

1. 通过&#x200B;**工具**、**常规**、**配置浏览器**导航到浏览器
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 从浏览器中，选择相应的配置，然后从工具栏中选择&#x200B;**属性**。

   例如，`global`的属性：`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在“模型”控制台中，将显示所有具有&#x200B;**内容片段模型**&#x200B;属性的文件夹。 通过&#x200B;**工具**、**资产**、**内容片段模型**&#x200B;进行导航；例如，`http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`。

用户可以使用&#x200B;**创建模型**&#x200B;向导（使用控制台中的&#x200B;**创建**）创建内容片段模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)。[

>[!CAUTION]
>
>您&#x200B;***必须***&#x200B;不要更改`/libs`路径中的任何内容。
>
>这是因为下次升级实例时，`/libs`的内容会被覆盖（应用修补程序或功能包时，可能会被覆盖）。

## 模型{#structure-of-a-model}的结构

向导将创建具有此结构的条目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此文件夹的子文件夹下。

* `jcr:content`

   每个模型都包含一个`jcr:content`节点，该节点：

   * 包含有关模型的信息属性，如`jcr:title`、`lastModified`、`lastModifiedBy`
   * 通常`sling:ResourceType`为`dam/cfm/models/console/components/data/entity/default`,

      `sling:ResourceSuperType`/`dam/cfm/models/console/components/data/entity`

* `model`

   `model`节点包含属性`dataTypesConfig`，用于确定模型编辑器中使用的数据类型。

* `items`

   在`items`节点下，将保存添加到模型的所有数据类型（在模型编辑器中拖放）。 每个项目都有一个随机节点名称，但为了使内容片段编辑器能与此模型一起使用，每个项目都必须具有`name`属性。 此外，在此节点上，将保存特定数据类型的所有配置属性，包括呈现组件所需的默认属性。

>[!CAUTION]
>
>在模型编辑器中拖放的所有数据类型都必须由用户输入`name`属性，因此，已实例化&#x200B;**。**
>
>在模型编辑器的&#x200B;**属性**&#x200B;选项卡中，它被视为&#x200B;**属性名称&amp;ast;**。

## 模型编辑器{#structure-of-the-model-editor}的结构

**内容片段模型编辑器**&#x200B;包含两个部分：

* 左侧的预览或视图面板，您可以在其中放置项目。 此功能：

   * 显示实例化的&#x200B;**数据类型**&#x200B;的预览。
   * 允许在模型编辑器中进行订购。

* 右侧面板中的&#x200B;**数据类型**/**属性**&#x200B;选项卡。 此功能：

   * 显示可拖动和实例化的列表数据类型。
   * 对于现成的模型编辑器，列表位于：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有呈现的数据类型都有两个脚本标签，当实例化时，这些标签将形成视图（左侧呈现的组件）和&#x200B;**属性**&#x200B;标签，后者定义用户可以为给定组件定义的属性。

>[!CAUTION]
>
>您&#x200B;***必须***&#x200B;不要更改`/libs`路径中的任何内容。
>
>这是因为下次升级实例时，`/libs`的内容会被覆盖（应用修补程序或功能包时，可能会被覆盖）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

实例化数据类型时，会为每个需要在内容片段中呈现组件的属性创建HTML输入。 例如，这些包括：

* **属性名称&amp;ast;** ( `name`)-充当组件的标识符

* **Render As** ( `metaType`)-键入要呈现的组件将作为

* **Description** ( `fieldDescription`)-内容片段中组件的说明

* 等。

