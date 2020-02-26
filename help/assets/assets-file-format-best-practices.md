---
title: 资产文件格式最佳实践
description: AEM资产中文件支持的最佳实践。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Assets file format best practices {#assets-file-format-best-practices}

AEM Assets支持许多专有和第三方文件格式库，以满足用户的各种文件支持要求。 支持的Adobe库包括Adobe Camera Raw、Gibson、Adobe PDF Rasterizer和Adobe inDesign Server。 此外，AEM Assets还支持第三方库，包括ImageMagick、TwelveMoxes等。

For the supported file formats, see [Assets supported formats](assets-formats.md).

## Adobe Camera raw库 {#adobe-camera-raw-library}

为获得最佳性能，Adobe建议将Adobe Camera raw库用于：

* RAW
* DNG

Adobe Camera raw库支持CMYK颜色配置文件作为输入。 但是，它仅支持JPEG格式的输出，并以RGB色彩空间生成输出。 它不会在缩略图中保留源文件色彩空间（例如CMYK）。

有关详细信息，请参 [阅AEM资产中的Camera Raw](camera-raw.md) 支持。

## Adobe PDF栅格化器库 {#adobe-pdf-rasterizer-library}

为获得最佳效果，Adobe建议对以下文件使用Adobe PDF栅格化器库：

* 内容密集型的PDF文件
* 未开箱生成缩览图的AI文件
* 对于具有专色(PMS)的AI文件

与开箱即用的栅格输出相比，使用PDF栅格化器生成的缩览图和预览的质量更高。 Adobe PDF Rasterizer库不支持任何色彩空间转换。 无论源PDF文件的色彩空间如何，Adobe PDF Rasterizer都只生成RGB输出。

## Adobe inDesign Server {#adobe-indesign-cc-server}

Adobe建议您使用Adobe inDesign服务器提取Adobe inDesign特定的再现，如IDML和HTML。 有关详细信息，请参 [阅在Adobe inDesign中将AEM资产添加为引用](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)。

## Dynamic Media  {#dynamic-media}

Dynamic media通过其全局、可扩展且性能优化的网络实时生成和交付多种形式的丰富内容。 它提供交互式查看体验并简化数字营销活动管理流程。 有关启用Dynamic Media的详细信息，请参 [阅配置Dynamic Media](config-dynamic.md)。

目前，Dynamic media可支持每个文件最多20 GB内容的视频。

## ImageMagick库 {#imagemagick-library}

Adobe建议在以下情况下使用ImageMagick库：

* 为EPS文件生成缩览图再现
* 保留图像配置文件信息
* 保留透明度
* 处理PSD和PSB文件

要了解如何在AEM中设置ImageMagic库，请参阅使 [用ImageMagick](media-handlers.md#an-example-using-imagemagick)。 有关最佳用法，请参 [阅配置ImageMagick的最佳实践](best-practices-for-imagemagick.md)。

## 图像转码库 {#image-transcoding-library}

Adobe Imaging Tronding library是一款图像处理解决方案，可执行核心图像处理功能，包括图像编码、转码、重新取样和调整大小等。

成像转码库支持以下MIME类型：

* JPG/JPEG
* PNG（8位和16位）
* GIF
* BMP
* TIFF/压缩TIFF（除32位Tiff和PTiff外）。
* ICO
* ICN

有关详细信息，请参阅 [成像转码库](imaging-transcoding-library.md)。
