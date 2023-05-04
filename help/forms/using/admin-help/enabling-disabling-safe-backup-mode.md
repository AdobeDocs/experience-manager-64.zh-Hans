---
title: 启用和禁用安全备份模式
seo-title: Enabling and disabling safe backup mode
description: 在“备份设置”页上，您可以以安全备份模式操作AEM表单，以便可靠地备份数据库和全局文档存储(GDS)(GDS)目录。 了解如何启用和禁用安全备份模式。
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 2%

---

# 启用和禁用安全备份模式 {#enabling-and-disabling-safe-backup-mode}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在“备份设置”页上，您可以以安全备份模式操作AEM表单，以便可靠地备份数据库和全局文档存储(GDS)(GDS)目录。

当AEM表单处于安全备份模式时，它可正常运行，但它不会主动从GDS目录中删除文件。

>[!NOTE]
>
>设置此选项不会备份您的系统；它为您的系统准备备份。

## 启用安全备份模式 {#enable-safe-backup-mode}

1. 在管理控制台中，单击设置>核心系统设置>备份设置。
1. 在“备份设置”页面上，选择在安全备份模式下操作，然后单击确定。

>[!NOTE]
>
>如果系统已在安全备份模式下运行，则单击“确定”后将不会创建新的保留。

## 禁用安全备份模式 {#disable-safe-backup-mode}

1. 在管理控制台中，单击设置>核心系统设置>备份设置。
1. 在“备份设置”页中，取消选择在安全备份模式下操作，然后单击确定。
