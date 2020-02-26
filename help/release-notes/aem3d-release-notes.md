---
title: AEM 3D发行说明
seo-title: AEM 3D发行说明
description: Adobe Experience Manager资产中特定于3D内容的发行说明。
seo-description: Adobe Experience Manager资产中特定于3D内容的发行说明。
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
content-type: reference
topic-tags: 3D
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f

---


# AEM 3D发行说明 {#aem-d-release-notes}

AEM-6.4-DynamicMedia-3D版本3.1.0（2018年10月10日）

AEM 3D功能包支持AEM资产中的3D内容。 它提供了上传、管理、预览和渲染3D资产的功能。 对查看和渲染的支持已针对单个对象（而不是具有多个对象的复杂场景）进行优化。

AEM 3D支持Adobe Dimension(Dn)和glTF资产类型。 这些资产类型的实施与本文档中描述的传统3D类型的实施有很大不同。 请参 [阅使用Adobe Dimension资产](/help/assets/working-dimension-assets.md)。

还包括与Autodesk® Maya®的服务器端集成（仅限Windows）。 在与AEM相同的服务器上安装和配置Maya时，您可以支持本机Maya文件格式，包括使用Maya的NVIDIA® mentalray® Standalone插件进行高质量渲染。 在服务器上安装和配置3ds Max支持本机。max文件格式。

请参 [阅与Autodesk Maya集成](/help/assets/integrate-maya-with-3d.md)。

另请参 [阅安装和配置AEM 3D资产和](/help/assets/install-config-3d.md)[高级配置设置](/help/assets/advanced-config-3d.md)。

另请参阅 [使用3D资产](/help/assets/assets-3d.md)。

## 系统要求 {#system-requirements}

**前提条件**

* AEM 6.4.2(AEM 6.4（带Service Pack 2）)
* Autodesk® FBX® SDK 2016.1.2

**支持的操作系统**

* Microsoft Windows 2012 server或更高版本
* Apple OS X El Capitan 10.6或更高版本
* RedHat Enterprise Linux 7.3

**AEM资产支持的Web浏览器**

* Google Chrome 53或更高版本（建议）。
* Apple Safari 9.1或更高版本。
* Firefox 48或更高版本。
* Microsoft Edge 25.10586或更高版本。

其他浏览器可能不支持在AEM中交互查看3D内容。 只有Google Chrome支持预览中的投影。

**硬件要求和建议**

* CPU —— 计算机的CPU对3D处理和渲染的要求很高。 因此，建议使用最少8个CPU核心的当代服务器。
* 内存——建议最少使用32 GB。
* 大容量存储——建议使用高带宽SSD存储。

   上传时，3D资产会转换为专有格式，以便快速进行交互式查看。 根据3D资产的类型，需要2-3倍于已上传3D资产大小的存储空间。

另请参阅 [使用3D资产](/help/assets/assets-3d.md)。

## 安装和配置AEM 3D {#installing-and-configuring-aem-d}

See [Installing and configuring AEM 3D](/help/assets/install-config-3d.md).

另请参 [阅将AEM 3D与Autodesk Maya集成](/help/assets/integrate-maya-with-3d.md) , [以及将AEM 3D与Autodesk 3ds Max集成](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md)。

## 支持的3D文件格式 {#supported-d-file-formats}

<table> 
 <tbody>
  <tr>
   <td><strong>格式</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>平台</strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>DN</td> 
   <td>Adobe Dimension</td> 
   <td>所有</td> 
   <td>需要访问基于云的转换服务。</td> 
  </tr>
  <tr>
   <td>GLTZ</td> 
   <td>Zipped gITF</td> 
   <td>所有</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>GLB</td> 
   <td>二进制gITF</td> 
   <td>所有</td> 
   <td>仅下载（GLB再现是为DN资产创建的）。</td> 
  </tr>
  <tr>
   <td>OBJ</td> 
   <td>Wavefront OBJ 3D </td> 
   <td>所有</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>FBX</td> 
   <td>Autodesk FBX(Kaydara Filmbox)</td> 
   <td>所有</td> 
   <td>Autodesk FBX SDK必须安装在“作者”节点上。</td> 
  </tr>
  <tr>
   <td>MA, MB</td> 
   <td>本机Autodesk Maya</td> 
   <td>仅限Windows</td> 
   <td>在“作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参 <a href="/help/assets/integrate-maya-with-3d.md" target="_blank">阅将AEM 3D与Autodesk Maya集成</a>。</td> 
  </tr>
  <tr>
   <td>JT</td> 
   <td>Siemens PLM Open CAD</td> 
   <td>仅限Windows</td> 
   <td>在“作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参 <a href="/help/assets/integrate-maya-with-3d.md">阅将AEM 3D与Autodesk Maya集成</a>。</td> 
  </tr>
  <tr>
   <td>*</td> 
   <td><p>可以启用Autodesk Maya支持的其他3D输入格式。</p> <p>请参 <a href="/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya" target="_blank">阅启用Maya支持的其他格式</a>。</p> </td> 
   <td>仅限Windows</td> 
   <td>在“作者”节点上需要Autodesk Maya才能启用这些文件格式。 请参 <a href="/help/assets/integrate-maya-with-3d.md">阅将AEM 3D与Autodesk Maya集成</a>。</td> 
  </tr>
  <tr>
   <td>MAX</td> 
   <td>本机Autodesk 3ds Max</td> 
   <td>仅限Windows</td> 
   <td>创作节点上需要Autodesk 3ds Max才能启用此文件格式。 请参 <a href="/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md">阅将AEM 3D与Autodesk 3ds Max集成</a>。</td> 
  </tr>
 </tbody>
