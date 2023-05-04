---
title: 指定安全设置
seo-title: Specify security settings
description: 了解如何指定安全设置。
seo-description: Learn how to specify security settings.
uuid: c86ba195-010d-40d6-9f9d-4cb4c364d104
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3c017f9a-aa7f-4d12-ba8b-9fd92c029157
exl-id: 3cc39a24-dbdf-4a4c-9c96-4d39d8cff20d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 6%

---

# 指定安全设置 {#specify-security-settings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过输出，可以控制是否解析XML输入中的外部实体。 默认情况下，这些表单已解析，但您可以更改此行为以提高AEM表单系统的安全性。

**阻止处理包含对外部实体的引用的XML数据文件**

1. 在管理控制台中，单击服务>输出。
1. 清除“解析外部实体”(Resolve External Entities)复选框。
1. 单击“保存”。
