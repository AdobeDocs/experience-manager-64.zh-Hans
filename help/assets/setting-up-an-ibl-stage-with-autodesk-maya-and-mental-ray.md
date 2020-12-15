---
title: 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台
seo-title: 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台
description: 如何使用Autodesk Maya和Mental Ray设置IBL舞台
seo-description: 如何使用Autodesk Maya和Mental Ray设置IBL舞台
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 70%

---


# 使用 Autodesk Maya 和 Mental Ray 设置 IBL 舞台 {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. 在 Maya 中，创建一个新的空白场景。

1. 创建代表性模型的一个（临时）引用。此操作有助于评估照明、设置相机和配置渲染器。
1. 设置基于图像的照明。

   1. 在&#x200B;**[!UICONTROL 渲染设置]**&#x200B;中，选择&#x200B;**[!UICONTROL 渲染使用：mental ray]**，然后打开“场景”选项卡。
   1. 打开&#x200B;**[!UICONTROL 渲染环境]**&#x200B;折叠面板，然后单击&#x200B;**[!UICONTROL 渲染创建基于图像的照明]**。
   1. 单击框左侧带有向右箭头的框图标以选择IBL节点`mentalRayIblShape1`，然后退出&#x200B;**[!UICONTROL 渲染设置]**。
   1. 在&#x200B;**[!UICONTROL 属性编辑器]**&#x200B;中，选择转换节点`mentalRayIbl1`，然后将转换节点重命名为`AdobeIbl`。
   1. 设置该节点的缩放比例，以使环境球显著大于要使用此舞台显示的最大 3D 对象（例如，`10000,10000,10000`）。
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

   根据以下建议配置&#x200B;**[!UICONTROL 渲染设置]**。

   * **[!UICONTROL 公用选]** 项卡

      取消选中所有&#x200B;**[!UICONTROL 可渲染相机]**&#x200B;的&#x200B;**[!UICONTROL Alpha渠道（遮罩）]**&#x200B;复选框。

   * **[!UICONTROL “质量”选项卡]**

      * **总体质量** - `0.5` 或更少
      * **间接扩散(GI)模式** -  `Final Gather`
      * **滤镜大小** - `2.0`,  `2.0`
   * 以您希望使用的典型图像大小渲染场景。如果需要，优化灯光或优化渲染设置，或者同时执行这两项操作，以便达到所需的效果。

      请注意，通过 Mental Ray 使用基于图像的照明进行渲染时，速度会非常缓慢且会消耗大量 CPU。Adobe 建议您配置最低质量设置，该设置仍能生成所需的渲染质量。


1. 删除您在步骤 2 中创建的引用。

1. 保存场景，然后退出 Autodesk Maya。

1. 将场景和 IBL PTIFF 上传到 AEM 并等待上传处理完成。

   请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

1. 解析任何文件依赖关系。

   请参阅[解析文件依赖关系](resolve-file-dependencies.md)。

   AEM 3D 可能检测不到舞台中已配置的 IBL 图像。在这种情况下，您必须手动解析缺失的依赖关系。您可以为每个缺失的依赖关系分配先前上传的相同 IBL PTIFF 图像。或者，您也可以分配不同的图像以进一步控制 IBL 效果。解析依赖关系后，请确保点按&#x200B;**[!UICONTROL 保存]**&#x200B;以启动重新处理。

1. 在 AEM 中打开资产属性。将&#x200B;**[!UICONTROL Title]**&#x200B;设置为将在&#x200B;**[!UICONTROL 舞台选择器]**&#x200B;下拉列表中显示的合适字符串。 确认将&#x200B;**[!UICONTROL 类]**&#x200B;设置为 **[!UICONTROL 3D 舞台]**。保存并退出。

1. 打开一个 3D 资产，选择新舞台，并验证它是否按预期方式进行预览和渲染。

