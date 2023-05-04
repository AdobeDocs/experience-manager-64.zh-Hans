---
title: 使用Apache Tika检测数字资产的MIME类型
description: 启用Apache Tika以帮助 [!DNL Experience Manager] 资产会在上传操作期间（而不是文件扩展名）从内容流中检测资产的MIME类型。
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---

# 使用Apache Tika检测数字资产的MIME类型 {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通常，Adobe Experience Manager Assets会检测您从其文件扩展名上传的资产的MIME类型。 如果您使用Apache Tika上传资产， [!DNL Experience Manager] 在上传操作期间，资产会从内容流中检测其MIME类型，而不是文件扩展名。

此功能默认处于禁用状态。 要启用该功能，请配置 **Day CQ DAM Mime类型** 服务。

>[!NOTE]
>
>使用Apache Tika库的MIME类型检测是一项资源密集型操作。

1. 转到 `https://[AEM_server]:[port]/system/console/configMgr` 打开Configuration Manager Web控制台。
1. 在服务列表中，找到 **[!UICONTROL Day CQ DAM Mime类型服务]** ，然后点按/单击 **[!UICONTROL 编辑]** 图标以在编辑模式下将其打开。

1. 选择 **[!UICONTROL 从内容中检测MIME]** 选项，以在忽略文件扩展名时启用解析已上传资产以确定其MIME类型。 默认情况下，此选项处于取消选中状态。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 
