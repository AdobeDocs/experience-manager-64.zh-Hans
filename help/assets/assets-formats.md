---
title: AEM Assets支持的文件格式
description: AEM Assets支持的文件格式和MIME类型列表以及每种格式支持的功能。
contentOwner: AG
feature: 资产管理，演绎版
role: 业务从业者，管理员
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 23%

---


# AEM Assets {#assets-supported-formats}中支持的文件格式

AEM Assets支持各种文件格式，并且每种功能都支持不同的MIME类型。

要将AEM Assets与其他符合标准的数字资产管理(DAM)解决方案和桌面软件集成，请使用Adobe的可扩展元数据平台(XMP)。

使用图例了解支持级别。

| 支持级别 | 描述 |
|:---:|---|
| ✓ | 支持 |
| * | 受支持，但需要附加功能 |
| - | 不适用 |

## 栅格图像格式{#supported-raster-image-formats}

资产管理功能支持的栅格图像格式如下：

| 格式 | 存储 | 元数据管理 | 元数据提取 | 缩略图生成 | 交互式编辑 | 元数据写回 | 分析 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD **‡** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**‡** 合并的图像是从PSD文件中提取的。它是由Adobe Photoshop生成并包含在PSD文件中的图像。 根据设置，合并的图像可能是实际图像，也可能不是实际图像。

Dynamic Media功能支持的栅格图像格式如下：

| 格式 | 上载<br>（输入格式） | 创建<br>图像<br>预设<br>（输出格式） | 预览<br> dynamic<br>再现 | 传送<br>动态<br>再现 | 下载<br> dynamic<br>再现 |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**‡** 合并的图像是从PSD文件中提取的。它是由Adobe Photoshop生成并包含在PSD文件中的图像。 根据设置，合并的图像可能是实际图像，也可能不是实际图像。

除上述信息外，请考虑以下事项：

