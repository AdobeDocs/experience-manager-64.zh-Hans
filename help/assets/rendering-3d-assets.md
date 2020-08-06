---
title: 渲染 3D 资产
seo-title: 渲染 3D 资产
description: 了解如何渲染您在AEM中处理和保存的3D资源，以创建网页的2D图像。
seo-description: 了解如何渲染您在AEM中处理和保存的3D资源，以创建网页的2D图像。
uuid: ee4d669c-72b1-4f7a-9a68-a7c6d59c7856
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5b044519-d034-4f05-98c5-f1b299a3ea37
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 65%

---


# 渲染 3D 资产 {#rendering-d-assets}

您可以渲染在 AEM 中处理并保存的 3D 资产，从而创建 2D 图像，以供在 Web 内容页面上使用。

请参阅[编辑页面内容](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content)。

## 渲染 3D 资产时的性能注意事项 {#performance-considerations-when-rendering-d-assets}

渲染 3D 内容会消耗大量服务器资源，如 CPU 和内存。因此，渲染通常会花费大量时间。除了显而易见的模型大小和服务器硬件之外，渲染时间还会因各种因素而明显不同：

* **渲染器选择**。

   AEM 3D 中的默认 Rapid Refine™ 渲染器可在降低一定质量的基础上缩短渲染时间。不过，它仍为许多应用程序生成了高质量的渲染效果。通过第三方应用程序提供的渲染器（例如，在 Autodesk® Maya® 或 Autodesk® 3ds Max® 中部署的 V-Ray™ 或 NVIDIA® Mental Ray®）可以广泛进行配置，并且在设计舞台时会在性能与质量之间加以权衡。

* **IBL 与传统灯光**。

   虽然此因素对于默认的 Rapid Refine 渲染器影响不大，但是对于第三方渲染器（例如 Mental Ray）而言，使用 IBL 舞台进行渲染的速度大大低于使用传统点光或聚光灯光进行渲染的速度。

Rapid Refine 渲染器通常需要数分钟才能渲染较大的图像。但是，第三方渲染器在配置为获取最高质量时，通常需要很多分钟，甚至长达数小时。

转换、处理和渲染作业会根据需要在服务器上排队，以防止服务器过载。卡片视图中最近上传的资产会显示消息“正在等待渲染...”。此状态表示必须完成其他处理或渲染作业，才能完成当前渲染作业开始。

>[!NOTE]
>
>无论 AEM 3D 交互式视图中显示哪些材料，3D 资产始终都会使用原始材料进行渲染。此功能适用于内置的 Rapid Refine 渲染器和所有本机渲染器。

**要渲染3D资产**:

1. 打开要查看的 3D 资产。

   请参阅[查看 3D 资产](viewing-3d-assets.md)。

1. 在 Adobe Experience Manager 中的&#x200B;**[!UICONTROL 导航]**&#x200B;页面上，点按&#x200B;**[!UICONTROL 资产]**。
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.
1. 导航到要渲染的3D对象。
1. 点按 3D 对象的卡片以在资产详细信息页面中打开它。
1. 在页面的左上角附近，点按下拉列表，然后选择&#x200B;**[!UICONTROL 渲染]**。

   ![chlimage_1-369](assets/chlimage_1-369.png)

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon (spotlight), then select a stage name with the background and lighting that you want to apply to the 3D object.

   请参阅[关于在 AEM 3D 中使用舞台](about-the-use-of-stages-in-aem-3d.md)。

   ![chlimage_1-370](assets/chlimage_1-370.png)

   **[!UICONTROL “舞台选择器”图标]**

1. On the **[!UICONTROL Render]** drop-down list on the left side of the asset details page, select a renderer.

   默认的 **Rapid Refine** 渲染器始终可用。如果您选择的舞台是本机格式，则相应的第三方渲染器也会显示在列表中以供您选择。

   请参阅[关于在 AEM 3D 中使用舞台](about-the-use-of-stages-in-aem-3d.md)。

1. 执行以下操作：

   * In the **[!UICONTROL Width]** and **[!UICONTROL Height]** fields, enter the pixel width and height that you want your image rendered.
   * In the **[!UICONTROL Image Name]** field, enter the name of the rendered image.
   * In the **[!UICONTROL Export Path]** field, enter the path where you want the rendered image stored. Or, tap the **[!UICONTROL Browse]** icon and navigate to a location.
   * (Optional) Select or deselect the **[!UICONTROL Overwrite existing imag]e **check box.

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon. 选择要对渲染后的图像应用的相机视图。

   左侧栏和右侧栏或顶部栏和底部栏是一个可视指示器，以指示将渲染的视图部分。当相机由选定的舞台提供时，您可以选择预定义的相机。

   ![chlimage_1-371](assets/chlimage_1-371.png)

   **[!UICONTROL “相机选择器”图标]**

1. 点按&#x200B;**[!UICONTROL 开始渲染]**&#x200B;以开始渲染过程。

   此时会临时显示一条消息，指示渲染已开始。为方便起见，此消息还包含指向所选输出文件夹的链接，以便您直接导航到该文件夹。

