---
title: 使用 Dynamic Media
seo-title: Working with Dynamic Media
description: 了解如何使用Dynamic Media交付资产以在Web、移动设备和社交网站上使用。
seo-description: Learn how to use Dynamic Media to deliver assets for consumption on web, mobile, and social sites.
uuid: 4dc0f436-d20e-4e8b-aeff-5515380fa44d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: a8063d43-923a-42ac-9a16-0c7fadd8f73f
exl-id: f8a3936e-82b5-46c7-9614-b97162e27d6a
feature: Asset Management,Renditions
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 7%

---

# 使用 Dynamic Media {#working-with-dynamic-media}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 有助于按需提供丰富的可视推销和营销资产，并可根据Web、移动设备和社交网站的使用情况自动缩放资产。 Dynamic Media使用一组主控资产，通过其全球、可扩展、性能优化的网络，实时生成并交付多种不同的丰富内容。

Dynamic Media提供交互式查看体验，包括缩放、360度旋转和视频。 Dynamic Media以独特的方式整合了Adobe Experience Manager数字资产管理（资产）解决方案的工作流程，以简化和简化数字营销活动管理流程。

<!-- DEAD ARTICLE >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## 使用Dynamic Media可以做什么 {#what-you-can-do-with-dynamic-media}

Dynamic Media允许您在发布资产之前对其进行管理。 在中详细介绍了如何一般处理资产 [使用数字资产](managing-assets-touch-ui.md). 一般主题包括上传、下载、编辑和发布资产；查看和编辑属性，以及搜索资产。

仅限Dynamic Media的功能包括：

* [传送横幅](carousel-banners.md)
* [图像集](image-sets.md)
* [交互式图像](interactive-images.md)
* [交互式视频](interactive-videos.md)
* [混合媒体集](mixed-media-sets.md)
* [全景图像](panoramic-images.md)

* [旋转集](spin-sets.md)
* [视频](video.md)
* [传送Dynamic Media资产](delivering-dynamic-media-assets.md)
* [管理资产](managing-assets.md)
* [使用概览创建自定义弹出窗口](custom-pop-ups.md)

另请参阅 [设置Dynamic Media](administering-dynamic-media.md).

>[!NOTE]
>
>要了解使用Dynamic Media与将Dynamic Media Classic与AEM集成之间的差异，请参阅 [Dynamic Media Classic集成与Dynamic Media](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media).

## Dynamic Media启用与Dynamic Media禁用 {#dynamic-media-on-versus-dynamic-media-off}

您可以通过以下特征判断Dynamic Media是否已启用（打开）：

* 下载或预览资产时，可以使用动态演绎版。
* 可以使用图像集、旋转集、混合媒体集。
* 将创建PTIFF演绎版。

单击图像资产时，资产的视图与Dynamic Media不同 [已启用](config-dynamic.md#enabling-dynamic-media). Dynamic Media使用按需HTML5查看器。

### 动态演绎版 {#dynamic-renditions}

动态演绎版，如图像预设和查看器预设(在 **[!UICONTROL 动态]**)在启用Dynamic Media时可用。

![chlimage_1-358](assets/chlimage_1-358.png)

### 图像集、旋转集、混合媒体集 {#image-sets-spins-sets-mixed-media-sets}

如果启用了Dynamic Media，则图像集、旋转集和混合媒体集将可用。

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF演绎版 {#ptiff-renditions}

启用Dynamic Media的资产包括 `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### 资产视图更改 {#asset-views-change}

启用Dynamic Media后，您可以通过单击 `+` 和 `-` 按钮。 您还可以单击/点按以放大特定区域。 还原后，您可以转到原始版本，并通过单击对角箭头来使图像全屏显示。 Dynamic Media启用如下所示：

![chlimage_1-361](assets/chlimage_1-361.png)

禁用Dynamic Media后，您可以放大和缩小并还原到原始大小：

![chlimage_1-362](assets/chlimage_1-362.png)
