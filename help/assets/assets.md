---
title: 简介 [!DNL Adobe Experience Manager Assets]
description: 了解数字资产管理、其用例和 [!DNL Adobe Experience Manager Asset] 服务。
contentOwner: AG
feature: Asset Management
role: Leader,Architect,User
exl-id: 9292871d-3b10-49f8-ac1a-4770b4e44048
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# 关于 [!DNL Adobe Experience Manager Assets] 作为DAM解决方案 {#about-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[!DNL Assets] 是数字资产管理(DAM)工具，是 [!DNL Experience Manager] 平台，使您的企业能够管理和分发数字资产。 组织内的用户可以管理、存储和访问多种类型的数字资产，如图像、视频、文档、音频剪辑、3D文件和富媒体，以在Web上使用、在打印中使用和用于数字分发。

## 什么是数字资产管理？ {#what-is-digital-asset-management}

[!DNL Assets] 在企业范围内共享和分发组织的关键数字资产。 组织内的用户可以通过Web界面（或CIFS或WebDAV文件夹）存储、管理和访问数字资产，如图像、图形、音频、视频和文档。

[!DNL Assets] 能力 [!DNL Experience Manager] 允许您执行以下操作：

* 以各种文件格式添加和共享图像、文档、音频文件和视频文件。
* 通过按标记、灯箱或星形（您的收藏夹）对资产进行分组来管理资产。 向资产中添加注释。
* 通过搜索文件名、文档全文以及搜索日期、文档类型和标记来查找资产。
* 添加或编辑资产的元数据信息。 元数据会与相应的资产一起自动进行版本控制。 您可以导入或导出资产元数据。
* 执行图像编辑功能，如缩放和添加图像过滤器。 使用WebDAV或CIFS文件夹同时导入和导出多个数字资产。
* 使用工作流和通知，可联合处理和下载任何资产集，并管理资产的访问权限。

### [!DNL Experience Manager Assets] 与 [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] 完全集成 [!DNL Sites] 和可无缝地用于所有用例。 例如，在创作网页时， [!DNL Sites] 作者可以通过内容查找器查找和使用数字资产。 的用户界面 [!DNL Assets] 与 [!DNL Sites]. 请参阅 [站点概述](/help/sites-authoring/qg-page-authoring.md) 以了解完整详细信息。

<!-- TBD: Update image for branding 

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

Assets managed within [!DNL Experience Manager] DAM can then be accessed via the content finder of WCM:

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png) -->

### 数字资产管理与图像组件 {#digital-asset-management-versus-image-component}

在确定是将图像放入DAM存储库还是使用图像组件时，请考虑图像生命周期：

* 如果图像的生命周期与页面相同，请使用图像组件。
* 如果图像具有单独的生命周期，例如，如果您使用图像两次或在WCM之外使用图像，则使用 [!DNL Assets].

## 什么是数字资产？ {#what-are-digital-assets}

资产是指数字文档、图像、视频或音频（或其中任一部分），它们可以具有多个演绎版，并且可以具有子资产（例如，photoshop文件中的图层、PowerPoint文件中的幻灯片、PDF中的页面、ZIP中的文件）。

资产本质上是一个二进制文件、元数据、演绎版以及子资产。 请参阅 [DAM性能指南](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html) 以了解详细信息。

>[!CAUTION]
>
>上传和/或编辑大量资产（尤其是图像）可能会影响您的 [!DNL Experience Manager] 部署。

### [!DNL Experience Manager Assets] 术语 {#aem-assets-terminology}

在中使用数字资产时 [!DNL Experience Manager]，您需要了解以下术语：

* **收藏集**:资产集合，基于物理位置（文件夹）、常用属性（保存的搜索文件夹）或用户选择（灯箱文件夹）。

* **元数据** [!DNL Assets] 有元数据；例如，作者、到期日期、DRM信息(Digital Rights Management)等。 元数据受访问控制。 [!DNL Assets] 支持以下各种现成的通用元数据架构：

   * 都柏林核心：包括作者、描述、日期、主题等。
   * IPTC:包括事件、模型、位置等。
   * WCM:包括页面属性， [!UICONTROL 开始时间] 和 [!UICONTROL 关闭时间]，等等。

* **标记**: [!DNL Assets] 标记和分类。 请参阅 [组织资产](/help/assets/organize-assets.md).

* **演绎版**:演绎版是资产的二进制表示形式。 [!DNL Assets] 始终具有主要表示形式 — 已上传文件的表示形式。 这些用户档案可以包含已创建的任意数量的其他表示形式，例如通过自定义工作流步骤或在上传资产时创建的表示形式。 演绎版可能具有不同的大小、不同的分辨率、添加的水印或某些其他更改的特性。

* **版本**:版本控制可创建数字资产在特定时间点的快照。 您可以将资产恢复到之前的版本。 请参阅 [版本控制 [!DNL Assets]](managing-assets-touch-ui.md#asset-versioning).

* **子资产**:子资产是构成资产的资产，例如， [!DNL Adobe Photoshop] 文件或页面PDF。 在 [!DNL Assets]，您可以像管理资产一样管理子资产。

### 如何处理数字资产 {#how-to-work-with-assets}

您可以对资产或收藏集执行操作。 操作可以创建或修改资产、收藏集和演绎版。 您对资产执行的许多基本操作（上传、删除、更新、保存子资产）都会触发预配置的工作流。 这些功能会自动打开 [!DNL Assets] 并详细描述 [!DNL Assets] 媒体处理程序。

您可以使用这些预配置工作流执行的任务：

* 在存储库中保存或删除资产。
* 提取并保存资产的元数据；单个元数据项将另存为XMP。
* 生成资产的演绎版和缩略图；包括根据需要自动调整大小和裁剪。
* 在必要时对资产进行转码。 例如，针对移动设备和Web使用的视频以每秒24帧的速度进行转码，下载每秒30帧的视频。 对于移动设备和Web使用的音频采用128 Kbps的转码，对于下载的音频采用192 Kbps的转码。

当然，您也可以手动应用工作流。 请参阅 [资产媒体处理程序](media-handlers.md)，以查看默认工作流的列表。

## [!DNL Experience Manager Assets] 和 [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

请参阅 [资产和Media Library](medialibrary.md) 以了解差异。

>[!MORELIKETHIS]
>
>* [视频简介 — Experience Manager Assets as a modern DAM](https://www.youtube.com/watch?v=PBwQqZgC-yo)

