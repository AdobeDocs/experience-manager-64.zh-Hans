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
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 请勿发布，但请勿DELETE自定义内容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

内容片段模型编辑器是基于的向导， `Formbuilder`继承自：

`granite/ui/components/foundation/form/formbuilder`

此组件具有渲染模型编辑器的拖放界面所需的工具，并包含每种工具的数据类型和属性。

## 位置 {#locations}

模型在启用了“内 `/conf`容片段模型”属性的文 [件夹下进行保存和创建](/help/assets/content-fragments-models.md#enable-content-fragment-models) 。 此设置也可在配置属性中 **查看**，可从配置浏 **览器访问**。

1. 通过工具、常规 **、配置**&#x200B;浏 **览器**&#x200B;导航 **到浏**&#x200B;览器。例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 从浏览器中，选择相应的配置，然后从 **工具栏** 中选择属性。

   例如，以下属性 `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在“模型”控制台中，将显示具有“内 **容片段模型** ”属性的所有文件夹。 通过工 **具**、资 **产**、内 **容片段模型导航**; 例如 `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`,

用户可以 [使用创建模型向导](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) (使用 **控制台中的创** 建 **)创建内容片** 段模型。

>[!CAUTION]
>
>您 ***不得*** 更改路径中的任 `/libs` 何内容。
>
>这是因为下次升级实 `/libs` 例时，内容会被覆盖（应用修补程序或功能包时可能会被覆盖）。

## 模型结构 {#structure-of-a-model}

向导将创建具有此结构的条目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此文件夹的子文件夹下。

* `jcr:content`

   每个模型都包含一 `jcr:content` 个节点，该节点：

   * 包含有关模型的信息属 `jcr:title`性， `lastModified`如 `lastModifiedBy`
   * 通常 `sling:ResourceType` 为 `dam/cfm/models/console/components/data/entity/default`,

      和 `sling:ResourceSuperType` `dam/cfm/models/console/components/data/entity`

* `model`

   节 `model` 点包含一个属性， `dataTypesConfig`用于确定模型编辑器中使用的数据类型。

* `items`

   在节点 `items` 下，将保存添加到模型的所有数据类型（在模型编辑器中拖放）。 每个项目都有一个随机节点名称，但为了使内容片段编辑器能够使用此模型，每个项目都必须具有一个属 `name` 性。 此外，在此节点上，将保存特定数据类型的所有配置属性，包括呈现组件所需的默认属性。

>[!CAUTION]
>
>在模型编辑器中拖放的所有数据类型都必须由用 **户输** 入属 `name` 性，因为已实例化。
>
>这被视为属 **性名称&amp;ast;** 在模 **型编辑器** 的“属性”(Properties)选项卡中。

## 模型编辑器的结构 {#structure-of-the-model-editor}

内容 **片段模型编辑器** 有两部分：

* 左侧的预览或视图面板，您可以在其中放置项目。 此功能：

   * 显示实例化 **的预览** “数据类型”。
   * 允许在模型编辑器中进行订购。

* 右 **侧面板****中的Data** Types/Properties选项卡。 此功能：

   * 显示可拖动和实例化的列表数据类型。
   * 对于现成的模型编辑器，列表位于：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有呈现的数据类型都有两个脚本标签，当实例化时，它们将形成视图（左侧呈现的组件）和“属性 **** ”选项卡，“属性”选项卡定义用户可以为给定组件定义的属性。

>[!CAUTION]
>
>您 ***不得*** 更改路径中的任 `/libs` 何内容。
>
>这是因为下次升级实 `/libs` 例时，内容会被覆盖（应用修补程序或功能包时可能会被覆盖）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

实例化数据类型时，会为每个需要在内容片段中呈现组件的属性创建HTML输入。 例如，这些包括：

* **属性名称&amp;ast;** ( `name`)-用作组件的标识符

* **渲染方式** ( `metaType`)-键入要渲染的组件，渲染方式为

* **描述** ( `fieldDescription`)-内容片段中组件的说明

* 等。

