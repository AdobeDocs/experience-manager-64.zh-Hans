---
title: 为HTML5表单设计表单模板
seo-title: Designing form templates for HTML5 forms
description: AEM Forms提供将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用Designer设计表单模板，并使用HTML5呈现功能。
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 3%

---

# 为HTML5表单设计表单模板 {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM中的HTML5表单组件提供将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用 [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_cn) 并使用“HTML5”演绎版功能。 这些表单模板及其资产可以驻留在AEM存储库、文件系统中，或通过http公开。 但是，如果您计划使用Forms Manager管理表单，则模板和资产应位于AEM存储库中。

尽管HTML5表单在很大程度上与PDF forms的行为匹配，但两种格式中有一些功能不适用于其他格式。 例如，在Adobe Reader中，条形码如何应用于PDF表单会因移动设备表单而异，或者表单的数字签名方式也因格式而异。 有关此类变体的更多信息，请参阅 [HTML5表单和PDF forms之间的功能区别](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

有关XFA的常见功能，请参阅以下最佳实践和准则以设计可同时使用这两种格式的表单。

## AEM Forms Designer中用于HTML5 Forms的功能 {#capabilities-in-aem-forms-designer-for-html-forms}

### 预览HTML {#preview-html}

“预览”HTML选项卡在“设计”模式下添加，以便表单设计人员在设计过程中以HTML5格式预览表单。 有关如何在AEM Forms Designer中启用和配置此功能的更多信息，请参阅 [预览HTML](/help/forms/using/preview-xdp-forms-html.md).

### 连笔签名 {#scribble-signature}

HTML5表单的关键目标是触控设备。 因此，在AEM Forms Designer中添加了新的涂写签名控件。 您可以单击或拖放表单模板上的潦草签名控件并对其进行配置。 它在HTML5呈现中呈现为涂写字段，可用于在触屏设备上涂写签名。 在台式机上，它可用作使用鼠标控件的涂写字段。 有关如何使用此功能的更多信息，请参阅 [XFA Scribble字段](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
