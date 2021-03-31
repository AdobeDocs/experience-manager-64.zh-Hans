---
title: 启用重复项检测功能
description: 了解如何在AEM中启用重复资源检测。
contentOwner: AG
feature: 资产管理，资产报表
role: 业务从业者，管理员
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 3%

---


# 启用重复项检测功能 {#enabling-duplicate-detection}

如果您尝试上传Adobe Experience Manager(AEM)资产中存在的资产，重复检测功能会将其标识为重复。 重复检测默认为禁用。 要启用该功能，请执行以下步骤：

1. 打开&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台配置]**&#x200B;页，地址为`https://[server]:[port]/system/console/configMgr`。
1. 编辑servlet **[!UICONTROL Day CQ DAM创建资产]**&#x200B;的配置。
1. 选择&#x200B;**[!UICONTROL 检测重复]**&#x200B;选项，然后单击/点按&#x200B;**[!UICONTROL 保存]**。

   ![在servlet中选择检测重复选项](assets/chlimage_1-377.png)

检测重复功能现在已在AEM Assets中启用。 当用户尝试上传AEM中存在的资产时，系统会检查冲突并指示它。 资产使用存储在`jcr:content/metadata/dam:sha1`的SHA-1哈希进行标识，这意味着无论文件名如何，都会检测到重复资产。

>[!MORELIKETHIS]
>
>* [重复现有存储库中的资产（来自社区成员的教程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

