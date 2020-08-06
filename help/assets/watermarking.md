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


# 为资产设置水印 {#watermarking}

Adobe Experience Manager(AEM)资产允许您为图像添加数字水印，帮助用户验证资产的真实性和版权所有权。 AEM Assets支持将文本用作PNG和JPEG文件上的水印。

要能够对资产应用水印，请在DAM更新资 [!UICONTROL 产工作流] 中添 [!UICONTROL 加水印步骤] 。

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. 在“工作流模型”页中，选择“ **[!UICONTROL DAM更新资产”工作]** 流，然后单 **[!UICONTROL 击编辑]**。

1. 从侧面板中，拖动添 **[!UICONTROL 加水印]** ，并将其添加到 [!UICONTROL DAM更新资产工作流] 。

   ![在DAM更新资产工作流中添加水印步骤](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >将添加 [!UICONTROL 水印步骤放] 在“流程缩略图 [!UICONTROL ”步骤之前的任] 意位置。

1. 打开添 **[!UICONTROL 加水印]** ，以显示其属性。
1. 在“参 **[!UICONTROL 数]** ”选项卡中，在各个字段中指定有效值，包括文本、字体类型、大小、颜色、位置、方向等。 要确认更改，请点按／单击完成图标。

   ![在资产的添加水印步骤中提供参数](assets/arguments_add_watermark_aem_assets.png)

1. 使用水印步骤保存 **[!UICONTROL DAM 更新资产]**&#x200B;工作流。
1. 从AEM用户界面上传示例资产。 在您在上述步骤中配置的位置，将显示带有字体大小、颜色等的水印。

要以编程方式或利用动态信息对PDF文档进行水印，请考虑使 [用AEM文档](/help/forms/using/overview-aem-document-services.md) Services产品。
