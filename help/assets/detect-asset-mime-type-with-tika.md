---
title: 使用Apache Tika检测数字资产的MIME类型
description: 启用Apache Tika可帮助AEM资产在上传操作（而非文件扩展名）期间从内容流检测资产的MIME类型。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# 使用Apache Tika检测数字资产的MIME类型 {#detecting-mime-type-of-assets-using-apache-tika}

通常，Adobe Experience Manager(AEM)资产会检测您从其文件扩展名上传的资产的MIME类型。 如果您使用Apache Tika上传资产，则AEM资产会在上传操作期间从内容流（而非文件扩展名）检测其MIME类型。

默认情况下，此功能处于禁用状态。 要启用该功能，请从配置 **管理器中配置Day CQ DAM Mime类型** 。

>[!NOTE]
>
>使用Apache Tika库的MIME类型检测是一项资源密集型操作。

1. 转到以 `https://[AEM_server]:[port]/system/console/configMgr` 打开Configuration Manager web控制台。
1. 从服务列表中，找到 **[!UICONTROL Day CQ DAM Mime类型服务]** ，然后点按／单击它旁边的编辑图 **** 标以在编辑模式下打开它。

1. 选择从 **[!UICONTROL 内容检测MIME选项]** ，以启用解析已上传资产以确定其MIME类型，同时忽略文件扩展名。 默认情况下，此选项处于未选中状态。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 
