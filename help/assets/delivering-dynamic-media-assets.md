---
title: 传送 Dynamic Media 资产
seo-title: 传送 Dynamic Media 资产
description: 了解如何交付动态媒体资产
seo-description: 了解如何交付动态媒体资产
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 23%

---


# 传送 Dynamic Media 资产 {#delivering-dynamic-media-assets}

您如何投放动态媒体资产（视频和图像）取决于网站的实施方式。

通过 Dynamic Media，您可以选择以下方式：

* 如果您的网站托管在 AEM 上，您会希望将 Dynamic Media 资产直接添加到您的页面。
* 如果您的网站不在AEM上，您可以选择：

   * 将视频或图像嵌入您的网站。
   * 将URL关联到您的Web应用程序。当您希望以弹出窗口或模态窗口的形式传送视频播放器时，可使用链接。
   * 如果您的站点是响应式的，您可以[传送优化的图像。](responsive-site.md)

>[!NOTE]
>
>智能成像可以与现有图像预设配合使用，并在投放的最后一毫秒使用智能功能根据浏览器或网络连接速度进一步减小图像文件大小。 有关详细信息，请参阅[智能成像](imaging-faq.md)。

有关更多信息，请参阅下列主题：

* [将Dynamic Media资产添加到网页](adding-dynamic-media-assets-to-pages.md)
* [在网页上嵌入视频查看器或图像查看器](embed-code.md)
* [在 Dynamic Media 中激活热链接保护](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* 将数字不可见水印(Digimarc)与Dynamic Media（即将推出）集成
* [将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md)
* [为响应式网站传送优化的图像](responsive-site.md)
* [HTTP2 内容交付](http2.md)
* [使 CDN 缓存内容无效](invalidate-cdn-cached-content.md)
* [使用规则集转换 URL](using-rulesets-to-transform-urls.md)

## HTTP/2投放Dynamic Media资源{#http-delivery-of-dynamic-media-assets}

AEM现在支持通过HTTP/2投放所有Dynamic Media内容（图像和视频）。 即，图像或视频的已发布URL或嵌入代码可与接受托管资产的任何应用程序集成。 随后，将通过HTTP/2协议传送已发布的资产。 此投放方法改进了浏览器和服务器通信的方式，使您的所有Dynamic Media资源都能得到更好的响应和加载时间。

请参阅[HTTP/2投放内容常见问题](/help/sites-administering/scene7-http2faq.md)以了解更多信息。
