---
title: 设计HTML5表单的表单模板
seo-title: 设计HTML5表单的表单模板
description: 'AEM Forms优惠将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用设计人员设计表单模板，并使用HTML5再现功能。 '
seo-description: 'AEM Forms优惠将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用设计人员设计表单模板，并使用HTML5再现功能。 '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# 设计HTML5表单的表单模板{#designing-form-templates-for-html-forms}

AEM优惠中的HTML5表单组件将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用[Forms设计人员](https://www.adobe.com/go/learn_aemforms_designer_63)设计表单模板，并使用HTML5再现功能。 这些表单模板及其资产可以驻留在AEM存储库、文件系统或通过http公开。 但是，如果您计划使用Forms管理器管理表单，模板和资产应驻留在AEM存储库中。

虽然HTML5表单在很大程度上与PDF forms的行为相匹配，但两种格式中都有一些不适用于其他格式的功能。 例如，在Adobe Reader州，条码在PDF表单上的应用方式因移动表单而异，或者表单的数字签名方式也因格式而异。 有关这些变体的详细信息，请参阅[HTML5表单与PDF forms之间的功能区别](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)。

有关常见的XFA功能，请参阅以下设计两种格式的表单的最佳实践和指南。

## AEM FormsHTML5Forms设计器{#capabilities-in-aem-forms-designer-for-html-forms}中的功能

### 预览HTML {#preview-html}

预览HTML选项卡在设计模式下添加，供表单设计人员在设计过程中预览HTML5格式的表单。 有关如何在AEM Forms设计器中启用和配置此功能的详细信息，请参阅[预览HTML](/help/forms/using/preview-xdp-forms-html.md)。

### 连笔签名 {#scribble-signature}

HTML5表单的关键目标是触控设备。 因此，在AEM Forms设计器中增加了新的涂写签名控件。 您可以单击或拖放表单模板上的涂鸦签名控件并对其进行配置。 它在HTML5再现中呈现为涂抹字段，并可用于在触控设备上涂抹签名。 在台式机上，可以使用鼠标控件将其用作涂鸦字段。 有关如何使用此功能的详细信息，请参阅[XFA Scribble Field](/help/forms/using/scribble-signature.md)。

![4](assets/4.png)
