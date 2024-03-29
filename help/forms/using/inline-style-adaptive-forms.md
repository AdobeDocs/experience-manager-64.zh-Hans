---
title: 自适应表单组件的内联样式
seo-title: Inline CSS properties for adaptive form components
description: 虽然您可以在自适应表单上应用自定义样式，但也可以在自适应表单的各个组件上应用内联CSS属性。
seo-description: While you can apply custom styles on an adaptive form, you can also apply inline CSS properties on individual components of an adaptive form.
uuid: ab948f02-3b41-4304-955b-6dd51d27088e
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 91a41bc1-3fa3-4467-b3f8-5570ba7757c0
feature: Adaptive Forms
exl-id: 8e7ba9d2-207f-419b-bcd5-74ba9b14ab92
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 3%

---

# 自适应表单组件的内联样式 {#inline-styling-of-adaptive-form-components}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以通过使用指定样式来定义自适应表单的整体外观和样式 [主题编辑器](/help/forms/using/themes.md). 此外，您还可以将内联CSS样式应用于单个自适应表单组件，并即时预览更改。 内联样式会覆盖主题中提供的样式。

## 应用内联CSS属性 {#apply-inline-css-properties}

要向组件添加内联样式，请执行以下操作：

1. 在表单编辑器中打开表单，然后将模式更改为样式模式。 要将模式更改为样式模式，请在页面工具栏中，点按 ![画布下拉列表](assets/canvas-drop-down.png) > **样式**.
1. 在页面中选择组件，然后点按编辑按钮 ![edit-button](assets/edit-button.png). 在侧栏中打开样式属性。

   您还可以从侧栏的表单层次结构树中选择组件。 表单层次结构树在侧栏中可用作表单对象。

   您还可以从侧栏中选择组件。 在样式模式下，您可以看到在表单对象下列出的组件。 但是，侧栏中的“表单对象”列表会列出字段和面板等组件。 字段和面板是可包含文本框和单选按钮等组件的通用组件。

   从侧栏中选择组件时，您会看到列出的所有子组件以及选定组件的属性。 您可以选择特定的子组件并设置其样式。

1. 单击侧栏中的选项卡以指定CSS属性。 您可以指定以下属性：

   * Dimension和位置（显示设置、内边距、高度、宽度、边距、位置、z-index、浮动、清除、溢出）
   * 文本（字体系列、粗细、颜色、大小、行高和对齐方式）
   * 背景（图像和渐变、背景颜色）
   * 边框（宽度、样式、颜色、半径）
   * 效果（阴影、容量）
   * 高级（允许您为组件编写自定义CSS）

1. 同样，您也可以将样式应用于组件的其他部分，如小组件、题注和帮助。
1. 点按 **完成** 确认更改或 **取消** 以放弃更改。

## 示例：字段组件的内联样式 {#example-inline-styles-for-a-field-component}

以下图像描述了将内联样式应用于文本字段前后的文本字段。

![应用内联样式之前的文本框组件](assets/no-style.png)

应用内联样式属性之前的文本框组件

请注意，在应用以下CSS属性后，文本框样式发生了更改，如下图所示。

<table> 
 <tbody> 
  <tr> 
   <td><p>选择器</p> </td> 
   <td><p>CSS属性</p> </td> 
   <td><p>价值</p> </td> 
   <td><p>效果</p> </td> 
  </tr> 
  <tr> 
   <td><p>字段</p> </td> 
   <td><p>边框</p> </td> 
   <td><p>边框宽度= 2像素</p> <p>边框样式=实线</p> <p>边框颜色=#1111</p> </td> 
   <td><p>在字段周围创建一个黑色的2像素宽边框</p> </td> 
  </tr> 
  <tr> 
   <td><p>文本框</p> </td> 
   <td><p>background-color</p> </td> 
   <td><p>#6495ED</p> </td> 
   <td><p>将背景颜色更改为玉米花蓝色(#6495ED)</p> <p>注意：您可以在值字段中指定颜色名称或其十六进制代码。</p> </td> 
  </tr> 
  <tr> 
   <td><p>标签</p> </td> 
   <td><p>维度和位置&gt;宽度</p> </td> 
   <td><p>100px</p> </td> 
   <td><p>将标签的宽度修复为100像素</p> </td> 
  </tr> 
  <tr> 
   <td>字段帮助图标</td> 
   <td>文本&gt;字体颜色</td> 
   <td>#2ECC40</td> 
   <td>更改帮助图标面的颜色。</td> 
  </tr> 
  <tr> 
   <td><p>长描述</p> </td> 
   <td><p>text-align</p> </td> 
   <td><p>居中</p> </td> 
   <td><p>将帮助的长说明与中心对齐</p> </td> 
  </tr> 
 </tbody> 
</table>

![应用内联样式后的文本框样式](assets/applied-style.png)
**图：** *应用内联样式属性后的文本框组件*

按照上述步骤，您可以选择其他组件（如面板、提交按钮和单选按钮）并设置其样式。

>[!NOTE]
>
>样式属性因您选择的组件而异。