* 对EPS文件的支持仅适用于栅格图像。 例如，默认不支持为 EPS 矢量图像生成缩略图。要添加支持，[配置ImageMagick](best-practices-for-imagemagick.md)。 要集成第三方工具以启用其他功能，请参阅[基于命令行的媒体处理程序](media-handlers.md#command-line-based-media-handler)。

* 将元数据写回添加到`NComm`处理函数时，它适用于PSB文件格式。

* 要使用Dynamic Media预览和生成EPS文件的动态演绎版，请参阅[Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 对于EPS文件，PostScript文档结构约定(PS-Adobe)3.0版或更高版本支持元数据写回。

## Dynamic Media {#unsupported-image-formats-dynamic-media}中不支持的栅格图像格式

以下列表描述了Dynamic Media中支持&#x200B;*不*&#x200B;的栅格图像文件格式的子类型。

另请参阅[检测Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html)不支持的文件格式。

* IDAT区块大小大于100 MB的PNG文件。
* PSB文件。
* 不支持具有CMYK、RGB、灰度或位图以外的色彩空间的PSD文件。 不支持DuoTone、Lab和索引色彩空间。
* 位深度大于16的PSD文件。
* 具有浮点数据的TIFF文件。
* 具有Lab色彩空间的TIFF文件。

## PDF栅格化器库{#supported-pdf-rasterizer-library}

Adobe PDF Rasterizer库可为大型和内容密集型Adobe Illustrator和PDF文件生成高质量的缩览图和预览。 Adobe建议对以下内容使用PDF栅格化器库：

* 需要大量处理的内容密集型AI/PDF文件。
* AI/PDF文件，默认情况下不生成缩略图。
* 具有Pantone Matching System(PMS)颜色的AI文件。

请参阅[使用PDF栅格器](aem-pdf-rasterizer.md)。

## 图像转码库{#supported-image-transcoding-library}

Adobe成像转码库是一款图像处理解决方案，可执行核心图像处理功能，如编码、转码、重新取样和调整大小。

成像转码库支持JPG/JPEG、PNG（8位和16位）、GIF、BMP、TIFF/压缩TIFF（32位TIFF文件和PTIFF文件除外）、ICO和ICN MIME类型。

请参阅[成像转码库](imaging-transcoding-library.md)。

## Camera Raw{#supported-camera-raw}

Adobe Camera Raw库使AEM Assets能够摄取原始图像。 请参阅[Camera Raw支持](camera-raw.md)。

## 文档格式{#supported-document-formats}

资产管理功能支持的文档格式如下：

| 格式 | 存储 | 元数据<br>管理 | 全文<br>提取 | 元数据<br>提取 | 缩览图生成<br> | 子资产<br>提取 | 元数据<br>写回 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODT | ✓ | ✓ | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  |
| RTF | ✓ | ✓ | ✓ |  |  |  |  |
| TXT | ✓ | ✓ | ✓ |  |  |  |  |
| XLS | ✓ | ✓ | ✓ |  |  |  |  |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |

Dynamic Media功能支持的文档格式如下：

| 格式 | 上载<br>（输入格式） | 创建<br>图像<br>预设<br>（输出格式） | 预览<br> dynamic<br>再现 | 传送<br>动态<br>再现 | 下载<br> dynamic<br>再现 |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

除了上述功能之外，还要考虑以下事项：

* 要使用Dynamic Media为PDF文件生成动态演绎版，请参阅[Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 要使用Dynamic Media预览AI文件并生成动态演绎版，请参阅[Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 要使用Dynamic Media为INDD文件生成动态演绎版，请参阅[InDesign(INDD)文件格式](../assets/managing-image-presets.md#indesign-indd-file-format)。

## 多媒体格式{#supported-multimedia-formats}

| 格式 | 存储 | 元数据管理 | 元数据提取 | 缩略图生成 | FFMPEG转码 |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | - | * |
| MIDI | ✓ | ✓ |  | - | * |
| 3GP | ✓ | ✓ |  | - | * |
| MP3 | ✓ | ✓ | ✓ | - | * |
| MPG | ✓ | ✓ |  | - | * |
| OGA | ✓ | ✓ |  | - | * |
| OGG | ✓ | ✓ |  | - | * |
| RA | ✓ | ✓ |  | - | * |
| WAV | ✓ | ✓ |  | - | * |
| WMA | ✓ | ✓ |  | - | * |
| DVI | ✓ | ✓ |  | * | * |
| FLV | ✓ | ✓ |  | * | * |
| M4V | ✓ | ✓ |  | * | * |
| MPEG | ✓ | ✓ |  | * | * |
| OGV | ✓ | ✓ |  | * | * |
| MOV | ✓ | ✓ |  | * | * |
| WMV | ✓ | ✓ |  | * | * |
| SWF | ✓ | ✓ |  |  |  |

## Dynamic Media转码{#supported-input-video-formats-for-dynamic-media-transcoding}的输入视频格式

| 视频文件扩展名 | 容器 | 推荐的视频编解码器 | 不支持的视频编解码器 |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC（所有配置文件） |  |
| MOV、QT | Apple QuickTime | H264/AVC、Apple ProRes422 &amp; HQ、Sony XDCAM、Sony DVCAM、HDV、Panasonic DVCPro、Apple DV (DV25)、Apple PhotoJPEG、Sorenson、Avid DNxHD、Avid AVR | Apple Intermediate、Apple Animation |
| FLV、F4V | Adobe Flash | H264/AVC、Flix VP6、H263、Sorenson | SWF（矢量动画文件） |
| WMV | Windows Media 9 | WMV3 (v9)、WMV2 (v8)、WMV1 (v7)、GoToMeeting（G2M2、G2M3、G2M4） | Microsoft Screen (MSS2)、Microsoft Photo Story (WVP2) |
| MPG、VOB、M2V、MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID、DIVX、HDV、MiniDV (DV25)、Techsmith Camtasia、Huffyuv、Fraps、Panasonic DVCPro | Indeo3 (IV30)、MJPEG、Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV、OGG | Ogg | Theora、VP3、Dirac |  |
| MXF | MXF | Sony XDCAM、MPEG-2、MPEG-4、Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D， RM | Red Raw Video | MJPEG 2000 |  |
| RAM、RM | RealVideo | 不支持 | Real G2 (RV20)、Real 8 (RV30)、Real 10 (RV40) |
| FLAC | Native Flac | 自由无损音频编解码器 |  |
| MJ2 | Motion JPEG2000 | Motion JPEG 2000编解码器 |  |

## 存档格式{#supported-archive-formats}

下表介绍了支持的存档格式和常见DAM工作流的适用性。

| 格式 | 存储 | 版本控制 | 工作流 | 发布 | 访问控制 | Dynamic Media 投放 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** 合并的图像是从PSD文件中提取的。它是由Adobe Photoshop生成并包含在PSD文件中的图像。 根据设置，合并的图像可能是实际图像，也可能不是实际图像。 使用`Deflate64`算法创建的ZIP存档在AEM中的支持有限。 不支持存档和取消存档操作。 但是，支持上传、浏览和下载等操作。

## 其他支持的格式{#other-supported-formats}

下表介绍了对几种其他文件格式的常见DAM工作流的适用性。

| 格式 | 存储 | 版本控制 | 工作流 | 发布 | 访问控制 | Dynamic Media 投放 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript(当配置有自己的投放域时) |  |  |  |  |  | ✓ |

**#** DAM中支持其他格式，用于存储、版本控制、ACL、工作流、发布和元数据管理。

## 支持的MIME类型{#supported-mime-types}

默认情况下，AEM会使用文件扩展名检测文件类型。 AEM可以从文件内容中检测到它。 对于后者，在AEM Web Console中的[!UICONTROL Day CQ DAM Mime类型服务]中选择[!UICONTROL 从内容]检测MIME选项。

在`/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`的CRXDE Lite中可以使用受支持MIME类型的列表。

| 文件扩展名 | MIME类型/Internet媒体类型 | 默认jobParam值 | 允许的jobParam值 |
|---|---|---|---|
| 图像 | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | 默认的jobParam适用于所有图像mime类型资产。<ul><li>[knockouBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdf选项](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| TTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| RTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [启用基于MIME类型的资产/Dynamic Media经典上传作业参数支持](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)。
>* [为上传作业参数支持配置基于MIME类型](config-dynamic.md)。

