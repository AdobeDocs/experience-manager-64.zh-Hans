---
title: XMP元数据
description: 了解使用的XMP（可扩展元数据平台）元数据标准 [!DNL Experience Manager] 用于元数据管理的资产。 XMP为创建、处理和交换各种应用程序的元数据提供了一种标准格式。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 19%

---

# XMP 元数据 {#xmp-metadata}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

XMP（可扩展元数据平台）是 [!DNL Experience Manager] 用于所有元数据管理的资产。 XMP为创建、处理和交换各种应用程序的元数据提供了一种标准格式。

除了提供可嵌入到所有文件格式的通用元数据编码之外，XMP还提供了丰富的 [内容模型](xmp.md#xmp-core-concepts) 和 [受Adobe](xmp.md#advantages-of-xmp) 和其他公司，以便XMP的用户与 [!DNL Experience Manager] 资产拥有强大的基础平台。

的 [XMP规范](https://www.adobe.com/devnet/xmp.html) 可从Adobe中获取。

## 什么是XMP? {#what-is-xmp}

[!DNL Experience Manager] 资产本身支持由Adobe带头的XMP — 可扩展元数据平台。 XMP是用于处理和存储数字资产中标准化的专有元数据的标准。 XMP旨在成为允许多个应用程序有效处理元数据的通用标准。

例如，生产专业人员可以使用Adobe应用程序内内置的XMP支持跨多种文件格式传递信息。 的 [!DNL Experience Manager] 资产存储库会提取XMP元数据，并使用该元数据来管理内容生命周期，并提供创建自动化工作流的功能。

XMP通过提供数据模型、存储模型和架构，使元数据的定义、创建和处理方式标准化。 本节将介绍所有这些概念。

来自EXIF、ID3或Microsoft Office的所有旧版元数据都会自动转换为XMP，该元数据可扩展以支持特定于客户的元数据架构，如产品目录。

XMP中的元数据由一组属性组成。 这些属性始终与\
称为资源的特定实体；即，属性是“关于”资源。 对于XMP，资源始终是资产。

### Adobe {#adobe}

Adobe首先在Adobe Acrobat软件产品中引入了XMP标准。 此后，XMP标准得到广泛采用。

### XMP生态系统 {#xmp-ecosystem}

XMP 定义了一个可与任何定义的元数据项集一起使用的[元数据](https://en.wikipedia.org/wiki/Metadata)模型。XMP 还为基本属性定义了一个特定的[架构[，这些基本属性可用于记录资源经过多个处理步骤的历史记录：从拍摄、](https://en.wikipedia.org/wiki/XML_schema)扫描](https://en.wikipedia.org/wiki/Image_scanner)或创作为文本，到照片编辑步骤（如[裁剪](https://en.wikipedia.org/wiki/Cropping_%28image%29)或颜色调整），再到组合到最终图像中。XMP 允许每个软件程序或设备向数字资源添加其自己的信息，该信息可保留在最终的数字文件中。

XMP 最常使用 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [资源描述框架](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF) 的子集进行序列化和存储，该子集又以 [XML](https://en.wikipedia.org/wiki/XML) 形式表示。

## XMP的优势 {#advantages-of-xmp}

XMP与其他编码标准和架构相比具有以下优势：

* 基于XMP的元数据功能非常强大且细粒度。
* XMP允许您为一个资产包含多个值。
* XMP具有标准化的编码，可让您轻松交换元数据。
* XMP是可扩展的。 您可以向资产中添加其他信息。

### 可扩展 {#extensible}

XMP标准旨在提供可扩展性，允许您向XMP数据中添加自定义类型的元数据。 而EXIF则不会 — 它有一个固定的无法扩展的属性列表。

>[!NOTE]
>
>XMP通常不允许嵌入二进制数据类型。 要在XMP中携带二进制数据（例如缩略图），必须以XML友好格式（如Base64）对它们进行编码。

## XMP核心概念 {#xmp-core-concepts}

以下各节介绍了XMP的核心概念，包括命名空间和架构、属性和值以及语言替代内容。

### 命名空间和架构 {#namespaces-and-schemata}

XMP架构是通用XML命名空间中的一组属性名称，其中包括\
数据类型和描述性信息。 XMP架构通过其XML命名空间URI进行标识。 使用命名空间可以防止不同架构中名称相同但含义不同的属性之间发生冲突。

例如， **创建者** 两个独立设计架构中的资产可能是指创建资产的人员，也可能是指创建资产的应用程序(例如，Adobe Photoshop)。

### 属性和值 {#properties-and-values}

XMP可以包含来自一个或多个架构的属性。

例如，许多Adobe应用程序使用的典型子集可能包括以下内容：

* 都柏林核心架构：dc:title， dc:creator， dc:subject， dc:format， dc:rights
* XMP基本架构：xmp:CreateDate， xmp:CreatorTool， xmp:ModifyDate， xmp:metadataDate
* XMP权限管理架构：xmpRights:WebStatement、xmpRights:Marked
* XMP媒体管理架构：xmpMM:DocumentID

### 替代语言 {#language-alternatives}

XMP让您能够添加 **xml:lang** 属性来指定文本的语言。
