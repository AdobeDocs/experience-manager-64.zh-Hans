---
title: 管理Dynamic Media查看器预设
seo-title: 管理Dynamic Media查看器预设
description: 如何创建和管理Dynamic Media查看器预设
seo-description: 如何创建和管理Dynamic Media查看器预设
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
translation-type: tm+mt
source-git-commit: fb4e6aef84d733c578e0f2ee7407016715e77cf5
workflow-type: tm+mt
source-wordcount: '4247'
ht-degree: 21%

---


# Managing Dynamic Media viewer presets {#managing-viewer-presets}

Dynamic Media查看器预设是一组设置，这些设置决定用户如何在其计算机屏幕和移动设备上视图富媒体资产。 如果您是管理员，则可以创建查看器预设。您可以设置一系列查看器配置选项。例如，可以更改查看器的显示大小或缩放行为。

有关创建和自定义您自己的HTML5查看器预设的说明，请参 *阅Adobe Scene7HTML5查看器SDK*。 SDK可在嵌入在SDK中的IS发布服务器上使用。 每个库版本都包含自己的SDK文档。

路径: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
例如，3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

See also the [Adobe Viewers Reference Guide](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html).

本节介绍如何创建、编辑和管理查看器预设。 无论您何时对资产进行预览，您都可以将查看器预设应用到资产。 See [Applying Viewer Presets](viewer-presets.md).

>[!NOTE]
>
>请注意，编 *辑任何预定义的现成查看器预设* ，都不受支持。 如果您尝试编辑现成的查看器预设，系统会提示您使用新名称保存查看器预设。

## 查看器的键盘辅助功能 {#keyboard-accessibility-for-viewers}

所有现成查看器都支持键盘辅助功能。

另请参阅 [键盘辅助功能和导航](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html)。

## Managing Dynamic Media viewer presets {#managing-presets}

You can add, edit, delete, publish, unpublish, and preview viewer presets in AEM by tapping **[!UICONTROL Tools > Assets > Viewer Presets]**.

![工具——资源](assets/tools-assets.png)

