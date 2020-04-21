---
title: 将 Dynamic Media 资产添加到页面
seo-title: 将 Dynamic Media 资产添加到页面
description: 如何在AEM中将Dynamic Media组件添加到页面
seo-description: 如何在AEM中将Dynamic Media组件添加到页面
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: ef00b3d307e01807f90bad8c8fde278204470bc3

---


# 将 Dynamic Media 资产添加到页面 {#adding-dynamic-media-assets-to-pages}

To add the dynamic media functionality to assets you use on your websites, you can add the **Dynamic Media** or **Interactive Media** component directly on the page. 为此，可进入布局模式并启用Dynamic Media组件。 然后，您可以将这些组件添加到页面，并将资产添加到该组件。 Dynamic Media 组件和交互式媒体组件是智能组件，它们知道您添加的是图像还是视频，并能据此相应地更改提供的选项。

如果您使用AEM作为WCM，则可以直接将Dynamic Media资产添加到页面。 如果您为 WCM 使用第三方，请[链接](linking-urls-to-yourwebapplication.md)或[嵌入](embed-code.md)资产。有关响应式第三方网站，请参阅[将优化的图像交付到响应式网站](responsive-site.md)。

>[!NOTE]
>
>在AEM中将资产添加到页面之前，必须先发布资产。 See [Publishing Dynamic Media Assets](publishing-dynamicmedia-assets.md).

## Adding a Dynamic Media component to a page {#adding-a-dynamic-media-component-to-a-page}

将 Dynamic Media 组件或交互式媒体组件添加到页面的过程与将组件添加到任何页面的过程相同。以下各部分详细介绍了 Dynamic Media 组件和交互式媒体组件。

>[!NOTE]
>
>如果具有只读权限的用户访问的网页上存在Dynamic Media组件、交互式媒体组件或两者，则分页符和组件将无法正确呈现。 原因在于，重建页面是为了确保组件的属性良好，并且任何引用的资源和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
>  
>要避免此问题，请确保AEM Sites用户拥有访问资产所需的权限。

