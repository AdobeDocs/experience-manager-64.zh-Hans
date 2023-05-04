---
title: 应用Dynamic Media图像预设
seo-title: Applying Dynamic Media image presets
description: 了解如何在Dynamic Media中应用图像预设
seo-description: Learn how to apply image presets in Dynamic Media
uuid: 8bafcbd0-6df0-4d5b-b2f7-116ddb4ec060
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5c1f60ac-3741-4002-9c5d-c128f118342b
exl-id: 07a4f315-a60e-456b-b02d-035b3f6ad9ad
feature: Image Presets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 10%

---

# 应用Dynamic Media图像预设 {#applying-image-presets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

图像预设使资产能够动态传送不同大小、不同格式或具有动态生成的其他图像属性的图像。 在导出图像时，您可以选择预设，这也会根据管理员指定的规范来重新设置图像的格式。

此外，您还可以选择响应式图像预设(由 **[!UICONTROL RESS]** 按钮)。

本节将介绍如何使用图像预设。 [管理员可以创建和配置图像预设](managing-image-presets.md).

>[!NOTE]
>
>智能成像可与您现有的图像预设配合使用，并在交付的最后一毫秒内使用智能功能，根据浏览器或网络连接速度进一步减小图像文件大小。 请参阅 [智能成像](imaging-faq.md) 以了解更多信息。

无论您何时预览图像，都可以将图像预设应用到图像。

**应用Dynamic Media图像预设**:

1. 打开资产，然后点按左边栏中的下拉菜单，然后点按 **[!UICONTROL 演绎版]**.

   >[!NOTE]
   >
   >* 静态演绎版显示在窗格的上半部分。 动态演绎版显示在下半部分。 仅对动态演绎版，您可以使用URL来显示图像。 的 **[!UICONTROL URL]** 按钮时，才会显示该按钮。 的 **[!UICONTROL RESS]** 按钮。
   >
   >* 当您选择 **[!UICONTROL 演绎版]** 的“详细信息”视图。 您可以增加可查看的预设数。请参阅 [增加显示的图像预设数](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).


   ![chlimage_1-208](assets/chlimage_1-208.png)

1. 执行以下任一操作：

   * 选择动态演绎版以预览图像预设。
   * 点按 **[!UICONTROL URL]**, **[!UICONTROL 嵌入]**&#x200B;或 **[!UICONTROL RESS]** 以显示弹出窗口。

   >[!NOTE]
   >
   >如果资产&#x200B;*和*&#x200B;图像预设尚未发布，则 **[!UICONTROL URL]** 按钮（或 **[!UICONTROL URL]** 和 **[!UICONTROL RESS]** 按钮，如果适用）将不可用。
   >
   >另请注意，图像预设会自动发布在Dynamic Media服务器上。
