---
title: 配置表单的基础知识
seo-title: Basics of configuring forms
description: 了解可帮助您创建交互式数据捕获应用程序的各种表单服务。
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---

# 配置表单的基础知识 {#basics-of-configuring-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Forms服务允许您创建交互式数据捕获客户端应用程序，以验证、处理、转换和交付通常在Designer中创建的表单。 表单作者开发了Forms服务以各种格式呈现的单个表单设计：

* 在Adobe Reader中或在浏览器中作为PDF
* 作为各种浏览器环境的HTML，包括兼容的XHTML 1.0渲染
* 作为表单指南(在支持AdobeFlash Player的各种浏览器环境中)。

有关Forms服务的其他信息，请参阅 [服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

使用管理控制台中的Forms页面，可以配置Forms服务的行为。 这些设置适用于服务的所有调用。 通过AEM Forms SDK发送的任何参数都会覆盖管理控制台中设置的设置；但是，它们只影响这一特定的援引。

在管理控制台中更改Forms设置后，单击保存。 您无需重新启动服务器，更改即可生效。 但是，在配置缓存模式设置时，您可能需要停止并重新启动Forms服务。 (请参阅 [启动和停止服务](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
