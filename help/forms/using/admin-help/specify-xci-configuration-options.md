---
title: 指定XCI配置选项
seo-title: Specify XCI configuration options
description: 了解如何指定XCI配置选项。
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 4%

---

# 指定XCI配置选项 {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

输出允许您指定用于渲染的自定义XCI文件。 (请参阅 [为输出指定文件位置](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) 默认情况下，输出会覆盖XCI文件中指定的一些选项，包括：

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

您可以为上面列出的选项选择取消覆盖的选项，在这种情况下，“输出”使用自定义XCI文件中指定的值。

1. 在管理控制台中，单击服务>输出。
1. 选中或取消选中使用系统默认XCI选项复选框。 如果选择此选项，“输出”将使用其数据包、创建者、制作者和compressObjectStream设置的默认值。 取消选择此选项后，“输出”将使用自定义XCI文件中指定的值。
1. 单击“保存”。
