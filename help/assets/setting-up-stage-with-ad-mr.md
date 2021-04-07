---
title: 使用 Autodesk Maya 和 Mental Ray 设置标准舞台
seo-title: 使用 Autodesk Maya 和 Mental Ray 设置标准舞台
description: 如何使用Autodesk Maya和Mental Ray设置标准舞台
seo-description: 如何使用Autodesk Maya和Mental Ray设置标准舞台
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
exl-id: facd0411-8a3c-4b1a-af9d-0d59e0399b2c
feature: 3D资产
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 77%

---

# 使用 Autodesk Maya 和 Mental Ray 设置标准舞台 {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. 在 Maya 中，创建一个新的空白场景。
1. 创建代表性模型的一个（临时）引用。此操作有助于评估照明、设置相机和配置渲染器。

1. 按常规方式添加灯光。目前，AEM 3D 支持以下灯光类型：

   * 平行光
   * 聚光灯光
   * 点光

   将舞台上传到 AEM 3D 时，其他灯光类型会被忽略或转换为以上支持的类型之一。查看资产和使用内置的 Rapid Refine 渲染器进行渲染时，会使用转换后的类型。使用Maya进行渲染时，会使用原始灯光类型。

1. 如果需要，创建一个地平面，并应用合适的材料。

   Adobe 建议您将地平面设置为单面。这样做可确保您能够在AEM 3D中从下方视图资产，而地平面不会隐藏资产。

1. （可选）创建并配置相机。

   让相机对着将插入资产的场景中心。请确保您将相机设置为可渲染。

1. 使用 Mental Ray 设置渲染。

   根据以下建议配置渲染设置：

   * **[!UICONTROL “公用”]** 选项卡

      取消选中所有可渲染相机的&#x200B;**[!UICONTROL Alpha渠道（蒙版）]**&#x200B;复选框。

   * **[!UICONTROL “质量”选项卡]**

      * **[!UICONTROL 整体]** `- 0.5` 质量或更低
      * **[!UICONTROL 间接扩散(GI)模式]** -  `Final Gather`
      * **[!UICONTROL 滤镜大小]** -  `2.0`、  `2.0`
   * 以您希望使用的典型图像大小渲染场景。如果需要，优化灯光或优化渲染设置，或者同时执行这两项操作，以便达到所需的效果。

      请注意，通过 Mental Ray 使用基于图像的照明进行渲染时，速度会非常缓慢且会消耗大量 CPU。Adobe 建议您配置最低质量设置，该设置仍能生成所需的渲染质量。


1. 删除您在步骤 2 中创建的引用。

1. 保存场景，然后退出 Autodesk Maya。
1. 将场景上传到 AEM 并等待上传处理完成。

   请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

   如果未在 AEM 服务器上配置 Autodesk® Maya®，请从 Maya 中导出 FBX，然后再将其上传到 AEM。

1. 在 AEM 中打开资产属性。将&#x200B;**[!UICONTROL Title]**&#x200B;设置为将在&#x200B;**[!UICONTROL 舞台选择器]**&#x200B;下拉列表中显示的适当字符串。 确认将&#x200B;**[!UICONTROL 类]**&#x200B;设置为 **[!UICONTROL 3D 舞台]**。保存并退出。
1. 打开一个 3D 资产，选择新舞台，并验证它是否按预期方式进行预览和渲染。
