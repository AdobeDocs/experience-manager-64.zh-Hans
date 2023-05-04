---
title: 删除表单和相关资源
seo-title: Deleting forms and related resources
description: 如何在AEM Forms中删除表单或资产，以及对引用和引用资产及XFA表单的影响。
seo-description: How to delete a form or an asset in AEM Forms and the impact on referenced and referring assets and XFA forms.
uuid: df522b87-59d8-4678-922d-c9aab82b1381
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: c8519eec-f841-4867-baa9-a9e03042755e
role: Admin
exl-id: 94a66d83-b359-4be6-b668-4b4ba024b1e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# 删除表单和相关资源 {#deleting-forms-and-related-resources}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以删除表单和资产，以从存储库中删除这些资产。 删除操作适用于所有资产类型和文件夹。

如果从创作实例中删除资产，则该资产也会从发布实例中删除。 AEM Forms服务器由创作实例和发布实例组成。 创作实例用于创建和管理表单资产和资源。 发布实例包含已发布的表单资产以及可用于最终用户的相关资源。

## 如何删除表单 {#how-to-delete-a-form}

1. 通过访问以下链接，登录到AEM Forms用户界面 `https://[hostname]:[portport]/aem/forms.html.`
1. 导航到要删除的表单并选择该表单。 单击删除 ![aem6forms_delete2](assets/aem6forms_delete2.png) 并确认删除操作。

   >[!NOTE]
   >
   >一次只能删除一个表单。 单独删除多个表单，或删除父文件夹。

1. 在删除资产之前，AEM Forms会检查是否有引用，并请求明确确认。 如果要删除资产而不考虑关系状态，请单击强制删除。

   >[!NOTE]
   >
   >删除由其他资产引荐的资产可能会导致功能问题。

   >[!NOTE]
   >
   >如果选定的资产是文件夹，并且在其层级中包含此类资产，请单独删除其他资产，或删除整个文件夹。

## 删除引用的XFA表单的影响 {#impact-of-deleting-a-referenced-xfa-form}

在AEM Forms中，XFA表单模板可以由自适应表单或其他XFA表单模板引用。 此外，模板可以引用资源或其他XFA模板。

不建议删除由自适应表单引用的XFA表单，因为它可能会损坏自适应表单。 当自适应表单引用XFA表单时，将绑定其字段。 删除XFA后，自适应表单无法将其字段与XFA字段同步，并且会显示此类字段的错误消息。 要详细了解引用的XFA删除的影响和有关脏AF的信息，请参阅 [更新引用的XFA表单](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

要删除此类XFA表单，请更新自适应表单并删除与XFA字段的绑定。
