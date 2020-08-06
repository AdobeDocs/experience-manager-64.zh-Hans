---
title: 关于使用 IBL 舞台
seo-title: 关于使用 IBL 舞台
description: AEM 3D 支持基于图像的照明 (IBL)，以便使用内置的 Adobe Rapid Refine 渲染器和第三方渲染器进行交互式查看和渲染。您可以使用常见的创作工具（如 Autodesk Maya 或 Autodesk 3ds Max）创建 IBL 舞台。
seo-description: AEM 3D 支持基于图像的照明 (IBL)，以便使用内置的 Adobe Rapid Refine 渲染器和第三方渲染器进行交互式查看和渲染。您可以使用常见的创作工具（如 Autodesk Maya 或 Autodesk 3ds Max）创建 IBL 舞台。
uuid: 6598fb8a-65b0-4b84-8063-fdc94f6ea935
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f9291151-851a-4aff-a50e-a24330ee0c13
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 72%

---


# 关于使用 IBL 舞台{#about-working-with-ibl-stages}

AEM 3D 支持基于图像的照明 (IBL)，以便使用内置的 Adobe Rapid Refine™ 渲染器和第三方渲染器进行交互式查看和渲染。您可以使用常见创作工具（如Autodesk® Maya®或Autodesk® 3ds Max®）创建IBL舞台。

## 用于 IBL 的图像 {#images-for-ibl}

用于基于图像的照明的图像应具有 HDR（高动态范围），这样才能获得最佳效果。它们必须采用纬度/经度格式，并且具有覆盖整个环境范围的球面映射。

目前，AEM 3D 仅支持 32 位 TIFF。如有必要，请使用 Adobe Photoshop 或类似工具在 Adobe Photoshop TIFF 导出对话框中采用以下设置将 HDR 图像转换为 TIFF：

* **[!UICONTROL 位深度]** - 32位（浮点）
* **[!UICONTROL 像素顺序]** -隔行(RGBRGB)
* **[!UICONTROL 图像压缩]** - LZW
* **[!UICONTROL 字节顺序]** - IBM PC

虽然通常情况下 IBL 舞台使用单个 HDR 图像便已足够，但 AEM 3D 允许使用最多三个不同的图像，从而增强对 IBL 效果的控制：

* **[!UICONTROL 扩散照明环境图像]** - 此类图像应当为 HDR 图像，但也可以相对较小，因为在将图像用于扩散照明之前，会对图像进行深度过滤。
* **[!UICONTROL 反射环境图像]** - 此类图像用于创建物体表面的反射。它可以是标准 8 位 RGB 图像，该图像的大小和分辨率提供所需的反射质量和锐化。如果指定了 HDR 图像，AEM 3D 会预先使用专有算法将其转换为 8 位 RGB。
* **[!UICONTROL 背景环境图像]** - 此类图像可用作背景。它可以是标准 8 位 RGB 图像，并且应当具有舞台背景所需的大小/分辨率/细节级别。如果指定了 HDR 图像，AEM 3D 会使用专有算法将其转换为 8 位 RGB。

>[!NOTE]
>该算法对某些IBL图像可能存在一定的困难。 该问题可能会导致预览或使用 Rapid Refine 进行渲染时背景过亮或过度饱和。在这种情况下，Adobe 建议您使用 Photoshop 或类似工具手动将 IBL 图像转换为 8 位 RGB 图像。然后，单独上传此图像并将其作为背景环境图像附加到舞台。扩散照明和反射环境图像必须始终为 32 位 TIFF。


## 调整 IBL 舞台外观 {#adjusting-the-ibl-stage-appearance}

您可以使用以下舞台属性来调整 IBL 舞台的外观：

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性</strong><br /> </td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>IBL Sun详细信息</td> 
   <td><p>允许您调整模拟太阳的补充光源的方向和强度。 <span class="diff-html-added">该光源增加照明亮度并使物体将投影投射到地面上。 使用 Rapid Refine 进行渲染时，支持使用 Google Chrome 预览投影；但是，目前不支持使用其他浏览器进行预览。</span></p> 
    <ul> 
     <li><strong>纬度</strong> -太阳光源的垂直位置(<code>0.0</code>-<code>1.0</code>)。<br /> 设置为 <code>0.0</code> 水平线(扩散照明环境图像的垂直中心); <code>1.0</code> 位于最高点(扩散照明环境图像的上边缘)。</li> 
     <li><strong>long</strong> —— 太阳光源的水平<code>0.0</code>位置(<code>1.0</code>-)。<br /> 设置为0.0时，左边对应； 1.0对应于扩散照明环境图像的右边缘。<br /> </li> 
     <li><strong>亮</strong> -太阳光源的亮度。 增加此值可使太阳光源变亮；减少此值可使太阳光源变暗。<br /> 关闭补充 <code>0</code> 照明并禁用投影的设置。 该参数不影响环境反射。<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>IBL相机高度</td> 
   <td>如果IBL背景在地平线附近出现扭曲，可以通过调整此属性来减少或消除扭曲。 <br /> </td> 
  </tr> 
  <tr> 
   <td>环境照明</td> 
   <td><p><span class="diff-html-added">可控制扩散照明。 如果扩散照明环境图像异常明亮或黑暗（例如夜景），您可能需要手动调整此属性以纠正照明亮度。</span></p> 
    <ul> 
     <li><strong>r、g、b</strong> —— 当前未使用。</li> 
     <li><strong>bright</strong> —— 亮 <span class="diff-html-added">度倍增器。 增加或减少此值可提高或降低总体照明强度（基本 IBL 照明和太阳光源的亮度）。</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

