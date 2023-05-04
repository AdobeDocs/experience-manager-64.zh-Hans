---
title: 配置自适应表单缓存
seo-title: Configure adaptive forms cache
description: 自适应表单缓存专门用于自适应表单和文档。 它缓存自适应表单和自适应文档，以缩短在客户端上呈现自适应表单或文档所需的时间。
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 2%

---

# 配置自适应表单缓存 {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

缓存是一种缩短数据访问时间、减少延迟和提高输入/输出(I/O)速度的机制。 自适应表单缓存仅存储自适应表单的HTML内容和JSON结构，而不保存任何预填充数据。 这有助于减少在客户端上渲染自适应表单或文档所需的时间。 它专为自适应表单而设计，并且还支持自适应文档。

>[!NOTE]
>
>使用自适应表单缓存时，使用AEM Dispatcher缓存自适应表单或文档的客户端库（CSS和JavaScript）。

>[!NOTE]
>
>在开发自定义组件时，在用于开发的服务器上，保持禁用自适应表单缓存。

## 配置缓存 {#configure-the-cache}

执行以下步骤以配置自适应表单缓存：

1. 转到AEM Web控制台配置管理器(位于 `https://[server]:[port]/system/console/configMgr`.
1. 单击 **自适应表单与交互式通信Web信道配置** 以编辑其配置值。
1. 在“编辑配置值”对话框中，指定AEM Forms服务器实例可以缓存的表单或文档的最大数量(位于 **自适应Forms数** 字段。 默认值为 100。

   >[!NOTE]
   >
   >要禁用缓存，请将“自适应Forms数”字段中的值设置为 **0**. 当禁用或更改缓存配置时，将重置缓存，并从缓存中删除所有表单和文档。

   ![自适应表单HTML缓存的配置对话框](assets/cache-configuration-edit.png)

1. 单击 **保存** 以保存配置。
