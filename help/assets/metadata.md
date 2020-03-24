---
title: 管理数字资产的元数据
description: 了解元数据的类型以及Adobe Experience Manager资产如何帮助管理资产的元数据，从而更轻松地对资产进行分类和组织。 Adobe Experience Manager Assets能够保留和管理资产中的任意元数据，因此，可以根据资产的元数据自动组织和处理资产。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5ef4c4e42165819191c6e3810c36183110f3f34a

---


# 管理数字资产的元数据 {#managing-metadata-for-digital-assets}

Adobe Experience Manager资产可保留每个资产的元数据。 这使得资产分类和组织更轻松，并且有助于寻找特定资产的人员。 元数据管理能够从上传到Experience Manager资产的文件中提取元数据，从而与创意工作流程相集成。 借助Experience Manager保留和管理资产中的元数据的功能，您可以根据元数据自动组织和处理资产。

* [XMP 元数据](xmp.md)
* [如何编辑或添加元数据](meta-edit.md)
* [元数据架构参考](meta-ref.md)

## 为何需要元数据 {#why-we-need-metadata}

元数据是指关于数据的数据。在这方面，数据是指您的数字资产，例如图像。 元数据对于有效管理资产至关重要。

元数据是资产可用的所有数据的集合，但不一定包含在该图像中。 一些元数据示例包括：

* 资产的名称。
* 上次修改的时间和日期。
* 资产存储在存储库中时的大小。
* 包含在其中的文件夹的名称。
* 相关资产或已应用的标记。

这些是Experience Manager可为资产管理的基本元数据属性，通过这些属性，用户可以查看所有资产（例如，按上次修改日期排序）-在尝试发现最近添加到存储库的资产时非常有用。

您可以向数字资产中添加更多高级别的数据，例如：

* 资产类型（是图像、视频、音频剪辑还是文档？）。
* 资产的所有者。
* 资产的标题。
* 资产的说明。
* 为资产分配的标记。

较多的元数据可以帮助您进一步对资产分类，随着数字信息量的增多，元数据会非常有用。仅根据文件名管理数百个文件是可能的。 但是，这种方法不可扩展，并且当所涉人员数量和受管理资产数量增加时，该方法会很快出现问题。

向资产中添加元数据后，资产会变得更有价值，因为资产会在以下方面得到改进,

* 更易于访问 - 用户可以更轻松地查找资产.
* 更易于管理 - 您可以更轻松地查找具有相同属性集的资产，并对它们应用更改.
* 更复杂 - 向资产中添加的元数据越多，元数据管理就会变得越重要.

由于这些原因，Experience Manager资产为您提供了为数字资产创建、管理和交换元数据的正确方法。

## 元数据的类型 {#types-of-metadata}

两种基本类型的元数据是技术元数据和描述性元数据。

技术性元数据对于处理数字资产的软件应用程序而言非常有用，因此不应该手动维护。Experience Manager资产和其他软件会自动确定技术元数据，并且在资产被修改时，元数据可能会发生更改。 资产的可用技术性元数据主要取决于资产的文件类型。技术元数据的一些示例包括：

* 文件大小
* 图像的尺寸（高度和宽度）
* 音频或视频文件的比特率
* 图像的分辨率（细节级别）

描述性元数据是与应用程序域相关的元数据，例如，资产所来自的业务。描述性元数据无法自动确定。它是手动或半自动创建的。 例如，启用GPS的相机可以自动跟踪纬度和经度并添加图像地理标记。

由于创建描述性元数据信息需要手动操作，人工成本较高，因此人们建立了相关标准，以便于在软件系统和组织之间交换元数据。

Experience Manager Assets支持元数据管理的所有相关标准。

鉴于元数据的重要性，以及创建元数据需要很大的手动工作量，人们建立了相关标准，以便于简化元数据交换。

## Encoding standards {#encoding-standards}

在文件中嵌入元数据有多种方法。 支持一系列编码标准选项：

* XMP:Experience Manager资产用来在存储库中存储提取的元数据。
* ID3：适用于音频和视频文件。
* Exif:图标。
* 其他／旧版：从Microsoft Word、PowerPoint、Excel等中。

### XMP {#xmp}

