---
title: 为图像加水印
description: 使用水印功能向PNG和JPEG图像添加数字水印。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 04de28347ddf0082d2e224aa3853297cad3aacd8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---


# 为您的资产设置水印{#watermarking}

Adobe Experience Manager(AEM)资产允许您为图像添加数字水印，帮助用户验证资产的真实性和版权所有权。 AEM Assets支持将文本用作PNG和JPEG文件上的水印。

要能够对资产应用水印，请在[!UICONTROL DAM更新资产]工作流中添加[!UICONTROL 水印]步骤。

1. 点按AEM徽标，然后转至&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]**。
1. 在“工作流模型”页中，选择&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流，然后单击&#x200B;**[!UICONTROL 编辑]**。

1. 从侧面板中，拖动&#x200B;**[!UICONTROL 添加水印]**&#x200B;步骤并将其添加到[!UICONTROL DAM更新资产]工作流。

   ![在DAM更新资产工作流中添加水印步骤](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >将[!UICONTROL 添加水印]步骤放在[!UICONTROL 处理缩略图]步骤之前的任意位置。

1. 打开&#x200B;**[!UICONTROL 添加水印]**&#x200B;步骤以显示其属性。
1. 在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡中，在各个字段中指定有效值，包括文本、字体类型、大小、颜色、位置、方向等。 要确认更改，请点按／单击完成图标。

   ![在资产的添加水印步骤中提供参数](assets/arguments_add_watermark_aem_assets.png)

1. 使用水印步骤保存 **[!UICONTROL DAM 更新资产]**&#x200B;工作流。
1. 从AEM用户界面上传示例资产。 在您在上述步骤中配置的位置，将显示带有字体大小、颜色等的水印。

要以编程方式或使用动态信息对PDF文档进行水印，请考虑使用[AEM文档服务](/help/forms/using/overview-aem-document-services.md)产品。
