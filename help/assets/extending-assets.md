---
title: 自定义和扩展资产
description: 了解自定义和扩展资产共享和资产编辑器的方式，这些功能为用户提供了专门定制的界面和一组功能。
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---

# 自定义和扩展资产 {#customizing-and-extending-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe编辑器是Enterprise Manager网站的用户用来查找、查看和处理存储库中的数字资产的主要访问点。

作为 [!DNL Experience Manager] 开发人员可以通过多种方式自定义和扩展资产编辑器，为用户提供专门定制的界面和一组功能。

可以自定义或增强功能的以下方面：

* [扩展资产编辑器](asseteditorx.md)
* [扩展资产搜索](searchx.md)
* [使用媒体处理程序和工作流处理资产](media-handlers.md)
* [将资产与活动流集成](extending-activity-stream.md)
* [资产代理开发](proxy.md)
* [配置ImageMagick的最佳实践](best-practices-for-imagemagick.md)

## 自定义外观 {#customizing-the-look-and-feel}

资产编辑器的外观和风格的以下方面是可自定义的：

* 徽标：您可以在界面中添加您自己组织的徽标。
* 颜色和字体：您可以更改界面中使用的颜色和字体。
* HTML代码：要进行更彻底的自定义，您可以更改定义界面的基础HTML代码。

## 自定义演绎版 {#customizing-renditions}

在 [!DNL Experience Manager Assets] 术语演绎版是资产的呈现形式。 通常，特定资产可能具有多个演绎版。 例如，全彩图像可能具有一个原始大小的呈现版本，另一个呈现版本具有缩小的大小，另一个呈现版本同时具有缩小的大小并转换为灰度。

可以自定义特定资产可用的演绎版，并创建新的演绎版。
