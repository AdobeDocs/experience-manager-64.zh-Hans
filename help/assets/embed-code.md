---
title: 在网页上嵌入Dynamic Media视频或图像查看器
seo-title: 在网页上嵌入Dynamic Media视频或图像查看器
description: 了解如何在网页上嵌入Dynamic Media视频或图像
seo-description: 了解如何在网页上嵌入Dynamic Media视频或图像
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: 组件
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 28%

---

# 在网页上嵌入Dynamic Media视频或图像查看器 {#embedding-the-video-or-image-viewer-on-a-web-page}

当您想 **[!UICONTROL 要播放视频或查看嵌入到网页中的资产时]** ，请使用嵌入代码功能。 将嵌入代码复制到剪贴板，以便将其粘贴到网页中。 不允许在“嵌入代码”对 **[!UICONTROL 话框中编辑代码]** 。

仅当&#x200B;_未_&#x200B;使用AEM作为WCM时，才嵌入URL。 如果您使用AEM作为WCM，请[直接在页面上添加资产。](adding-dynamic-media-assets-to-pages.md)

请参阅[将URL关联到您的Web应用程序。](linking-urls-to-yourwebapplication.md)

请参阅[为响应式网站传送优化的图像。](responsive-site.md)

>[!NOTE]
>
>只有在发布选定的资产后，才可复制其嵌入代码。此外，您还必须发布查看器预设或图像预设。
>
>请参阅[发布资产](publishing-dynamicmedia-assets.md)。
>
>请参阅[发布查看器预设](managing-viewer-presets.md#publishing-viewer-presets)。
>
>请参阅[发布图像预设](managing-image-presets.md#publishing-image-presets)。

**要在网页上嵌入Dynamic Media视频或图像查看器，请执行以下操作**:

1. 导航到要复制其嵌入代码的&#x200B;*published*&#x200B;视频或图像资产。

   请注意，只有在首次&#x200B;*发布*&#x200B;资产&#x200B;*后*，才可复制嵌入代码。此外，还必须发布查看器预设或图像预设。

   请参阅[发布资产](publishing-dynamicmedia-assets.md)。

   请参阅[发布查看器预设](managing-viewer-presets.md#publishing-viewer-presets)。

   请参阅[发布图像预设](managing-image-presets.md#publishing-image-presets)。

1. 在左边栏中，选择下拉菜单，然后点按&#x200B;**[!UICONTROL 查看器]**。
1. 在左边栏中，点按查看器预设名称。查看器预设将应用于资产。
1. 点按&#x200B;**[!UICONTROL 嵌入]**。
1. 在&#x200B;**[!UICONTROL 嵌入代码]**&#x200B;对话框中，将整个代码复制到剪贴板，然后点按&#x200B;**[!UICONTROL 关闭]**。
1. 将嵌入代码粘贴到网页中。

## 使用HTTP/2交付Dynamic Media资产 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2是经过更新的新Web协议，可改进浏览器和服务器的通信方式。 它提供了更快的信息传输，并降低了所需的处理能力。 现在，Dynamic Media资产的交付可以通过HTTP/2进行，从而提供更好的响应和加载时间。

请参阅[HTTP2内容交付](http2.md) ，以了解有关使用Dynamic Media帐户的HTTP/2入门的完整详细信息。
