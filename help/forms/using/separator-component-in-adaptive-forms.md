---
title: 自适应表单中的分隔符组件
seo-title: Separator component in adaptive forms
description: 您可以使用分隔符组件以可视方式分隔表单的各个部分。
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# 自适应表单中的分隔符组件 {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

可以使用分隔符组件以可视方式分隔表单的面板。 您可以通过指定分隔符组件的以下属性来定义分隔符组件的整体外观和样式：

* **元素名称：** 指定组件的名称。 SOM表达式使用元素名称字段中指定的值来寻址组件。
* **厚度：** 以像素为单位指定分隔符组件的厚度。
* **列：** 指定分隔符组件所跨的列数。
* **CSS类：** 指定分隔符组件的自定义CSS类
* **内联样式：** 借助AEM Forms，您现在可以将内联CSS样式应用于单个自适应表单组件并实时预览更改。

要指定分隔符组件的属性，请执行以下操作：

1. 选择分隔符组件并点按 ![cppr](assets/cmppr.png). 将在侧栏中打开属性。
1. 单击内联CSS属性部分中的选项卡以指定CSS属性。 例如：a.在字段选项卡中，单击 **添加项目**. 将添加一行包含两个字段。
1. 在左侧的第一个字段中，指定要应用的CSS3属性。 例如， **边框**. 您还可以通过单击向下箭头按钮来选择属性。 下拉列表并不详尽，您可以在此字段中指定任何受支持的CSS3属性名称。
1. 在相邻的字段中，为指定的CSS3属性指定有效值。 例如， **3像素纯黑色**.
1. 单击 **添加项目** 以指定其他属性及其值。
1. 单击 **预览** 以预览表单中的更改。
1. 单击 **确定** 确认更改，或**取消**退出对话框而不进行任何更改。
