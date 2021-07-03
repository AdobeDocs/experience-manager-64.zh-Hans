---
title: 使用Apache Tika检测数字资产的MIME类型
description: 启用Apache Tika以帮助AEM Assets在上传操作期间（而不是文件扩展名）从内容流中检测MIME类型的资产。
contentOwner: AG
feature: 元数据，开发人员工具，资产管理
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 3%

---

# 使用Apache Tika检测数字资产的MIME类型 {#detecting-mime-type-of-assets-using-apache-tika}

通常，Adobe Experience Manager(AEM)Assets会检测您从其文件扩展名上传的资产的MIME类型。 如果您使用Apache Tika上传资产，则在上传操作期间，AEM Assets会从内容流中检测其MIME类型，而不是文件扩展名。

此功能默认处于禁用状态。 要启用该功能，请从Configuration Manager中配置&#x200B;**Day CQ DAM Mime Type**&#x200B;服务。

>[!NOTE]
>
>使用Apache Tika库的MIME类型检测是一项资源密集型操作。

1. 转到`https://[AEM_server]:[port]/system/console/configMgr`以打开Configuration Manager Web控制台。
1. 在服务列表中，找到&#x200B;**[!UICONTROL Day CQ DAM Mime类型服务]**，然后点按/单击服务旁边的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标，以在编辑模式下将其打开。

1. 选择&#x200B;**[!UICONTROL 从内容中检测MIME]**&#x200B;选项，以启用解析已上传资产以确定其MIME类型，同时忽略文件扩展名。 默认情况下，此选项处于取消选中状态。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 