</table>

## 增强功能和新增功能 {#enhancements-and-new-features}

3.0版

* 支持Autodesk 3ds Max本机文件格式。
* 通过各种更改和错误修复提高稳定性、质量和用户体验。
* 配置设置已移至 `/libs/settings/dam/v3d/`

版本3.1

* 对Adobe Dimension本机文件格式(.dn)的有限支持。
* 用于glTF资源的全新3D查看器。
* Amazon AWS中托管的基于云、由Adobe管理的转化服务的新界面。 最初，此服务仅从Dn转换为glTF格式。

## 限制和已知问题 {#restrictions-and-known-issues}

### Adobe Dimension支持 {#adobe-dimension-support}

* 此版本的AEM3D对使用Adobe Dimension创建的。dn文件的支持有限。
* 在上传处理过程中，AEM利用基于云的Adobe托管转换服务从本机。dn文件创建glTF再现。 需要访问转换服务并选择Amazon AWS端点。
* 提供了新的glTF查看器，它支持在AEM资产和站点／屏幕中查看Dn资产。 尚不支持查看器中的阶段。
* Dn模型可嵌入显示的IBL灯和背景（如果有）。 或者，查看器应用默认照明或默认背景色，或同时应用两者。
* Dn资产的高质量渲染尚不可用。
* 依赖项（如纹理映射）嵌入在Dn资产中，无法在AEM中显式管理。

### 兼容性 {#compatibility}

* **不支持作为Windows服务运行（仅限Windows）** -这可能有效，但尚未测试。
* **Dynamic Media** (模 `dynamicmedia-scene7` 式)- AEM3D与随AEM 6.4一起发布的新Dynamic media解决方案的兼容性尚未完全验证。 如果Dynamic media和AEM3D一起部署，建议您仅将3D资产及其依赖关系放在未分配给Dynamic media的AEM资产存储库的区域中。 此建议对于3D阶段需要但Dynamic media不支持的32位TIFF文件尤为重要。

### 常规 {#general}

* **解析依赖关系快捷键** -此快捷键在3D资产的卡片视图中可用。 卡片视图中的资产卡片会显示“未解析的依赖关系”横幅。 该快捷键将打开“基 **本属性** ”(Basic Properties)选项卡，而不 **是“依赖关系** ”(Dependencies)选项卡。 解决方法：手动导航到依赖关系选项卡。

* **舞台选择器不可用** -包含灯光的3D资产由AEM自动标记为3D舞台。 “详细信息”视图中的阶段没有“阶段”选择器可用。 要将3D资产标记为3D对象，请导航到“基本属性” **，将“资产类”更改为** 3D对象 **，然后单击“**********&#x200B;保存”。

* **下载包含依赖项和演绎版的3D资产** -当从AEM下载3D资产时，同时选中了“依赖项”和“再现” ******** ，下载不仅包括主3D资产的演绎版，还包括所有依赖项的演绎版。

* **Autodesk 3ds max集成** -目前不支持使用3ds max进行渲染。

### 文件类型限制 {#file-type-restrictions}

* **Mathematica(.ma)文件** - Mathematica文件使用与本机Maya文件相同的文件后缀。 安装功能包并启用Maya .ma文件格式时，AEM3D尝试将Maya文件作为Maya文件收录失败。 此类资产会在卡片视图中显示错误横幅。

