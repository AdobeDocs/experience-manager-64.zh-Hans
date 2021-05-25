---
title: 配置RTE以生成无障碍站点
seo-title: 配置RTE以生成无障碍站点
description: 了解如何配置AEM富文本编辑器以生成无障碍站点。
seo-description: 了解如何配置AEM富文本编辑器以生成无障碍站点。
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# 配置RTE以生成可访问的站点{#configuring-rte-for-producing-accessible-sites}

AEM同时支持以下两项：

* 标准辅助功能，包括图像的替代文本
* 以及在使用富文本编辑器(RTE)的组件创建内容时可访问的其他功能

>[!NOTE]
>
>* [WCAG 2.0快速指南](/help/managing/qg-wcag.md)
* [创建辅助内容（WCAG 2.0符合性）](/help/sites-authoring/creating-accessible-content.md)


内容作者在向页面添加内容时，可以使用RTE的功能来提供辅助功能信息。 这可以包括通过标题和段落元素添加结构性信息。

您可以通过为组件配置RTE插件](#configuring-the-plugin-features)来配置和自定义这些功能。 [例如，`paraformat`插件允许您添加其他块级语义元素，包括扩展支持的标题级别数量，超出默认提供的基本`H1`、`H2`和`H3`。

RTE可在触屏优化UI和经典UI中的各种组件中使用。 但是，使用RTE的主要组件是&#x200B;**Text**&#x200B;组件。

AEM中的&#x200B;**Text**&#x200B;组件同时适用于触屏UI和经典UI。 下图显示了启用了一系列插件（包括`paraformat`）的富文本编辑器：

* 触屏UI中的&#x200B;**Text**&#x200B;组件：

   ![触屏UI中全屏模式的文本组件(RTE)。](assets/chlimage_1-206.png)

* 经典UI中的&#x200B;**Text**&#x200B;组件：

   ![经典UI中文本组件的编辑对话框(RTE)。](assets/chlimage_1-207.png)

>[!NOTE]
经典UI和触屏UI中可用的RTE功能之间存在差异。 有关更多详细信息，请参阅
* [插件及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [插件及其功能 — 触屏UI](/help/sites-administering/rich-text-editor.md#aboutplugins)



## 配置插件功能{#configuring-the-plugin-features}

[配置富文本编辑器](/help/sites-administering/rich-text-editor.md)页面上提供了有关配置RTE的完整说明。 这涵盖所有问题，包括关键步骤：

* [插件及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [配置位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [激活插件并配置功能属性](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [配置RTE的其他功能](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

通过在CRXDE Lite的相应`rtePlugins`子分支中配置插件（请参阅下图），可以激活该插件的所有功能或特定功能。

![CRXDE Lite显示了rtePlugin示例。](assets/chlimage_1-208.png)

### 示例 — 指定RTE选择字段{#example-specifying-paragraph-formats-available-in-rte-selection-field}中可用的段落格式

新的语义块格式可通过以下方式供选择：

1. 根据RTE，确定并导航到[配置位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)。
1. [启用“段落”选择字段](/help/sites-administering/rich-text-editor.md);通过 [激活插件](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)。
1. [在“段落”选择字段中指定要使用的格式](/help/sites-administering/rich-text-editor.md)。
1. 然后，内容作者可以从RTE的选择字段中使用段落格式。 可以访问它们：

   * 在触屏UI中使用段落([pilcrow](https://en.wikipedia.org/wiki/Pilcrow))图标：

   ![段落(Pilcrow)图标。](do-not-localize/chlimage_1-7.png)

   * 使用经典UI中的&#x200B;**Format**&#x200B;字段（下拉选择器）。


RTE中通过段落格式选项提供的结构元素，为开发无障碍内容提供了良好的基础。 内容作者不能使用RTE设置字体大小、颜色或其他相关属性的格式，从而阻止创建内联格式。 相反，他们必须选择相应的结构元素（如标题），并使用从“样式”选项中选择的全局样式。 这可确保清晰的标记，为使用自己的样式表和正确结构化内容进行浏览的用户提供更多选项。

## 使用源编辑功能{#use-of-the-source-edit-feature}

在某些情况下，内容作者会发现需要检查和调整使用RTE创建的HTML源代码。 例如，在RTE中创建的一段内容可能需要额外的标记以确保符合WCAG 2.0。可以通过RTE的[源编辑](/help/sites-administering/rich-text-editor.md#aboutplugins)选项来完成此操作。 您可以在`misctools`插件](/help/sites-administering/rich-text-editor.md#aboutplugins)上指定[ `sourceedit`功能。

>[!CAUTION]
请仔细使用`sourceedit`功能。 键入错误和/或不受支持的功能可能会导致更多问题。

## 添加对其他HTML元素和属性的支持{#adding-support-for-additional-html-elements-and-attributes}

要进一步扩展AEM的辅助功能，可以基于RTE（例如&#x200B;**Text**&#x200B;和&#x200B;**Table**&#x200B;组件）扩展现有组件，并包含其他元素和属性。

以下过程说明了如何使用&#x200B;**标题**&#x200B;元素扩展&#x200B;**表**&#x200B;组件，该元素向辅助型技术用户提供有关数据表的信息：

### 示例 — 将题注添加到表属性对话框{#example-adding-the-caption-to-the-table-properties-dialog}

在`TablePropertiesDialog`的构造函数中，添加一个用于编辑题注的附加文本输入字段。 请注意，必须将`itemId`设置为`caption`（即DOM属性的名称），才能自动处理其内容。

在&#x200B;**Table**&#x200B;中，必须明确地设置或从DOM元素中删除属性。 该值由`config`对象中的对话框传递。 请注意，应使用相应的`CQ.form.rte.Common`方法（`com`是`CQ.form.rte.Common`的快捷方式）设置/删除DOM属性，以避免浏览器实施中出现的常见缺陷。

>[!NOTE]
此过程仅适用于经典UI。

### 分步说明{#step-by-step-instructions}

1. 开始CRXDE Lite。 例如：[http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. 复制：

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   到:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   如果中间文件夹不存在，则可能需要创建中间文件夹。

1. 复制：

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   到:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`。

1. 打开以下文件进行编辑（双击打开）：

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. 在`constructor`方法中，在读取行之前：

   ```
   var dialogRef = this;
   ```

   添加以下代码：

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. 打开以下文件：

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`。

1. 在`transferConfigToTable`方法的末尾添加以下代码：

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. 使用&#x200B;**Save All**&#x200B;保存更改

>[!NOTE]
纯文本字段不是唯一允许为标题元素值输入的类型。 任何通过`getValue()`方法提供字幕值的ExtJS小组件均可使用。
要为其他元素和属性添加编辑功能，请确保以下两点：
* 每个对应字段的`itemId`属性将设置为相应DOM属性(`TablePropertiesDialog`)的名称。
* 在DOM元素上显式设置和/或删除属性(`Table`)。

