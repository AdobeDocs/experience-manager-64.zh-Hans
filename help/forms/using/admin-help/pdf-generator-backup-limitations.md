---
title: PDF生成器备份限制
seo-title: PDF Generator backup limitations
description: 了解PDF生成器备份限制。
seo-description: Learn about PDF Generator backup limitations.
uuid: 9537ffde-4396-46d1-81ea-edcd25923ffb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 23386353-b2bf-49f1-947a-dd7587bba175
noindex: true
exl-id: d2ba9881-02b6-470b-b110-7d4609e6ab24
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 5%

---

# PDF生成器备份限制 {#pdf-generator-backup-limitations}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

无法备份PDF生成器用于转换文件的临时目录。 即使服务将正确恢复，数据仍可能丢失，因为PDF生成器会按设置的时间间隔审查和清除临时目录的内容。
