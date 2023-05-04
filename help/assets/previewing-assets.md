---
title: 预览 Dynamic Media 资产
seo-title: Previewing Dynamic Media assets
description: 了解如何在Dynamic Media中预览资产
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 5%

---

# 预览 Dynamic Media 资产 {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以使用 **[!UICONTROL 预览]** ，以了解客户在其Web浏览器中查看Dynamic Media数字资产时的外观。 为资产分配的默认嵌入式跨设备查看器将用于 **[!UICONTROL 预览]**.

查看器是各种设置或“预设”的集合，这些设置或“预设”（如查看器的显示大小、缩放行为、颜色方案、边框、字体等）决定了用户在其计算机屏幕和移动设备上查看富媒体资产的方式。

除了使用视频、旋转集和图像集的专用预览功能外，您还可以使用您创建的查看器预设来预览资产。 或者，使用图像预设来预览图像的演绎版。

* [应用图像预设](image-presets.md)
* [应用查看器预设](viewer-presets.md)

>[!NOTE]
>
>当您位于AEM的网页（站点）上时，无法在编辑模式下预览 **[!UICONTROL 资产]** 。 您需要通过单击 **[!UICONTROL 右上角的]** “预 **览** ”来转到“预览”模式。

**预览资产**:

1. 从 **Adobe Experience Manager**，在 **[!UICONTROL 导航]** 页面，点按 **[!UICONTROL 资产]s**，则 **[!UICONTROL 文件]** 以访问资产。
1. 在页面的右上角附近，从 **[!UICONTROL 查看]** 下拉列表中，点按 **[!UICONTROL 列表视图]**.
1. （可选）使用 **[!UICONTROL 类型]** 列，按要预览的类型对资产进行排序。
1. 在 **[!UICONTROL 标题]** 列中，单击要预览的资产的标题名称（而非缩略图图像）。
1. 根据您单击的资产类型，执行以下任一操作：

<table> 
 <tbody>
  <tr>
   <td><strong>您点按的资产类型</strong><br /> </td> 
   <td><strong>能否预览特定演绎版中的资产？</strong></td> 
   <td><strong>能否在特定查看器中预览资产？</strong></td> 
  </tr>
  <tr>
   <td><p>图像</p> </td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>预览特定演绎版中的资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>演绎版 </strong>从列表中，选择要预览的特定演绎版。</li> 
    </ul> <p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>查看器</strong> 从列表中，选择要应用于资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>图标，以分别增加或减少选定图像的缩放比例。 单击 <strong>重置</strong> 以将图像恢复为原始缩放。<br /> 如果您在移动设备上，请双击图像以逐步放大。 达到最大缩放时，再次双击图像以重置缩放状态。 在图像上拖动以进行平移。</p> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>多媒体</td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>预览特定演绎版中的资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>演绎版 </strong>从列表中，选择要预览的特定演绎版。</li> 
    </ul> <p>选择要预览的高分辨率视频演绎版可能会导致视频显示被截断。 这是因为演绎版预览在用于预览的嵌入式查看器的上下文中，向您显示了客户将看到的确切分辨率。</p> <p>在资产级别预览自适应视频集时，演绎版会分组到一个播放体验中。 也就是说，自适应视频的大小会被适当地调整，以便观看，并在观看设备和连接速度的上下文中使用最佳分辨率进行回放。<br /> </p> <p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>查看器</strong> 从列表中，选择要应用于资产的查看器。</li> 
    </ul> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.</p> </td> 
  </tr>
  <tr>
   <td>图像集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>查看器</strong> 从列表中，选择要应用于资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>图标，以分别增加或减少选定图像的缩放比例。 单击 <strong>重置</strong> 以将图像恢复为原始缩放。<br /> 如果您在移动设备上，请双击图像以逐步放大。 达到最大缩放时，再次双击图像以重置缩放状态。 在图像上拖动以进行平移。</p> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.</p> </td> 
  </tr>
  <tr>
   <td>旋转集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>查看器</strong> 从列表中，选择要应用于资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>图标，以分别增加或减少选定图像的缩放比例。 单击 <strong>重置</strong> 以将图像恢复为原始缩放。<br /> 如果您在移动设备上，请双击图像以逐步放大。 达到最大缩放时，再次双击图像以重置缩放状态。 在图像上拖动以进行平移。</p> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.</p> </td> 
  </tr>
  <tr>
   <td>混合媒体集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击 <strong>查看器</strong> 从列表中，选择要应用于资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>图标，以分别增加或减少选定图像的缩放比例。 单击 <strong>重置</strong> 以将图像恢复为原始缩放。<br /> 如果您在移动设备上，请双击图像以逐步放大。 达到最大缩放时，再次双击图像以重置缩放状态。 在图像上拖动以进行平移。</p> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.</p> </td> 
  </tr>
  <tr>
   <td>轮播集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 选择要应用于资产的查看器。</li> 
    </ul> <p>要在用户界面中启用或禁用查看器预设，请参阅 <a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>.</p> </td> 
  </tr>
 </tbody>
</table>
