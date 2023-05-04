---
title: 图像编辑器
seo-title: Image Editor
description: 图像编辑器是AEM的核心部分，可由组件使用，以便于内容作者处理图像。
seo-description: The Image Editor is a core piece of AEM and can be leveraged by components to facilitate the manipulation of images by content authors.
uuid: de6ac71b-380a-4b67-b697-ac34a79a9cc4
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: components
discoiquuid: f6347492-cf48-4835-b8fd-ce9a75a09abe
exl-id: 843c67d6-dda1-448f-a992-19574066e1c3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 14%

---

# 图像编辑器{#image-editor}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

图像编辑器是AEM的核心部分，可由组件使用，以便于内容作者处理图像。

>[!CAUTION]
>
>要使用本文中描述的图像编辑器功能， [功能包24267](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) 必须安装。

## 图像映射的相对单位 {#relative-units-for-image-map}

图像编辑器将图像映射区域保留为绝对和相对单位。 当提供相对单位作为数据属性时，用于在响应式图像组件的客户端上动态地调整图像映射（相对于图像大小）的大小。

### imageMap属性 {#imagemap-property}

图像映射坐标将作为 `imageMap` 属性。 其格式如下。

资产会按如下方式存储地图区域：

`[area1][area2][...]`

区域格式：

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

示例:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## 支持SVG图像 {#support-for-svg-images}

图像编辑器支持可缩放矢量图形(SVG)。

* 从 DAM 拖放上传 SVG 资源以及从本地文件系统上传 SVG 文件均受支持。

## 按MIME类型启用插件 {#enabling-plugins-by-mime-type}

在某些情况下，由于服务器端处理中不支持，因此必须限制某些MIME类型的创作操作。 例如，可能不允许编辑SVG图像。

可以通过设置 `supportedMimeTypes` 属性。

### 示例 {#example}

例如，应当仅允许对GIF、JPEG、PNG、WEBP和TIFF图像进行裁剪。

的 `supportedMimeTypes` 属性后，必须在 `cq:editConfig` 图像组件的节点。

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
