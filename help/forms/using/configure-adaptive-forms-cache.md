---
title: 配置自适应表单缓存
seo-title: 配置自适应表单缓存
description: '自适应表单缓存专门设计用于自适应表单和文档。 它缓存自适应表单和自适应文档，以减少在客户端上呈现自适应表单或文档所需的时间。 '
seo-description: '自适应表单缓存专门设计用于自适应表单和文档。 它缓存自适应表单和自适应文档，以减少在客户端上呈现自适应表单或文档所需的时间。 '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---


# 配置自适应表单缓存 {#configure-adaptive-forms-cache}

缓存是一种缩短数据访问时间、减少延迟和提高输入／输出(I/O)速度的机制。 自适应表单缓存仅存储自适应表单的HTML内容和JSON结构，而不保存任何预填数据。 它有助于缩短在客户端上呈现自适应表单或文档所需的时间。 它专门为自适应表单设计，还支持自适应文档。

>[!NOTE]
>
>使用自适应表单缓存时，请使用AEM Dispatcher缓存自适应表单或文档的客户端库（CSS和JavaScript）。

>[!NOTE]
>
>在开发自定义组件时，在用于开发的服务器上保持禁用自适应表单缓存。

## 配置缓存 {#configure-the-cache}

请执行以下步骤以配置自适应表单缓存：

1. 请转至AEM Web控制台配置管理器(位 `https://[server]:[port]/system/console/configMgr`于)。
1. 单击 **自适应表单和交互式通信Web渠道配置** ，以编辑其配置值。
1. 在“编辑配置值”对话框中，在“Number of Adaptive Bidow”(自适应Forms)字段中指定AEM Forms服务器实例可缓存的最 **大表单或文档** 。 默认值为 100。

   >[!NOTE]
   >
   >要禁用缓存，请将“Number of Adaptive Genative”(自适应Forms)字段中的值设 **置为0**。 在禁用或更改缓存配置时，将重置缓存并从缓存中删除所有表单和文档。

   ![自适应表单HTML缓存的配置对话框](assets/cache-configuration-edit.png)

1. Click **Save** to save the configuration.

