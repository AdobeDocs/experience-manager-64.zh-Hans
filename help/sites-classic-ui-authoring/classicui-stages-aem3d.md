---
title: 关于在 AEM 3D 中使用舞台
seo-title: 关于在 AEM 3D 中使用舞台
description: 舞台是轻量级 3D 场景文件，可为第三方渲染器提供基本的查看环境（灯光、背景、地面或其他固定几何图形）、可选的预定义相机和渲染设置。
seo-description: 舞台是轻量级 3D 场景文件，可为第三方渲染器提供基本的查看环境（灯光、背景、地面或其他固定几何图形）、可选的预定义相机和渲染设置。
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 78%

---


# 关于在 AEM 3D 中使用舞台{#about-the-use-of-stages-in-aem-d}

舞台是轻量级 3D 场景文件，可为第三方渲染器提供基本的查看环境（灯光、背景、地面或其他固定几何图形）、可选的预定义相机和渲染设置。

>[!NOTE]
>
>OBJ 3D 格式不支持灯光。因此，它不能用于向 AEM 3D 提供舞台。

舞台的文件格式决定了您可以对该舞台使用的渲染器。例如，如果Autodesk® Maya®用于高质量渲染，则舞台必须采用`.ma`或`.mb`格式。 如果您打算只使用默认的 Rapid Refine™ 渲染器，则任何支持的舞台文件格式均可接受。

在上传到AEM之前，AEM 3D中除输出图像类型和大小外的所有渲染设置都必须经过预配置并保存到舞台文件中。

