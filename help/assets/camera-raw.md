---
title: Camera Raw支持
description: 了解如何在Adobe Experience Manager Assets中启用Camera Raw支持。
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---

# 使用Camera Raw处理图像 {#camera-raw-support}

您可以启用Camera Raw支持来处理原始文件格式（如CR2、NEF和RAF），并以JPEG格式渲染图像。 Adobe Experience Manager Assets使用Software Distribution提供的[Camera Raw包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg)支持该功能。

>[!NOTE]
>
>该功能仅支持JPEG呈现。 Windows 64位、Mac OS和RHEL 7.x均支持此功能。

要在Adobe Experience Manager Assets中启用Camera Raw支持，请执行以下步骤：

1. 从Software Distribution下载[Camera Raw包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg)。

1. 访问 `https://[aem_server]:[port]/workflow`. 打开&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流。

1. 打开&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤。

1. 在&#x200B;**[!UICONTROL 缩略图]**&#x200B;选项卡中提供以下配置：

   * **[!UICONTROL 缩略图]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL 跳过 MIME 类型]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![奇利马奇](assets/chlimage_1-334.png)

1. 在&#x200B;**[!UICONTROL Web启用图像]**&#x200B;选项卡的&#x200B;**[!UICONTROL 跳过列表]**&#x200B;字段中，指定`audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`。

   ![奇利马奇](assets/chlimage_1-335.png)

1. 从侧面板中，在&#x200B;**[!UICONTROL 缩略图创建]**&#x200B;步骤下添加&#x200B;**[!UICONTROL Camera Raw/DNG处理程序]**&#x200B;步骤。

1. 在&#x200B;**[!UICONTROL Camera Raw/DNG处理程序]**&#x200B;步骤中，在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡中添加以下配置：

   * **[!UICONTROL Mime类型]**: `image/dng` 和  `image/x-raw-(.*)`
   * **[!UICONTROL Command]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. 单击&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>请确保上述配置与&#x200B;**[!UICONTROL 使用Camera Raw和DNG处理步骤]**&#x200B;的示例DAM更新资产配置相同。

现在，您可以将Camera Raw文件导入[!DNL Experience Manager]资产。 安装Camera Raw包并配置所需的工作流后，侧窗格列表中会显示&#x200B;**[!UICONTROL 图像调整]**&#x200B;选项。

![chlimage_1-337](assets/chlimage_1-337.png)

*图：侧面板中的选项*

![chlimage_1-338](assets/chlimage_1-338.png)

*图：使用选项对图像进行轻量级编辑*

保存对Camera Raw图像的编辑后，将为该图像生成新的演绎版`AdjustedPreview.jpg`。 对于除Camera Raw以外的其他图像类型，所做的更改会反映在所有演绎版中。

## 最佳实践、已知问题和限制 {#best-practices}

该功能具有以下限制：

* 该功能仅支持JPEG呈现。 Windows 64位、Mac OS和RHEL 7.x支持此功能。
* RAW和DNG格式不支持元数据写回。
* Camera Raw库在每次处理的总像素数方面存在限制。 目前，它最多可以处理文件长边上的65000个像素，或者无论先遇到什么条件，都可以处理512 MP。
