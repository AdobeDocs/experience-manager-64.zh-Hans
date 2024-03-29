---
title: 为多个就地编辑器配置RTE。
description: 通过配置富文本编辑器，在Adobe Experience Manager中创建多个就地编辑器。
contentOwner: AG
exl-id: 8537582c-7e48-4a93-b93c-9187400e264d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 3%

---

# 配置多个就地编辑器 {#configure-multiple-in-place-editors}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以在Adobe Experience Manager中配置富文本编辑器，以使其具有多个就地编辑器。 配置完毕后，您可以选择相应的内容并打开相应的编辑器。

![特定就地编辑器](assets/rte-inplace-editor.png)

## 配置多个编辑器 {#configure-multiple-editors}

要启用 `cq:InplaceEditingConfig` 节点类型已通过定义 `cq:ChildEditorConfig` 节点类型。

例如：

```js
   /**
       * Configures in-place editing of a component.
       *
       * @prop active true to activate in-place editing for the component.
       * @prop editorType ID of in-place editor to use.
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional).
       * @node config editor's config (used if no configPath is specified; optional).
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a sub-component. The name of the this node is
      * used as DD ID.
      *
      * @prop type type of the inline editor. For example, ["image"].
      * @prop title Title of the inline editor.
      * @prop icon Icon to represent the inline editor.
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

要配置多个编辑器，请执行以下步骤：

1. 在节点上 `cq:inplaceEditing` （类型） `cq:InplaceEditingConfig`)定义以下属性：

   * 名称:`editorType`
   * 类型: `String`
   * 价值: `hybrid`

1. 在此节点下，创建一个节点：

   * 名称: `cq:ChildEditors`
   * 类型: `nt:unstructured`

1. 在 `cq:childEditors` 节点，为每个就地编辑器创建一个节点：

   * 名称：每个节点的名称是它所表示属性的名称，与放置目标的名称一样。 例如， `image` 和 `text`.
   * 类型: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >定义的放置目标与子编辑器之间存在关联。 的名称 `cq:ChildEditorConfig` 节点被视为放置目标ID，用作所选子编辑器的参数。 如果可编辑的子区域没有放置目标（例如，在文本组件中），则子编辑器的名称仍会被视为标识相应可编辑区域的ID。

1. 在每个节点(`cq:ChildEditorConfig`)定义属性：

   * 名称: `type`.
   * 值：注册的就地编辑器名称；例如， `image` 和 `text`.

   * 名称: `title`.
   * 值：可用编辑器的组件选择列表中显示的标题。 例如， `Image` 和 `Text`.

### 富文本编辑器的其他配置 {#additional-configuration-for-rich-text-editors}

多个富文本编辑器的配置略有不同，因为您可以单独配置每个RTE实例。 有关详细信息，请参阅 [配置富文本编辑器](/help/sites-administering/rich-text-editor.md). 要让多个RTE为每个就地RTE创建配置，请执行以下操作： Adobe建议在 `cq:InplaceEditingConfig` 因为每个RTE可以有不同的配置。 在新节点下，创建每个RTE配置。

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    someconfig
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>但是，对于RTE， `configPath` 当组件中只有一个文本编辑器实例（可编辑的子区域）时，支持属性。 此用途 `configPath` 提供用于支持与组件的旧用户界面对话框向后兼容。

>[!CAUTION]
>
>请勿将RTE配置节点命名为 `config`. 否则，RTE配置仅适用于管理员，而不适用于组中的用户 `content-author`.

## 代码示例 {#code-samples}

您可以在 [GitHub上的aem-authoring-hybrideditors项目](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). 您可以将完整项目下载为 [ZIP存档](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip).

## 添加就地编辑器 {#add-an-in-place-editor}

有关添加就地编辑器的一般信息，请参阅此文档 [自定义页面创作](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [在Experience Manager中配置富文本编辑器](/help/sites-administering/rich-text-editor.md).