可扩展元数据平台(XMP)是一个开放标准，Experience Manager Assets使用它管理所有元数据。 该标准提供可嵌入到所有文件格式的通用元数据编码。 Adobe和其他公司支持XMP标准，因为它提供了丰富的内容模型。 XMP标准和Experience Manager Assets的用户拥有一个强大的平台，可以在此基础上继续构建。 有关详细信息，请参 [阅XMP](https://www.adobe.com/products/xmp.html)。

### ID3 {#id}

当您在计算机或便携式 MP3 播放器上播放数字音频文件时，会显示这些 ID3 标记中存储的数据。

ID3 标记是专为 MP3 文件格式而设计。有关各种格式的其他信息如下：

* ID3标记适用于MP3和mp3PRO文件。
* WAV 无标记。
* WMA具有不允许开放源代码实现的专有标签。
* Ogg Vorbis 使用嵌入在 Ogg 容器中的 Xiph 注释。
* AAC 使用专有标记格式。

### Exif {#exif}

可交换图像文件格式(Exif)是数字摄影中最常用的元数据格式。 它提供了一种将固定的元数据属性词汇嵌入许多文件格式（如JPEG、TIFF、RIFF和WAV）的方法。 Exif将元数据存储为元数据名称和元数据值的对。 这些元数据名称——值对也称为标记，不要与Experience Manager中的标记相混淆。 由于Exif是由现代数码相机自动创建并通过现代图形软件提供支持的，因此它可被视为元数据管理的最低标准。

Exif的一个主要限制是一些常用的图像文件格式（如BMP、GIF或PNG）不支持它。

通常由Exif定义的元数据字段具有技术性质，在描述性元数据管理中的使用有限。 因此，Experience Manager Assets提供了将Exif属性映射到常见元数 [据架构](metadata-schemas.md) 和 [XMP的功能](xmp-writeback.md)。

### Other metadata {#other-metadata}

可以从文件中嵌入的其他元数据包括Microsoft Word、PowerPoint、Excel等。

## Metadata schemata {#metadata-schemata}

元数据架构是可用于各种应用程序的预定义元数据属性定义集。 属性始终与资产相关联，也就是说属性是“关于”资源的数据。

如果不存在满足您需求的元数据架构，您还可以设计自己的元数据架构。 请勿复制现有信息。 在组织内部，将架构分开使元数据共享更容易。 Experience Manager为您提供了最受欢迎的元数据架构的默认列表。 该列表可帮助您快速启动元数据战略并快速选择所需的元数据属性。

支持的元数据架构如下所列。

### Standard metadata {#standard-metadata}

* dc - 都柏林核心 - 最重要、应用最广泛的元数据集.
* DICOM - 医学数字成像和通信.
* Iptc4xmpCore和iptc4xmpExt - International Press Communications Standard —— 许多特定于主题的元数据。
* rdf - 资源描述框架 - 适用于通用语义 Web 元数据.
* xmp - 可扩展元数据平台.
* xmpBJ - 基本工单.

### Application-specific metadata {#application-specific-metadata}

特定于应用程序的元数据包括技术和描述性元数据。 如果您使用这类元数据，其他应用程序将无法使用这些元数据。例如，如果您有一个资产包含Adobe Photoshop元数据，而另一个图像渲染应用程序则尝试访问该元数据，它可能无法访问该元数据。 如果您发现资产中有许多特定于应用程序的元数据，则可以创建一个将特定于应用程序的属性更改为标准属性的工作流步骤。

* acdsee - metadata managed by the ACDSee program [www.acdsee.com/](https://www.acdsee.com/).
* album - Adobe Photoshop Album.
* cq —— 由Experience Manager Assets使用。
* dam —— 由Experience Manager资产使用。
* dex - Optima SC Description Explorer.
* crs - Adobe Photoshop Camera Raw.
* lr - Adobe Lightroom.
* mediapro - IView MediaPro.
* MicrosoftPhoto 和 MP - Microsoft Photo.
* pdf 和 pdfx
* photoshop 和 psAux - Adobe Photoshop

### Digital Rights Management metadata {#digital-rights-management-metadata}

* cc - Creative Commons
* xmpRights
* plus —— 图片授权通用系统- https://www.useplus.com/
* prism - https://www.idealliance.org/prism-metadata行业标准元数据的发布要求
* prl - Prism 权限语言
* pur - Prism 使用权限
* xmpPlus - PLUS 与 XMP 的集成

### Photography-specific metadata {#photography-specific-metadata}

* exif - 照相机中的大量技术性信息，包括 GPS 定位
* crs - Photoshop Camera Raw
* Iptc4xmpCore和iptc4xmpExt
* TIFF - 图像元数据（并非只适用于 TIFF 图像）

### Print-specific metadata {#print-specific-metadata}

* pdf和pdfx - Adobe PDF和第三方应用程序
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata
* xmp
* xmpPG - 适用于分页文本的 xmp

### Multimedia-specific metadata {#multimedia-specific-metadata}

* xmpDM - Dynamic Media
* xmpMM - 媒体管理

## Metadata-driven workflows {#metadata-driven-workflows}

创建元数据驱动的工作流可以帮助您实现一些流程的自动化，从而提高效率。 在元数据驱动的工作流中，工作流管理系统会读取该工作流，然后相应地执行某些预定义操作。例如，以下是可以利用元数据驱动的工作流实现的功能：

* 该工作流可以检查图像是否含有标题。如果图像没有标题，系统会通知特定用户添加标题。
* 该工作流可以检查资产上的版权声明是否允许分发。如果允许分发，系统会将资产发送到某台服务器。如果不允许分发，系统会将资产发送到另一台服务器。
* 工作流可以检查资产，而无需预定义的强制元数据，也可以检查元数据 *无效* 。
