---
title: 为响应式网站传送优化的图像
description: 如何使用Dynamic Media中的响应代码功能来交付优化的图像
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
exl-id: 36bb526c-a6d9-4296-8318-97ac72d6b3ba
feature: Publishing
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 12%

---

# 为响应式网站传送优化的图像 {#delivering-optimized-images-for-a-responsive-site}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

当您想要与Web开发人员共享代码以进行响应式服务时，请使用响应式代码功能。 复制响应式(**[!UICONTROL RESS]**)代码，以便您可以将其与web开发人员共享。

如果您的网站位于第三方WCM上，则使用此功能很有意义。 但是，如果您的网站改为位于AEM上，则域外图像服务器会呈现该图像并将其提供给网页。

另请参阅 [在网页上嵌入视频查看器。](embed-code.md)

另请参阅 [将URL关联到您的Web应用程序。](linking-urls-to-yourwebapplication.md)

**为响应式网站提供优化的图像**:

1. 导航到您要为提供响应代码的图像，然后在下拉菜单中，点按 **[!UICONTROL 演绎版]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. 选择响应式图像预设。 将显 **[!UICONTROL 示]** URL **[!UICONTROL 和]** RESS按钮。

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >必须发布选定的资产&#x200B;*和*&#x200B;选定的图像预设或查看器预设，才能使 **[!UICONTROL URL]** 或 **[!UICONTROL RESS]** 按钮可用。
   >
   >Dynamic Media — 混合模式要求您发布图像预设；Dynamic Media - Scene7模式会自动发布图像预设。

1. 点按 **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在 **[!UICONTROL 嵌入响应式图像]** 对话框中，选择并复制响应式代码文本，然后将其粘贴到您的网站中，以访问响应式资产。
1. 编辑嵌入代码中的默认断点，以便直接与代码中响应式网站的断点相匹配。 此外，还可以测试不同页面断点处提供的不同图像分辨率。

## 使用HTTP/2交付Dynamic Media资产 {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2是经过更新的新Web协议，可改进浏览器和服务器的通信方式。 它提供了更快的信息传输，并降低了所需的处理能力。 HTTP/2支持交付Dynamic Media资产，从而提供更好的响应和加载时间。

请参阅 [HTTP2内容交付](http2.md) 有关开始使用HTTP/2与您的Dynamic Media帐户的完整详细信息。
