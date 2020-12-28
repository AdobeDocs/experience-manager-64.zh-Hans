---
title: 查看 3D 资产
seo-title: 查看 3D 资产
description: AEM 中的资产详细信息页面提供了交互式 3D 查看器。该查看器提供了各种控件，其中包括一组交互式相机控件，可让您对 3D 资产执行绕行、缩放和平移操作。
seo-description: AEM 中的资产详细信息页面提供了交互式 3D 查看器。该查看器提供了各种控件，其中包括一组交互式相机控件，可让您对 3D 资产执行绕行、缩放和平移操作。
uuid: 06dea4d6-c33a-45da-a9a7-7caae9d1717a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 5e1e0039-670e-4051-9f2a-e88162482467
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 65%

---


# 查看 3D 资产{#viewing-d-assets}

AEM 中的资产详细信息页面提供了交互式 3D 查看器。该查看器提供了各种控件，其中包括一组交互式相机控件，可让您对 3D 资产执行绕行、缩放和平移操作。

![chlimage_1-16](assets/chlimage_1-16.png)

除了在 AEM 3D 中使用默认舞台之外，您还可以使用在第三方应用程序中创建并上传到 AEM 的舞台。

请参阅[关于在 AEM 3D 中使用舞台](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)。

>[!NOTE]
>
>要查看 3D 资产，您的设备或桌面浏览器必须已启用 WebGL。此外，基础图形硬件必须具有足够的功能和内存来渲染所需大小的模型。

## 查看 3D 资产时的性能注意事项  {#performance-considerations-when-you-view-d-assets}

在资产详细信息页面视图中打开 3D 资产所用的时间取决于多个因素。这些因素包括如下几项：

* 服务器的带宽和延迟。
* 模型大小（人脸数量）。
* 映射的数量和大小。
* 舞台的复杂性。例如，IBL 图像的大小。

此外，在以交互方式操作相机时，还要考虑客户端计算机（如工作站、笔记本或移动触控设备）的功能。 具备良好图形功能的相当强大的系统可以使交互式 3D 查看体验更流畅、更舒适。

**要视图3D资产**:

1. 确保您已将 3D 资产上传到 AEM。

   请参阅[关于 AEM 中 3D 资产的上传和处理](/help/sites-classic-ui-authoring/classicui-upload-proc-3d.md)。
1. 在 **[!UICONTROL Adobe Experience Manager]** 中的&#x200B;**[!UICONTROL 导航]**&#x200B;页面上，点按&#x200B;**[!UICONTROL 资产]**。
1. 在页面的右上角附近，从&#x200B;**[!UICONTROL 视图]**&#x200B;下拉列表中，点按&#x200B;**[!UICONTROL 卡视图]**。

1. 导航到要查看的 3D 资产。
1. 点按3D资产的卡片，以在资产详细信息页面中将其打开。

1. 执行以下操作之一：

   * 在资产详细信息页面的右下角，使用相机控件调板更改资产的各种视图。

      如果您使用的是没有滚轮的非触控输入设备（例如经典的 Apple 单键鼠标），您仍可以在各种模式下更改 3D 资产的缩放级别或透视效果。通过在按住 `SHIFT` 键的同时按下鼠标按钮并向上或向下拖动，可以完成该操作。

      使用典型笔记本电脑上的触控板时，通常很难用双指手势来控制缩放或透视行为。在这种情况下，您可以在操作过程中按住 `SHIFT` 键。这样可以降低捏合手势的速度，并使您可以更轻松地达到所需的确切缩放级别或透视效果。或者，在按`SHIFT`键时，您可以使用单指向上或向下拖动，以影响缩放或透视行为。
   <table> 
    <tbody> 
      <tr> 
      <td><strong>相机控件名称</strong><br /> </td> 
      <td><strong>描述</strong></td> 
      </tr> 
      <tr> 
      <td><p>缩放</p> <p>或</p> <p>佩尔普</p> </td> 
      <td><p>点按或单击可在缩放和透视模式之间切换。</p> <p>或者，在操作过程中按住<code>ALT/OPTION</code>键可临时切换至“透视<br />”模式。 松开该键可恢复到“缩放”模式。</p> 
        <ul> 
        <li><strong>缩放</strong>-将相机移近或远离您所查看资产的<br /> 多利移入和移出行为。缩放是鼠标滚轮（如果可用）、移动设备上的双指捏合手势，或者在按住 Shift 键的同时使用鼠标左键向上或向下拖动时的默认行为。</li> 
        <li><strong>透视</strong>-更改相机的焦距(也称为视图场)，同时保持视图中资产的相对大小。透视是鼠标滚轮（如果可用）、移动设备上的双指捏合手势，或者在按住 Shift 键的同时使用鼠标左键向上或向下拖动时的替换行为。</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td><p>绕行</p> <p>或</p> <p>平</p> </td> 
      <td><p>点按或单击可在“绕行”和“平移”模式之间切换。</p> <p>或者，在操作过程中按住<code>ALT/OPTION</code>键可暂时切换到“平移”模式。 松开该键可恢复到“绕行”模式。</p> 
        <ul> 
        <li><strong>绕行</strong>-在以目标点为中心的球体上移动查看摄像机，该点默认位于3D资产的中心附近。绕行是鼠标左键拖动或移动设备上的单次触摸拖动的默认行为。</li> 
        <li><strong>平移</strong>-在查看平面中移动相机。目标点会相应移动，这样随后的绕行操作将会使相机围绕新的目标点移动。平移是鼠标左键拖动和单次触摸拖动的替换行为。</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td><p>检查</p> <p>或</p> <p>目标</p> </td> 
      <td><p>点按或单击可在检查模式和目标模式之间切换。</p> 
        <ul> 
        <li><strong>检查</strong>-点按或单击进入目标模式。</li> 
        <li><strong>目标</strong>-点按或单击3D资产上任意位置的点，以将视图放在资产该部分的中心。<br /> 绕行操作使用新的目标点。</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td>重置</td> 
      <td>点按或单击以将视图目标点恢复到模型的中心。 重置还会使相机<br />更近或更远地移开，以便以合理的查看大小完整地显示资产。</td> 
      </tr> 
    </tbody> 
    </table>

1. 在资产详细信息页面的右上角附近，点按&#x200B;**[!UICONTROL 舞台选择器]**&#x200B;图标。 选择要应用于 3D 资产的包含背景和灯光的舞台名称。

   ![](do-not-localize/chlimage_1-2.png)

   舞台提供查看3D模型的环境背景、地平面和照明。

   请参阅[关于在 AEM 3D 中使用舞台](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)。

1. 在资产详细信息页面的右上角附近，点按&#x200B;**[!UICONTROL 相机选择器]**&#x200B;图标，然后选择要应用于3D资产的相机视图。

   ![](do-not-localize/chlimage_1-3.png)

   舞台通常会提供预定义相机。您可以重新选择当前相机以将其恢复到预定义设置。

   请参阅[关于在 AEM 3D 中使用舞台](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)。

1. 在该页面的右上角，点按&#x200B;**[!UICONTROL 保存]**。
1. 执行下列操作之一：

   * 渲染 3D 资产。

      请参阅[渲染 3D 资产](/help/sites-classic-ui-authoring/classicui-rendering-3d.md)。

   * 在该页面的右上角，点按&#x200B;**[!UICONTROL 关闭]**&#x200B;以返回到“资产”页面。

