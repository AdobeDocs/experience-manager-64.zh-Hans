---
title: 使用Apache Tika检测数字资产的MIME类型
description: 启用Apache Tika以帮助AEM Assets在上传操作（而非文件扩展名）期间从内容流检测MIME类型的资产。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 3%

---


# 使用Apache Tika检测数字资产{#detecting-mime-type-of-assets-using-apache-tika}的MIME类型

通常，Adobe Experience Manager(AEM)资产会检测您从其文件扩展名上传的资产的MIME类型。 如果您使用Apache Tika上传资产，AEM Assets会在上传操作（而非文件扩展名）期间从内容流检测其MIME类型。

此功能默认为禁用状态。 要启用该功能，请从Configuration Manager中配置&#x200B;**Day CQ DAM Mime类型**&#x200B;服务。

>[!NOTE]
>
>使用Apache Tika库的MIME类型检测是一项资源密集型操作。

1. 转到`https://[AEM_server]:[port]/system/console/configMgr`以打开Configuration Manager Web控制台。
1. 在服务列表中，找到&#x200B;**[!UICONTROL Day CQ DAM MIME类型服务]**，然后点按／单击其旁边的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标，以在编辑模式下将其打开。

1. 选择&#x200B;**[!UICONTROL 从内容]**&#x200B;检测MIME选项，以启用解析已上传的资产以确定其MIME类型，同时忽略文件扩展名。 默认情况下，此选项处于未选中状态。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 
