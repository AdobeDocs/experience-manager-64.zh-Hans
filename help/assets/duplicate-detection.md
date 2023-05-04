---
title: 启用重复项检测
description: 了解如何在AEM中启用重复资产的检测。
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 2%

---

# 启用重复项检测 {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如果您尝试上传Adobe Experience Manager Assets中存在的资产，重复项检测功能会将其标识为重复项。 默认情况下，重复项检测处于禁用状态。 要启用该功能，请执行以下步骤：

1. 打开 **[!UICONTROL Adobe Experience Manager Web控制台配置]** 页面 `https://[server]:[port]/system/console/configMgr`.
1. 编辑Servlet的配置 **[!UICONTROL Day CQ DAM创建资产]**.
1. 选择 **[!UICONTROL 检测重复项]** 选项，然后单击/点按 **[!UICONTROL 保存]**.

   ![在Servlet中选择检测重复项选项](assets/chlimage_1-377.png)

检测重复项功能现已在 [!DNL Experience Manager] 资产。 当用户尝试上传AEM中存在的资产时，系统会检查是否存在冲突并指示该冲突。 资产使用存储在 `jcr:content/metadata/dam:sha1`，这表示无论文件名如何，都会检测重复的资产。

>[!MORELIKETHIS]
>
>* [在现有存储库中复制资产（社区成员提供的教程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

