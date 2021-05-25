---
title: 启用重复项检测功能
description: 了解如何在AEM中启用重复资产的检测。
contentOwner: AG
feature: 资产管理，资产报表
role: Business Practitioner,Administrator
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 3%

---

# 启用重复项检测功能 {#enabling-duplicate-detection}

如果您尝试上传Adobe Experience Manager(AEM)资产中存在的资产，重复项检测功能会将其标识为重复项。 默认情况下，重复项检测处于禁用状态。 要启用该功能，请执行以下步骤：

1. 打开&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台配置]**&#x200B;页面（位于`https://[server]:[port]/system/console/configMgr`）。
1. 编辑Servlet **[!UICONTROL Day CQ DAM创建资产]**&#x200B;的配置。
1. 选择&#x200B;**[!UICONTROL 检测重复项]**&#x200B;选项，然后单击/点按&#x200B;**[!UICONTROL 保存]**。

   ![在Servlet中选择检测重复项选项](assets/chlimage_1-377.png)

检测重复项功能现已在AEM Assets中启用。 当用户尝试上传AEM中存在的资产时，系统会检查是否存在冲突并指示该冲突。 资产使用存储在`jcr:content/metadata/dam:sha1`的SHA-1哈希进行标识，这意味着无论文件名如何，都会检测到重复的资产。

>[!MORELIKETHIS]
>
>* [在现有存储库中复制资产（社区成员提供的教程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

