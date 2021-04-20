---
title: 全景图像
Description: Learn how to work with panoramic images in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 5%

---

# 全景图像 {#panoramic-images}

本节介绍如何使用全景图像查看器渲染球面全景图像，实现房间、属性、位置或风景的沉浸式360°查看体验。

另请参阅[管理查看器预设](managing-viewer-presets.md)。

![全景图2](assets/panoramic-image2.png)

## 上传要与全景图像查看器{#uploading-assets-for-use-with-the-panoramic-image-viewer}一起使用的资产

要使上传的资源成为您要与全景图像查看器一起使用的球面全景图像，该资源必须具有以下一项或两项：

* 宽高比为2。

   您可以在以下位置覆盖&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的默认宽高比设置2:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用关键字`equirectangular`、`spherical`和`panorama`或`spherical`和`panoramic`标记。 请参阅[使用标记](/help/sites-authoring/tags.md)。

纵横比和关键字条件都适用于资产详细信息页面和&#x200B;**[!UICONTROL 全景媒体]** 组件的全景资产。

要上传资产以用于全景图像查看器，请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

## 配置Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

要使全景图像查看器在AEM中正常工作，您必须将全景图像查看器预设与Dynamic Media Classic和Dynamic Media Classic特定的元数据同步，以便查看器预设在JCR中进行更新。 为此，请按照以下方式配置Dynamic Media Classic:

1. [为每个Dynamic Media帐户登录公司 Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) 桌面应用程序。

1. 在页面右上角附近，单击&#x200B;**[!UICONTROL 设置>应用程序设置>发布设置>图像服务器]**。
1. 在&#x200B;**[!UICONTROL 图像服务器发布]**&#x200B;页面上，从顶部附近的&#x200B;**[!UICONTROL 发布上下文]**&#x200B;下拉菜单中，选择&#x200B;**[!UICONTROL 图像服务]**。

1. 在同一&#x200B;**[!UICONTROL 图像服务器发布]**&#x200B;页上，找到标题&#x200B;**[!UICONTROL 请求属性]**。
1. 在&#x200B;**[!UICONTROL 请求属性]**&#x200B;标题下，找到&#x200B;**[!UICONTROL 回复图像大小限制]**。 然后，在关联的&#x200B;**[!UICONTROL 宽度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;字段中，增加全景图像的最大允许图像大小。

   Dynamic Media Classic的限制为25,000,000像素。 宽高比为2:1的图像的最大允许大小为7000 x 3500。 但是，对于典型的桌面屏幕，4096 x 2048像素就足够了。

   >[!NOTE]
   >
   >仅支持在允许的最大图像大小内的图像。 对超过大小限制的图像的请求将导致403响应。

1. 在&#x200B;**[请求属性]**&#x200B;标题下，执行以下操作：

   * 将&#x200B;**[!UICONTROL 请求模糊处理模式]**&#x200B;设置为&#x200B;**[!UICONTROL 禁用]**。
   * 将&#x200B;**[!UICONTROL 请求锁定模式]**&#x200B;设置为&#x200B;**[!UICONTROL 禁用]**。

   在AEM中使用&#x200B;**[!UICONTROL 全景媒体]**&#x200B;组件时，必须使用这些设置。

1. 在&#x200B;**[!UICONTROL 图像服务器发布]**&#x200B;页面底部，点按左侧的&#x200B;**[!UICONTROL 保存]**。

1. 在右下角，点按&#x200B;**[!UICONTROL 关闭]**。

### 对Panoramic Media组件{#troubleshooting-the-panoramic-media-wcm-component}进行故障诊断

如果将图像放入WCM中的&#x200B;**[!UICONTROL 全景媒体]**&#x200B;组件中，并且组件占位符已折叠，您可能希望对以下问题进行疑难解答：

* 如果遇到“403禁止”错误，则可能是由请求的图像大小过大引起的。 查看[配置Dynamic Media Classic](#configuring-dynamic-media-classic-scene)中的&#x200B;*回复图像大小限制*&#x200B;设置。

* 对于资产上的&#x200B;*无效锁*&#x200B;或页面上显示的&#x200B;*解析错误*，请选中&#x200B;**[!UICONTROL 请求模糊处理模式]**&#x200B;和&#x200B;**[!UICONTROL 请求锁定模式]**&#x200B;以确保禁用它们。
* 对于受污染的画布错误，请为图像资产的先前请求设置&#x200B;**[!UICONTROL 规则集定义文件路径和失效CTN]**。
* 如果图像请求的大小超过支持的限制后图像质量变得非常低，请检查“**[!UICONTROL JPEG编码属性>质量]**”设置是否不为空。 **[!UICONTROL Quality]**&#x200B;字段的典型设置为`95`。 可以在&#x200B;**[!UICONTROL 图像服务器发布]**&#x200B;页面上找到设置。 要访问页面，请参阅[配置Dynamic Media Classic](#configuring-dynamic-media-classic-scene)。

## 预览全景图像{#previewing-panoramic-images}

请参阅[预览资产](previewing-assets.md)。

## 发布全景图像{#publishing-panoramic-images}

请参阅[发布资产](publishing-dynamicmedia-assets.md)。
