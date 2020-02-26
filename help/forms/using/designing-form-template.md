---
title: 为HTML5表单设计表单模板
seo-title: 为HTML5表单设计表单模板
description: 'AEM Forms提供将XFA表单模板渲染为HTML5格式的功能。 表单设计人员可以使用设计人员设计表单模板，并使用HTML5再现功能。 '
seo-description: 'AEM Forms提供将XFA表单模板渲染为HTML5格式的功能。 表单设计人员可以使用设计人员设计表单模板，并使用HTML5再现功能。 '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 为HTML5表单设计表单模板 {#designing-form-templates-for-html-forms}

AEM中的HTML5表单组件提供将XFA表单模板渲染为HTML5格式。 表单设计人员可以使用 [Forms Designer设计表单模板](https://www.adobe.com/go/learn_aemforms_designer_63) ，并使用HTML5再现功能。 这些表单模板及其资产可以驻留在AEM存储库、文件系统中，或通过http公开。 但是，如果您计划使用Forms manager管理表单，则模板和资产应驻留在AEM存储库中。

尽管HTML5表单在很大程度上与PDF表单的行为匹配，但两种格式中有一些功能不适用于其他格式。 例如，Adobe Reader中PDF表单上的条形码应用方式因移动表单而异，或表单的数字签名方式也因格式而异。 有关这些变体的详细信息，请参 [阅HTML5表单与PDF表单功能区分](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)。

有关常见的XFA功能，请参阅以下设计两种格式均可用的表单的最佳实践和准则。

## AEM Forms Designer for HTML5 Forms中的功能 {#capabilities-in-aem-forms-designer-for-html-forms}

### 预览HTML {#preview-html}

“预览HTML”选项卡在“设计”模式中添加，供表单设计人员在设计过程中预览HTML5格式的表单。 有关如何在AEM Forms Designer中启用和配置此功能的详细信息，请参阅 [预览HTML](/help/forms/using/preview-xdp-forms-html.md)。

### 连笔签名 {#scribble-signature}

HTML5表单的主要目标是触控设备。 因此，AEM Forms Designer中新增了一个涂抹签名控件。 您可以单击或拖放表单模板上的涂鸦式签名控件并对其进行配置。 它在HTML5再现中呈现为涂抹字段，可用于在触控设备上涂抹签名。 在台式机器上，可以使用鼠标控制将其用作涂抹字段。 有关如何使用此功能的详细信息，请参阅 [XFA涂抹字段](/help/forms/using/scribble-signature.md)。

![4](assets/4.png)

[联系支持](https://www.adobe.com/account/sign-in.supportportal.html)
