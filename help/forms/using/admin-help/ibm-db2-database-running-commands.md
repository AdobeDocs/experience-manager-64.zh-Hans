---
title: '"IBM DB2数据库：运行命令以进行定期维护”'
seo-title: "IBM DB2 database: Running commands for regular maintenance"
description: 本文档列出了为定期维护AEM Forms数据库而建议使用的IBM DB2命令。
seo-description: This document lists IBM DB2 commands that are recommended for regular maintenance of your AEM forms database.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
exl-id: b4877c24-3450-44b6-adcd-78a694b28857
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# IBM DB2数据库：运行命令以进行定期维护 {#ibm-db-database-running-commands-for-regular-maintenance}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

建议使用以下IBM DB2命令来定期维护AEM Forms数据库。 有关DB2数据库的维护和性能优化的详细信息，请参阅 *IBM DB2管理指南*.

* **运行统计：** 此命令更新描述数据库表的物理特征及其关联的索引的统计信息。 由AEM表单生成的动态SQL语句会自动使用这些更新的统计信息，但在数据库内构建的静态SQL语句要求 `db2rbind` 命令。
* **db2rbind:** 此命令重新绑定数据库中的所有包。 运行 `runstats` 用于重新验证数据库中所有包的实用程序。
* **重组表或索引：** 此命令检查是否需要对某些表和索引进行重组。

   随着数据库的增长和变化，重新计算表统计信息对于提高数据库性能至关重要，应定期执行。 这些命令可以通过使用脚本或通过使用cron作业手动运行。

>[!NOTE]
>
>运行 `runstats` 命令时，数据库必须包含数据，并且必须至少执行了一个目录同步。

对于小型数据库（如10,000个用户或2,500个组），只需调用 `runstats` 命令来缩短同步计时。

对于较大的数据库（如100,000个用户或10,000个组），运行 `reorg` 命令 `runstats` 命令。

## 在AEM Forms数据库上使用runstats命令 {#use-the-runstats-command-on-your-aem-forms-database}

运行 `runstats` 命令。

>[!NOTE]
>
>的 `runstats` 命令只需在第一次数据库同步期间运行。 但是，在该过程中必须运行两次：在用户和群组同步期间，在群组成员同步期间，先执行一次。 确保脚本在您每次运行时都完全执行。

有关正确的语法和用法，请参阅数据库制造商的文档。 下面， `<schema>` 用于表示与DB2用户名关联的架构。 如果安装了简单的缺省DB2，则此为数据库架构名称。

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGROUPENTITY FOR INDEXES ALL 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY FOR INDEXES ALL
```

## 在AEM Forms数据库上运行reorg命令 {#run-the-reorg-command-on-your-aem-forms-database}

运行 `reorg` 命令。 有关正确的语法和用法，请参阅数据库制造商的文档。

```as3
     TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY 
  
     TABLE <schema>.EDCPRINCIPALENTITY 
  
     TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALUSERENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGROUPENTITY 
  
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
```
