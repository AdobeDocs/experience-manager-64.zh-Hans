---
title: 识别PDF文档中的有效证书和过期证书
seo-title: Recognizing valid and expired certificates in PDF documents
description: 了解如何识别PDF文档中的有效和过期的证书。
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 识别PDF文档中的有效证书和过期证书 {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在Adobe Reader中打开具有由Reader扩展应用的使用权限的PDF文档时，将显示一个状态栏，用于描述该PDF文档中启用的特定使用权限。

当指定PDF文档的使用权限的数字证书过期，并在Adobe Reader中打开PDF文档时，将显示一个对话框，告知用户PDF文档具有使用权限，但这些权限处于禁用状态。 尽管该消息表示PDF文档已被更改或篡改，但情况不一定如此。 Adobe Reader在证书过期或文档被修改时显示此消息。 在Adobe Reader 7.0.x或更高版本中，您无法确定当前出现的问题是哪种情况。

关闭对话框后，Adobe Reader会打开PDF文档。 使用Acrobat Reader DC扩展应用的使用权限无法按预期使用。 如果PDF文档是交互式表单，则表单字段会被锁定，用户无法更改表单数据。
