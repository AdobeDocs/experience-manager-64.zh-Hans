---
title: 配置富文本编辑器
description: 了解如何配置AEM富文本编辑器。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7849a3e2d9d8241382652fb1c8e6e302ffd853e0
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---


# Configure the Rich Text Editor {#configure-the-rich-text-editor}

富文本编辑器(RTE)为作者提供了各种功能来编辑其文本内容。 提供图标、选择框、工具栏和菜单，实现所见即所得的文本编辑体验。

要了解如何使用RTE功能进行创作，请参 [阅使用富文本编辑器进行创作](/help/sites-authoring/rich-text-editor.md)。 RTE可以配置为启用、禁用和扩展创作组件中的可用功能。 以下工作流说明了在Experience Manager中完成RTE配置任务的建议顺序。

![配置富文本编辑器的典型工作流程](assets/rte_workflow_v1.png)

*图： 配置富文本编辑器的典型工作流程*

## 了解触屏优化UI和经典UI {#understand-touch-enabled-ui-and-classic-ui}

触屏优化UI是AEM的标准UI。 Adobe在版本5.6中 [引入了触](/help/sites-authoring/responsive-layout.md) 屏UI，该界面具有用于创作环境的响应式设计。触屏UI专为触控和桌面设备而设计。 UI与原始经典UI差别很大。

![触屏优化UI中的富文本编辑器工具栏](assets/chlimage_1-404.png)

*图： 触屏优化UI中的富文本编辑器工具栏*

![经典UI中的富文本编辑器工具栏](assets/rtedefault.png)

*图： 经典UI中的富文本编辑器工具栏*

