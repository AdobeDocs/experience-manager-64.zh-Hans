---
title: 输出服务概述
seo-title: Overview of output service
description: 输出允许您将XML表单数据与在Designer中创建的表单设计合并，以创建各种格式的文档输出流。
seo-description: Output lets you merge XML form data with a form design created in Designer to create a document output stream in various formats.
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
exl-id: 00ca8bdf-77be-4f4c-a3d3-d61d13eeba7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---

# 输出服务概述 {#overview-of-output-service}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

输出允许您将XML表单数据与在Designer中创建的表单设计合并，以创建各种格式的文档输出流。 输出流可以发送到网络打印机、本地打印机或磁盘文件

您可以使用管理控制台中的“输出”页来管理输出服务。 未通过AEM Forms API指定对等设置时，将在运行时使用您配置的设置。 通过AEM Forms SDK完成的配置将覆盖使用管理控制台配置的设置。

有关输出服务的其他信息，请参阅 [服务参考](https://www.adobe.com/go/learn_aemforms_services_61).

在管理控制台的“输出”页面上，您可以执行以下几项任务：

* 指定用于国际化的字符集。 (请参阅 [更改字符集](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* 为URL、URI、XCI和文件位置指定绝对路径和相对路径。 (请参阅 [为输出指定文件位置](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* 配置缓存大小和策略。 (请参阅 [指定缓存模式](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) 和 [配置缓存设置](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* 使字体在应用程序服务器上可用。 (请参阅 [使字体可用](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* 指定要嵌入的字体。 (请参阅 [指定要嵌入的字体](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* 指定XCI配置选项。 (请参阅 [指定XCI配置选项](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* 指定安全设置。 (请参阅 [指定安全设置](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

更改设置后，单击“保存”(Save)，将其应用于“输出”(Output)。 您无需重新启动服务器即可使更改生效，但在配置缓存设置时可能需要重新启动输出服务。
