---
title: AEM 3D发行说明
seo-title: AEM 3D发行说明
description: Adobe Experience Manager资产中特定于3D内容的发行说明。
seo-description: Adobe Experience Manager资产中特定于3D内容的发行说明。
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes, 3D
content-type: reference
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 9710c9931b4f17073c712f5869a1843c1d99ee8e
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 0%

---


# AEM 3D发行说明{#aem-d-release-notes}

>[!IMPORTANT]
>
>不再支持AEM 6.4中的AEM 3D功能包。 Adobe建议您将[AEM中的3D资产功能用作Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)或[AEM 6.5.3或更高版本。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM-6.4-DynamicMedia-3D版本3.1.0（2018年10月10日）

AEM 3D功能包支持AEM Assets的3D内容。 它提供上传、管理、预览和渲染3D资产的功能。 对单个对象（而非具有多个对象的复杂场景）的查看和渲染支持已得到优化。

AEM 3D支持Adobe Dimension(Dn)和glTF资产类型。 这些资产类型的实施与本文档中描述的传统3D类型的实施大体不同。 请参阅[使用Adobe Dimension资产](/help/assets/working-dimension-assets.md)。

还包括与Autodesk® Maya®（仅限Windows）的服务器端集成。 在与AEM位于同一台服务器上安装和配置Maya时，您可以支持本机Maya文件格式，包括使用Maya的NVIDIA® mental ray® Standalone插件进行高质量渲染。 在服务器上安装和配置3ds Max支持本机。max文件格式。

请参阅[与Autodesk Maya](/help/assets/integrate-maya-with-3d.md)集成。

另请参阅[安装和配置AEM 3D资产](/help/assets/install-config-3d.md)和[高级配置设置](/help/assets/advanced-config-3d.md)。

另请参阅[使用3D资产](/help/assets/assets-3d.md)。

## 系统要求{#system-requirements}

**前提条件**

* AEM 6.4.2(AEM 6.4（带有Service Pack 2）
* Autodesk® FBX® SDK 2016.1.2

**支持的操作系统**

* Microsoft Windows 2012 Server或更高版本
* Apple OS X El Capitan 10.6或更高版本
* RedHat Enterprise Linux 7.3

**支持的AEM AssetsWeb浏览器**

* Google Chrome 53或更高版本（建议）。
* Apple Safari 9.1或更高版本。
* Firefox 48或更高版本。
* Microsoft Edge 25.10586或更高版本。

其他浏览器可能不支持AEM中3D内容的交互式查看。 只有Google Chrome支持预览中的投影。

**硬件要求和建议**

* CPU —— 计算机CPU对3D处理和渲染的要求很高。 因此，建议使用至少8个CPU核心的当代服务器。
* 内存——建议最少使用32 GB。
* 质量存储-建议使用高带宽SSD存储。

   上传时，3D资产会转换为专有格式，以便快速进行交互式查看。 根据3D资产的类型，需要大小为已上传3D资产的2-3倍的存储空间。

另请参阅[使用3D资产](/help/assets/assets-3d.md)。

## 安装和配置AEM 3D {#installing-and-configuring-aem-d}

请参阅[安装和配置AEM 3D](/help/assets/install-config-3d.md)。

另请参阅[将AEM 3D与Autodesk Maya](/help/assets/integrate-maya-with-3d.md)集成和[将AEM 3D与Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md)集成。

## 支持的3D文件格式{#supported-d-file-formats}

| 格式 | 描述 | 平台 | 注释 |
|--- |--- |--- |--- |
| DN | Adobe Dimension | 所有 | 需要访问基于云的转换服务。 |
| GLTZ | Zipped gITF | 所有 |  |
| GLB | 二进制gITF | 所有 | 仅下载（为DN资产创建GLB演绎版）。 |
| OBJ | Wavefront OBJ 3D | 所有 |  |
| FBX | Autodesk FBX(Kaydara Filmbox) | 所有 | Autodesk FBX SDK必须安装在“作者”节点上。 |
| MA, MB | 本机Autodesk Maya | 仅限Windows | “作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参阅[将AEM 3D与Autodesk Maya](/help/assets/integrate-maya-with-3d.md)集成。 |
| JT | Siemens PLM Open CAD | 仅限Windows | “作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参阅[将AEM 3D与Autodesk Maya](/help/assets/integrate-maya-with-3d.md)集成。 |
| * | 可以启用Autodesk Maya支持的其他3D输入格式。 请参阅[启用Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya)支持的其他格式。 | 仅限Windows | “作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参阅[将AEM 3D与Autodesk Maya](/help/assets/integrate-maya-with-3d.md)集成。 |
| MAX | 本机Autodesk 3ds Max | 仅限Windows | 创作节点上需要Autodesk 3ds Max才能启用此文件格式。 请参阅[将AEM 3D与Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md)集成。 |

## 增强和新增功能{#enhancements-and-new-features}

3.0版

* 支持Autodesk 3ds Max本机文件格式。
* 通过各种更改和错误修复提高稳定性、质量和用户体验。
* 配置设置已移至`/libs/settings/dam/v3d/`

版本3.1

* 对Adobe Dimension本机文件格式(.dn)的有限支持。
* 用于glTF资源的新3D查看器。
* 托管在AmazonAWS的基于云、由Adobe管理的转换服务的新界面。 最初，此服务仅从Dn转换为glTF格式。

## 限制和已知问题{#restrictions-and-known-issues}

### Adobe Dimension支持{#adobe-dimension-support}

* 此版本的AEM 3D对使用Adobe Dimension创建的。dn文件的支持有限。
* 在上传处理过程中，AEM利用基于云的、由Adobe托管的转换服务从本机。dn文件创建glTF再现。 需要访问转换服务并选择AmazonAWS端点。
* 提供了新的glTF查看器，它支持在AEM Assets和站点／屏幕中查看Dn资产。 尚不支持查看器中的阶段。
* Dn模型可嵌入显示的IBL灯和背景（如果存在）。 或者，查看器应用默认照明或默认背景颜色，或两者。
* Dn资产的高质量渲染尚不可用。
* 依赖项（如纹理映射）嵌入在Dn资产中，无法在AEM中显式管理。

### 兼容性 {#compatibility}

* **不支持作为Windows服务运行（仅限Windows）** -此操作可能有效，但尚未对其进行测试。
* **Dynamic Media** ( `dynamicmedia-scene7` 模式)- AEM33D与发布于AEM 6.4的新Dynamic Media解决方案的兼容性尚未完全验证。如果Dynamic Media和AEM 3D部署在一起，建议您仅将3D资产及其依赖项放置在未分配给Dynamic Media的AEM Assets存储库的某个区域。 此建议对于3D舞台所需的32位TIFF文件尤为重要，但Dynamic Media不支持。

### 常规 {#general}

* **解析依赖关系** 快捷方式——此快捷键在3D资产的卡视图中可用。卡视图卡中的资产卡会显示“未解析的依赖关系”横幅。 该快捷键会打开&#x200B;**基本属性**&#x200B;选项卡，而不是&#x200B;**依赖关系**&#x200B;选项卡。 解决方法：手动导航到“依赖关系”选项卡。

* **舞台选择器不可用** -包含灯光的3D资产由AEM自动标记为3D舞台。“详细信息”视图中没有舞台选择器可用。 要将3D资产标记为3D对象，请导航到&#x200B;**基本属性**，将&#x200B;**资产类**&#x200B;更改为&#x200B;**3D对象**，然后单击&#x200B;**保存**。

* **下载包含依赖项和演绎版的3D** 资产 **** -当从AEM下载3D资产时， **同时选** 中“依赖项”和“演绎版”选项，下载内容不仅包括主3D资产的演绎版，还包括所有依赖项的演绎版。

* **Autodesk 3ds Max集成** -目前不支持使用3ds Max进行渲染。

### 文件类型限制{#file-type-restrictions}

* **Mathematica(.ma)文件** - Mathematica文件使用与本机Maya文件相同的文件后缀。安装功能包并启用Maya .ma文件格式时，AEM3D尝试将Maya文件作为Maya文件收录Mathemica文件失败。 此类资产会在卡片视图中显示错误横幅。

* **Targa(.tga)图像文件** -旧的3D模型文件可能包括对TGA文件的引用。AEM不支持此格式。 Adobe建议在将3D资产上传到AEM之前，将这些文件转换为其他格式。
* **HDR图像** - HDR图像用于具有基于图像的照明(IBL)的舞台。目前，仅支持32位TIFF图像用于此用途。
* **32位TIFF图像** - 32位TIFF图像用于具有基于图像的照明的舞台。AEM不支持为这些资产创建再现，从而导致缩略图为空，并且无法进行预览。 与IBL舞台一起使用时，资产仍可正常工作。
* **Autodesk 3ds Max(.max)文件** -如果在“作者”节点上安装并配置了Autodesk 3ds Max, AEM将支持。max文件的摄取和转换。目前不支持将。max文件用作舞台。

### 自动依赖关系解析{#automatic-dependency-resolution}

* **上传后未解析的文件依赖** -当3D资产及其依赖项通过相同的上传操作上传时，某些依赖项可能无法自动解析。如果从属文件很大，则更可能出现此问题。 要更正此问题，请访问资产的&#x200B;**属性／依赖项**&#x200B;页面，该页面在上传后显示未解析的依赖项。 现在应显示以前未解析的依赖项。 单击&#x200B;**保存**&#x200B;以最终确定资产。 要防止将来出现此问题，您可以在上传3D对象之前，在单独的事务中上传所有依赖项。

* **区分大小写** -自动相关性解析尝试以区分大小写的方式匹配文件名。例如，如果在3D资产中找到的原始依赖项为`image.jpg`，则该依赖项解析为名为`Image.jpg`、`image.JPG`或任何其他大小写变体的资产。

### 3D舞台{#d-stages}

* **舞台缩览图** -自动生成的舞台缩览图可能不能准确地表示舞台。
* **非IBL舞台的舞台几何** - Rapid Refine渲染器不渲染具有非IBL光照的舞台中的几何，包括背景和地面。此类几何仍在资产详细信息视图(3D预览)中合理显示。

* **带IBL照明的FBX舞台** -您可以上传带IBL照明的FBX舞台。但是，FBX格式没有传输IBL图像名称的规定。 因此，文件依赖关系解析失败。 上传后，必须手动将IBL图像分配给舞台。 可以将相同的32位TIFF图像指定给以下三个依赖项：**扩散照明环境图像**、**反射环境图像**&#x200B;和&#x200B;**背景环境图像**，或者可以分配不同的图像。

* **IBL舞台背景图像** -对于某些IBL场景，背景图像可能质量差，如过亮或过模糊。为最大限度地提高IBL舞台的图像背景的视觉质量，Adobe建议您准备单独的高分辨率8位JPEG图像，并将其作为&#x200B;**背景环境图像**&#x200B;附加到IBL舞台。

* **使用IBL舞台用Maya进行渲染时显示黑色图像** -此问题可能是由于Maya找不到IBL图像依赖关系，因为舞台引用的原始IBL图像已被其他名称的图像替换。要避免此问题，请确保Maya IBL舞台引用的三个依赖关系中至少有一个与Maya文件中的原始IBL文件引用同名。
* **IBL舞台的反向背景图像** - IBL舞台的图像有意水平翻转，以匹配随Autodesk Maya提供的NVIDIA心理光线渲染器的行为。解决方法：上传用于PhotoshopIBL舞台的图像前，请翻转它们。
* **IBL舞台的亮度** - IBL图像的自动分析可能导致场景太暗或太亮。要调整IBL舞台的照明亮度，请导航至&#x200B;**基本属性**&#x200B;并根据需要调整&#x200B;**环境照明**&#x200B;的&#x200B;**bright**&#x200B;值。

### AEM Sites3D组件{#aem-sites-d-component}

* **每页一个3D组件** -此时，每个网页上只允许一个3D组件实例。如果将多个3D组件添加到同一页面，则所有3D组件均无法正常工作。
* **在站点中预览时3D视图缺失** -使用Previewin  **** Sites时，必须在浏览器中重新加载页面才能完全初始化3D查看器。在作者节点或发布节点上直接视图网页（即从路径中删除`edit.html`时）时，这不是问题。

* **iOS设备上不提供全屏模式** -无论使用何种浏览器，iOS设备上均不提供全屏按钮。

### 发布3D内容{#publishing-d-content}

* **3D组件配置** -必须在所有活动的发布节点上安装3D功能包，并且每个节点必须使用CRXDE列 **表** 配置到相同的配置选项，网址为 `/libs/settings/dam/v3D/WebGLSites`。

* **发布后缺少纹理、背景** 或照明-AEM Sites **** 的Publishmechanism会自动发布页面的主要依赖项，包括3D模型和3D组件引用的3D舞台。3D舞台和3D模型通常取决于IBL图像和纹理映射的辅助资源，而站点发布机制不会自动发布这些资源。 解决方法：在从站点发布网页之前，从资产发布所有3D资产。 这样做可确保3D资产的所有依赖关系在“发布”节点上均可用。
