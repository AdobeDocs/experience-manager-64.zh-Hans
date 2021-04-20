---
title: 资源文件格式最佳实践
description: AEM Assets中文件支持的最佳实践。
contentOwner: AG
feature: Asset Management,Developer Tools
role: Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---


# 资产文件格式最佳实践{#assets-file-format-best-practices}

AEM Assets支持许多专有和第三方文件格式库，以满足用户的各种文件支持需求。 支持的Adobe库包括Adobe Camera Raw、Gibson、Adobe PDF Rasterizer和Adobe InDesign Server。 此外，AEM Assets还支持第三方库，包括ImageMagick、TwelveMoxes等。

有关支持的文件格式，请参阅[资产支持的格式](assets-formats.md)。

## Adobe Camera Raw库{#adobe-camera-raw-library}

为获得最佳性能，Adobe建议使用Adobe Camera Raw库：

* RAW
* DNG

Adobe Camera Raw库支持CMYK颜色用户档案作为输入。 但是，它以RGB色彩空间生成输出，并仅支持JPEG格式的输出。 它不会在缩览图中保留源文件色彩空间（例如CMYK）。

有关详细信息，请参阅AEM Assets中的[Camera Raw支持](camera-raw.md)。

## Adobe PDF光栅器库{#adobe-pdf-rasterizer-library}

为获得最佳效果，Adobe建议对以下文件使用Adobe PDF栅格化库：

* 内容密集型PDF文件
* 未开箱生成缩览图的AI文件
* 对于具有专色(PMS)颜色的AI文件

与开箱即用的栅格输出相比，使用PDF栅格化工具生成的缩览图和预览的质量更高。 Adobe PDF栅格化器库不支持任何色彩空间转换。 无论源PDF文件的色彩空间如何，Adobe PDF栅格化器仅生成RGB输出。

## Adobe InDesign server {#adobe-indesign-cc-server}

Adobe建议您使用Adobe InDesign服务器提取Adobe InDesign特定的再现，如IDML和HTML。 有关详细信息，请参阅[在Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)中将AEM资产添加为引用。

## Dynamic Media  {#dynamic-media}

Dynamic Media通过其全球、可扩展且性能优化的网络实时生成和交付多种不同的丰富内容。 它提供交互式观看体验并简化数字活动管理流程。 有关启用Dynamic Media的详细信息，请参阅[配置Dynamic Media](config-dynamic.md)。

目前，Dynamic Media支持每个文件最多15 GB的内容。

## ImageMagick库{#imagemagick-library}

Adobe建议在以下情况下使用ImageMagick库：

* 为EPS文件生成缩览图再现
* 保留图像用户档案信息
* 保留透明度
* 处理PSD和PSB文件

要了解如何在AEM中设置ImageMagic库，请参阅[使用ImageMagick](media-handlers.md#an-example-using-imagemagick)。 有关最佳用法，请参阅[配置ImageMagick](best-practices-for-imagemagick.md)的最佳实践。

## 图像转码库{#image-transcoding-library}

Adobe图像转码库是一款图像处理解决方案，可执行核心图像处理功能，包括图像编码、转码、重新取样和调整大小等。

映像转码库支持以下MIME类型：

* JPG/JPEG
* PNG（8位和16位）
* GIF
* BMP
* TIFF/压缩TIFF（除32位Tiff和PTiff外）。
* ICO
* ICN

有关详细信息，请参阅[成像转码库](imaging-transcoding-library.md)。