1. 在AEM中，打开要添加Dynamic Media或交互式媒体组件的页面。
1. 在左窗格中，单击“组 **[!UICONTROL 件]** ”图标并筛选 **[!UICONTROL Dynamic Media]**。 如果没有可用的Dynamic Media组件，您需要启用Dynamic Media组件。 有关更 [多信息，请参阅编辑页面模板](/help/sites-authoring/templates.md#editing-templates-template-authors) 。

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 将Dynamic Media **** 或 **** Interactive Media组件拖到页面上所需的位置。
1. 单击组件周围的蓝框，然后点按配 **[!UICONTROL 置]** （扳手）图标。
1. [根据需要编辑组件](#dynamic-media-components) ，然后单击复选标记以保存更改。

## 本地化Dynamic Media组件 {#localizing-dynamic-media-components}

您可以通过以下两种方式之一本地化Dynamic Media组件：

* 在“站点”的网页中，打开“属 **[!UICONTROL 性]** ”，然后选择“ **[!UICONTROL 高级]** ”选项卡。 选择所需的本地化语言。

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 从站点选择器中，选择所需的页面或页面组。 点按 **[!UICONTROL 属性]** ，然后选择 **[!UICONTROL 高级选项]** 卡。 选择所需的本地化语言。

   >[!NOTE]
   >
   >请注意，并非所有语言在“语言”菜单中 **[!UICONTROL 可用]** ，当前都分配了令牌。

## Dynamic Media components {#dynamic-media-components}

Dynamic Media和Interactive Media位于“组件”中的“ [!UICONTROL Dynamic Media] ”选项 [!UICONTROL 卡下]。 您可以对任何交互式资产（如交互式视频、交互式图像或传送集）使用“交互式媒体”组件。 对于所有其他 Dynamic Media 资产，请使用 Dynamic Media 组件。

>[!NOTE]
>
>这些组件在默认情况下不可用，在使用之前需要通过模板编辑器使用。 [在模板编辑器中](/help/sites-authoring/templates.md#editing-templates-template-authors)使组件可用后，您可以像添加任何其他AEM组件一样将组件添加到页面。

![chlimage_1-539](assets/chlimage_1-539.png)

### Dynamic Media 组件 {#dynamic-media-component}

Dynamic Media组件是智能的，具体取决于您添加的是图像还是视频，您有各种选项。 该组件支持图像预设、基于图像的查看器（例如图像集、旋转集、混合媒体集）和视频。此外，查看器是响应式的。 也就是说，屏幕的大小会根据屏幕大小自动更改。 所有查看器都是 HTML5 查看器。

>[!NOTE]
>
>如果具有只读权限的用户访问的网页上存在Dynamic Media组件、交互式媒体组件或两者，则分页符和组件将无法正确呈现。 原因在于，重建页面是为了确保组件的属性良好，并且任何引用的资源和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
>  
>要避免此问题，请确保AEM Sites用户拥有访问资产所需的权限。

>[!NOTE]
>
>添加 Dynamic Media 组件时，如果 **[!UICONTROL Dynamic Media 设置]**&#x200B;为空或无法正常添加资产，请检查以下各项：
>
>* 您已经[启用了 Dynamic Media](config-dynamic.md)。默认情况下，Dynamic Media 处于禁用状态。
>* 图像具有金字塔 TIFF 文件。在启用 Dynamic Media 之前导入的图像没有金字塔 TIFF 文件。
>



#### 处理图像时 {#when-working-with-images}

Dynamic Media 组件允许您添加动态图像，包括图像集、旋转集和混合媒体集。您可以缩放图像，并在适当的情况下在旋转集内旋转图像，或从其他类型的集合中选择图像。

您还可以直接在组件中配置查看器预设、图像预设或图像格式。要使图像成为响应式图像，您可以设置断点，或应用响应式图像预设。

You must edit the following Dynamic Media Settings by clicking the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>默认情况下，Dynamic media图像组件是自适应的。 If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** settings.

* **[!UICONTROL 查看器预]**&#x200B;设从下拉菜单中选择现有的查看器预设。 如果未显示您要查找的查看器预设，则可能需要将其显示出来。请参阅管理查看器预设。如果您正在使用图像预设，则无法选择查看器预设，反之亦然。如果您查看的是图像集、旋转集或混合媒体集，这是唯一可用的选项。显示的查看器预设也是智能的 - 仅显示相关的查看器预设。

* **[!UICONTROL 查看器修饰符]**“查看器修饰符”的形式为name=value对（带有&amp;分隔符），您可以按《查看器参考指南》中所述更改查看器。 查看器修饰符的示例是posterimage=img.jpg&amp;caption=text.vtt,1，它为视频缩略图设置不同的图像并将隐藏字幕／子标题文件与视频相关联。

* **[!UICONTROL 图像预]**&#x200B;设从下拉菜单中选择现有的图像预设。 如果未显示您要查找的图像预设，则可能需要将其显示出来。请参阅管理图像预设。如果您正在使用图像预设，则无法选择查看器预设，反之亦然。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 图像修饰符]**您可以通过提供其他图像命令来应用图像效果。 图像预设和图像服务命令参考中介绍了这些设置。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 断点]**&#x200B;如果您在响应式站点上使用此资产，则需要添加图像断点。 图像断点之间需要使用逗号 (,) 进行分隔。当图像预设中未定义高度或宽度时，可以使用此选项。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 标题]**&#x200B;更改图像的标题。

* **[!UICONTROL 替代文]**本为关闭图形的用户添加图像标题。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL URL，打开方式]**&#x200B;您可以设置资产以打开链接。 设置 URL，并在打开方式中指示是要在同一窗口中还是在新窗口中打开该 URL。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 宽度]** 和 **[!UICONTROL 高]**&#x200B;度如果希望图像具有固定大小，请输入以像素为单位的值。 将这两个值留空会使资产成为自适应资产。

#### 处理视频时 {#when-working-with-video}

使用Dynamic Media组件将动态视频添加到网页。 编辑该组件时，您可以选择使用预定义的视频查看器预设，以在页面上播放视频。

![chlimage_1-540](assets/chlimage_1-540.png)

You must edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>默认情况下，Dynamic Media 视频组件为自适应组件。If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the [!UICONTROL Advanced] tab.

* **[!UICONTROL 查看器预]**&#x200B;设从下拉菜单中选择现有的视频查看器预设。 如果未显示您要查找的查看器预设，则可能需要将其显示出来。请参阅管理查看器预设。

* **[!UICONTROL 查看器修饰符]** Viewer修饰符的形式为name=value对，带有&amp;分隔符，允许您根据Adobe查看器参考指南中的概述更改查看器。 查看器修饰符的示例为posterimage=img.jpg&amp;caption=text.vtt,1

   例如，通过查看器修饰符，您可以执行以下操作：

   * 将题注文件与视频关联https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html更多 [内容](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html)
   * 将导航文件与视频https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html关 [联](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html)

You can edit the following [!UICONTROL Advanced Settings] by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 标题]**&#x200B;更改视频的标题。

* **[!UICONTROL 宽度]** 和 **[!UICONTROL 高]**&#x200B;度如果希望视频大小固定，请输入以像素为单位的值。 将这两个值留空会使视频成为自适应资产。

#### 使用智能裁切时 {#when-working-with-smart-crop}

使用Dynamic Media组件将智能裁剪图像资产添加到网页。 编辑该组件时，您可以选择使用预定义的视频查看器预设，以在页面上播放视频。

另请参阅 [图像用户档案](image-profiles.md)。

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

You can edit the following [!UICONTROL Dynamic Media Settings] by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>默认情况下，Dynamic media图像组件是自适应的。 如果要使其变为固定大小，请在“高级”选项卡的组件中设置 [!UICONTROL 它] ，并使用“宽度”和“高 **** 度” ****。

* **[!UICONTROL 图像修饰符]**您可以通过提供其他图像命令来应用图像效果。 图像预设和图像服务命令参考中介绍了这些设置。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

You can edit the following **[!UICONTROL Advanced]** settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 标题]**&#x200B;更改智能裁剪图像的标题。

