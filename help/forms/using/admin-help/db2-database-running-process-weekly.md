---
title: '"DB2数据库：每周运行进程”'
seo-title: "DB2 database: Running a process weekly"
description: 了解如何提高AEM Forms DB2数据库的性能。
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%

---

# DB2数据库：每周运行进程{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如果您的AEM表单DB2数据库开始运行缓慢，则每周运行以下进程可以提高其性能：

1. 启动DB2控制中心：

   (Windows)选择“开始”>“程序”>“IBM DB2”>“一般管理工具”>“控制中心”。

   （Linux和UNIX）在命令提示符下，键入 `db2jcc` 命令。

1. 在DB2控制中心对象树中，单击“所有数据库”。
1. 单击为AEM表单创建的数据库，然后单击表文件夹。
1. 在“内容”窗格中选择所有数据库表，右键单击它们并选择“运行统计”。
1. 转到“统计”>“索引统计”。
1. 选择“收集所有索引的统计信息”，选择“收集具有扩展详细统计信息的索引的统计信息”，然后单击“确定”。

该过程完成后，会显示一条消息。 关闭消息。