>[!NOTE]
>
>默认情况下，当您在资产的详细信息视图中选择查看器时，系统会显示15个查看器预设。 您可以提高此限制。请参阅[增加显示的查看器预设数量](#increasing-the-number-of-viewer-presets-that-display)。

## 对响应式设计网页的查看器支持 {#viewer-support-for-responsive-designed-web-pages}

不同的网页有不同的需求。 例如，有时您希望网页提供链接，在单独的浏览器窗口中打开HTML5查看器。 在其他情况下，可能需要将HTML5查看器直接嵌入到托管页面。 在后一种情况下，网页可能具有静态布局。 或者，它可能具有响应 *性* ，并在不同设备或不同浏览器窗口大小下以不同方式显示。 为了满足这些需求，Dynamic Media附带的所有预定义现成HTML5查看器都支持静态网页和响应式设计网页。

有关 [如何将响应](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) 式查看器嵌 ** 入到网页上的详细信息，请参阅“图像服务API帮助”中的响应式图像库。

>[!NOTE]
>
>请注意，您必须先发布所有现成的查看器，然后才能首次使用它们。\
>See [Publishing Viewer Presets.](#publishing-viewer-presets)

## 查看器预设系统兼容性  {#viewer-preset-system-compatibility}

Dynamic Media附带的所有现成查看器预设均与以下系统完全兼容：

* 台式机
* Apple iPhone
* Apple iPad
* Android智能手机
* Android平板电脑
* 对于视频，Blackberry和Windows Phone 8还提供了对MP4 [回放](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678)[的额外支持](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)。

### Rich media types for viewer presets {#rich-media-types-for-viewer-presets}

管理员在创建新查看器预设时可以添加和自定义以下富媒体类型。

| 富媒体类型 | 描述 |
|:---|:---|
| **轮播集** | 热点或图像映射，或者两者都添加到一系列两个或多个图像中。 客户可以向左或向右平移图像，然后单击图像上的热点以获取更多详细信息，或直接从网站的类别、主页或登陆页购买。 |
| **弹出缩放** | 在原始图像旁边显示缩放区域的副本图像。没有可用的控件 - 用户在要查看的区域上方移动选择。 |
|  | 在决定此查看器的整体带宽使用率时，请考虑到主图像和弹出图像都在查看器中呈现。主图像的大小（暂存宽度和暂存高度）和缩放因子决定弹出图像的大小。为避免弹出图像过大，请平衡这两个值：如果主图像较大，请减小缩放因子的值。（弹出宽度和弹出高度决定弹出窗口的大小，但它们不决定在查看器中呈现的弹出图像的大小。） |
|  | 例如，如果主图像的大小是 350 X 350 像素，缩放因子为 3，则生成的弹出图像的大小就是 1050 X 1050 像素。如果主图像的大小是 300 X 300 像素，缩放因子为 4，则弹出图像的大小就是 1200 X 1200 像素。根据 JPEG 质量设置（建议的设置在 80 到 90 之间），您可以显著减小文件的大小。建议的缩放因子为 2.5 到 4，具体视主图像的大小而定。 |
| **内联缩放** | 在原始查看器中显示缩放区域的图像。 没有可使用的控件。 即，用户将选定内容移动到要视图的区域上。 |
| **图像集** | 在“图像集”查看器中，用户可以通过单击缩略图，查看项目的不同视图或颜色变量。此查看器还提供了用于仔细检查图像的缩放工具。 |
| **交互式图像** | 热点会添加到图像的某些部分，然后客户可以单击这些部分以获取更多详细信息，或直接从网站的类别、主页或登陆页购买。 |
| **交互式视频** | 缩略图会添加到视频中的时间轴区段，然后客户可以单击该区段以获取更多详细信息，或直接从网站的类别、主页或登陆页购买。 |
| **混合媒体** | 在一个查看器中显示不同类型的媒体。您可以包含旋转集、图像集、图像和视频。 |
| **全景图像** | 全景图像和全景VR查看器渲染球面全景图像，让用户沉浸在房间、房产、位置或风景的360°观看体验中。 |
|  | 要使上传的图像符合球面全景图的要求，它必须具有以下任一或两者： <ul><li>宽高比为2:1。</li><li>用关键字标记为等角形、球形和全景图、球形和全景图。 请参 [阅使用标记](../sites-authoring/tags.md)。</li></ul> |
|  | 长宽比和关键字条件均适用于资产详细信息页面和“全景媒体”WCM组件的全景资产。 |
|  | 重要： 此查看器仅在Dynamic Media -Scene7模式下可用。 |
| **旋转集** | 提供图像的不同视图，以便用户可以旋转对象来从不同的侧边和角度进行检查。 |
| **视频** | 使用渐进式或自适应比特率流播放视频。 自适应比特率流会自动执行设备和带宽检测，以正确的格式提供正确质量的视频。 |
| **垂直缩放** | 通过垂直缩放查看器，您可以最大化产品图像查看体验，为用户提供最佳的产品展示效果。 色板的垂直位置如下所示： <ul><li>确保色板位于折叠上方。 使用水平色板(具体取决于用户的桌面屏幕大小)时，只有用户向下滚动页面后，才能显示色板。 通过将色板垂直放置在查看器中，可确保无论用户的屏幕大小如何，色板都是可见的。</li><li>最大化主图像大小。 使用水平色板时，必须在页面上保留空间，以确保它们可见。 此定位缩小了主图像的大小。 但是，对于垂直色板布局，您无需分配此空间。 因此，您可以最大化主图像大小。</li></ul> |
| **缩放** | 用户可以通过单击该选项来缩放区域。用户可以单击相应控件来放大图像、缩小图像以及将图像重置为默认大小。 |

## 列表现成查看器预设 {#list-of-out-of-the-box-viewer-presets}

下表列出了Dynamic Media附带的所有预定义现成查看器预设。

另请参 [阅实时演示](https://landing.adobe.com/zh-Hans/na/dynamic-media/ctir-2755/live-demos.html)。

有关查看器支持的Web浏览器和操作系统版本的信息，可以查看查看器发行说明。

请参 *阅《查看器* 参考指南》的目录 [中的查看器发行说明](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html)。

>[!NOTE]
>
>Dynamic Media中的所有现成查看器预设均已激活（开启），但您必须发布它们。\
>See [Publishing Viewer Presets](#publishing-viewer-presets).
>
>您创建和添加的任何新查看器预设都必须同时激活 *和发* 布。\
>请参 [阅激活或取消激活查看器预设](#activating-or-deactivating-viewer-presets) 和发 [布查看器预设](#publishing-viewer-presets)。

| 查看器预设标题 | 类型 | CSS 文件名称 |
|:---|:---|:---|
| 传送_虚线_深色 | 传送(_S) | html5_carouselviewer_dotted_dark.css |
| 轮盘_虚线_光 | 传送(_S) | html5_carouselviewer_dotted_light.css |
| 传送_数字_暗 | 传送(_S) | html5_carouselviewer_numeric_dark.css |
| 传送_数字_光 | 传送(_S) | html5_carouselviewer_numeric_light.css |
| 弹出 | 弹出_缩放 | html5_flyoutviewer.css |
| ImageSet_dark | 图像集 | html5_zoomviewer_dark.css |
| ImageSet_light | 图像集 | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | 混合媒体 | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | 混合媒体 | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | 弹出_缩放 | html5_inlinezoomviewer.css |
| 混合媒体_深色 | 混合媒体 | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | 混合媒体 | html5_mixedmediaviewer_light.css |
| PanoramicImage | 全景图像 | html5_panoramicimage.css |
| PanoramicImageVR | 全景图像 | html5_panoramicimage.css |
| Shoppable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shoppable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Interactive_Video | html5_interactivevideover_light.css |
| SpinSet_dark | 旋转集 | html5_spinviewer_dark.css |
| SpinSet_light | 旋转集 | html5_spinviewer_light.css |
| 视频（包括对隐藏式字幕的支持） | 视频 | html5_videoviewer.css |
| Video_social（包括对隐藏式字幕和社交媒体的支持） | 视频 | html5_videoviewersocial.css |
| Zoom_dark | 缩放 | html5_basiczoomviewer_dark.css |
| Zoom_light | 缩放 | html5_basiczoomviewer_light.css |
| ZoomVertical_dark | 垂直缩放 | html5_zoomverticalviewer_dark.css |
| ZoomVertical_light | 垂直缩放 | html5_zoomverticalviewer_light.css |

### 支持的移动查看器手势矩阵 {#supported-mobile-viewers-gestures-matrix}

下表标识了iOS、Android 2.x和Android 3.x设备支持的移动查看器手势。

| 手势 | 弹出缩放 | 缩放 | 旋转 |
|---|---|---|---|
| **拖动** | 平移 | 平移 | 平移 |
| **点按** | 显示弹出窗口 | 显示或隐藏用户界面 | 显示或隐藏用户界面 |
| **多次点击** | 不适用 | 放大或重置 | 放大或重置 |
| **开合** | 不适用 | 放大（仅限iOS和Android 3x） | 放大（仅限iOS和Android 3x） |
| **捏合关闭** | 不适用 | 缩小（仅限iOS和Android 3x） | 缩小（仅限iOS和Android 3x） |
| **轻扫** | 滚动色板条 | 滚动图像 | 旋转 |
| **弗里克** | 滚动色板条 | 滚动图像 | 旋转 |

## 增加显示的Dynamic Media查看器预设数 {#increasing-the-number-of-viewer-presets-that-display}

AEM在从“详细信息”视图>“查看器”查看资产时显示 **[!UICONTROL 各种查看器预设]**。 您可以增加或减少显示的查看器数量。

**要增加显示的Dynamic Media查看器预设的数量，请执行以下操作**:

1. 导航到 **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 导航到位于的查看器预设列表节点 `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. 在 **[!UICONTROL limit]** 属性中，将默认设 **[!UICONTROL 置为15的Value]**（值）更改为所需的数字。
1. 导航到查看器预设数据源： `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. 在limit属 **[!UICONTROL 性中]** ，将数字更改为所需的数字，例如 `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 点按 **[!UICONTROL 全部保存]**。

## 创建新的Dynamic Media查看器预设 {#creating-a-new-viewer-preset}

通过创建查看器预设，您可以将各种设置应用于视图并与资产交互。 但是，您无需创建新的查看器预设。 如果您愿意，可以使用AEM Assets附带的现成默认查看器预设。

如果选择创建新的查看器预设，则在保存该查看器预设后，查看器的状态将在“查看器预设”页面中自动激 **活**(设置 **[!UICONTROL 为开启]** )。 此状态意味着无论您何时预览图 **[!UICONTROL 像或视频]** ，都可以在 **[!UICONTROL Dynamic Media组件]** 和交互式媒体组件中看到它。

某些查看器预设具有排他性设置，这些设置会影响查看器的使用和整体行为。 根据您正在创建的查看器预设，您可能需要注意这些特殊注意事项。

请参 [阅创建交互式查看器预设的特殊注意事项](#special-considerations-for-creating-an-interactive-viewer-preset)。

请参 [阅创建传送横幅查看器预设的特殊注意事项](#special-considerations-for-creating-a-carousel-banner-viewer-preset)。

**要创建新的Dynamic Media查看器预设，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.

   ![查看器预设](assets/viewerpresets.png)

1. 在“查看 **[!UICONTROL 器预设]** ”页面的工具栏中，点按 **[!UICONTROL 创建]**。
1. 在&#x200B;**[!UICONTROL 新查看器预设]**&#x200B;对话框的&#x200B;**[!UICONTROL 预设名称]**&#x200B;字段中，输入新预设的名称。请谨慎选择该名称，因为在您点按&#x200B;**[!UICONTROL 创建]**&#x200B;后，将再也不能编辑该名称。

   When you save the preset later in these steps, the name appears on the Viewer Presets page under the **[!UICONTROL Preset Title]** column header.

1. 在富媒 **[!UICONTROL 体类型]** 下拉菜单中，选择要创建的查看器预设类型，然后点按页面右上角的创 **[!UICONTROL 建]**。

   请参阅[查看器预设的富媒体类型](#rich-media-types-for-viewer-presets)。

1. On the **Edit Viewer Preset** page, tap the **[!UICONTROL Appearance]** tab.
1. 执行下列操作之一：

   * In the **[!UICONTROL Selected Type]** pull-down menu, select a component whose visual design you want to customize. 或者，您也可以点按查看器中的任何可视元素，以将其选中进行配置。

      通过可视编辑器，您可以查看特定属性对样式的影响。 只需设置或调整任何属性，即可使用编辑器左侧的范例即时查看它对查看器有何影响。

      《查看器参考指南》中的任何“自定义&lt;viewer_name>查 *看器”帮助主题* ，都介绍了每种类型的查看器预设 [的CSS样式属性](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html)。

      例如，如果要创建类型的查看器预设，请参 `Mixed_Media`阅自定 [义混合媒体查看器](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) ，了解列表和每个属性的说明。

   * 如果您在单独的CSS文件中定义了样式设置，则可以将CSS文件上传到AEM Assets。 Tap **[!UICONTROL Import CSS]** below the **[!UICONTROL Selected Type]** pull-down menu (you may need to scroll the visual editor up to see it) to find the uploaded CSS file and associate it with the viewer preset.

      导入CSS文件时，可视编辑器会检查CSS是否使用正确的查看器标记。 例如，如果要创建缩放查看器，则必须使用父查看器元素上定义的查看器类名称来定义您导 `.s7mixedmediaviewer` 入的所有CSS规则。

      只要正确定义给定查看器的CSS标记，就可以导入任意手工CSS。 (CSS标记在《查看器参考指南》的任 *何“自定义&lt;查看器* 名称>查看器”帮助 [主题中均有介绍](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html)。 例如，如果要阅读有关缩放查看器的CSS标记，请参阅自 [定义缩放查看器](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html)。) 但是，可视编辑器可能不理解某些CSS值。 在这种情况下，可视编辑器会尝试覆盖错误，以便CSS仍可正常工作。
   >[!NOTE]
   >
   >如果您希望直接在其原始表单中编辑 CSS，请点按“选定类型”下拉菜单下的&#x200B;**[!UICONTROL 显示/隐藏 CSS]**（您可能需要向上滚动可视编辑器才能看到此选项）。****
   >
   >与可视编辑器一样，当您直接在CSS中更改属性时，您可以立即看到它对查看器范例产生的影响。 并且，同一属性会在可视编辑器中同时自动更新。 因此，您可以使用原始CSS编辑器或可视编辑器，或同时使用两者。

   >[!NOTE]
   >
   >对于按钮图稿，选择2x图像并上传高分辨率图稿。 处理交互式图像和购物横幅时，您还可以从各种现成的热点按钮中进行选择。

1. (Optional) Near the top of the **[!UICONTROL Edit Viewer Preset]** page, tap **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]**, or **[!UICONTROL Phone]** to uniquely define visual styles for different device and screen types.
1. On the **[!UICONTROL Edit Viewer Preset]** page, tap the **Behavior** tab. 或者，您也可以点按或单击查看器中的任何可视元素，以选择进行配置。
1. 从&#x200B;**[!UICONTROL 选定类型]**&#x200B;下拉菜单中，选择要更改其行为的组件。

   可视编辑器中的许多组件都有与其关联的详细说明。 当您展开组件以显示其关联的参数时，这些说明会显示在蓝色框中。

   有些“查看器类型”具有的组件允许您在 **IS 命令**&#x200B;文本字段中指定“图像提供”命令。有关可使用的命令列表，请参阅[图像提供 API 参考](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html)。

   >[!NOTE]
   >
   >**如果您使用触控设备，如手机或平板电脑……**
   >
   >在文本字段中键入值后，点按用户界面中的其他位置，以提交所做的更改并关闭虚拟键盘。如果您点按 **[!UICONTROL Enter]**，则不会执行任何操作。

1. 在页面的右上角附近，点按&#x200B;**[!UICONTROL 保存]**。
1. 发布新查看器预设。 您必须先发布预设，然后才能在您的网站上使用预设。

   See [Publishing Viewer Presets](#publishing-viewer-presets).

## 创建交互式查看器预设的特殊注意事项 {#special-considerations-for-creating-an-interactive-viewer-preset}

**关于面板中图像缩略图的显示模式**

When you create or edit an Interactive Video viewer preset, you have the choice of which **[!UICONTROL Display Mode]** setting to use when you select `InteractiveSwatches` from the **[!UICONTROL Selected Component]** pull-down menu under the **[!UICONTROL Behavior]** tab. 您选择的显示模式会影响缩略图在视频播放时的显示方式和显示时间。 You can choose either a `segment`display mode (default) or a `continuous`display mode.

| 显示模式 | 描述 |
|---|---|
| [!UICONTROL 区段] | [!UICONTROL 区段] 是现成的交互式视频查看器预设Shoppable_Video_light和Shoppable_Video_dark的默认显示模式，以及您自己创建的任何交互式视频查看器预设。 |
|  | 在此模式下，当分配给视频区段的缩略图数少于显示面板中的可见点数时，不会从下一个或以前的子区段中提取缩略图来填充面板中的任何空白点。 即保留分配给特定视频段的色板的显示。 |
| [!UICONTROL 连续] | In [!UICONTROL Continuous] display mode, if the number of thumbnails in a segment is less than the number that are visible in the panel, the viewer automatically includes the display of thumbnails from the next segment, or the previous segment, in cases where the last thumbnail is displayed. |

**关于交互式视频查看器中的自动滚动行为**

交互式视频查看器中缩略图的自动滚动行为与您选择的显示模式无关。

When you create or edit an interactive video viewer preset, you access **[!UICONTROL Auto Scroll]** from the **[!UICONTROL Behavior]** tab. 在“行为”选项卡的&#x200B;**[!UICONTROL 选定的组件]**&#x200B;下拉菜单中，点按 **[!UICONTROL InteractiveSwatches]**。The **[!UICONTROL Auto Scroll]** check box is listed below the IS Command text field.

如果在查看器预设中禁用&#x200B;**[!UICONTROL 自动滚动]**（清除复选框），则在用户播放视频时，该面板仅显示整个视频长度的第一个缩略图。但是，如果需要，用户可以使用向上和向下箭头图标手动滚动缩略图。

在查看器预设中启用（选择）**[!UICONTROL 自动滚动]**&#x200B;后，在视频播放过程中，分配给视频区段的缩略图图像会在区段开始时滚动到视图中。但是，在某些情况下，区段内某些缩略图的显示时间是其之前或之后缩略图显示时间的两倍。发生此行为的原因是区段中缩略图的数量大于面板中可见缩略图的数量，且不可平均分割。

为了说明这一点，假定您有一个30秒的视频区段。 在30秒内共显示9个缩略图。 您的浏览器的大小调整为显示面板中有四个可见的缩略图位置。 30秒视频时间段分为三个子段。 下表显示了特定时间子区段显示哪些缩略图的细分：

| **视频子区段** | **子区段时间（以秒为单位）** | **面板中可见的缩略图** |
|---|---|---|
| 1 | 0-10 | 1，2，3，4 |
| 2 | 10-20 | 4，5，6，7 |
| 3 | 20-30 | 6，7，8，9 |

视频子区段3不超出分配给它的缩略图。 另请注意，缩略图 4、6 和 7 在面板中出现的时间是其他缩略图的两倍。

查看器根据可用位置数量，在面板中显示缩略图的数量逻辑如下：

* 子段数=舍入到下一个子段（缩略图数／缩略图面板中可见的插槽数，视浏览器窗口大小而定）。

   使用上表中的示例，9个缩略图/ 4个插槽= 2.25; 查看器逻辑将其舍入为3个子段。

* 缩略图数量=舍入到下一个缩略图（缩略图数量／视频子区段数量）。

   使用上表中的示例，9个缩略图/ 3个视频子区段= 3个缩略图。

* 子区段的持续时间=视频总持续时间／视频子区段的数量。

   使用上表中的示例，30秒/ 3个视频子段=每个视频子段的10秒显示。

### 创建传送横幅查看器预设的特殊注意事项 {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

创建传送横幅查看器预设时，可以按如下方式访问更改热点样式：

|  | **描述** | **操作** |
|---|---|---|
| **热点图标** | 更改用于热点的图标 | 要更改热点图标图像，请在“外观” **[!UICONTROL 选项卡]** 的“选 **[!UICONTROL 定组件”中]**，点 **[!UICONTROL 按ImageMapEffect]**。 Under **[!UICONTROL Icon]**, select **[!UICONTROL Background]** and in the **[!UICONTROL Image]** field navigate to the background image you want. |

## 激活或取消激活Dynamic Media查看器预设 {#activating-or-deactivating-viewer-presets}

用户界面中可用的查看器预设取决于哪些查看器预设在创作模式下处于活动状态。 默认情况下，查看器预设 *在创* 建后处于开启状态。 如果关闭预设，您将不会在创作模式下看到它。 如果预设已发布。 无论它是打开还是关闭，它都始终会被发布。 如果列表变得太笨重，或者您不希望某个查看器预设可供使用，您可能希望取消激活查看器预设。

**要激活或取消激活Dynamic Media查看器预设，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. 在“查 **[!UICONTROL 看器预设]** ”页面的“状态 **[!UICONTROL ”列标题下]** ，点按切换以激活或取消激活查看器预设。

   已激活的查看器预设可在右侧的蓝色框中进行切换； 停用的查看器预设可在灰色浅框内左侧显示切换。

## Publishing Dynamic Media viewer presets {#publishing-viewer-presets}

激活(或 *打开*)查看器预设的状态意味着查看器预设在Dynamic Media组件、交互式媒体组件中以及每次视图资产时都可见。

但是，要传送带有查看器预设的资产，还必须发布查看器预设。 All viewer presets must be activated *and* published to obtain URL or embed code for an asset. 您必须激活并发布Dynamic media附带的所有现成查看器预设。 您创建和添加的自定义查看器预设将自动激活，但也必须发布。

请参阅 [激活或取消激活查看器预设](#activating-or-deactivating-viewer-presets)。

另请参阅[预览资产](previewing-assets.md)。

**要发布Dynamic Media查看器预设，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. 选择一个或多个要发布的查看器预设。
1. 在工具栏中，点按&#x200B;**[!UICONTROL 发布]**&#x200B;图标。

## Sorting Dynamic Media viewer presets {#sorting-viewer-presets}

**要对Dynamic Media查看器预设进行排序，请执行以下操作**:

1. 点按 AEM 左上角的 AEM 徽标，然后点按左边栏中的&#x200B;**工具**（锤子图标）**[!UICONTROL > Assets > 查看器预设]**。
1. 单击&#x200B;**[!UICONTROL 预设标题]**、**[!UICONTROL 类型]**、**[!UICONTROL 已发布]**&#x200B;或&#x200B;**[!UICONTROL 状态]**&#x200B;来按列标题进行排序。例如，单击&#x200B;**[!UICONTROL 类型]**&#x200B;按字母顺序或反向字母顺序对查看器预设类型进行排序。

## Editing Dynamic Media viewer presets {#editing-viewer-presets}

请注意，编 *辑任何预定义的现成查看器预设* ，都不受支持。 如果您编辑现成的查看器预设，系统会提示您用新名称保存该查看器预设。

**要编辑Dynamic Media查看器预设，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. 选中查看器预设标题左侧的框，以选择预设。
1. 在工具栏中，点按&#x200B;**[!UICONTROL 编辑]**。
1. On the **[!UICONTROL Edit Viewer Preset]** page make the changes you want to the viewer preset.
1. 执行下列操作之一：

   * Tap **[!UICONTROL Save]** to save your changes and return to the **[!UICONTROL Viewer Preset]** page.
   * Tap **[!UICONTROL Cancel]** to void any changes you made and return to the **[!UICONTROL Viewer Preset]** page.

## 删除自定义Dynamic Media查看器预设 {#deleting-custom-viewer-presets}

您可以删除已创建并添加到Dynamic Media的查看器预设。

**要删除自定义Dynamic Media查看器预设，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Viewer Presets]**.
1. 在“查看 **[!UICONTROL 器预设]** ”页面上，选 **[!UICONTROL 中预设标题]**，然后点按废 **[!UICONTROL 纸篓图]** 标。
1. 点按 **[!UICONTROL 删除]**。

## Applying a Dynamic Media viewer preset to an asset {#applying-a-viewer-preset-to-an-asset}

如果已发布资产和选定的查看器，则在选择查看器预设后 **[!UICONTROL 将显示]** “ **[!UICONTROL URL]** ”和“嵌入”按钮。

**要将Dynamic Media查看器预设应用到资产，请执行以下操作**:

1. 打开资产，在页面左上角附近，点按下拉菜单，然后选择查 **[!UICONTROL 看器]**。

   >[!NOTE]
   >
   >如果已发布资产和选定的查看器，则在选择查看器预设后 **[!UICONTROL 将显示]** “ **[!UICONTROL URL]** ”和“嵌入”按钮。

1. 从左侧窗格中选择一个查看器预设，以将其应用到资产。

   You can [copy the URL to share](linking-urls-to-yourwebapplication.md) with other users.

## 使用Dynamic Media查看器预设传送资产 {#delivering-assets-with-viewer-presets}

要获取查看器预设的 URL，请参阅[将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md)。另请参阅[将视频查看器嵌入网页](embed-code.md)。

如果您使用AEM作为WCM，则可以直接在页面上使用查看器预设添加资产。 See [Adding Dynamic Media Assets to Pages](adding-dynamic-media-assets-to-pages.md).
