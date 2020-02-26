---
title: 为图像加水印
description: 使用水印功能向PNG和JPEG图像添加数字水印。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# 为资产加水印 {#watermarking}

Adobe Experience Manager(AEM)资产允许您向图像添加数字水印，帮助用户验证资产的真实性和版权所有权。 AEM资产支持用作PNG和JPEG文件上的水印的文本。

要能够对资产应用水印，请在 [!UICONTROL DAM更新资产工作流中添] 加 [!UICONTROL “水印] ”步骤。

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. 在“工作流模型”页面中，选择“ **[!UICONTROL DAM更新资产”工作流]** ，然后单击 **[!UICONTROL 编辑]**。

1. 从侧面板中，拖动“添 **[!UICONTROL 加水印]** ”步骤并将其添加到 [!UICONTROL DAM更新资产工作流中] 。

   ![在DAM更新资产工作流中添加水印步骤](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >将“添加 [!UICONTROL 水印] ”步骤放在“流程缩略图”步 [!UICONTROL 骤之前的任意位置] 。

1. 打开添 **[!UICONTROL 加水印]** ，以显示其属性。
1. 在“参 **[!UICONTROL 数]** ”选项卡中，在各个字段中指定有效值，包括文本、字体类型、大小、颜色、位置、方向等。 要确认更改，请点按／单击完成图标。

   ![在资产的添加水印步骤中提供参数](assets/arguments_add_watermark_aem_assets.png)

1. 使用水印步骤保存 **[!UICONTROL DAM 更新资产]**&#x200B;工作流。
1. 从AEM用户界面中，上传示例资产。 在您在上述步骤中配置的位置，将显示带有字体大小、颜色等的水印。
