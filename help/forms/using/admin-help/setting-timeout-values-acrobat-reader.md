---
title: 设置超时值以用于Acrobat Reader DC扩展
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: 了解如何设置超时值以与Acrobat Reader DC扩展一起使用。
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---

# 设置超时值以用于Acrobat Reader DC扩展  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在Acrobat Reader DC扩展中处理许多PDF文件时，请确保正确设置了以下超时值，以防止作业超时和失败：

**文档处理超时**

此值可以在管理控制台中设置。 单击设置>核心系统设置>配置，然后为默认文档处理超时指定一个值。

**用户管理器AEM表单超时：** 可以通过编辑config.xml文件来设置此值。 在管理控制台中，单击设置>用户管理>配置>导入和导出配置文件，然后单击导出。 打开导出的config.xml文件并编辑以下行：

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

保存并将config.xml文件导入回管理控制台。

**应用程序服务器会话超时：** 此值可以在应用程序服务器上设置。 有关更多信息，请参阅随应用程序服务器提供的文档。
