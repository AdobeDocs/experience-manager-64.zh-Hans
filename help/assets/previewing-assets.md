---
title: 预览 Dynamic Media 资产
seo-title: 预览 Dynamic Media 资产
description: 了解如何在Dynamic Media中预览资源
seo-description: 了解如何在Dynamic Media中预览资源
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: 资产管理，演绎版
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 33%

---

# 预览 Dynamic Media 资产 {#previewing-assets}

您可以使用&#x200B;**[!UICONTROL 预览]**&#x200B;查看Dynamic Media数字资产在客户自己的Web浏览器中查看时的外观。 分配给资产的默认嵌入式跨设备查看器用于&#x200B;**[!UICONTROL 预览]**。

查看器是各种设置（或称“预设”，例如查看器的显示大小、缩放行为、颜色方案、边框、字体等）的集合，这些设置决定了用户在其计算机屏幕和移动设备上查看富媒体资产的方式。

除了对视频、旋转集和图像集使用专用的预览功能外，您还可以通过使用已创建的查看器预设来预览资产。或者，使用图像预设来预览图像的演绎版。

* [应用图像预设](image-presets.md)
* [应用查看器预设](viewer-presets.md)

>[!NOTE]
>
>当您位于AEM的网页（站点）上时，无法在编辑模式下预览 **[!UICONTROL 资产]** 。 您需要通过单击 **[!UICONTROL 右上角的]** “预 **览** ”来转到“预览”模式。

**要预览资产**:

1. 从&#x200B;**Adobe Experience Manager**&#x200B;的&#x200B;**[!UICONTROL 导航]**&#x200B;页面，点按&#x200B;**[!UICONTROL 资产]s**，然后点按&#x200B;**[!UICONTROL 文件]**&#x200B;以访问资产。
1. 在页面右上角附近，从&#x200B;**[!UICONTROL 视图]**&#x200B;下拉列表中，点按&#x200B;**[!UICONTROL 列表视图]**。
1. （可选）使用&#x200B;**[!UICONTROL 类型]**&#x200B;列按要预览的类型对资产进行排序。
1. 在&#x200B;**[!UICONTROL 标题]**&#x200B;列下，单击要预览的资产的标题名称（而非缩略图）。
1. 根据您单击的资产类型，执行下列任一操作：

<table> 
 <tbody>
  <tr>
   <td><strong>您点击的资产类型</strong><br /> </td> 
   <td><strong>是否能够预览特定演绎版中的资产？</strong></td> 
   <td><strong>是否能够在特定查看器中预览资产？</strong></td> 
  </tr>
  <tr>
   <td><p>图像</p> </td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>要预览特定演绎版中的资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>演绎版</strong>，然后选择要预览的特定演绎版。</li> 
    </ul> <p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>查看器</strong>，然后选择要应用到资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-</strong> 图标可分别增大和减小选定图像的缩放比例。单击<strong>重置</strong>可使图像恢复到原始缩放比例。
<br />如果您使用的是移动设备，请连按两次图像以逐步放大。当您达到最大缩放比例时，再连按两次图像可重置缩放状态。横向拖动图像可进行平移。
</p> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。<br /> </p> </td> 
  </tr>
  <tr>
   <td>多媒体</td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>要预览特定演绎版中的资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>演绎版</strong>，然后选择要预览的特定演绎版。</li> 
    </ul> <p>选择要预览的高分辨率视频演绎版可能会导致视频出现截断。 这是因为演绎版预览在用于预览的嵌入式查看器的上下文中向您显示了客户将看到的确切分辨率。</p> <p>当您在资产级别预览自适应视频集时，演绎版将分组为一个播放体验。 也就是说，自适应视频的大小调整为适合查看，并在查看设备和连接速度上下文中使用最佳分辨率进行回放。<br /> </p> <p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>查看器</strong>，然后选择要应用到资产的查看器。</li> 
    </ul> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。</p> </td> 
  </tr>
  <tr>
   <td>图像集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>查看器</strong>，然后选择要应用到资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-</strong> 图标可分别增大和减小选定图像的缩放比例。单击<strong>重置</strong>可使图像恢复到原始缩放比例。
<br />如果您使用的是移动设备，请连按两次图像以逐步放大。当您达到最大缩放比例时，再连按两次图像可重置缩放状态。横向拖动图像可进行平移。
</p> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。</p> </td> 
  </tr>
  <tr>
   <td>旋转集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>查看器</strong>，然后选择要应用到资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-</strong> 图标可分别增大和减小选定图像的缩放比例。单击<strong>重置</strong>可使图像恢复到原始缩放比例。
<br />如果您使用的是移动设备，请连按两次图像以逐步放大。当您达到最大缩放比例时，再连按两次图像可重置缩放状态。横向拖动图像可进行平移。
</p> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。</p> </td> 
  </tr>
  <tr>
   <td>混合媒体集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 单击列表中的<strong>查看器</strong>，然后选择要应用到资产的查看器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-</strong> 图标可分别增大和减小选定图像的缩放比例。单击<strong>重置</strong>可使图像恢复到原始缩放比例。
<br />如果您使用的是移动设备，请连按两次图像以逐步放大。当您达到最大缩放比例时，再连按两次图像可重置缩放状态。横向拖动图像可进行平移。
</p> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。</p> </td> 
  </tr>
  <tr>
   <td>旋转集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定查看器中预览资产</strong></p> 
    <ul> 
     <li>在页面的左上角附近，单击图标以显示下拉列表。 选择要应用于资产的查看器。</li> 
    </ul> <p>要在用户界面中启用或禁用查看器预设，请参阅<a href="/help/assets/managing-viewer-presets.md">管理查看器预设</a>。</p> </td> 
  </tr>
 </tbody>
</table>
