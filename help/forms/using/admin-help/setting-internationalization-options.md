---
title: 设置国际化选项
seo-title: Setting internationalization options
description: 了解如何指定用于呈现表单的区域设置，以及如何指定用于对输出流进行编码的字符集。
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 3%

---

# 设置国际化选项{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 指定用于呈现表单的区域设置 {#specify-the-locale-used-to-render-forms}

您可以指定呈现PDF表单时使用的区域设置。 PDF表单上的字段使用指定的区域设置来显示数据。 例如，如果区域设置为德语，则表单对数字值使用德语小数分隔符。 区域设置还用于将验证消息作为HTML转换的一部分发送到客户端设备（如Web浏览器）。

1. 在管理控制台中，单击服务> Forms。
1. 在“国际化”的“语言”列表下，选择用于呈现表单的区域设置。 默认值为英语（美国）。
1. 单击“保存”。

## 指定用于对输出流进行编码的字符集 {#specify-the-character-set-used-to-encode-the-output-stream}

1. 在“国际化”下的“字符集”列表中，选择一个字符集。 此设置取决于所使用的API，即renderHTMLForm或renderPDFForm。 要指定所列字符集以外的字符集，请选择“自定义”，然后在显示的框中指定编码值。

   对于HTML转换，AEM表单支持由 `java.nio.charset` 包。 如果sFormPreference是PDFForm，则仅支持特定字符集。 字符集必须是有效的规范名称。 默认值为ISO-8859-1。

1. 单击“保存”。
