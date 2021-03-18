---
title: 设计可访问的HTML5表单
seo-title: 设计可访问的HTML5表单
description: HTML5表单使用ARIA HTML5辅助工具标准。 这些表单支持选项卡式导航，并经过认证可与通用屏幕阅读器兼容。
seo-description: HTML5表单使用ARIA HTML5辅助工具标准。 这些表单支持选项卡式导航，并经过认证可与通用屏幕阅读器兼容。
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: 移动设备表单
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 设计可访问的HTML5表单{#designing-accessible-html-forms}

HTML5表单使用ARIA HTML5辅助工具标准生成可访问的HTML表单。 这些表单支持选项卡式导航（Mozilla FireFox除外），并经认证可与常见屏幕阅读器兼容。 要生成具有良好辅助功能的HTML5表单，请根据某些[基本设计准则](/help/forms/using/best-practices-for-html5-forms.md)设计XFA表单模板。 设计准则包括配置正确的跳位顺序并为每个表单控件提供演讲文本内容。 AEM Forms Designer支持设置这些表单控件属性以生成可访问的PDF和HTML5表单。

*注意：选项卡式导航不涵盖受保护的字段，如显示值总和的计算字段。要使屏幕阅读器阅读受保护字段的值，请将空的“只读”字段放在受保护字段的顶部或旁边。 将受保护字段的值指定给新的只读字段。 屏幕阅读器或选项卡式导航可以选取此只读字段并将其作为受保护字段的值进行标注。*

AEM Forms Designer包含许多可传递给屏幕阅读器的“讲话文本”选项。 对于表单中的每个对象，用户可以为屏幕阅读器文本指定以下设置之一：

* 自定义屏幕阅读器文本，可以使用“辅助工具”调板设置。 作者可以对按钮和字段的名称及其用途进行注释。
* 工具提示，可在“辅助功能”调板中设置。
* 表单中字段的题注。
* 对象的名称，在“绑定”选项卡的“名称”选项中指定。

![辅助](assets/accessibility.png)

当工具提示、屏幕Reader文本和题注等多个选项在Form控件上可用时，屏幕Reader仅使用这些属性之一。 默认顺序为“自定义屏幕Reader文本”、“工具提示”、“题注”和“名称”。 可以使用“辅助功能”调板中的“屏幕Reader”**“优先级”**&#x200B;选项覆盖默认顺序。