* **[!UICONTROL 替代文]**本为关闭图形的用户添加智能裁剪图像的标题。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL URL，打开方式]**&#x200B;您可以设置资产以打开链接。 设置 URL，并在打开方式中指示是要在同一窗口中还是在新窗口中打开该 URL。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONCONTROL高度和宽** 度 ****&#x200B;如果希望智能裁剪图像具有固定大小，请输入以像素为单位的值。 将这两个值留空会使视频成为自适应资产。

### Interactive Media component {#interactive-media-component}

交互式媒体组件适用于具有交互功能的资产，例如热点或图像映射。如果您具有交互式图像、交互式视频或传送横幅，请使用交互式媒体组件。

交互式媒体组件是智能的——根据您添加的图像还是视频，您有各种选项。 此外，查看器是响应式的 - 其屏幕大小可根据设备屏幕大小自动进行更改。所有查看器都是 HTML5 查看器。

>[!NOTE]
>
>如果具有只读权限的用户访问的网页上存在Dynamic Media组件、交互式媒体组件或两者，则分页符和组件将无法正确呈现。 原因在于，重建页面是为了确保组件的属性良好，并且任何引用的资源和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
> 
>要避免此问题，请确保AEM Sites用户拥有访问资产所需的权限。

![chlimage_1-541](assets/chlimage_1-541.png)

您可以通过在组件中单击&#x200B;**[!UICONTROL 编辑]**，来编辑以下&#x200B;**[!UICONTROL 常规]**&#x200B;设置。

* **[!UICONTROL 查看器预]**&#x200B;设从下拉菜单中选择现有的查看器预设。 如果未显示您要查找的查看器预设，则可能需要将其显示出来。查看器预设必须先发布，然后才能使用。请参阅管理查看器预设。

* **[!UICONTROL 标题]**&#x200B;更改视频的标题。

* **[!UICONTROL 宽度]** 和 **[!UICONTROL 高]**&#x200B;度如果希望视频大小固定，请输入以像素为单位的值。 将这两个值留空会使视频成为自适应资产。

您可以通过在组件中单击&#x200B;**[!UICONTROL 编辑]**，来编辑以下&#x200B;**[!UICONTROL 添加到购物车]**&#x200B;设置。

* **[!UICONTROL 显示产品资]**&#x200B;产默认情况下，此值处于选中状态。 产品资产会按“商务”模块中的定义显示产品的图像。清除复选标记不会显示产品资产。

* **[!UICONTROL 显示产品价]**&#x200B;格默认情况下，此值处于选中状态。 产品价格会按“商务”模块中的定义显示项目的价格。清除复选标记不会显示产品价格。

* **[!UICONTROL 显示产品表]**&#x200B;单默认情况下，此值未选中。 产品表单包含所有产品变量，例如大小和颜色。清除复选标记不会显示产品变量。

### 全景媒体组件 {#panoramic-media-component}

全景媒体组件适用于那些球面全景图像的资源。 此类图像提供房间、房产、位置或风景的360°查看体验。 要使图像成为球形全景图，它必须具有以下任一或两者：

* 宽高比为2:1。
* 用关键字“equirectangular”或(“spherical” + “panorama”)或(“spherical” + “panoramic”)进行标记。 请参阅 [使用标记](/help/sites-authoring/tags.md)。

长宽比和关键字条件都适用于资产详细信息页面和“全景媒体”WCM组件的全景资产。

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

通过点按组件中的配置，可以编 **[!UICONTROL 辑以下]** 设置。

* **[!UICONTROL 查看器预]**&#x200B;设从查看器预设下拉菜单中选择现有查看器。

如果未显示您要查找的查看器预设，请检查以确保已发布该查看器预设。 您必须先发布查看器预设，然后才能使用它们。 请参阅[管理查看器预设](managing-viewer-presets.md)。

### 使用HTTP/2投放Dynamic Media资产 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2是新的、更新的Web协议，它改进了浏览器和服务器通信的方式。 它提供了更快的信息传输，并减少了所需的处理能力。 Dynamic Media资产的投放现在可以通过HTTP/2，从而提供更好的响应和加载时间。

有关 [Dynamic Media帐户的HTTP](http2.md) /2快速入门的完整详细信息，请参阅内容的HTTP2投放。

>[!MORELIKETHIS]
>
>* [了解使用AEM Dynamic Media进行颜色管理](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [将自定义视频缩略图与AEM Dynamic Media结合使用](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [了解AEM Dynamic Media的资产查看器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [将交互式视频与AEM Dynamic Media结合使用](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [在AEM Dynamic Media中使用视频播放器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [将图像锐化与AEM Dynamic Media结合使用](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

