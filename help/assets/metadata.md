---
title: 在 [!DNL Adobe Experience Manager].
description: 了解元数据的类型以及如何 [!DNL Adobe Experience Manager Assets] 可帮助管理资产的元数据，以便更轻松地分类和组织资产。 [!DNL Experience Manager] 可以根据资产的元数据自动组织和处理资产。
contentOwner: AG
feature: Tagging, Metadata
role: Architect, Leader
exl-id: 05bbf89a-4cf5-49bb-aea8-a585c641eda2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1446'
ht-degree: 5%

---

# 管理数字资产的元数据 {#managing-metadata-for-digital-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] 保留每个资产的元数据。 它允许更轻松地对资产进行分类和组织，并帮助正在查找特定资产的用户。 能够从上传到的文件中提取元数据 [!DNL Experience Manager Assets]，元数据管理与创意工作流集成。 通过使用资产保留和管理元数据的功能，您可以根据资产的元数据自动组织和处理资产。

* [XMP 元数据](xmp.md).
* [如何编辑或添加元数据](meta-edit.md).
* [元数据架构引用](meta-ref.md).

## 为什么我们需要元数据 {#why-we-need-metadata}

元数据是指有关数据的数据。 在这方面，数据是指您的数字资产，如图像。 元数据对于高效的资源管理非常关键。

元数据是资产可用的所有数据的集合，但不一定包含在该图像中。 元数据的一些示例包括：

* 资产的名称。
* 上次修改的时间和日期。
* 资产存储在存储库中时的大小。
* 其所包含文件夹的名称。
* 相关资产或已应用的标记。

以上是基本的元数据属性， [!DNL Experience Manager] 可以管理资产，以便用户查看所有资产。 例如，在尝试发现最近添加的资产时，按上次修改日期对资产进行排序非常有用。

您可以向数字资产中添加更多高级数据，例如：

* 资产类型（是图像、视频、音频剪辑还是文档？）。
* 资产的所有者。
* 资产的标题。
* 资产的描述。
* 分配给资产的标记。

更多元数据可帮助您进一步对资产进行分类，并且随着数字信息量的增加，该元数据会非常有用。 可以仅根据文件名管理几百个文件。 但是，这种方法不具备扩展性。当相关人员数量和管理资产数量增加时，这个数字就不够了。

随着元数据的增加，数字资源的价值会随之增长，因为资源会变得：

* 更易于访问 - 系统和用户可以轻松地找到它。
* 更易于管理 - 您可以轻松地找到具有一组相同属性的资源并对其应用更改。
* 完整 - 元数据越多，资源就能携带更多信息和具体情境。

出于这些原因， [!DNL Assets] 为您提供了为数字资产创建、管理和交换元数据的正确方法。

## 元数据类型 {#types-of-metadata}

两种基本类型的元数据是技术元数据和描述性元数据。

技术元数据对于处理数字资产的软件应用程序非常有用，不应手动维护。 [!DNL Experience Manager Assets] 而其他软件会自动确定技术元数据，在修改资产时，元数据可能会发生更改。 资产的可用技术元数据在很大程度上取决于资产的文件类型。 技术元数据的一些示例包括：

* 文件的大小。
* Dimension（高度和宽度）。
* 音频或视频文件的比特率。
* 图像的分辨率（详细程度）。

描述性元数据是与应用程序域相关的元数据，例如资产所来自的业务。 描述性元数据无法自动确定。 它是手动或半自动创建的。 例如，启用了GPS的相机可以自动跟踪纬度和经度，并添加地理标记图像。

手动创建描述性元数据信息的成本很高。 因此，制定标准以简化跨软件系统和组织的元数据交换。 [!DNL Experience Manager Assets] 支持元数据管理的所有相关标准。

## 编码标准 {#encoding-standards}

在文件中嵌入元数据的方法有多种。 支持一系列编码标准：

