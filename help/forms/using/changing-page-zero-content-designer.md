---
title: 在设计器中更改零页内容
seo-title: 在设计器中更改零页内容
description: 您知道在非Adobe PDF查看器中查看XFA PDF时，如何更改XFA PDF的“Page Zero”上显示的消息？
seo-description: 您知道在非Adobe PDF查看器中查看XFA PDF时，如何更改XFA PDF的“Page Zero”上显示的消息？
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---


# 在设计器中更改零页内容 {#changing-page-zero-content-in-designer}

当非Adobe PDF查看器（如Chrome或Firefox中的默认PDF查看器）无法读取PDF/XFA表单的内容时，默认情况下会显示“零页”内容。 默认的“Page Zero”消息如下所示。

![defaultpage0message](assets/defaultpage0message.png)

AEM Forms功能包1版本的设计器允许您更改在零页上显示的消息。 要更改“Page Zero”（零页）消息，请执行以下步骤：

1. 确保已安装AEM Forms功能包1版本的Designer。 您可以从设计人员的“关于”屏幕检查版本。

1. 打开要更改其“零页”内容的表单。

1. 单击“ **文件”>“表单属性**”。

1. 在表单属性对话框中，单 ![击加](assets/plus.png) （加号图标）以添加自定义属性。

1. 指定 **_pagezerocontent** 作为属性的名称。
1. 以富文本格式添加新的“零页”消息作为值。 例如：

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. 将表单另存为PDF。

1. 视图浏览器中的PDF表单以确认消息已更新。 上面的示例值如下所示：

   ![更改消息](assets/changedmessage.png)

>[!NOTE]
>
>当您重新打开表单时，您刚刚创建的自定义属性可能无法在表单属性对话框中正常显示。 但是，它工作正常，并且表单显示更新的“零页”消息。

