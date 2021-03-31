---
title: 使用Apache Tika检测MIME类型的数字资产
description: 启用Apache Tika以帮助AEM Assets在上传操作（而非文件扩展名）期间检测内容流中的MIME类型资产。
contentOwner: AG
feature: 元数据，开发人员工具，资产管理
role: 管理员，架构师
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 3%

---


# 使用Apache Tika检测数字资产{#detecting-mime-type-of-assets-using-apache-tika}的MIME类型

通常，Adobe Experience Manager(AEM)资产会检测您从其文件扩展名上传的资产的MIME类型。 如果您使用Apache Tika上传资产，AEM Assets会在上传操作（而非文件扩展名）期间从内容流中检测其MIME类型。

默认情况下，此功能处于禁用状态。 要启用该功能，请从Configuration Manager中配置&#x200B;**Day CQ DAM Mime类型**&#x200B;服务。

>[!NOTE]
>
>使用Apache Tika库的MIME类型检测是一项资源密集型操作。

1. 转到`https://[AEM_server]:[port]/system/console/configMgr`以打开Configuration Manager Web控制台。
1. 在服务列表中，找到&#x200B;**[!UICONTROL Day CQ DAM Mime类型服务]**&#x200B;并点按/单击其旁边的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标以在编辑模式下打开它。

1. 选择&#x200B;**[!UICONTROL 从内容]**&#x200B;检测MIME选项，以启用对已上传资产的分析，以在忽略文件扩展名时确定其MIME类型。 默认情况下，此选项处于未选中状态。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 