* XMP:使用者 [!DNL Assets] 用于在存储库中存储提取的元数据。
* ID3:，用于音频和视频文件。
* Exif:，用于图像文件。
* 其他/旧版：从 [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]，等等。

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP)是一个开放标准， [!DNL Experience Manager Assets] ，以用于所有元数据管理。 该标准提供了可嵌入所有文件格式的通用元数据编码。 Adobe和其他公司支持XMP standard，因为它提供了丰富的内容模型。 XMP standard和的用户 [!DNL Experience Manager Assets] 拥有强大的平台可进行构建。 有关更多信息，请参阅 [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

当您在计算机或便携式MP3播放器上播放数字音频文件时，会显示存储在这些ID3标记中的数据。

ID3标记专为MP3文件格式而设计。 有关格式的其他信息：

* ID3标记在MP3和mp3PRO文件中有效。
* WAV没有标记。
* WMA具有不允许开源实施的专有标记。
* Ogg Vorbis使用嵌入在Ogg容器中的Xiph注释。
* AAC使用专有标记格式。

### Exif {#exif}

可交换图像文件格式(Exif)是数字摄影中最常用的元数据格式。 它提供了一种在多种文件格式(如JPEG、TIFF、RIFF和WAV)中嵌入固定的元数据属性词汇的方法。 Exif将元数据存储为元数据名称和元数据值的对。 这些元数据名称 — 值对也称为标记，请不要将其与 [!DNL Experience Manager]. 现代数码相机创建Exif元数据，现代图形软件支持它。 Exif格式是元数据管理（尤其是对于图像）的最低常用分母。

Exif的一个主要限制是一些常见的图像文件格式(如BMP、GIF或PNG)不支持它。

Exif定义的元数据字段通常具有技术性，在描述性元数据管理中的用法有限。 因此， [!DNL Experience Manager Assets] 选件将Exif属性映射到 [通用元数据架构](metadata-schemas.md) 和 [XMP](xmp-writeback.md).

### 其他元数据 {#other-metadata}

可从文件中嵌入的其他元数据包括 [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]，等等。

## 元数据架构 {#metadata-schemata}

元数据架构是预定义的元数据属性定义集，可在各种应用程序中使用。 属性始终与资产关联，这意味着这些属性是“关于”资源的。

如果不存在能满足您需求的元数据架构，您还可以设计自己的元数据架构。 请勿复制现有信息。 在组织内对架构进行划分，可更轻松地共享元数据。 [!DNL Experience Manager] 为您提供最常用元数据架构的默认列表。 该列表可帮助您快速启动元数据策略，并快速选择所需的元数据属性。

下面列出了支持的元数据架构。

### 标准元数据 {#standard-metadata}

* DC - [!DNL Dublin Core] 是一组重要且被广泛使用的元数据。
* DICOM — 医学中的数字成像和通信。
* `Iptc4xmpCore` 和 `iptc4xmpExt`  — 国际新闻传播标准包含许多特定于主题的元数据。
* RDF — 资源描述框架 — 用于通用语义Web元数据。
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ`  — 基本工作单。

### 特定于应用程序的元数据 {#application-specific-metadata}

特定于应用程序的元数据包括技术和描述性元数据。 如果您使用此类元数据，其他应用程序可能无法使用该元数据。 例如，其他图像渲染应用程序可能无法访问 [!DNL Adobe Photoshop] 元数据。 您可以创建一个工作流步骤，以将特定于应用程序的属性更改为标准属性。

* ACDSee — 由 [!DNL ACDSee] 项目。 请参阅 [www.acdsee.com/](https://www.acdsee.com/).
* 专辑 —  [!DNL Adobe Photoshop Album].
* CQ — 使用者 [!DNL Experience Manager Assets].
* DAM — 使用者 [!DNL Experience Manager Assets].
* DEX - [优化SC描述资源管理器](http://www.optimasc.com/products/dex/index.html) 是用于Windows操作系统的元数据和文件管理的工具集合。
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto和MP -Microsoft Photo。
* PDF和PDF/X。
* Photoshop和psAux - [!DNL Adobe Photoshop].

### Digital Rights Management元数据 {#digital-rights-management-metadata}

* 抄送 - [!DNL Creative Commons].
* [!DNL XMPRights]。
* 加 —  [图片许可通用系统](https://www.useplus.com).
* 棱镜 —  [行业标准元数据的发布要求](https://www.idealliance.org/prism-metadata).
* PRL - PRISM权限语言。
* PUR - PRISM使用权限。
* `xmpPlus`  — 将PLUS与XMP集成。

### 特定于摄影的元数据 {#photography-specific-metadata}

* Exif — 相机的技术信息，包括GPS位置。
* CRS - [!DNL Camera Raw] 架构。
* `iptc4xmpCore` 和 `iptc4xmpExt`.
* TIFF — 图像元数据(不仅适用于TIFF图像)。

### 特定于打印的元数据 {#print-specific-metadata}

* PDF和PDF/X - Adobe PDF和第三方应用程序。
* 棱镜 —  [行业标准元数据的发布要求](https://idealliance.org/specifications/prism-metadata/).
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG`  — 分页文本的XMP元数据。

### 特定于多媒体的元数据 {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM`  — 媒体管理。

## 元数据驱动的工作流 {#metadata-driven-workflows}

创建元数据驱动的工作流可以帮助您实现某些流程的自动化，从而提高效率。 在元数据驱动的工作流中，工作流管理系统读取该工作流，并因此执行一些预定义的操作。 例如，您可以使用元数据驱动的工作流的一些方式：

* 工作流可以检查图像是否具有标题。 如果没有，系统会通知您添加标题。
* 该工作流可以检查资产上的版权声明是否允许分发。 因此，系统会将资产发送到一台或另一台服务器。
* 工作流可以检查没有预定义的必需元数据的资产，或检查具有 *无效* 元数据。
