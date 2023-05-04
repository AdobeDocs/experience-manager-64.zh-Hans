---
title: 指定安全设置
seo-title: Specifying security settings
description: 了解如何指定安全设置。
seo-description: Learn how to specify security settings.
uuid: 63ba7819-e4eb-4d28-8463-142ff4233a1e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 36a7e16f-d09d-4cc5-babd-1ccadba76e16
exl-id: 0bda2e58-9470-48fa-a60b-04a1a32689bb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 6%

---

# 指定安全设置 {#specifying-security-settings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Forms允许您控制是否解析XML输入中的外部实体。 默认情况下，这些表单已解析，但您可以更改此行为以提高AEM表单系统的安全性。

**阻止处理包含对外部实体的引用的XML数据文件**

1. 在管理控制台中，单击 **[!UICONTROL 服务>Forms]**.
1. 清除“解析外部实体”(Resolve External Entities)复选框。
1. 单击“**[!UICONTROL 保存]**”。
