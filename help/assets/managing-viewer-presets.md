---
title: 管理Dynamic Media查看器预设
seo-title: Managing Dynamic Media viewer presets
description: 如何创建和管理Dynamic Media查看器预设
seo-description: How to create and manage Dynamic Media viewer presets
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Viewer Presets
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4256'
ht-degree: 11%

---

# 管理Dynamic Media查看器预设 {#managing-viewer-presets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Dynamic Media查看器预设是一组设置，用于确定用户在其计算机屏幕和移动设备上查看富媒体资产的方式。 如果您是管理员，则可以创建查看器预设。 设置适用于查看器配置选项数组。 例如，您可以更改查看器的显示大小或缩放行为。

有关创建和自定义您自己的HTML5查看器预设的说明，请参阅AdobeDynamic Media *HTML5查看器SDK API文档*. 该SDK位于嵌入在SDK中的IS发布服务器上。 每个库版本都包含其自己的SDK文档。

路径: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
例如，3.10 SDK: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

另请参阅 [AdobeDynamic Media查看器参考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

本节介绍如何创建、编辑和管理查看器预设。 无论您何时预览资产，都可以将查看器预设应用到资产。 请参阅 [应用查看器预设](viewer-presets.md).

>[!NOTE]
>
>请注意，编辑任意 *预定义的现成查看器预设* 不支持此方案。 如果您尝试编辑现成的查看器预设，系统会提示您使用新名称保存查看器预设。

## 查看器的键盘辅助功能 {#keyboard-accessibility-for-viewers}

所有现成的查看器都支持键盘辅助功能。

另请参阅 [键盘辅助功能和导航](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## 管理Dynamic Media查看器预设 {#managing-presets}

您可以通过点按在AEM中添加、编辑、删除、发布、取消发布和预览查看器预设 **[!UICONTROL 工具>资产>查看器预设]**.

![tools-assets](assets/tools-assets.png)

>[!NOTE]
>
>默认情况下，当您在资产的详细信息视图中选择查看器时，系统会显示15个查看器预设。 您可以提高此限制。请参阅[增加显示的查看器预设数量](#increasing-the-number-of-viewer-presets-that-display)。

## 查看器支持响应式设计的网页 {#viewer-support-for-responsive-designed-web-pages}

不同的网页有不同的需求。 例如，有时您希望网页提供一个链接，以在单独的浏览器窗口中打开HTML5查看器。 在其他情况下，可能需要直接将HTML5查看器嵌入到托管页面。 在后一种情况下，网页可以具有静态布局。 或者，可能 *响应式* 和在不同设备或浏览器窗口大小不同的情况下以不同的方式显示。 为了满足这些需求，Dynamic Media附带的所有预定义开箱即用HTML5查看器都支持静态网页和响应式设计的网页。

请参阅 [响应式图像库](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) 在 *图像提供API帮助* 有关如何将响应式查看器嵌入网页的更多信息。

>[!NOTE]
>
>请注意，在首次使用所有现成查看器之前，必须先发布这些查看器。\
>请参阅 [发布查看器预设。](#publishing-viewer-presets)

## 查看器预设系统兼容性  {#viewer-preset-system-compatibility}

Dynamic Media附带的所有现成查看器预设都与以下系统完全兼容：

* 台式机
* AppleiPhone
* AppleiPad
* Android智能手机
* Android平板电脑
* 对于视频，还提供了对MP4播放的其他支持 [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) 和 [Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### 查看器预设的富媒体类型 {#rich-media-types-for-viewer-presets}

管理员在创建新查看器预设时，可以添加和自定义以下富媒体类型。

| 富媒体类型 | 描述 |
|:---|:---|
| **轮播集** | 热点或图像映射，或两者都添加到两个或更多图像的系列中。 客户可以向左或向右平移图像，然后单击图像上的热点以获取更多详细信息，或直接从网站的类别、主页或登陆页面购买。 |
| **弹出缩放** | 在原始图像旁边显示缩放区域的第二个图像。 没有可使用的控件 — 用户将所选内容移动到要查看的区域上。 |
|  | 在确定此查看器的完整带宽使用情况时，请考虑在查看器中同时提供主图像和弹出图像。 主图像大小（暂存宽度和暂存高度）和缩放因子决定弹出图像的大小。 要防止弹出文件过大，请平衡以下两个值：如果主图像较大，请降低缩放因子值。 （弹出宽度和弹出高度决定弹出窗口的大小，但不决定提供给查看器的弹出图像的大小。） |
|  | 例如，如果主图像的大小为350 x 350像素，缩放因子为3，则生成的弹出图像的大小为1050 x 1050像素。 如果主图像大小为300 x 300像素，缩放因子为4，则弹出图像的大小为1200 x 1200像素。 根据JPEG质量设置（建议的设置介于80到90之间），您可以显着减小文件大小。 推荐的缩放因子为2.5到4，具体取决于主图像的大小。 |
| **内联缩放** | 在原始查看器中显示缩放区域的图像。 没有可使用的控件。 也就是说，用户会在要查看的区域上移动所做的选择。 |
| **图像集** | 在图像集查看器中，用户可以通过单击缩略图来查看项目的不同视图或颜色变化。 此查看器还提供了用于仔细检查图像的缩放工具。 |
| **交互式图像** | 热点会添加到图像的某些部分，随后客户可以单击这些部分以获取更多详细信息，或直接从网站的类别、主页或登陆页面购买。 |
| **交互式视频** | 缩略图会添加到视频中的时间轴区段，客户随后可以单击该区段以获取更多详细信息，或直接从网站的类别、主页或登陆页面购买。 |
| **混合媒体** | 在一个查看器中显示不同类型的媒体。 您可以包含旋转集、图像集、图像和视频。 |
| **全景图像** | 全景图像和全景VR查看器可渲染球面全景图像，以让用户沉浸在房间、属性、位置或景观的360°观看体验中。 |
|  | 要使上传的图像符合球面全景图的条件，该图像必须具有以下任一项或两项： <ul><li>宽高比为2:1。</li><li>使用等矩形关键字标记，或者使用球面和全景关键字标记，或者使用球面和全景关键字标记。 请参阅 [使用标记](../sites-authoring/tags.md).</li></ul> |
|  | 纵横比和关键字条件都适用于资产详细信息页面和“全景媒体”WCM组件的全景资产。 |
|  | 重要信息：此查看器仅在Dynamic Media - Scene7模式下可用。 |
| **旋转集** | 提供图像的多个视图，以便用户可以旋转对象以检查不同的侧边和角度。 |
| **视频** | 使用渐进式比特率流或自适应比特率流播放视频。 自适应比特率流自动执行设备和带宽检测，以正确的格式提供正确质量的视频。 |
| **垂直缩放** | 通过垂直缩放查看器，您可以最大化产品图像查看体验，从而让用户更好地呈现产品。 色板的垂直位置可执行以下操作： <ul><li>确保色板位于折页上方。 使用水平色板时，根据用户的桌面屏幕大小，在用户向下滚动页面之前，不会显示色板。 通过将色板垂直放置在查看器中，可确保无论用户的屏幕大小如何，都可以看到这些色板。</li><li>最大化主图像大小。 使用水平色板时，必须保留页面上的空间，以确保它们可见。 此定位缩小了主图像的大小。 但是，使用垂直色板布局时，您无需分配此空间。 因此，您可以最大化主图像大小。</li></ul> |
| **缩放** | 允许用户通过单击来放大区域。 用户可以单击控件来放大、缩小图像，并将图像重置为默认大小。 |

## 现成查看器预设列表 {#list-of-out-of-the-box-viewer-presets}

下表标识了Dynamic Media附带的所有预定义现成查看器预设。

另请参阅 [实时演示](https://landing.adobe.com/zh-Hans/na/dynamic-media/ctir-2755/live-demos.html).

有关查看器支持的Web浏览器和操作系统版本的信息，您可以查看查看器发行说明。

请参阅 *查看器发行说明* 目录 [查看器参考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

>[!NOTE]
>
>Dynamic Media中所有现成的查看器预设均已激活（开启），但您必须发布它们。\
>请参阅 [发布查看器预设](#publishing-viewer-presets).
>
>您创建和添加的任何新查看器预设都必须同时激活 *和* 已发布。\
>请参阅 [激活或取消激活查看器预设](#activating-or-deactivating-viewer-presets) 和 [发布查看器预设](#publishing-viewer-presets).

| 查看器预设标题 | 类型 | CSS 文件名称 |
|:---|:---|:---|
| 轮播_点线_深色 | 轮播(_S) | html5_carouselviewer_dotted_dark_css |
| 轮播_虚线_光 | 轮播(_S) | html5_carouselviewer_dotted_light.css |
| 轮播_数值_深色 | 轮播(_S) | html5_carouselviewer_numeric_dark_css |
| 轮播_数值_光 | 轮播(_S) | html5_carouselviewer_numeric_light.css |
| 弹出 | Flyout_Zoom | html5_flyoutviewer.css |
| ImageSet_dark | 图像集 | html5_zoomviewer_dark.css |
| ImageSet_light | 图像集 | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | 混合媒体 | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | 混合媒体 | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | Flyout_Zoom | html5_inlinezoomviewer.css |
| MixedMedia_dark | 混合媒体 | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | 混合媒体 | html5_mixedmediaviewer_light.css |
| 全景图像 | 全景图像(_I) | html5_panoramicimage.css |
| 全景图像VR | 全景图像(_I) | html5_panoramicimage.css |
| Shoppable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shoppable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark_css |
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

下表标识了iOS、Android 2.x和Android 3.x设备上支持的移动查看器手势。

| 手势 | 弹出缩放 | 缩放 | 旋转 |
|---|---|---|---|
| **拖动** | 平移 | 平移 | 平移 |
| **点按** | 显示弹出窗口 | 显示或隐藏用户界面 | 显示或隐藏用户界面 |
| **双击** | 不适用 | 放大或重置 | 放大或重置 |
| **捏开** | 不适用 | 放大(仅iOS和Android 3x) | 放大(仅iOS和Android 3x) |
| **捏合关闭** | 不适用 | 缩小(仅限iOS和Android 3x) | 缩小(仅限iOS和Android 3x) |
| **轻扫** | 滚动色板条 | 滚动图像 | 旋转 |
| **弗里克** | 滚动色板条 | 滚动图像 | 旋转 |

## 增加显示的Dynamic Media查看器预设数 {#increasing-the-number-of-viewer-presets-that-display}

AEM在从以下位置查看资产时，会显示各种查看器预设 **[!UICONTROL 详细信息视图>查看器]**. 您可以增加或减少显示的查看器数量。

**要增加显示的Dynamic Media查看器预设数，请执行以下操作**:

1. 导航到 **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 导航到位于的查看器预设列表节点 `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. 在 **[!UICONTROL limit]** 属性中，将默认设 **[!UICONTROL 置为15的Value]**（值）更改为所需的数字。
1. 导航到位于的查看器预设数据源 `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. 在 **[!UICONTROL 限制]** 属性中，例如将数字更改为所需的数字 `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 点按 **[!UICONTROL 全部保存]**.

## 创建新的Dynamic Media查看器预设 {#creating-a-new-viewer-preset}

通过创建查看器预设，您可以应用各种设置来查看资产并与之交互。 但是，您无需创建新的查看器预设。 如果您愿意，可以使用AEM Assets附带的默认现成查看器预设。

如果您选择创建新的查看器预设，则在保存该查看器预设后，查看器的状态将自动激活(设置为 **开**) **[!UICONTROL 查看器预设]** 页面。 此状态表示它在 **[!UICONTROL Dynamic Media]** 组件和 **[!UICONTROL 交互式媒体]** 组件，以及预览图像或视频时的使用说明。

某些查看器预设具有可影响查看器的使用和整体行为的排他设置。 根据您创建的查看器预设，您可能需要注意这些特殊注意事项。

请参阅 [创建交互式查看器预设的特殊注意事项](#special-considerations-for-creating-an-interactive-viewer-preset).

请参阅 [创建轮播横幅查看器预设的特殊注意事项](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**创建新的Dynamic Media查看器预设**:

1. 点按AEM左上角的AEM徽标，然后点按左边栏中的 **[!UICONTROL 工具>资产>查看器预设]**.

   ![查看器预设](assets/viewerpresets.png)

1. 在 **[!UICONTROL 查看器预设]** 页面，在工具栏中，点按 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL 新查看器预设]** 对话框中 **[!UICONTROL 预设名称]** 字段，输入新预设的名称。 请仔细选择名称 — 在您点按后，这些名称将不可编辑 **[!UICONTROL 创建]**.

   当您稍后在这些步骤中保存预设时，该预设的名称会显示在“查看器预设”页面的 **[!UICONTROL 预设标题]** 列标题。

1. 在 **[!UICONTROL 富媒体类型]** 下拉菜单中，选择要创建的查看器预设类型，然后点按页面右上角的 **[!UICONTROL 创建]**.

   请参阅 [查看器预设的富媒体类型](#rich-media-types-for-viewer-presets).

1. 在 **编辑查看器预设** 页面，点按 **[!UICONTROL 外观]** 选项卡。
1. 执行下列操作之一：

   * 在 **[!UICONTROL 选定类型]** 下拉菜单中，选择要自定义其可视设计的组件。 或者，您也可以点按查看器中的任何可视元素以选择进行配置。

      通过可视编辑器，您可以查看特定属性对样式有何影响。 只需设置或调整任何属性，即可使用编辑器左侧的示例立即查看该属性对查看器有何影响。

      每种类型的查看器预设的CSS样式属性在任何“自定义” *&lt;viewer_name>* 查看者”帮助主题 [查看器参考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

      例如，如果您创建的是类型的查看器预设 `Mixed_Media`，请参阅 [自定义混合媒体查看器](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) ，以获取每个属性的列表和描述。

   * 如果您在单独的CSS文件中定义了样式设置，则可以将CSS文件上传到AEM Assets。 点按 **[!UICONTROL 导入CSS]** 下面 **[!UICONTROL 选定类型]** 下拉菜单（您可能需要向上滚动可视编辑器才能看到它），以查找上传的CSS文件并将其与查看器预设关联。

      导入CSS文件时，可视编辑器会检查CSS是否使用正确的查看器标记。 例如，如果要创建缩放查看器，则必须使用其查看器类名称定义导入的所有CSS规则 `.s7mixedmediaviewer` 在父查看器元素上定义。

      只要为给定查看器正确定义CSS标记，就可以导入任意手工CSS。 (CSS标记在任何“自定义” *&lt;viewer name=&quot;&quot;>* 查看者”帮助主题 [查看器参考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html). 例如，如果要阅读有关缩放查看器的CSS标记，请参阅 [自定义缩放查看器](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) 但是，可视编辑器可能无法理解某些CSS值。 在这种情况下，可视编辑器会尝试覆盖错误，以便CSS仍然可以工作。
   >[!NOTE]
   >
   >如果您希望直接在其原始表单中编辑 CSS，请点按“选定类型”下拉菜单下的&#x200B;**[!UICONTROL 显示/隐藏 CSS]**（您可能需要向上滚动可视编辑器才能看到此选项）。****
   >
   >与可视编辑器一样，当您直接在CSS中更改属性时，您可以立即查看该属性对查看器示例有何影响。 而且，该同一属性会在可视化编辑器中同时自动更新。 因此，您可以使用原始CSS编辑器或可视编辑器，或者两者交替使用。

   >[!NOTE]
   >
   >对于按钮图稿，选择2x图像并上传高分辨率艺术品。 使用交互式图像和购物横幅时，您还可以从各种现成的热点按钮中进行选择。

1. （可选）靠近 **[!UICONTROL 编辑查看器预设]** 页面，点按 **[!UICONTROL 桌面]**, **[!UICONTROL 平板电脑]**&#x200B;或 **[!UICONTROL 电话]** 用于为不同设备和屏幕类型唯一定义可视样式。
1. 在 **[!UICONTROL 编辑查看器预设]** 页面，点按 **行为** 选项卡。 或者，您也可以点按或单击查看器中的任何可视元素，以选择进行配置。
1. 从&#x200B;**[!UICONTROL 选定类型]**&#x200B;下拉菜单中，选择要更改其行为的组件。

   可视化编辑器中的许多组件都有与其关联的详细说明。 当您展开组件以显示其关联参数时，这些描述会显示在蓝色框中。

   有些“查看器类型”具有的组件允许您在 **IS 命令**&#x200B;文本字段中指定“图像提供”命令。有关可使用的命令列表，请参阅[图像提供 API 参考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html)。

   >[!NOTE]
   >
   >**如果您使用的是触控设备，如手机或平板电脑……**
   >
   >在文本字段中键入值后，点按用户界面中的其他位置，以提交更改并关闭虚拟键盘。 如果您点按 **[!UICONTROL 输入]**，则不会执行任何操作。

1. 在页面的右上角附近，点按 **[!UICONTROL 保存]**.
1. 发布新查看器预设。 您必须先发布预设，然后才能在您的网站上使用预设。

   请参阅 [发布查看器预设](#publishing-viewer-presets).

## 创建交互式查看器预设的特殊注意事项 {#special-considerations-for-creating-an-interactive-viewer-preset}

**关于面板中图像缩略图的显示模式**

在创建或编辑交互式视频查看器预设时，您可以选择 **[!UICONTROL 显示模式]** 设置 `InteractiveSwatches` 从 **[!UICONTROL 选定的组件]** 下方的下拉菜单 **[!UICONTROL 行为]** 选项卡。 您选择的显示模式会影响视频播放时缩略图的显示方式和显示时间。 您可以选择 `segment`显示模式（默认）或 `continuous`显示模式。

| 显示模式 | 描述 |
|---|---|
| [!UICONTROL 市场细分] | [!UICONTROL 区段] 是现成交互式视频查看器预设的默认显示模式：Shoppable_Video_light和Shoppable_Video_dark，以及您自己创建的任何交互式视频查看器预设。 |
|  | 在此模式下，如果分配给视频区段的缩略图数量少于显示面板中的可见点数，则不会提取下一个或上一个子区段的缩略图以填充面板中的任何空白点。 即，它保留分配给特定视频区段的色板的显示。 |
| [!UICONTROL 连续] | 在 [!UICONTROL 连续] 显示模式下，如果区段中缩略图的数量小于面板中可见缩略图的数量，则在显示最后一个缩略图的情况下，查看器会自动包含来自下一个区段或上一个区段的缩略图显示。 |

**关于交互式视频查看器中的自动滚动行为**

交互式视频查看器中缩略图的自动滚动行为与您选择的显示模式无关。

在创建或编辑交互式视频查看器预设时，您可以访问 **[!UICONTROL 自动滚动]** 从 **[!UICONTROL 行为]** 选项卡。 在“行为”选项卡的&#x200B;**[!UICONTROL 选定的组件]**&#x200B;下拉菜单中，点按 **[!UICONTROL InteractiveSwatches]**。的 **[!UICONTROL 自动滚动]** 复选框列在“IS命令”文本字段的下方。

如果在查看器预设中禁用&#x200B;**[!UICONTROL 自动滚动]**（清除复选框），则在用户播放视频时，该面板仅显示整个视频长度的第一个缩略图。但是，如果需要，用户可以使用向上和向下箭头图标手动滚动缩略图。

在查看器预设中启用（选择）**[!UICONTROL 自动滚动]**&#x200B;后，在视频播放过程中，分配给视频区段的缩略图图像会在区段开始时滚动到视图中。但是，在某些情况下，区段内某些缩略图的显示时间是其之前或之后缩略图显示时间的两倍。发生此行为的原因是区段中缩略图的数量大于面板中可见缩略图的数量，且不可平均分割。

为了说明这一点，假设您有一个30秒的视频区段。 此外，30秒内共显示9个缩略图。 您的浏览器的大小调整为显示面板中有四个可见的缩略图位置。 30秒视频时间段分为三个子段。 下表显示了在给定时间子区段中显示哪些缩略图的划分：

| **视频子区段** | **子区段时间（以秒为单位）** | **面板中可见的缩略图** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

视频子区段3不会超出分配给它的缩略图。 另请注意，缩略图4、6和7在面板中的显示时间是其他缩略图的两倍。

查看器根据可用位置数量在面板中显示缩略图数量的逻辑如下：

* 子区段数量=舍入到下一个子区段（缩略图数量/缩略图面板中的可见版块数量，具体取决于浏览器窗口大小）。

   使用上表中的示例，9个缩略图/ 4个版块= 2.25;查看器逻辑会将其舍入为3个子区段。

* 缩略图数量=舍入到下一个缩略图（缩略图数量/视频子区段数量）。

   使用上表中的示例，9个缩略图/ 3个视频子区段= 3个缩略图。

* 子区段的持续时间=视频总持续时间/视频子区段的数量。

   使用上表中的示例， 30秒/ 3个视频子区段=每个视频子区段的10秒显示。

### 创建轮播横幅查看器预设的特殊注意事项 {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

创建轮播横幅查看器预设时，可以按如下方式访问更改热点样式：

|  | **描述** | **操作** |
|---|---|---|
| **热点图标** | 更改用于热点的图标 | 要更改热点图标图像，请在 **[!UICONTROL 外观]** 选项卡，在 **[!UICONTROL 选定的组件]**，点按 **[!UICONTROL ImageMapEffect]**. 在 **[!UICONTROL 图标]**，选择 **[!UICONTROL 背景]** 和 **[!UICONTROL 图像]** 字段，导航到所需的背景图像。 |

## 激活或停用Dynamic Media查看器预设 {#activating-or-deactivating-viewer-presets}

用户界面中可用的查看器预设取决于哪些查看器预设在创作模式下处于活动状态。 默认情况下，查看器预设为 *开* 创建后。 如果关闭预设，则在“创作”模式下将看不到该预设。 如果预设已发布。 无论是打开还是关闭，都会始终发布该内容。 如果列表变得太笨重，或者您不希望某个查看器预设可供使用，您可能需要停用查看器预设。

**激活或停用Dynamic Media查看器预设**:

1. 点按AEM左上角的AEM徽标，然后点按左边栏中的 **[!UICONTROL 工具>资产>查看器预设]**.
1. 在 **[!UICONTROL 查看器预设]** 页面下 **[!UICONTROL 州]** 列标题中，点按切换以激活或停用查看器预设。

   已激活的查看器预设在右侧蓝色框中显示切换开关；已停用的查看器预设的切换开关会显示在灰色浅框中的左侧。

## 发布Dynamic Media查看器预设 {#publishing-viewer-presets}

激活(或车削 *开*)查看器预设的状态表示该预设在Dynamic Media组件、交互式媒体组件以及您查看资产时均可见。

但是，要交付带有查看器预设的资产，还必须发布查看器预设。 必须激活所有查看器预设 *和* 发布以获取资产的URL或嵌入代码。 您必须激活并发布Dynamic media附带的所有现成查看器预设。 您创建和添加的自定义查看器预设将自动激活，但也必须发布。

请参阅 [激活或取消激活查看器预设](#activating-or-deactivating-viewer-presets).

另请参阅 [预览资产](previewing-assets.md).

**发布Dynamic Media查看器预设**:

1. 点按AEM左上角的AEM徽标，然后点按左边栏中的 **[!UICONTROL 工具>资产>查看器预设]**.
1. 选择要发布的一个或多个查看器预设。
1. 在工具栏中，点按 **[!UICONTROL 发布]** 图标。

## 为Dynamic Media查看器预设排序 {#sorting-viewer-presets}

**对Dynamic Media查看器预设进行排序**:

1. 点按 AEM 左上角的 AEM 徽标，然后点按左边栏中的&#x200B;**工具**（锤子图标）**[!UICONTROL > Assets > 查看器预设]**。
1. 单击&#x200B;**[!UICONTROL 预设标题]**、**[!UICONTROL 类型]**、**[!UICONTROL 已发布]**&#x200B;或&#x200B;**[!UICONTROL 状态]**&#x200B;来按列标题进行排序。例如，单击&#x200B;**[!UICONTROL 类型]**&#x200B;按字母顺序或反向字母顺序对查看器预设类型进行排序。

## 编辑Dynamic Media查看器预设 {#editing-viewer-presets}

请注意，编辑任意 *预定义的现成查看器预设* 不支持此方案。 如果您编辑现成的查看器预设，系统会提示您使用新名称保存该查看器预设。

**编辑Dynamic Media查看器预设**:

1. 点按AEM左上角的AEM徽标，然后点按左边栏中的 **[!UICONTROL 工具>资产>查看器预设]**.
1. 选中查看器预设标题左侧的框以选择预设。
1. 在工具栏中，点按 **[!UICONTROL 编辑]**.
1. 在 **[!UICONTROL 编辑查看器预设]** 页面对查看器预设进行所需的更改。
1. 执行下列操作之一：

   * 点按 **[!UICONTROL 保存]** ，以保存所做的更改并返回到 **[!UICONTROL 查看器预设]** 页面。
   * 点按 **[!UICONTROL 取消]** 撤消您所做的任何更改并返回到 **[!UICONTROL 查看器预设]** 页面。

## 删除自定义Dynamic Media查看器预设 {#deleting-custom-viewer-presets}

您可以删除已创建并添加到Dynamic Media的查看器预设。

**删除自定义Dynamic Media查看器预设**:

1. 点按AEM左上角的AEM徽标，然后点按左边栏中的 **[!UICONTROL 工具>资产>查看器预设]**.
1. 在 **[!UICONTROL 查看器预设]** 页面，检查 **[!UICONTROL 预设标题]**，然后点按 **[!UICONTROL 垃圾]** 图标。
1. 点按 **[!UICONTROL 删除]**.

## 将Dynamic Media查看器预设应用到资产 {#applying-a-viewer-preset-to-an-asset}

如果已发布资产和选定的查看器，则在选择查看器预设后 **[!UICONTROL 将显示]** “ **[!UICONTROL URL]** ”和“嵌入”按钮。

**将Dynamic Media查看器预设应用到资产**:

1. 打开资产，在页面的左上角附近，点按下拉菜单，然后选择 **[!UICONTROL 查看器]**.

   >[!NOTE]
   >
   >如果已发布资产和选定的查看器，则在选择查看器预设后 **[!UICONTROL 将显示]** “ **[!UICONTROL URL]** ”和“嵌入”按钮。

1. 从左窗格中选择一个查看器预设，以将其应用到资产。

   您可以 [复制要共享的URL](linking-urls-to-yourwebapplication.md) 其他用户。

## 使用Dynamic Media查看器预设传送资产 {#delivering-assets-with-viewer-presets}

要获取查看器预设的URL，请参阅 [将URL关联到您的Web应用程序](linking-urls-to-yourwebapplication.md). 另请参阅 [在网页上嵌入视频查看器](embed-code.md).

如果您使用AEM作为WCM，则可以直接在页面上使用查看器预设添加资产。 请参阅 [将Dynamic Media Assets添加到页面](adding-dynamic-media-assets-to-pages.md).
