---
title: 更改字符集
seo-title: Change the character set
description: 您可以指定用于对输出流进行编码的字符集。 了解如何更改字符集。
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 7961efc6-4b11-423a-871d-7b37e3f36781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 更改字符集 {#change-the-character-set}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以指定用于对输出流进行编码的字符集。

1. 在管理控制台中，单击 **[!UICONTROL 服务>输出]**.
1. 在“国际化”下的“字符集”列表中，选择一个字符集。 此设置取决于 `TransformationFormat` 和 `PrintFormat` 通过API指定。 要指定所列字符集以外的字符集，请选择“自定义”，然后在显示的框中指定编码值。

   如果 `TransformationFormat` 是PDF和PDF/A或 `PrintFormat` 是PCL、PostScript、Zebra标签、IPL、DPL、TPCL、GenericColorPCL或GenericPSLevel3，则仅支持特定字符集。

   字符集必须是有效的规范名称。 默认值为ISO-8859-1。

1. 单击“**[!UICONTROL 保存]**”。
