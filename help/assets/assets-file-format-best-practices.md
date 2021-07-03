---
title: 资产文件格式最佳实践
description: 有关AEM Assets中文件支持的最佳实践。
contentOwner: AG
feature: 资产管理，开发人员工具
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# 资产文件格式最佳实践 {#assets-file-format-best-practices}

AEM Assets支持许多专有和第三方文件格式库，以满足用户的各种文件支持要求。 支持的Adobe库包括Adobe Camera Raw、Gibson、Adobe PDF Rasterizer和Adobe InDesign Server。 此外，AEM Assets还支持第三方库，包括ImageMagick、TwelveMones等。

有关支持的文件格式，请参阅[资产支持的格式](assets-formats.md)。

## Adobe Camera Raw库 {#adobe-camera-raw-library}

为获得最佳性能，Adobe建议使用Adobe Camera Raw库：

* 原始
* DNG

Adobe Camera Raw库支持将CMYK颜色配置文件作为输入。 但是，它以RGB色彩空间生成输出，并且仅支持JPEG格式的输出。 缩略图中不保留源文件色彩空间（例如CMYK）。

有关更多信息，请参阅AEM Assets中的[Camera Raw支持](camera-raw.md)。

## Adobe PDF光栅器库 {#adobe-pdf-rasterizer-library}

为获得最佳结果，Adobe建议对以下文件使用Adobe PDF光栅器库：

* 内容密集型的PDF文件
* 未开箱生成缩略图的AI文件
* 对于具有专色(PMS)颜色的AI文件

与开箱即用的光栅输出相比，使用PDF光栅化器生成的缩略图和预览的质量更高。 Adobe PDF光栅化器库不支持任何颜色空间转换。 无论源PDF文件的颜色空间如何，Adobe PDF光栅器仅生成RGB输出。

## Adobe InDesign服务器 {#adobe-indesign-cc-server}

Adobe建议您使用Adobe InDesign服务器提取特定于Adobe InDesign的呈现版本，如IDML和HTML。 有关更多信息，请参阅[将AEM资产添加为Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)中的引用。

## Dynamic Media  {#dynamic-media}

Dynamic Media通过其全球、可扩展且性能优化的网络，实时生成并交付多种丰富内容变体。 它提供交互式查看体验并简化数字营销活动管理流程。 有关启用Dynamic Media的详细信息，请参阅[配置Dynamic Media](config-dynamic.md)。

目前，Dynamic Media支持每个文件最多15 GB的内容。

## ImageMagick库 {#imagemagick-library}

Adobe建议在以下情况下使用ImageMagick库：

* 为EPS文件生成缩略图呈现
* 保留图像配置文件信息
* 保持透明度
* 处理PSD和PSB文件

要了解如何在AEM中设置ImageMagic库，请参阅[使用ImageMagick](media-handlers.md#an-example-using-imagemagick)。 有关最佳用法，请参阅[配置ImageMagick](best-practices-for-imagemagick.md)的最佳实践。

## 图像转码库 {#image-transcoding-library}

Adobe图像转码库是一款图像处理解决方案，可执行核心的图像处理功能，包括图像编码、转码、重新取样、调整大小等。

映像转码库支持以下MIME类型：

* JPG/JPEG
* PNG（8位和16位）
* GIF
* BMP
* TIFF/压缩TIFF（除32位Tiff和PTiff外）。
* ICO
* ICN

有关详细信息，请参阅[成像转码库](imaging-transcoding-library.md)。
