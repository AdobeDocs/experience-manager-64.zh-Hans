---
title: 配置资产上传限制
description: 了解如何配置Adobe Experience Manager(AEM)Assets以限制用户可上传的资产（文件）类型。
contentOwner: AG
feature: 上传，资产摄取，资产管理
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 29%

---

# 配置资产上传限制 {#configuring-asset-upload-restrictions}

您可以配置Adobe Experience Manager(AEM)资产，以限制用户可以上传的资产（文件）类型。 此功能可帮助您消除用户以不需要的格式上传资产或上传任何恶意文件的可能性。 `Day CQ DAM Asset Upload Restriction`服务允许您控制用户可上传的文件类型。 默认情况下，AEM Assets允许用户上传所有MIME类型的资产。 但是，您可以配置该服务，以限制用户仅上传特定MIME类型的文件。

1. 要打开Configuration Manager Web控制台，请访问`https://[AEM_server]:[port]/system/console/configMgr`。
1. 在编辑模式下打开&#x200B;**[!UICONTROL Day CQ DAM资产上传限制]**&#x200B;服务。 默认情况下，选中&#x200B;**允许所有MIME**&#x200B;选项，该选项允许用户上传所有MIME类型的文件。

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. 要限制用户仅上传某些MIME类型的文件，请取消选择 **[!UICONTROL llow all MIME]** 选项，并使用正则表达式在允许的资产MIME（正则表达式）字 **[!UICONTROL 段中指定允许的MIME类型]** 。

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. 单击／点按 **[!UICONTROL 保存]** ，以保存更改。 如果为允许的MIME类型指定MIME字符串，则对于MIME类型与这些字段中配置的MIME字符串不匹配的任何资产，上传操作都将失败。
