---
title: 在Designer中更改“零页面”内容
seo-title: Changing Page Zero content in Designer
description: 您知道在非Adobe PDF查看器中查看XFAPDF的“零页”上显示的消息时，如何更改该消息？
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 3%

---

# 在Designer中更改“零页面”内容 {#changing-page-zero-content-in-designer}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

默认情况下，当非Adobe PDF查看器(如Chrome或Firefox中的默认PDF查看器)无法读取PDF/XFA表单的内容时，会显示“零页”内容。 默认的零页消息如下所示。

![defaultpage0message](assets/defaultpage0message.png)

AEM Forms功能包1版本的Designer允许您更改在“零页”上显示的消息。 要更改“零页”消息，请执行以下步骤：

1. 确保您安装了AEM Forms Feature Pack 1版本的Designer。 您可以从设计器的“关于”屏幕中检查版本。

1. 打开要更改“零页”内容的表单。

1. 单击 **文件>表单属性**.

1. 在表单属性对话框中，单击 ![plus](assets/plus.png) （加号图标）来添加自定义属性。

1. 指定 **_pagezerocontent** 作为属性的名称。
1. 以富文本格式添加新的零页消息作为值。 例如：

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. 将表单另存为PDF。

1. 在浏览器中查看PDF表单，以确认消息已更新。 上述示例值如下所示：

   ![更改消息](assets/changedmessage.png)

>[!NOTE]
>
>重新打开表单时，您刚刚创建的自定义属性可能无法正确显示在表单属性对话框中。 但是，它运行正常，并且表单会显示更新的“零页”消息。
