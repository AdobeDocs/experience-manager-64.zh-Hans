---
title: 使用AEM 3D资源
seo-title: 使用 3D 资产
description: 了解如何在AEM 3D中使用3D资源
seo-description: 了解如何在AEM 3D中使用3D资源
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 5%

---


# 使用AEM 3D资源{#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 6.4中不再支持AEM 3D。 Adobe建议您将[AEM中的3D资产功能用作Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)或[AEM 6.5.3或更高版本。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

通过 AEM 3D (Adobe Experience Manager 3D)，您可以上传、管理、查看和渲染 3D 内容。单个对象的查看和渲染支持已得到优化。

另请参阅 [AEM 3D 发行说明](/help/release-notes/aem3d-release-notes.md)。

另请参阅[安装和配置 AEM 3D](install-config-3d.md)。

## 关于AEM 3D {#about-models-and-stages-in-aem-d}中的模型和舞台

AEM 3D允许您在称为舞台的预定义环境中视图和渲染高质量的独立静态3D模型。 基本上，舞台为3D场景提供“照明”以及在本机应用程序（如Autodesk® Maya®或Autodesk 3ds Max®）中进行渲染的设置。 此外，舞台可以选择地包括预定义的相机、背景和地平面几何。

上传的包含光照的3D文件假定为舞台。 您可以通过在资产详细信息页面中打开资产，将此类资产还原为简单的3D对象。 点按&#x200B;**[!UICONTROL 视图属性]**，然后点按&#x200B;**[!UICONTROL 基本]**&#x200B;选项卡。 在元数据标题下的资产类下拉列表下，选择&#x200B;**[!UICONTROL 3D对象]**。

创建要用于AEM 3D的3D模型时，请注意以下事项：

* 您的3D模型文件应仅包含一个对象，没有背景、地平面、场景照明或摄像机。
* 将模型放在地平面上方。 当用提供地平面的舞台视图或渲染时，此位置尤其重要。 配置设置可用（默认情况下为启用），当使用Rapid Refine预览或渲染时，该设置会使对象移动到地平面上方。 此设置不影响使用第三方渲染器进行渲染（例如，通过Maya），因此未位于地平面上方的对象可能会部分隐藏。
* 定位模型，使其在横向上以坐标系来源(0,0,0)合理居中。 这样做可确保您获得良好的交互式查看体验。
* 除纹理映射外，还支持外部文件引用。 因此，在将主模型文件上传到AEM之前，必须将任何引用内容嵌入主模型文件。

   请参阅[关于 AEM 中 3D 资产的上传和处理](upload-processing-3d-assets.md)。

* 一般场景照明由舞台提供。 因此，Adobe不建议您在3D模型文件中包含光。 可在模型中包含灯。 但是，它们必须只针对模型。 例如，可能需要包括额外的照明，以使被其他部分遮住的对象的一部分变亮。 因此，光是舞台灯就看不见了。

## AEM 3D {#supported-files-in-aem-d}中支持的文件

典型的3D资产具有主模型文件，且没有或更多引用文件。 引用的文件包括纹理映射或&#x200B;**IBL（基于图像的照明）**&#x200B;图像。

### 关于主3D模型文件{#about-the-primary-d-model-file}

主3D模型文件包含实际的3D模型几何和应用于模型曲面的（缺省）材料的定义。 AEM 3D支持以下主要3D模型文件格式：

* Wavefront OBJ文件格式(`.obj`)

   OBJ格式需要一个或多个单独的外部MTL文件（材料模板库）(`.mtl`)。

* Autodesk FBX(Filmbox)文件格式(`.fbx`)

   Autodesk 3D文件交换格式；二进制和ASCII格式。

   在第三方应用程序中创建FBX文件时，Adobe建议使用以下配置设置（请参阅下表）。 这些设置可以帮助您为要在AEM中使用的3D文件获得最佳效果。 选项名称取自&#x200B;**[!UICONTROL Autodesk Maya FBX Export Options]**&#x200B;对话框。

