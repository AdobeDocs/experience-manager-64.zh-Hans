---
title: 关于在 AEM 3D 中使用舞台
seo-title: 关于在 AEM 3D 中使用舞台
description: 舞台是光权重3D场景文件，它们提供基本的查看环境。
seo-description: 舞台是光权重3D场景文件，它们提供基本的查看环境。
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 56%

---


# 关于在 AEM 3D 中使用舞台 {#about-the-use-of-stages-in-aem-d}

舞台是轻量级 3D 场景文件，可为第三方渲染器提供基本的查看环境（灯光、背景、地面或其他固定几何图形）、可选的预定义相机和渲染设置。

>[!NOTE]
>
>The **[!UICONTROL OBJ 3D]** format does not support lights. 因此，它不能用于向 AEM 3D 提供舞台。

舞台的文件格式决定了您可以对该舞台使用的渲染器。For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. 如果您打算只使用默认的 Rapid Refine™ 渲染器，则任何支持的舞台文件格式均可接受。

在上传到AEM之前，AEM 3D中除输出图像类型和大小外的所有渲染设置都必须经过预配置并保存到舞台文件中。