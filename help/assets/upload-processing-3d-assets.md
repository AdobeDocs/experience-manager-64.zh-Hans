---
title: 关于 AEM 中 3D 资产的上传和处理
seo-title: 关于 AEM 中 3D 资产的上传和处理
description: 上传和处理3D资产的最佳实践。
seo-description: 上传和处理3D资产的最佳实践。
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 69%

---


# 关于 AEM 中 3D 资产的上传和处理 {#about-the-uploading-and-processing-of-d-assets-in-aem}

可使用标准上传或同步机制将 3D 资产及其关联的引用文件纳入 AEM Assets。

请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

Adobe建议您在上传主3D模型文件之前或同时上传所有引用的文件。 但是，这并不作为一项要求。

上传完成后，您的 3D 文件会进行转换，并且还会应用其他处理以准备好资产进行查看和渲染。

## 上传 3D 资产的最佳实践 {#best-practices-for-uploading-d-assets}

* 通常，不会限制您在 AEM Assets 文件夹层次结构中上传 3D 内容的位置。但是，AEM 3D 的自动文件依赖关系解析存在范围限制，以便控制搜索大型资产存储库所需的时间。因此，Adobe 建议您在上传 3D 资产及其文件依赖项时，应在合理的范围（通用祖父文件夹）内对每个文件执行此操作。解析文件依赖关系后，您可以将 3D 资产及其依赖项随意移动到存储库中的任意位置，而不会丢失已建立的关系。
* Adobe 建议您在上传&#x200B;*之前*&#x200B;为 3D 内容确定一致的文件夹结构。下面的提示建议了一些您可以采取的方法：

   * **为您上传的每个 3D 资产建立一个单独的文件夹**。

      该文件夹包含主 3D 模型文件及其所有依赖项。将所有资产和依赖项放在一个文件夹中很容易实现，但浏览其内容却很麻烦。这样也难以在各模型之间共享依赖项（纹理映射）。

   * **将模型保存在一个文件夹中，将依赖项保存在同级文件夹或子文件夹中**。

      这种方法为在各模型之间共享依赖项提供了有利支持。但是，如果资产数量较大，查找特定的依赖项就会比较困难。

   * **为模型和依赖项分别提供独立的并行文件夹层次结构**。

      您可以采用这种方法来模拟 3D 创作应用程序（如 Autodesk Maya）存储内容的首选方式。

* 除非所依赖资产的关联 3D 资产或引用它们的资产也被删除，否则不应删除所依赖的资产。但是，您可以随意删除 3D 资产，而无需删除其依赖的资产。如果意外丢失了依赖关系，您可以轻松解析该依赖关系来进行恢复。

   请参阅解析文件依赖关系。

## 上传 3D 文件时的性能注意事项 {#performance-considerations-when-uploading-d-files}

通常，转换和处理 3D 文件会消耗服务器上的大量 CPU 和内存资源。此操作还会花费大量时间。处理时间通常会根据模型的大小和服务器的功能而大不相同。例如，少于 10 万个人脸的典型小模型通常在不到一分钟内便可进行查看；在 2-3 分钟内即可完全处理。然而，拥有超过一百万个人脸的大模型则可能需要几十分钟才能完全处理。

转换、处理和渲染作业会按需要排队，以防止严重减缓服务器速度。The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. 此状态表示必须先完成其他处理或渲染作业，才会处理当前资产。

机制可用于限制CPU用于摄取处理和渲染。 有关 [如何配置](advanced-config-3d.md) CPU限制的信息，请参阅高级配置设置。

## 监测您上传的 3D 文件的处理状态 {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. 每个上传的3D模型通常经历以下4-6个有序处理阶段：

<table> 
 <tbody> 
  <tr> 
   <td><strong>处理阶段</strong><br /> </td> 
   <td><strong>处理名称</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>正在处理</td> 
   <td>基本的初始处理和元数据提取。</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>转换格式</td> 
   <td>3D模型正从本机格式（Autodesk® Maya®或Autodesk® 3ds Max®）转换为中间格式(FBX)。</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>创建预览</td> 
   <td>摄取并处理FBX或OBJ文件。 在可能的情况下，对文件依赖关系进行评估并将其解析为资产引用。</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>创建地阴影</td> 
   <td>可选。允许您在3D对象下方的地面上生成环境遮挡投影。 请参 <a href="/help/assets/advanced-config-3d.md">阅高级配置设置</a> ，以启用或禁用此处理。</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>创建光照图</td> 
   <td>可选。允许您提高交互式预览的质量，并快速使用默认渲染器进行渲染。请参 <a href="/help/assets/advanced-config-3d.md">阅高级配置设置</a> ，以启用或禁用此处理。</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>创建动画</td> 
   <td>可选。允许您渲染一个简单的动画，之后，将该动画用作卡片视图中的可视缩略图。请参 <a href="/help/assets/advanced-config-3d.md">阅高级配置设置</a> ，以启用或禁用此处理。</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>等待处理</td> 
   <td>当其他3D资产具有处理优先级时显示。 例如，存在之前已上传但尚未完成处理的资产时。</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. 您无需等待所有处理阶段完成。