<table> 
 <tbody> 
  <tr> 
   <td><strong>“Autodesk Maya FBX Export”对话框中的选项</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>保留引用<br /> </td> 
   <td><p>取消选择.</p> <p>AEM 3D当前不支持外部引用。</p> </td> 
  </tr> 
  <tr> 
   <td>平滑网格<br /> </td> 
   <td>选择.</td> 
  </tr> 
  <tr> 
   <td>将NURBS曲面转换为</td> 
   <td><strong>软件渲染网格</strong></td> 
  </tr> 
  <tr> 
   <td>动画</td> 
   <td><p>选择或取消选择。</p> <p>如果选择选择此选项，AEM 3D将忽略文件中的动画信息。</p> </td> 
  </tr> 
  <tr> 
   <td>相机</td> 
   <td><p>选择<strong>3D舞台</strong>。</p> <p>取消选择3D模型。</p> </td> 
  </tr> 
  <tr> 
   <td>灯光</td> 
   <td><p>选择<strong>3D舞台</strong>。</p> <p>取消选择<strong>3D模型</strong>。</p> </td> 
  </tr> 
  <tr> 
   <td>单位——自动</td> 
   <td>选择. AEM 3D在导入时转换。</td> 
  </tr> 
  <tr> 
   <td>轴转换——向上轴</td> 
   <td><p><strong>Y-up</strong></p> <p>从Maya导出时，Y-up会产生一致的结果，是此AEM 3D版本中FBX文件的首选坐标系。</p> </td> 
  </tr> 
  <tr> 
   <td>嵌入媒体</td> 
   <td>两个选项都受支持。 如果选择了“嵌入”,AEM 3D会将嵌入的媒体提取到与模型文件同名的相邻文件夹，并附加<code>.fbm</code>。</td> 
  </tr> 
  <tr> 
   <td>FBX文件格式——类型</td> 
   <td>支持二进制<strong>或<strong>ASCII </strong>。</strong></td> 
  </tr> 
  <tr> 
   <td>FBX文件格式——版本</td> 
   <td>建议使用FBX 2014/2015。 其他版本也可能运行正常。</td> 
  </tr> 
 </tbody> 
</table>

如果在AEM创作服务器上安装和配置Autodesk Maya，则支持以下其他文件格式：

* 玛雅汽车台

   ASCII `.ma`和二进制`.mb`格式。

* `Jupiter Tesselation (ISO 14306-1).jt`。

   行业标准的CAD数据交换、协作和产品可视化格式。

### 支持纹理映射文件{#support-for-texture-map-files}

3D模型文件中的材料定义可以包括对提供纹理映射的外部图像文件的引用。 AEM 3D支持以下类型的纹理映射文件：

* 扩散颜色纹理
* 镜面颜色纹理
* 环境颜色纹理
* 位移图（也称为凹凸图）
* 标准地图
* 不透明度映射
* 粗糙度图（也称为“光泽”、“反射率”或“余弦功率图”）

主3D模型文件中的材料可以引用AEM 3D忽略的其他类型的映射。

### IBL（基于图像的照明）图像{#ibl-image-based-lighting-images}

定义舞台的3D模型文件可以引用单个IBL环境图像。 目前，AEM 3D仅支持经纬度格式的32位TIFF图像，用于扩散IBL和反射。 对于球面场景背景，还支持8位RGB图像。

请参阅[关于使用IBL阶段](working-with-ibl-stages.md)。

>[!NOTE]
>
>当前忽略主3D模型文件中存在的文件参照（上述参照除外）。 AEM 3D不支持对辅助3D模型文件的引用。
Y-up是此版本FBX文件的首选坐标系。

## 主3D模型文件{#material-shading-in-a-primary-d-model-file}中的材料底纹

原始本机模型文件可包含与着色器（如Blinn、Lambert或过程式着色器）一起使用的材料定义。 仅当您使用相应的本机应用程序（如Autodesk Maya）进行渲染时，才支持这些可能复杂的材料。

出于查看目的，或者当您使用默认的Rapid Refine™渲染器进行渲染时，所有材料都会被简化、替换，或者两者同时使用，以便与类似Phong的着色器一起使用。 此着色器支持有限的属性集。 忽略材料定义中的其他属性。

请参阅[查看 3D 资产](viewing-3d-assets.md)。

请参阅[渲染 3D 资产](rendering-3d-assets.md)。

## 在主3D模型文件{#naming-materials-in-a-primary-d-model-file}中命名材料

*表面*&#x200B;定义为由相同材料覆盖的3D模型的表面区域。 此材料还提供曲面的名称。 因此，Adobe建议您相应地命名主3D模型文件中包含的材料。 例如，使用“Body”、“Windows”、“Tires”或“Rims”等特定名称比使用“Red”、“Glass”、“Rubber”、“Alumin”等模糊名称更为可取。

