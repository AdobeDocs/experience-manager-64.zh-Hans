---
title: 向数字资产添加水印
description: 了解如何使用水印功能向资产添加数字水印。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 4%

---

# 对数字资产添加水印 {#watermarking}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] 允许您向资产添加数字水印，以帮助用户验证资产的真实性和版权所有权。 [!DNL Experience Manager Assets] 支持在PNG和JPEG文件上用作水印的文本。

Adobe Experience Manager Assets允许您向图像添加数字水印，以帮助用户验证资产的真实性和版权所有权。 [!DNL Experience Manager] Assets支持在PNG和JPEG文件中用作水印的文本。

要对资产应用水印，请在 [!UICONTROL DAM更新资产] 工作流。

1. 访问 [!DNL Experience Manager] 用户界面，然后转到 **[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]**.
1. 从工作流模型页面中，选择 **[!UICONTROL DAM更新资产]** 工作流和单击 **[!UICONTROL 编辑]**.

1. 从侧面板中，将 **[!UICONTROL 添加水印]** 步骤并将其添加到 [!UICONTROL DAM更新资产] 工作流。

   ![在DAM更新资产工作流中拖动添加水印步骤](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >将 [!UICONTROL 添加水印] 在之前的任意位置 [!UICONTROL 流程缩略图] 中。

1. 打开 **[!UICONTROL 添加水印]** 步骤以显示其属性。
1. 在 **[!UICONTROL 参数]** 选项卡，在各种字段中指定有效值，包括文本、字体类型、大小、颜色、位置、方向等。 要确认更改，请单击 **[!UICONTROL 完成]**.

   ![在资产的添加水印步骤中提供参数](assets/arguments_add_watermark_aem_assets.png)

1. 使用水印步骤保存 **[!UICONTROL DAM 更新资产]**&#x200B;工作流。
1. 从 [!DNL Experience Manager] 用户界面中，上传示例资产。 在您在上述步骤中配置的位置，水印会以字体大小、颜色等显示。

要以编程方式或使用动态信息对PDF文档进行水印，请考虑使用 [[!DNL Experience Manager] 文档服务](/help/forms/using/overview-aem-document-services.md) 服务。

## 提示和限制 {#tips-limitations}

* 仅支持基于文本的水印。 图像不用作水印，即使您在创建 [!UICONTROL 添加水印过程].
* 仅支持PNG和JPEG文件加水印。 其他资产格式不会添加水印。