>[!MORELIKETHIS]
>
>* [UI建议](/help/sites-deploying/ui-recommendations.md)
>* 关于弃用经典UI，请参 [阅AEM 6.4发行说明](/help/release-notes/deprecated-removed-features.md)
>* 有关UI的区别，请参 [阅触屏UI和经典UI](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* 要详细了解触屏优化UI，请参 [阅AEM触屏优化UI](/help/sites-developing/touch-ui-concepts.md)


## 各种编辑模式 {#editingmodes}

作者可以使用不同的组件模式在AEM中创建和编辑文本内容。 用于创作内容和设置内容格式的工具栏选项以及不同编辑模式下启用RTE的组件的用户体验会因RTE配置而异。

| 编辑模式 | 编辑区域 | 建议启用的功能 | 触屏UI | 经典 UI |
|--- |--- |--- |--- |--- |
| 内嵌 | 就地编辑，实现快速、细微的编辑； 不打开对话框即可设置格式 | 最低RTE功能 | Y | Y |
| RTE全屏 | 覆盖整个页面 | 所有必需的RTE功能 | Y | N |
| 对话框 | 对话框，但不涵盖整个页面 | 经典UI中所有必需的RTE功能； 审慎地启用触控UI中的功能 | Y | Y |
| 全屏对话框 | 与全屏模式相同； 包含RTE旁边对话框的字段 | 所有必需的RTE功能 | Y | N |

>[!NOTE]
>
>在触屏优化UI的内联编辑模式下，源编辑功能不可用。 无法在全屏模式下拖动图像。 所有其他功能在所有模式下都有效。

### 内联编辑 {#inline-editing}

打开(慢速多次点按／单击)后，可在页面中编辑内容。 会显示一个包含基本选项的紧凑工具栏。

![在触屏优化UI中使用基本工具栏进行内联编辑](assets/chlimage_1-405.png)

*图： 在触屏优化UI中使用基本工具栏进行内联编辑*

在经典UI中，慢速多次单击组件可进行内联编辑，橙色轮廓可以突出显示内容。 如果内容查找器处于打开状态，则窗口顶部将显示一个包含可用RTE格式选项的工具栏。 如果内容查找器未打开，则不显示格式选项，您只能进行基本文本编辑。

### Full screen editing {#full-screen-editing}

AEM组件可以以全屏视图打开，从而隐藏页面内容并占据可用屏幕。 考虑对内联编辑的详细版本进行全屏编辑，因为它优惠的编辑选项最多。 在使用内联编辑模 ![式时，可以从紧凑](assets/rte_fullscreen.png)工具栏中单击rte_fullscreen来打开它。

对话框全屏模式提供详细的RTE工具栏以及对话框模式中可用的选项和组件。 它仅适用于包含RTE和其他组件的对话框。

![在触屏优化UI中以全屏模式进行编辑时的详细RTE工具栏](assets/chlimage_1-406.png)

*图： 在触屏优化UI中以全屏模式进行编辑时的详细RTE工具栏*

### 对话框编辑 {#dialog-editing}

在经典UI中多次单击组件时，将打开一个对话框，用于编辑内容。 现有页面顶部将打开对话框。 在某些特定情况下，对话框以弹出窗口的形式打开。 例如，当文本组件是多列页面布局中某列的一部分，且该对话框的可用区域较少时。

![触屏优化UI中的对话框编辑模式](assets/dialog_editing_modetouchui.png)

*图： 触屏优化UI中的对话框编辑模式*

![经典UI中包含用于编辑的详细工具栏的对话框](assets/chlimage_1-407.png)

*图： 经典UI中包含用于编辑的详细工具栏的对话框*

## 关于RTE插件和相关功能 {#aboutplugins}

该功能通过一系列插件提供，每个插件都具有：

* 属 `features` 性：

   * 用于激活或取消激活该插件的基本功能。
   * 可以使用标准化过程进行配置。

* 在适当时，需要进行专门配置的更多属性和选项。

RTE的基本功能由特定于相应插件的节点上 `features` 的属性值激活或取消激活。

下表列表了当前插件，如下所示：

* 带有指向API文档的链接的插件ID。 激活插件时，ID将 [用作节点名称](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)。
* 属性的允许 `features` 值。
* 插件提供的功能描述。

| 插件ID | 特征 | 描述 |
|--- |--- |--- |
| 编辑 | 剪切复制粘贴——默认粘贴——纯文本粘贴-wordhtml | [剪切、复制和，三种粘贴模式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles)。 |
| [findreplace](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | 查找替换 | 查找和替换。 |
| [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | 粗体下划线 | [基本文本格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles)。 |
| [图像](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | 图像 | 基本图像支持（从内容或内容查找器中拖动）。 根据浏览器的不同，支持对作者具有不同的行为 |
| [按键](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | 要定义此值，请参阅 [选项卡大小](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tabsize)。 |
| [证明](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifleft justifycenter justifyright | 段落对齐。 |
| [链接](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modifylink取消链接锚点 | [超链接和锚点](/help/sites-administering/configure-rich-text-editor-plug-ins.md#linkstyles)。 |
| [列表](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | 有序无序缩进 | 此插件同时控制缩 [进和列表](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indentmargin); 包括嵌套列表。 |
| [错误工具](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specifars sourceedit | 其他工具允许作者输入 [特殊字符](/help/sites-administering/configure-rich-text-editor-plug-ins.md#spchar) 或编辑HTML源。 此外，如果要定义 [自己的列表](/help/sites-administering/configure-rich-text-editor-plug-ins.md#definerangechar) ，还可以添加一整套特殊字符。 |
| 参数格式 | 参数格式 | 默认段落格式为段落、标题1、标题2和标`<p>`题3 `<h1>`(、 `<h2>`和 `<h3>`)。 您可以添 [加更多段落格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#paraformats) 或扩展列表。 |
| 拼写检查 | 检查文本 | [语言识别拼写检查器](/help/sites-administering/configure-rich-text-editor-plug-ins.md#adddict)。 |
| 样式 | 样式 | 支持使用CSS类设置样式。 [如果要添加](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles) （或扩展）您自己的样式范围以用于文本，请添加新的文本样式。 |
| 上标 | 下标上标 | 基本格式的扩展，添加子和超级脚本。 |
| 表 | 表可删除的插入程序removerow插入列remove列cellprops mergecellsselectrow选择列 | 如果 [要为整个表](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles)或单个单元格添加您自己的样式，请参阅配置表样式。 |
| 撤消 | 撤消重做 | 撤消和重 [做操作的历史](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undohistory) 大小。 |

>[!NOTE]
>
>对话框模式不支持全屏插件。 使用设置 `dialogFullScreen` 将工具栏配置为全屏模式。

## 了解配置路径和位置 {#understand-the-configuration-paths-and-locations}

您 [为作者提供的RTE编辑模式](#editingmodes) （和UI）决定激活RTE插件时配置详细 [信息的位置](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin):

| 编辑模式 | 触屏UI的位置 | 经典UI的位置 |
|---|---|---|
| 内嵌 | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| 全屏 | `cq:editConfig/cq:inplaceEditing` | 不适用 |
| 对话框 | `cq:dialog` | `dialog` |
| 全屏对话框 | `cq:dialog` | 不适用 |

>[!NOTE]
>
>请勿将节点命名为 `cq:inplaceEditing``config`。 在节 `cq:inplaceEditing` 点上，定义以下属性：
>
>* **名称**: `configPath`
>* **类型**: `String`
>* **值**: 包含实际配置的节点的路径

>
>
请勿将RTE配置节点命名为 `config`。 否则，RTE配置只对管理员有效，对组中的用户无效 `content-author`。

仅在触屏UI中配置在对话框编辑模式下应用的以下属性：

* `useFixedInlineToolbar`: 将在RTE节点(sling:resourceType=)上定义的此布尔属 `cq/gui/components/authoring/dialog/richtext`性设置 `True`为，使RTE工具栏成为固定的而不是浮动的。

   如果此属性为true，则默认情况下，Richtext编辑从“foundation-contentloaded”事件开始。

   要防止出现这种情况，请 `customStart` 将属 `True`性设置为并将“rte-开始”事件触发为开始RTE编辑。 当此属性为“true”时，默认行为(单击时的rte开始)不起作用。

* `customStart`: 将在RTE节点上定义的此布尔属 `True`性设置为，以通过触发开始来控制何时事件RTE `rte-start`。

* `rte-start`: 在RTE事件编 `contenteditable-div` 辑RTE时触发此开始。 仅当设置 `customStart` 为True时，才有效。

在触屏启用对话框中使用RTE时，必须将属 `useFixedInlineToolbar` 性设置为true才能避免问题。

## 自定义就地编辑 {#customizing-in-place-editing}

您可以通过配置以下属性来定义文本编辑器开始的HTML选择器：

* **`editElementQuery`** -在上定 `cq:InplaceEditingConfig`义，此属性用于指定HTML元素的选择器，在该元素上将开始文本组件的内联编辑。 如果未指定，则直接在文本组件HTML上启动内联编辑。
* **`textPropertyName`** -在上定 `cq:InplaceEditingConfig`义，此属性用于指定将保存在内容节点上的属性的名称，在内联编辑后，将保留文本组件的HTML值。

对话框模式的相应属性为 `name`。

## 通过激活插件启用RTE功能 {#enable-rte-functionalities-by-activating-plug-ins}

RTE功能通过一系列插件提供，每个插件都具有features属性。 您可以配置features属性以启用或禁用每个插件的各种功能。

有关RTE插件的详细配置，请 [参阅如何激活和配置RTE插件](/help/sites-administering/configure-rich-text-editor-plug-ins.md)。

下载此示例配置以了解如何配置RTE。 在此包中，所有功能均已启用。

[获取文件](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>核心 [组件文本组件](https://helpx.adobe.com/experience-manager/core-components/using/text.html) ，允许模板编辑器在用户界面中将许多RTE插件配置为内容策略，从而无需进行技术配置。 内容策略可以如所述使用RTE用户界面配置。 有关详细信息，请参 [阅RTE用户界面设置和内容策略](/help/sites-administering/rich-text-editor.md#rtecontentpolicies)[、创建页面模板](/help/sites-authoring/templates.md)以及核心组件开 [发人员文档](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)。

>[!NOTE]
>
>为便于参考，默认文本组件（作为标准安装的一部分提供）可在以下位置找到：
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`

>
>
要创建您自己的文本组件，请复制上述组件，而不是编辑这些组件。

## 配置RTE工具栏 {#dialogfullscreen}

AEM允许您针对不同的编辑模式以不同方式配置富文本编辑器的UI。 默认设置如下所示。 您可以根据要求覆盖这些默认值。

为获得最佳创作体验：

* 在浮动对话框中，只启用那些没有弹出窗口的插件，因为浮动对话框的大小较小。
* 在全屏对话框中，启用所有所需的插件，甚至具有较大弹出窗口的插件， `Paste` 如插件。 请使用下 `dialogFullScreen` 述的配置。

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

内联模式和全屏模式使用不同的UI设置。 工具栏属性用于指定工具栏的按钮。 例如，如果按钮本身是一个功能(例如， `Bold`)，则它被指 `PluginName#FeatureName` 定为(例如 `links#modifylink`)。 如果按钮是跨距（包含插件的某些功能），则它指定 `#PluginName` 为(例如 `#format`)。 分隔符( |)可以使用“-”指定一组按钮之间的值。

内嵌模式或全屏模式下的弹出节点包含正在使用的浏览器的列表。 节点下的每个 `popovers` 子节点都以插件命名(例如 `format`,)。 它有一个 `items` 属性，其中包含插件功能的列表(例如 `format#bold`)。

## RTE用户界面设置和内容策略 {#rtecontentpolicies}

管理员可以使用内容策略控制RTE选项，例如，不要按照上述说明进行配置。 当内容策略用作可编辑模板的一部分时，内容策略会定义组件的 [设计属性](../sites-authoring/templates.md)。 例如，如果将使用RTE的文本组件与可编辑的模板一起使用，内容策略可以定义粗体选项可用，并提供一些段落格式选项。 内容策略可重复使用，并可以跨多个模板应用。

从AEM 6.4 Service Pack 3开始，RTE流中从用户界面配置到内容策略的可用选项。

* 用户界面配置设置定义了内容策略可用的选项。
* 如果删除或未启用RTE的用户界面配置，则内容策略无法配置它。
* 作者只能访问用户界面配置和内容策略提供的功能。

例如，您可以看到文本核 [心组件文档](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)。

## 自定义工具栏图标和命令之间的映射 {#iconstoolbar}

可以自定义RTE工具栏上显示的Coral图标与可用命令之间的映射。 除了Coral图标，您还不能使用任何其他图标。

1. 创建名为的 `icons` 节点 `uiSettings/cui`。

1. 为其下的各个图标创建节点。
1. 在每个单独的图标节点上，指定Coral图标和映射到该图标的命令。

下面是将命令“粗体”映射到名为的“珊瑚”图标的示例代码片 `textItalic`段。

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

在页面上，可以包含CoralUI 2 RTE clientlib或CoralUI 3 RTE clientlib。 默认情况下，富文本编辑器包含CoralUI 3 RTE clientlib。 要切换到CoralUI 2 RTE，请执行以下步骤。

>[!NOTE]
>
>Adobe不建议将切换作为最佳实践。 切换到CoralUI 2 RTE作为最后手段。 如果插件不依赖RTE内部（如类），则CoralUI 2 RTE的自定义插件可与CoralUI 3 RTE一起使用。 如果您正在为CoralUI 3 RTE使用自定义插件，请使用 `rte.coralui3` 库。

1. 叠加下 `/libs/cq/gui/components/authoring/editors/clientlibs/core` 的节 `/apps`点，并执行以下操作：

   * Replace `rte.coralui3` with `rte.coralui2` for the dependencies property.
   * Replace `cq.authoring.editor.core.inlineediting.rte.coralui3` with `cq.authoring.editor.core.inlineediting.rte.coralui2` for the embed property.
   * Replace `cq.authoring.rte.coralui3` with `cq.authoring.rte.coralui2` for the embed property.

1. 叠加节点 `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` 和 `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` 下 `/apps`方。

   从中删除 `cq.authoring.dialog` 类别 `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` 并将其添加到 `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`。

1. 将页面中包含的任何其他依赖关系从更改 `rte.coralui3` 为 `rte.coralui2`。 例如，在覆盖下的节点 `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` 后， `/apps`将对它的任何依赖关系从 `rte.coralui3` 更改为 `rte.coralui2`。

1. 叠加下 `cq/ui/widgets` 的节 `/apps`点。 将节点上的 `cq.rte` 依赖项替换 `/apps/cq/ui/widgets` 为 `cq.coralui2.rte`。

>[!NOTE]
>
>CoralUI 2 RTE使用handlebars模板进行插件对话框。 因此，CoralUI 2 RTE clientlib对handlebars clientlib有依赖关系。 CoralUI 3 RTE不使用handlebars模板，并且没有任何关联的依赖关系。 如果您的自定义插件使用handlebars模板，请在网页中包含handlebars clientlib。

## 更多信息 {#further-information}

有关配置RTE的详细信息，请参 [阅AEM Widget API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) 参考。

尤其要查看可用的插件和相关选项：

* CQ. [form.RichText组件提供](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) 一个表单字段，用于编辑样式文本信息（富文本）。 要了解富文本表单的所有可用参数，请参阅配置选项。
* RichText组件使用CQ.form.rte.plugins.Plugin下列 [出的插件提供各种功能](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)。 对于每个插件：

   * 有关可启用（或禁用）的功能的详细信息，请参阅功能。
   * 有关相应插件的详细配置，请参阅所有可用参数的配置选项。

* 还提供有关链接的HTML规则的更多信息。

以上选项可用于扩展和自定义您自己的RTE。 例如，要在创建链接时列表页面中可用的锚点，您可以提供自己的锚点实现 `LinkPlugin`。

## 已知限制 {#known-limitations}

AEM RTE功能有以下限制：

* RTE功能仅在AEM组件对话框中受支持。 触屏优化UI上的页面属性和基 [架等向导](/help/sites-developing/page-properties-views.md)[或基](/help/sites-authoring/scaffolding.md) 础表单不支持RTE。

* AEM在混合设备 [上不工作](/help/release-notes/known-issues.md)。

* 请勿命名RTE配置节点 `config`。 否则，RTE配置仅对管理员有效，对组中的用户无效 `content-author`。

* RTE不支持嵌入内容的内联框架或iframe。

>[!MORELIKETHIS]
>
>* [配置RTE插件](configure-rich-text-editor-plug-ins.md)
>* [使用富文本编辑器进行创作](../sites-authoring/rich-text-editor.md)
>* [为可访问站点配置RTE](rte-accessible-content.md)
>* [触屏UI和经典UI功能奇偶校验](../release-notes/touch-ui-features-status.md)
>* [创建复合多字段组件的教程范例](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

