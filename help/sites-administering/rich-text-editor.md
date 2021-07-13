---
title: 配置富文本编辑器
description: 了解如何配置AEM富文本编辑器。
contentOwner: AG
exl-id: 2d5e9ada-1567-43dc-ab19-6891e20e1d0b
source-git-commit: 160f403d2ec9bfbede75fac2c4315314f98ab27e
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 1%

---

# 配置富文本编辑器 {#configure-the-rich-text-editor}

富文本编辑器(RTE)为作者提供了多种用于编辑其文本内容的功能。 提供了图标、选择框、工具栏和菜单，以体验所见即所得的文本编辑体验。

要了解如何使用RTE功能进行创作，请参阅[使用富文本编辑器进行创作](/help/sites-authoring/rich-text-editor.md)。 RTE可配置为启用、禁用和扩展创作组件中可用的功能。 以下工作流说明了在Experience Manager中完成RTE配置任务的建议顺序。

![配置富文本编辑器的典型工作流](assets/rte_workflow_v1.png)

*图：配置富文本编辑器的典型工作流*

## 了解触屏优化UI和经典UI {#understand-touch-enabled-ui-and-classic-ui}

触屏优化UI是AEM的标准UI。 Adobe在版本5.6中为创作环境引入了[响应式设计](/help/sites-authoring/responsive-layout.md)的触屏UI。触屏UI专为触控和桌面设备而设计。 UI与原始经典UI有很大不同。

![触屏UI中的富文本编辑器工具栏](assets/chlimage_1-404.png)

*图：触屏UI中的富文本编辑器工具栏*

![经典UI中的富文本编辑器工具栏](assets/rtedefault.png)

*图：经典UI中的富文本编辑器工具栏*

