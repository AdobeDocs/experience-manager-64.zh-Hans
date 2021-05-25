---
title: 设计无障碍的HTML5表单
seo-title: 设计无障碍的HTML5表单
description: HTML5表单使用ARIA HTML5辅助功能标准。 这些表单支持选项卡式导航，并经认证与通用屏幕阅读器兼容。
seo-description: HTML5表单使用ARIA HTML5辅助功能标准。 这些表单支持选项卡式导航，并经认证与通用屏幕阅读器兼容。
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: 移动设备表单
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 设计可访问的HTML5表单{#designing-accessible-html-forms}

HTML5表单使用ARIA HTML5辅助功能标准生成无障碍的HTML表单。 这些表单支持选项卡式导航（Mozilla FireFox除外），并经认证与常见屏幕阅读器兼容。 要生成具有良好辅助功能的HTML5表单，请根据一些[基本设计准则](/help/forms/using/best-practices-for-html5-forms.md)来设计XFA表单模板。 设计准则包括配置正确的选项卡顺序并为每个表单控件提供讲话文本内容。 AEM Forms Designer支持设置这些表单控件属性以生成无障碍的PDF和HTML5表单。

*注：选项卡式导航不涵盖受保护的字段，如显示值总和的计算字段。为了让屏幕阅读器读取受保护字段的值，请在受保护字段的顶部或旁边放置一个空的只读字段。 将受保护字段的值分配给新的只读字段。 屏幕阅读器或选项卡式导航可选取此只读字段，并将其作为受保护字段的值来标注。*

AEM Forms Designer包含许多可传递给屏幕阅读器的“讲话文本”选项。 对于表单中的每个对象，用户可以为屏幕阅读器文本指定以下几个设置之一：

* 自定义屏幕阅读器文本，可使用辅助功能面板进行设置。 作者可以对按钮和字段的名称及其用途添加批注。
* 工具提示，可在辅助功能面板中设置。
* 表单中字段的字幕。
* 对象的名称，在“绑定”(Binding)选项卡的“名称”(Name)选项中指定。

![辅助功能](assets/accessibility.png)

当表单控件上有多个选项(如工具提示、屏幕Reader文本和标题)可用时，屏幕Reader仅使用这些属性之一。 默认顺序为“自定义屏幕Reader文本”、“工具提示”、“标题”和“名称”。 您可以使用辅助功能面板中的屏幕Reader **优先级**&#x200B;选项覆盖默认顺序。
