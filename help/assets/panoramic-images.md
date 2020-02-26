---
title: 全景图像
seo-title: 全景图像
description: 了解如何在Dynamic media中处理全景图像。
seo-description: 了解如何在Dynamic media中处理全景图像。
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# 全景图像 {#panoramic-images}

本节介绍如何使用全景图像查看器来渲染球面全景图像，以实现房间、属性、位置或横向的沉浸式360°查看体验。

See also [Managing Viewer Presets](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 上传资产以与全景图图像查看器一起使用 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

要使上传的资产成为您要与全景图像查看器一起使用的球面全景图像，该资产必须具有以下一项或两项：

* 宽高比为2。

   您可以在以下位置覆盖 **[!UICONTROL CRXDE Lite中的默认长宽比设置]** 2:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用关键字 `equirectangular`或和 `spherical`、 `panorama`或和 `spherical` 标记 `panoramic`。 请参阅 [使用标记](/help/sites-authoring/tags.md)。

纵横比和关键字条件都适用于资产详细信息页面和&#x200B;**[!UICONTROL 全景媒体]** 组件的全景资产。

要上传资产以与全景图像查看器一起使用，请参阅上 [传资产](managing-assets-touch-ui.md#uploading-assets)。

## 配置Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

要使全景图像查看器在AEM中正常工作，您必须将全景图像查看器预设与特定于Dynamic Media Classic和Dynamic Media Classic的元数据同步，以便在JCR中更新查看器预设。 为此，请按以下方式配置Dynamic Media Classic:

1. [为每个公司帐户登录Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 实例。

1. 在页面的右上角附近，单击“设置”>“应 **[!UICONTROL 用程序设置”>“发布设置”>“图像服务器”]**。
1. 在“图 **[!UICONTROL 像服务器发布]** ”页面上，从顶部附近的“发布上下文 **[!UICONTROL ”下拉菜单中，选择“图]** 像服务” ****。

1. 在同一图像服 **[!UICONTROL 务器发布页面上]** ，找到标题“请 **[!UICONTROL 求属性”]**。
1. 在“请求 **[!UICONTROL 属性]** ”标题下，找到“ **[!UICONTROL 回复图像大小限制”]**。 然后，在关联的“宽 **[!UICONTROL 度]** ”和“高 **** 度”字段中，增加全景图像允许的最大图像大小。

   Dynamic Media Classic的像素数限制为25,000,000像素。 宽高比为2:1的图像的最大允许大小为7000 x 3500。 但是，对于典型的桌面屏幕，4096 x 2048像素就足够了。

   >[!NOTE]
   >
   >仅支持在允许的最大图像大小以内的图像。 对超过大小限制的图像的请求将导致403响应。

1. 在“请 **求属性”标题下** ，执行以下操作：

   * 将“请 **[!UICONTROL 求模糊处理模式]** ”设置 **[!UICONTROL 为“禁用”]**。
   * 将“请 **[!UICONTROL 求锁定模式]** ”设置 **[!UICONTROL 为“禁用”]**。
   在AEM中使用全景媒体组 **[!UICONTROL 件时]** ，需要这些设置。

1. 在“图像服务 **[!UICONTROL 器发布]** ”页面的底部，点按 **[!UICONTROL 保存]**。

1. 在右下角，点按关 **[!UICONTROL 闭]**。

### 全景媒体组件疑难解答 {#troubleshooting-the-panoramic-media-wcm-component}

如果将图像放入WCM中的 **[!UICONTROL Panoramic Media]** （全景媒体）组件中，并且组件占位符已折叠，则可能需要对以下问题进行疑难解答：

* 如果遇到“403禁止”错误，则可能是由于请求的图像大小过大所致。 查看配 *置Dynamic Media Classic* (Scene7) [中的“回复图像大小限制”设置](#configuring-dynamic-media-classic-scene)。

* 对于页面上 *显示的资产锁定无效* ，或“解析”错误，请选中“请 *求模糊处理模式* ”和“锁定模式 ******** ”，确保它们被禁用。
* 对于受污染的画布错误，请为图像 **[!UICONTROL 资产的先前请求设置规则集定义文件路径和失效CTN]** 。
* 如果图像请求的大小超过支持的限制后图像质量变得非常低，请检查“ **[!UICONTROL JPEG编码属性”>“质量]** ”设置是否为空。 “质量”字段的典型 **[!UICONTROL 设置]** 是 `95`。 您可以在“图像服务器发布”页 **[!UICONTROL 面上找到该设置]** 。 要访问页面，请参阅 [配置Dynamic Media Classic](#configuring-dynamic-media-classic-scene)。

## 预览全景图像 {#previewing-panoramic-images}

See [Previewing Assets](previewing-assets.md).

## 发布全景图像 {#publishing-panoramic-images}

请参阅[发布资产](publishing-dynamicmedia-assets.md)。
