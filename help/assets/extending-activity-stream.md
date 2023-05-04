---
title: 将资产与活动流集成
description: 描述的录制功能 [!DNL Experience Manager] 以及如何配置 [!DNL Experience Manager] 以记录特定事件。
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 2%

---

# 将资产与活动流集成 {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets用户可执行多项操作，例如创建、上传和删除资产。 可以记录这些操作，以便提供用户所执行操作的历史记录。 本节介绍 [!DNL Experience Manager] 以及如何配置 [!DNL Experience Manager] 以记录特定事件。

## 性能注意事项和默认行为 {#performance-considerations-and-default-behavior}

例如，此集成可能占用CPU和磁盘空间，而执行批量导入时则会占用这些空间。 因此， [!DNL Experience Manager] 默认情况下，资产与活动流的集成处于禁用状态。

## 支持的操作事件 {#supported-action-events}

可以将以下事件配置为记录：

* 已接受许可证（已接受）
* 已创建资产(ASSET_CREATED)
* 已移动资产(ASSET_MOVED)
* 已删除资产(ASSET_REMOVED)
* 许可证被拒绝（拒绝）
* 已下载资产（已下载）
* 资产版本控制（版本控制）
* 已恢复资产版本（已恢复）
* 更新了资产元数据(METADATA_UPDATED)
* 已发布到外部系统的资产(PUBLISHED_EXTERNAL)
* 资产的原始更新(ORIGINAL_UPDATED)
* 更新了资产演绎版(RENDITION_UPDATED)
* 已删除资产演绎版(RENDITION_REMOVED)
* 更新了子资产(SUBASSET_UPDATED)
* 已删除子资产(SUBASSET_REMOVED)

## 配置 [!DNL Assets] 事件记录 {#configuring-aem-assets-events-recording}

的 [Web控制台](/help/sites-deploying/configuring-osgi.md) 提供对 [!DNL Assets] 事件记录器调整。 配置 [!DNL Assets] 事件记录器，请按如下步骤继续：

1. 导航到 **[!UICONTROL Web控制台]**

1. 单击 **[!UICONTROL 配置]**.

1. 双击 **[!UICONTROL Day CQ DAM事件记录器]**.

1. 检查 **[!UICONTROL 启用此服务]**.

1. 检查 **[!UICONTROL 事件类型]** 您希望在用户活动流中记录。

1. 单击“**[!UICONTROL 保存]**”。

## 读取记录的事件 {#reading-recorded-events}

记录的事件将存储为活动。 您可以使用 [ActivityManager API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