>[!MORELIKETHIS]
>
>* [UI推荐](/help/sites-deploying/ui-recommendations.md)
* 有关弃用经典UI的信息，请参阅[AEM 6.4发行说明](/help/release-notes/deprecated-removed-features.md)
* 有关UI之间的差异，请参阅[触屏UI和经典UI](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
* 要详细了解触屏UI，请参阅[AEM触屏UI的概念](/help/sites-developing/touch-ui-concepts.md)


## 各种编辑模式 {#editingmodes}

作者可以使用不同的组件模式在AEM中创建和编辑文本内容。 在不同编辑模式下，用于创作内容和设置内容格式的工具栏选项以及启用RTE的组件的用户体验因RTE配置而异。

| 编辑模式 | 编辑区域 | 建议启用的功能 | 触屏 UI | 经典 UI |
|--- |--- |--- |--- |--- |
| 内嵌 | 就地编辑，以便进行快速、细微的编辑；不打开对话框即可设置格式 | 最小RTE功能 | Y | Y |
| RTE全屏 | 涵盖整个页面 | 所有必需的RTE功能 | Y | N |
| 对话框 | 对话框，但不涵盖整个页面 | 经典UI中所有必需的RTE功能；谨慎地启用触屏UI中的功能 | Y | Y |
| 全屏对话框 | 与全屏模式相同；包含对话框的字段以及RTE | 所有必需的RTE功能 | Y | N |

>[!NOTE]
在触屏UI的内联编辑模式下，源编辑功能不可用。 不能以全屏模式拖动图像。 所有其他功能在所有模式下均可工作。

### 内联编辑 {#inline-editing}

打开（慢速双击/单击）后，可以在页面内编辑内容。 此时会显示一个包含基本选项的紧凑工具栏。

![在触屏UI中使用基本工具栏进行内联编辑](assets/chlimage_1-405.png)

*图：在触屏UI中使用基本工具栏进行内联编辑*

在经典UI中，慢速双击组件可进行内联编辑，橙色大纲会突出显示内容。 如果内容查找器处于打开状态，则窗口顶部将显示一个包含可用RTE格式选项的工具栏。 如果内容查找器未打开，则不会显示格式选项，您只能进行基本文本编辑。

### 全屏编辑 {#full-screen-editing}

AEM组件可以以全屏视图打开，这会隐藏页面内容并占据可用屏幕。 考虑全屏编辑内联编辑的详细版本，因为它提供了最多的编辑选项。 使用内联编辑模式时，可通过单击紧凑工具栏中的![rte_fullscreen](assets/rte_fullscreen.png)打开该工具栏。

对话框全屏模式提供了详细的RTE工具栏以及对话框模式中可用的选项和组件。 该变量仅适用于包含RTE和其他组件的对话框。

![在触屏UI中以全屏模式编辑时，显示的详细RTE工具栏](assets/chlimage_1-406.png)

*图：在触屏UI中以全屏模式编辑时，显示的详细RTE工具栏*

### 对话框编辑 {#dialog-editing}

在经典UI中双击组件时，将打开一个用于编辑内容的对话框。 此时将打开现有页面顶部的对话框。 在某些特定情况下，会以弹出窗口的形式打开该对话框。 例如，当文本组件是多列页面布局中列的一部分，且可用于对话框的区域较少时。

![触屏UI中的对话框编辑模式](assets/dialog_editing_modetouchui.png)

*图：触屏UI中的对话框编辑模式*

![经典UI中包含用于编辑的详细工具栏的对话框](assets/chlimage_1-407.png)

*图：经典UI中包含用于编辑的详细工具栏的对话框*

## 关于RTE插件和关联的功能 {#aboutplugins}

该功能通过一系列插件提供，每个插件均具有：

* `features`属性：

   * 用于激活或停用该插件的基本功能。
   * 可以使用标准化过程进行配置。

* 在适当情况下，需要进行专门配置的更多属性和选项。

RTE的基本功能由特定于相应插件的节点上的`features`属性的值激活或停用。

下表列出了当前的插件，其中显示：

* 包含API文档链接的插件ID。 在[激活插件](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)时，ID将用作节点名称。
* `features`属性的允许值。
* 插件提供的功能描述。

| 插件ID | 功能 | 描述 |
|--- |--- |--- |
| 编辑 | 剪切复制paste-default paste-plaintext paste-wordhtml | [剪切、复制和，三种粘贴模式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles)。 |
| [findreplace](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | 查找替换 | 查找并替换。 |
| [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | 粗斜体下划线 | [基本文本格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles)。 |
| [图像](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | 图像 | 基本图像支持（从内容或内容查找器中拖动）。 根据浏览器的不同，作者支持的行为各不相同 |
| [键](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | 要定义此值，请参阅[选项卡大小](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tab-size)。 |
| [证明](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifleft justifcenter justifright | 段落对齐。 |
| [链接](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink取消链接锚点 | [超链接和锚点](/help/sites-administering/configure-rich-text-editor-plug-ins.md#link-styles)。 |
| [列表](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | 已排序的未排序缩进输出 | 此插件同时控制[缩进和列表](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indent-margin);包括嵌套列表。 |
| [misctools](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | 其他工具允许作者输入[特殊字符](/help/sites-administering/configure-rich-text-editor-plug-ins.md#special-char)或编辑HTML源。 此外，如果要定义自己的列表，还可以添加整个[范围的特殊字符](/help/sites-administering/configure-rich-text-editor-plug-ins.md#define-range-char)。 |
| 参数格式 | paraformat | 默认段落格式为“段落”、“标题1”、“标题2”和“标题3”（`<p>`、`<h1>`、`<h2>`和`<h3>`）。 您可以[添加更多段落格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#para-formats)或扩展列表。 |
| 拼写检查 | checktext | [语言感知拼写检查程序](/help/sites-administering/configure-rich-text-editor-plug-ins.md#add-dict)。 |
| 样式 | 样式 | 支持使用CSS类的样式。 [如果您想要添](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles) 加（或扩展）自己的样式范围以用于文本，请添加新的文本样式。 |
| 子上标 | 下标上标 | 基本格式的扩展，添加子和超脚本。 |
| 表 | 表removetable insertrow removerow insertcolumn removecolumn cellprops mergecells splitcell selectrow selectcolumns | 如果要为整个表或单个单元格添加自己的样式，请参阅[配置表样式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles)。 |
| 撤消 | 撤消重做 | [撤消和重做](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undo-history)操作的历史记录大小。 |

>[!NOTE]
对话框模式不支持全屏插件。 使用`dialogFullScreen`设置配置全屏模式的工具栏。

## 了解配置路径和位置 {#understand-the-configuration-paths-and-locations}

在[激活RTE插件](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)时，您为作者提供的[ RTE编辑（和UI）](#editingmodes)模式决定了配置详细信息的位置：

| 编辑模式 | 触屏UI的位置 | 经典UI的位置 |
|---|---|---|
| 内嵌 | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| 全屏 | `cq:editConfig/cq:inplaceEditing` | 不适用 |
| 对话框 | `cq:dialog` | `dialog` |
| 全屏对话框 | `cq:dialog` | 不适用 |

>[!NOTE]
请勿将`cq:inplaceEditing`下的节点命名为`config`。 在`cq:inplaceEditing`节点上，定义以下属性：
* **名称**: `configPath`
* **类型**: `String`
* **值**:包含实际配置的节点的路径

请勿将RTE配置节点命名为`config`。 否则，RTE配置仅对管理员生效，而对组`content-author`中的用户则不生效。

配置以下仅在触屏UI中在对话框编辑模式中应用的属性：

* `useFixedInlineToolbar`:将RTE节点（一个具有sling:resourceType=的节点）中定义的此布尔属 `cq/gui/components/authoring/dialog/richtext`性设置为， `True`以修复RTE工具栏而不是浮动工具栏。

   当此属性为true时，富文本编辑默认在“foundation-contentloaded”事件中启动。

   要防止出现这种情况，请将属性`customStart`设置为`True`并触发“rte-start”事件以开始RTE编辑。 当此属性为“true”时，默认行为（单击时启动rte）不起作用。

* `customStart`:将RTE节点上定义的此布尔属性设 `True`置为，以通过触发事件来控制何时启动RTE  `rte-start`。

* `rte-start`:在RTE中开始编 `contenteditable-div` 辑RTE时，会触发此事件。仅当`customStart`已设置为true时，这项操作才起作用。

在触屏启用对话框中使用RTE时，必须将属性`useFixedInlineToolbar`设置为true才能避免出现问题。

## 就地自定义编辑 {#customizing-in-place-editing}

您可以通过配置以下属性来定义文本编辑器启动的HTML选择器：

* **`editElementQuery`**  — 在上定 `cq:InplaceEditingConfig`义，此属性用于指定HTML元素的选择器，在该选择器中将启动文本组件的内联编辑。如果未指定，则直接在文本组件HTML上启动内联编辑。
* **`textPropertyName`**  — 在上定 `cq:InplaceEditingConfig`义，此属性用于指定将保存在内容节点中的属性名称，文本组件的HTML值将在内联编辑后保留在该节点中。

对话框模式对应的属性为`name`。

## 通过激活插件启用RTE功能 {#enable-rte-functionalities-by-activating-plug-ins}

RTE功能通过一系列插件提供，每个插件都具有features属性。 您可以配置features属性以启用或禁用每个插件的各种功能。

有关RTE插件的详细配置，请参阅[如何激活和配置RTE插件](/help/sites-administering/configure-rich-text-editor-plug-ins.md)。

下载此配置示例，以了解如何配置RTE。 在此包中，已启用所有功能。

[获取文件](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
[核心组件文本组件](https://helpx.adobe.com/experience-manager/core-components/using/text.html)允许模板编辑器将用户界面中的许多RTE插件配置为内容策略，从而无需进行技术配置。 内容策略可以与RTE用户界面配置配合使用，如所述。 有关更多信息，请参阅[RTE用户界面设置和内容策略](/help/sites-administering/rich-text-editor.md#rtecontentpolicies)、[创建页面模板](/help/sites-authoring/templates.md)和[核心组件开发人员文档](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)。

>[!NOTE]
出于参考目的，默认的文本组件（作为标准安装的一部分提供）可在以下位置找到：
* `/libs/wcm/foundation/components/text`
* `/libs/foundation/components/text`

要创建自己的文本组件，请复制上述组件，而不是编辑这些组件。

## 配置RTE工具栏 {#dialogfullscreen}

AEM允许您针对不同的编辑模式以不同方式配置富文本编辑器的UI。 下面提供了默认设置。 您可以根据要求覆盖这些默认值。

要获得最佳创作体验：

* 在浮动对话框中，仅启用那些没有弹出窗口的插件，因为浮动对话框的大小较小。
* 在全屏对话框中，启用所有必需的插件，甚至包含较大弹出窗口的插件（如`Paste`插件）。 使用下面描述的`dialogFullScreen`配置。

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

内联模式和全屏模式使用不同的UI设置。 工具栏属性用于指定工具栏的按钮。 例如，如果按钮本身是功能（例如`Bold`），则会将其指定为`PluginName#FeatureName`（例如`links#modifylink`）。 如果按钮是弹出窗口（包含插件的某些功能），则会将其指定为`#PluginName`（例如，`#format`）。 分隔符( |)。

内嵌或全屏模式下的弹出节点包含正在使用的浏览器的列表。 `popovers`节点下的每个子节点都以插件命名（例如，`format`）。 其属性`items`包含插件的功能列表（例如`format#bold`）。

## RTE用户界面设置和内容策略 {#rtecontentpolicies}

管理员可以使用内容策略（例如，不执行上述配置）来控制RTE选项。 当用作[可编辑模板](../sites-authoring/templates.md)的一部分时，内容策略会定义组件的设计属性。 例如，如果将使用RTE的文本组件与可编辑的模板一起使用，则内容策略可以定义提供粗体选项和一些段落格式选项。 内容策略可重复使用，并可跨多个模板应用。

AEM 6.4 Service Pack 3之后，RTE流程中从用户界面配置到内容策略的下游可用选项。

* 用户界面配置设置定义可用于内容策略的选项。
* 如果RTE的用户界面配置已删除或未启用项目，则内容策略无法对其进行配置。
* 作者只能访问用户界面配置和内容策略提供的此类功能。

例如，您可以看到[文本核心组件文档](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)。

## 自定义工具栏图标和命令之间的映射 {#iconstoolbar}

您可以自定义RTE工具栏中显示的Coral图标与可用命令之间的映射。 除Coral图标外，您不能使用任何其他图标。

1. 在`uiSettings/cui`下创建名为`icons`的节点。

1. 为下方的各个图标创建节点。
1. 在每个图标节点上，指定一个Coral图标和一个映射到该图标的命令。

下面是一个示例代码片段，用于将命令“粗体”映射到名为`textItalic`的Coral图标。

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## 切换到CoralUI 2富文本编辑器 {#switch-to-coralui-rich-text-editor}

在页面上，您可以包含CoralUI 2 RTE clientlib或CoralUI 3 RTE clientlib。 默认情况下，富文本编辑器包含CoralUI 3 RTE clientlib。 要切换到CoralUI 2 RTE，请执行以下步骤。

>[!NOTE]
Adobe不建议将切换作为最佳实践。 切换到CoralUI 2 RTE作为最后手段。 如果CoralUI 2 RTE的自定义插件不依赖RTE内部版本（如类），则此插件可与CoralUI 3 RTE配合使用。 如果要对CoralUI 3 RTE使用自定义插件，请使用`rte.coralui3`库。

1. 在`/apps`下叠加节点`/libs/cq/gui/components/authoring/editors/clientlibs/core`，然后执行以下操作：

   * 将依赖项属性的`rte.coralui3`替换为`rte.coralui2`。
   * 将embed属性的`cq.authoring.editor.core.inlineediting.rte.coralui3`替换为`cq.authoring.editor.core.inlineediting.rte.coralui2`。
   * 将embed属性的`cq.authoring.rte.coralui3`替换为`cq.authoring.rte.coralui2`。

1. 在`/apps`下叠加`/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3`和`/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`节点。

   从`/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3`中删除类别`cq.authoring.dialog`，并将其添加到`/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`。

1. 将页面上包含的任何其他依赖项从`rte.coralui3`更改为`rte.coralui2`。 例如，在`/apps`下覆盖节点`/libs/mcm/campaign/components/touch-ui/clientlibs/rte`后，将对该节点的任何依赖项从`rte.coralui3`更改为`rte.coralui2`。

1. 在`/apps`下叠加节点`cq/ui/widgets`。 将节点`/apps/cq/ui/widgets`上的依赖项`cq.rte`替换为`cq.coralui2.rte`。

>[!NOTE]
CoralUI 2 RTE对插件对话框使用handlebars模板。 因此，CoralUI 2 RTE clientlib对handlebars clientlib存在依赖关系。 CoralUI 3 RTE不使用handlebars模板，并且没有任何关联的依赖项。 如果您的自定义插件使用handlebars模板，请在网页中包含handlebars clientlib。

## 更多信息 {#further-information}

有关配置RTE的更多信息，请参阅[AEM小组件API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html)参考。

特别是，要查看可用的插件和相关选项，请执行以下操作：

* [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)组件提供了用于编辑样式化文本信息（富文本）的表单字段。 要了解富文本表单的所有可用参数，请参阅配置选项。
* 富文本组件使用[CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)下列出的插件提供了多种功能。 对于每个插件：

   * 有关可启用（或禁用）的功能的详细信息，请参阅功能。
   * 有关相应插件的详细配置，请参阅配置选项以了解所有可用参数。

* 还提供了有关链接HTML规则的更多信息。

以上选项可用于扩展和自定义您自己的RTE。 例如，要列出在创建链接时页面中可用的锚点，您可以提供您自己的`LinkPlugin`实施。

## 已知限制 {#known-limitations}

AEM RTE功能具有以下限制：

* 仅在AEM组件对话框中支持RTE功能。 在触屏UI中，向导或基础表单（如[页面属性](/help/sites-developing/page-properties-views.md)和[基架](/help/sites-authoring/scaffolding.md)）不支持RTE。

* AEM在[混合设备](/help/release-notes/known-issues.md)上不起作用。

* 请勿将RTE配置节点命名为`config`。 否则，RTE配置将仅对管理员生效，而对组`content-author`中的用户则不生效。

* RTE不支持嵌入内容的内联框架或iFrame。

>[!MORELIKETHIS]
* [配置RTE插件](configure-rich-text-editor-plug-ins.md)
* [使用富文本编辑器进行创作](../sites-authoring/rich-text-editor.md)
* [为可访问的站点配置RTE](rte-accessible-content.md)
* [触屏UI和经典UI功能对等性](../release-notes/touch-ui-features-status.md)
* [创建复合多字段组件的教程示例](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