* **Targa(.tga)图像文件** -较旧的3D模型文件可能包括对TGA文件的引用。 AEM不支持此格式。 Adobe建议您在将3D资产上传到AEM之前，将这些文件转换为其他格式。
* **HDR图像** - HDR图像用于具有基于图像的照明(IBL)的舞台。 目前，仅支持32位TIFF图像用于此目的。
* **32位TIFF图像** - 32位TIFF图像用于具有基于图像的照明的舞台。 AEM不支持为这些资产创建再现，因此会生成空白的缩略图，并且无法进行预览。 与IBL舞台一起使用时，资产仍可正常工作。
* **Autodesk 3ds Max(.max)文件** -如果在“作者”节点上安装和配置了Autodesk 3ds Max，则AEM支持。max文件的获取和转换。 目前不支持将。max文件用作舞台。

### 自动相关性解析 {#automatic-dependency-resolution}

* **上传后无法解析的文件依赖关系** -当使用相同的上传操作上传3D资产及其依赖项时，可能不会自动解析某些依赖项。 如果从属文件很大，则更可能出现此问题。 要更正此问题，请访问资产的“属 **性／依赖关系** ”页面，该页面在上传后显示未解析的依赖项。 现在应显示以前未解析的依赖项。 单击 **保存** ，以完成资产。 为防止将来出现此问题，您可以在上传3D对象之前，在单独的事务中上传所有依赖项。

* **区分大小写** -自动依赖关系解析尝试以区分大小写的方式匹配文件名。 例如，如果在3D资产中找到的原始依赖关系是 `image.jpg`，则该依赖关系会解析为名为、或任何其他大小写变 `Image.jpg`体的 `image.JPG`资产。

### 3D舞台 {#d-stages}

* **舞台缩览图** -自动生成的舞台缩览图可能无法准确表示舞台。
* **非IBL舞台的舞台几何** - Rapid Refine渲染器不渲染具有非IBL照明的舞台中的几何，包括背景和地平面。 此类几何图形仍在资产详细信息视图（3D预览）中合理显示。

* **具有IBL照明的FBX舞台** -您可以上传具有IBL照明的FBX舞台。 但是，FBX格式没有传输IBL图像名称的规定。 因此，文件依赖关系解析失败。 上传后，必须手动将IBL图像分配给舞台。 您可以将相同的32位TIFF图像分配给三个依赖项，这三个依赖项是扩散照明环境图像 **、反射环境图像和背景环境图像**********，或者可能分配不同的图像。

* **IBL舞台的背景图像** -对于某些IBL场景，背景图像可能质量较差，如过亮或过模糊。 为最大限度地提高IBL舞台的图像背景的视觉质量，Adobe建议您准备单独的高分辨率8位JPEG图像，并将其作为背景环境图像附加到IBL **舞台**。

* **使用IBL舞台用Maya渲染时的黑色图像** -此问题可能是由于Maya找不到IBL图像依赖关系，因为由舞台引用的原始IBL图像被替换为其他名称的图像。 要避免此问题，请确保Maya IBL舞台引用的三个依赖关系中至少有一个与Maya文件中的原始IBL文件引用同名。
* **IBL舞台的反向背景图像** - IBL舞台的图像有意水平翻转，以匹配随Autodesk Maya提供的NVIDIA心理光线渲染器的行为。 解决方法：在上传Photoshop中用于IBL舞台的图像之前，请翻转它们。
* **IBL舞台的亮度** -对IBL图像的自动分析可能会导致场景太暗或太亮。 要调整IBL舞台的照明亮度，请导航到 **Basic Properties** ，并根据需 **要调整** Environment **** Lighting的明亮值。

### AEM Sites 3D组件 {#aem-sites-d-component}

* **每页一个3D组件** -此时，每个网页仅允许3D组件的一个实例。 如果向同一页面添加了多个3D组件，则所有3D组件均无法正常工作。
* **在站点中预览时3D视图缺失** -在站点中使用 **Preview** 时，必须在浏览器中重新加载页面才能完全初始化3D查看器。 在“作者”节点或“发布”节点上直接查看网页(即从路 `edit.html` 径中删除时)时，这并不是问题。

* **全屏模式在iOS设备上不可用** -无论使用何种浏览器，iOS设备上都不提供全屏按钮。

### 发布3D内容 {#publishing-d-content}

* **3D组件配置** -必须在所有活动的发布节点上安装3D功能包，并且每个节点必须配置 **CRXDE Lite** ，以使用上的相同配置选项 `/libs/settings/dam/v3D/WebGLSites`。

* **发布后缺少纹理、背景或光线** - AEM Sites中的 **Publish** （发布）机制会自动发布页面的主要依赖关系，包括3D模型和3D组件引用的3D舞台。 3D舞台和3D模型通常取决于IBL图像和纹理映射的辅助资源，而站点发布机制不会自动发布这些资源。 解决方法：在从站点发布网页之前，先从资产发布所有3D资产。 这样做可确保3D资产的所有依赖关系在“发布”节点上可用。

