---
title: 运行AdministrationConsole时的注意事项
seo-title: Considerations when running AdministrationConsole
description: 本文档列出了运行管理控制台时要考虑的几点。
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 3%

---

# 运行管理控制台时的注意事项 {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

运行管理控制台时，需考虑以下事项：

* 如果您使用URL访问管理控制台， `https://*[hostname]*:*[port]*/adminui`，指定的主机名不能包含下划线字符。 否则，指向管理控制台某些区域的链接可能无法正常工作。
* 如果在日语版操作系统的Windows资源管理器中运行管理控制台，则可能会遇到以下问题：

   * 单击链接会返回到登录页面，而不是预期链接。
   * 单击链接会显示权限错误。

   最佳做法是从其他浏览器（如Mozilla Firefox）运行管理控制台，以确保无链接失败。

* 在管理控制台中执行搜索时，请勿使用反斜线字符()。
