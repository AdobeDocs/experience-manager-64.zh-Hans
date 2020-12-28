---
title: 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台
seo-title: 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台
description: 了解如何使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台。
seo-description: 了解如何使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台。
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 75%

---


# 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. 在 Maya 中，创建一个新的空白场景。

1. 创建代表性模型的一个（临时）引用。此操作有助于评估照明、设置相机和配置渲染器。
1. 设置基于图像的照明。

   1. 在“渲染设置”中，选择&#x200B;**[!UICONTROL 渲染使用: mental ray]**，然后打开“场景”选项卡。****
   1. 打开&#x200B;**[!UICONTROL 环境]**&#x200B;折叠面板，然后单击&#x200B;**[!UICONTROL 创建基于图像的照明]**。
   1. 单击框左侧带有向右箭头的框图标以选择IBL节点`mentalRayIblShape1`，然后退出[!UICONTROL 渲染设置]。
   1. 在&#x200B;**[!UICONTROL 属性编辑器]**&#x200B;中，选择转换节点`mentalRayIbl1`，然后将转换节点重命名为`AdobeIbl`。

   1. 设置节点的[!UICONTROL 缩放]，使环境球显着大于要用此舞台显示的最大3D对象（例如`10000,10000,10000`）。
   1. 选择 `AdobeIblShape` 节点并对其进行如下配置：

      * **[!UICONTROL 映射]** - 球形
      * **[!UICONTROL 类型]** - 图像文件
      * **[!UICONTROL 发光]** - true
   1. 将所需的32位TIFF图像附加到`AdobeIbl`节点。


1. 设置地平面。

   * 创建一个合适的平面用作地平面，并调整其大小以使其适合 IBL 球，同时穿过坐标原点。
   * 将&#x200B;**[!UICONTROL Use Background]**&#x200B;材料连接到地平面，并将其命名为`AdobeUseBackground`，然后将其连接到地平面对象。

1. （可选）创建并配置相机。

   让相机对着将插入资产的场景中心。请确保您将相机设置为可渲染。

1. 使用 Mental Ray 设置渲染。

   根据以下建议配置[!UICONTROL 渲染设置]。

   * **[!UICONTROL 公用选]** 项卡

      取消选中所有可渲染相机的&#x200B;**[!UICONTROL Alpha渠道（遮罩）]**&#x200B;复选框。

   * **[!UICONTROL “质量”选项卡]**

      * **[!UICONTROL 总体质量]** - `0.5` 或更少
      * **[!UICONTROL 间接扩散(GI)模式]** -  `Final Gather`
      * **[!UICONTROL 滤镜大小]** - `2.0`,  `2.0`
   * 以您希望使用的典型图像大小渲染场景。如果需要，优化灯光或优化渲染设置，或者同时执行这两项操作，以便达到所需的效果。

      请注意，通过 Mental Ray 使用基于图像的照明进行渲染时，速度会非常缓慢且会消耗大量 CPU。Adobe 建议您配置最低质量设置，该设置仍能生成所需的渲染质量。


1. 删除您在步骤 2 中创建的引用。

1. 保存场景，然后退出 Autodesk Maya。

1. 将场景和 IBL PTIFF 上传到 AEM 并等待上传处理完成。

   请参阅[上传资产](/help/assets/managing-assets-touch-ui.md#uploading-assets)。

1. 解析任何文件依赖关系。

   请参阅[解析文件依赖关系](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md)。

   AEM 3D 可能检测不到舞台中已配置的 IBL 图像。在这种情况下，您必须手动解析缺失的依赖关系。您可以为每个缺失的依赖关系分配先前上传的相同 IBL PTIFF 图像。或者，您也可以分配不同的图像以进一步控制 IBL 效果。解析依赖关系后，请确保点按&#x200B;**保存**&#x200B;以启动重新处理。

1. 在 AEM 中打开资产属性。将“标题”设置为将在“舞台选择器”下拉列表中显示的合适字符串。确认将&#x200B;**[!UICONTROL 类]**&#x200B;设置为 **[!UICONTROL 3D 舞台]**。保存并退出。

1. 打开一个 3D 资产，选择新舞台，并验证它是否按预期方式进行预览和渲染。

