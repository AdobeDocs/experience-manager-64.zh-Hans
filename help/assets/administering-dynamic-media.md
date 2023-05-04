---
title: 设置Dynamic Media
seo-title: Setting Up Dynamic Media
description: 要设置Dynamic Media，您需要配置Dynamic Media并管理图像预设和查看器预设
seo-description: To set up dynamic media, you need to configure dynamic media and manage image and viewer presets
uuid: bcd1f9ab-4201-4222-9e4a-ba82b3c7cd6c
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 36a4a4e7-8bb2-4853-b335-cf9148be410c
exl-id: dd43de7b-8556-4e3f-9d90-14f0f5bd13e7
feature: Configuration
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---

# 设置Dynamic Media {#setting-up-dynamic-media}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 通过按需提供丰富的可视推销和营销资产，以及根据Web、移动设备和社交网站的使用情况自动调整资产供应情况，帮助您管理资产。 Dynamic Media使用一组主控资产，通过其全球、可扩展、性能优化的网络，实时生成并交付多种不同的丰富内容。

>[!NOTE]
>
>本文档介绍了直接集成到AEM中的Dynamic Media功能。 如果您将Dynamic Media Classic集成到AEM中，请参阅 [Dynamic Media Classic集成文档](/help/sites-administering/scene7.md).
>
>请参阅 [双重使用方案](/help/sites-administering/scene7.md#dual-use-scenario) 有时，您可能希望将AEM与Dynamic Media Classic集成并使用Dynamic Media。

如果您管理的是Dynamic Media，请关注以下主题：

* [配置Dynamic Media-Scene7模式](config-dms7.md)  — 如果您是新的Dynamic Media客户，请使用此配置。
* [配置Dynamic Media — 混合模式](config-dynamic.md)  — 如果您是现有的Dynamic Media客户，请使用此配置来升级AEM。
* [管理图像预设](managing-image-presets.md)
* [管理查看器预设](managing-viewer-presets.md)
* [Dynamic Media - Scene7模式故障诊断](troubleshoot-dms7.md)

另请参阅以下主题：

* [视频编码和视频配置文件](video-profiles.md)
* [图像配置文件](image-profiles.md)

>[!NOTE]
>
>**如果您正在升级：**
>
>* 启动并运行AEM后，您上传的任何资产都会自动启用Dynamic Media（除非系统管理员明确禁用了）。 如果您使用的是AEM的升级实例，并且是Dynamic Media的新实例，则可能需要重新处理资产以启用Dynamic Media。

