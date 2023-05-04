---
title: 面向EMC Documentum用户的Connector备份策略
seo-title: Backup strategy for Connector for EMC Documentum users
description: 检查如何为EMC Documentum用户创建Connector备份策略。
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 5d8a0476-5231-4e1d-96c4-ae3df68e09f0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e83b1a59-a730-4d22-9d58-1c9c38e5d534
exl-id: 933c3903-2040-41f4-b803-4d672ce9a2dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 2%

---

# 面向EMC Documentum用户的Connector备份策略 {#backup-strategy-for-connector-for-emc-documentum-users}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如果安装了EMC Documentum的连接器，除了本章中的说明外，您的备份和恢复策略还必须包括备份（或恢复）相应ECM系统所安装的计算机。 （请参阅ECM Documentum文档）。

使用ECM存储库并执行以下任务来备份AEM表单环境：

* 按照本文档中描述的说明备份AEM表单。
* 按照 [备份EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

使用ECM存储库并执行以下任务来恢复AEM表单环境：

* 按照 [恢复EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* 按照本文档中描述的说明恢复AEM表单。
