---
title: 全景图像
description: 了解如何在Dynamic Media中处理全景图像。
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# 全景图像 {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本节介绍如何使用全景图像查看器来渲染球形全景图像，以便在室内、属性、位置或横向享受沉浸式360°的观看体验。

另请参阅 [管理查看器预设](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 上传资产以与全景图像查看器一起使用 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

要将上传的资产限定为要与全景图像查看器一起使用的球形全景图像，该资产必须具有以下任一项或两项：

* 宽高比为2。

   您可以覆盖 **[!UICONTROL CRXDE Lite]** 在以下位置：

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用关键词标记 `equirectangular`或 `spherical`和 `panorama`或 `spherical` 和 `panoramic`. 请参阅 [使用标记](/help/sites-authoring/tags.md).

纵横比和关键字条件都适用于资产详细信息页面和&#x200B;**[!UICONTROL 全景媒体]** 组件的全景资产。

要上传资产以与全景图像查看器一起使用，请参阅 [上传资产](managing-assets-touch-ui.md#uploading-assets).

## 配置Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

要使全景图像查看器在AEM中正常工作，您必须将全景图像查看器预设与特定于Dynamic Media Classic和Dynamic Media Classic的元数据同步，以便查看器预设在JCR中进行更新。 要完成此操作，请以下方式配置Dynamic Media Classic:

1. [登录到Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) 每个公司帐户。

1. 在页面的右上角附近，单击 **[!UICONTROL 设置>应用程序设置>发布设置>图像服务器]**.
1. 在 **[!UICONTROL 图像服务器发布]** 页面，从 **[!UICONTROL 发布上下文]** 下拉菜单，选择 **[!UICONTROL 图像提供]**.

1. 相同 **[!UICONTROL 图像服务器发布]** 页面，找到标题 **[!UICONTROL 请求属性]**.
1. 在 **[!UICONTROL 请求属性]** 标题，定位 **[!UICONTROL 回复图像大小限制]**. 然后，在关联的 **[!UICONTROL 宽度]** 和 **[!UICONTROL 高度]** 字段，请增加全景图像允许的最大图像大小。

   Dynamic Media Classic的限制为25,000,000像素。 宽高比为2:1的图像的最大允许大小为7000 x 3500。 但是，对于典型的桌面屏幕，4096 x 2048像素就足够了。

   >[!NOTE]
   >
   >仅支持位于允许的最大图像大小范围内的图像。 对超过大小限制的图像的请求将导致403响应。

1. 在 **[请求属性]** 标题中，执行以下操作：

   * 已设置 **[!UICONTROL 请求模糊处理模式]** to **[!UICONTROL 已禁用]**.
   * 已设置 **[!UICONTROL 请求锁定模式]** to **[!UICONTROL 已禁用]**.

   使用 **[!UICONTROL 全景媒体]** 组件。

1. 在 **[!UICONTROL 图像服务器发布]** 页面的左侧，点按 **[!UICONTROL 保存]**.

1. 在右下角，点按 **[!UICONTROL 关闭]**.

### 全景媒体组件故障诊断 {#troubleshooting-the-panoramic-media-wcm-component}

如果您将图像放入 **[!UICONTROL 全景媒体]** 组件且组件占位符已折叠，则您可能需要对以下问题进行故障诊断：

* 如果遇到403禁止错误，则可能是由于请求的图像大小过大所致。 查看 *回复图像大小限制* 设置 [配置Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* 对于 *无效锁* 或 *解析错误* 显示在页面上，勾选 **[!UICONTROL 请求模糊处理模式]** 和 **[!UICONTROL 请求锁定模式]** 以确保禁用。
* 对于受污染的画布错误，请设置 **[!UICONTROL 规则集定义文件路径与无效CTN]** ，以处理图像资产的先前请求。
* 如果在图像请求中大小超过支持的限制时，图像质量变得非常低，请检查 **[!UICONTROL JPEG编码属性>质量]** 设置不为空。 的典型设置 **[!UICONTROL 质量]** 字段 `95`. 您可以在 **[!UICONTROL 图像服务器发布]** 页面。 要访问页面，请参阅 [配置Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## 预览全景图像 {#previewing-panoramic-images}

请参阅 [预览资产](previewing-assets.md).

## 发布全景图像 {#publishing-panoramic-images}

请参阅 [发布资产](publishing-dynamicmedia-assets.md).
