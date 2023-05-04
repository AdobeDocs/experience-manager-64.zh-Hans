---
title: 传送Dynamic Media资产
seo-title: Delivering Dynamic Media Assets
description: 了解如何交付Dynamic Media资产
seo-description: Learn how to deliver dynamic media assets
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 14%

---

# 传送Dynamic Media资产 {#delivering-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如何交付Dynamic Media资产（视频和图像）取决于网站的实施方式。

使用Dynamic Media，您可以选择以下几个选项：

* 如果您的网站托管在AEM上，则您希望将Dynamic Media资产直接添加到您的页面。
* 如果您的网站不在AEM上，则可以选择以下任一选项：

   * 在您的网站上嵌入视频或图像。
   * 将 URL 关联到您的 Web 应用程序. 当您希望将视频播放器作为弹出窗口或模式窗口进行传送时，请使用链接。
   * 如果您的网站是响应式的，您可以 [提供优化的图像。](responsive-site.md)

>[!NOTE]
>
>智能成像可与您现有的图像预设配合使用，并在交付的最后一毫秒内使用智能功能，根据浏览器或网络连接速度进一步减小图像文件大小。 请参阅 [智能成像](imaging-faq.md) 以了解更多信息。

有关更多信息，请参阅以下主题：

* [将Dynamic Media Assets添加到网页](adding-dynamic-media-assets-to-pages.md)
* [在网页上嵌入视频查看器或图像查看器](embed-code.md)
* [在 Dynamic Media 中激活热链接保护](https://helpx.adobe.com/cn/experience-manager/6-4/assets/using/hotlink-protection.html)
* 将数字不可见水印(Digimarc)与Dynamic Media（即将推出）集成
* [将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md)
* [为响应式网站传送优化的图像](responsive-site.md)
* [HTTP2 内容交付](http2.md)
* [使 CDN 缓存内容无效](invalidate-cdn-cached-content.md)
* [使用规则集转换 URL](using-rulesets-to-transform-urls.md)

## HTTP/2交付Dynamic Media资产 {#http-delivery-of-dynamic-media-assets}

AEM现在支持通过HTTP/2交付所有Dynamic Media内容（图像和视频）。 即，图像或视频的已发布URL或嵌入代码可与接受托管资产的任何应用程序集成。 然后，将通过HTTP/2协议来交付已发布的资产。 这种交付方法改进了浏览器和服务器通信的方式，从而可以缩短所有Dynamic Media资产的响应和加载时间。

请参阅 [HTTP/2内容交付常见问题解答](/help/sites-administering/scene7-http2faq.md) 以了解更多。
