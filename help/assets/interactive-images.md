---
title: 交互式图像
seo-title: Interactive Images
description: 了解如何在Dynamic Media中处理交互式图像
seo-description: Learn how to work with interactive images in dynamic media
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
exl-id: 4d3299e2-269b-4a41-a979-c884c707666d
feature: Interactive Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4283'
ht-degree: 1%

---

# 交互式图像 {#interactive-images}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过将“购物”热点拖放到图像上，您可以轻松地为客户打造出丰富且引人入胜的静态图像体验。 购物热点将有关产品或服务的其他信息与直接的销售点“添加到购物车”或“购买”功能相结合。 客户可以点按这些热点，并直接链接到产品或服务，将其添加到购物车，或链接到网页。 此类直接体验可提高客户在您网站上的参与度和转化率。

下面是一个带有概览弹出窗口的购物横幅。 用户通过点按模型上的圆或“热点”来激活概览。

![chlimage_1-368](assets/chlimage_1-368.png)

通过转到以下内容，查看上述网页上的交互式图像的实际操作情况：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## 观看如何创建交互式图像横幅 {#watch-how-interactive-image-banners-are-created}

观看10分钟33秒的演练 [交互式图像横幅的创建方式](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). 您还将了解如何预览、编辑和传送交互式图像横幅。

## 快速入门：交互式图像 {#quick-start-interactive-images}

以下工作流分步描述旨在帮助您在AEM Assets中快速启动并运行交互式图像。

查找 **示例** 标题。 本指南包含一个简短教程，该教程基于以下尚未添加交互式图像的网页示例：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

本教程有助于说明在您的网站上集成交互式图像的步骤。

**交互式图像工作流**:

1. **（可选）识别热点变量**  — 如果您使用AEM Assets和Dynamic Media独立版，请首先识别现有概览实施中使用的动态变量，以便您在创建交互式图像时输入热点数据。 请参阅 [（可选）识别热点变量](#optional-identifying-hotspot-variables).

   但是，如果您使用AEM Sites或AEM eCommerce，或者同时使用两者，则无需执行此步骤。

   请参阅 [AEM Assets中的电子商务概念](/help/sites-administering/concepts.md).

1. **（可选）创建交互式图像查看器预设**  — 自定义用于表示热点的图形图像。 如果您打算使用名为的现成交互式图像查看器预设，则无需创建您自己的交互式图像查看器预设 `Shoppable_Banner` 中。

   请参阅 [（可选）创建交互式图像查看器预设](managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **上传图像横幅**  — 上传要进行交互的图像横幅。

   请参阅 [上传图像横幅](#uploading-an-image-banner).

1. **将热点添加到图像横幅**  — 向图像横幅添加一个或多个热点，并将每个热点与超链接、概览或体验片段之类的操作相关联。 添加热点后，您将通过发布交互式图像来完成此任务。

   * 请参阅 [将热点添加到图像横幅](#adding-hotspots-to-an-image-banner).
   * 请参阅 [预览交互式图像](#optional-previewing-interactive-images)  — 可选。 如果需要，您可以查看购物横幅的呈现形式并测试其交互性。
   * 请参阅 [发布资产](publishing-dynamicmedia-assets.md) 有关如何发布交互式图像资产的详细信息。

1. **在AEM中将交互式图像添加到您的网站或您的网站**

   * 如果您使用AEM Sites、AEM eCommerce或两者兼有，则可以通过将交互式媒体组件拖动到页面上，将交互式图像直接添加到AEM中的网页。 请参阅 [将Dynamic Media Assets添加到页面](adding-dynamic-media-assets-to-pages.md).
   * 如果您使用AEM Assets和Dynamic Media独立版，则必须在您的网站上复制嵌入代码，然后将其与现有概览相集成。 请参阅 [将交互式图像与您的网站集成](#integrating-an-interactive-image-with-your-website).
   * 如果您使用的是第三方WCM（Web内容管理器），则必须将新的交互式视频与您网站上使用的现有概览实施相集成。 请参阅 [将交互式图像与现有概览集成](#integrating-an-interactive-image-with-an-existing-quickview).

## （可选）识别热点变量 {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>仅当满足以下条件时，才需要执行此任务：
>
>* 您希望通过触发概览来为图像添加交互性。
>* 您的AEM实施会执行以下操作 *not* 使用电子商务集成框架，将产品数据从任何电子商务解决方案(如IBM Websphere Commerce、Elastic Path、hybris或Intershop)中提取到AEM中。 请参阅 [AEM Assets中的电子商务概念](/help/sites-administering/concepts.md).
>
>如果您的AEM实施使用电子商务，则可以跳过此任务并继续执行下一项任务。

首先，识别现有概览实施所使用的动态变量，以便您输入热点数据以创建交互式图像。

在AEM Assets中将热点添加到横幅图像时，您需要分配一个SKU(库存单位；您提供的每个不同产品或服务的唯一标识符)以及每个热点的可选附加变量。 此类热点变量稍后会用于将热点与概览内容进行匹配。

必须正确识别要与热点数据关联的变量数量和类型。 添加到横幅图像的每个热点都必须包含足够的信息，以便在现有的后端系统中明确地识别产品。

有不同的方法来识别用于热点数据的一组变量。

有时，与负责现有概览实施的IT专家进行咨询可能已足够，因为他们可能知道在系统中识别概览所需的最少数据集。 但是，在大多数情况下，也可以简单地分析前端代码的现有行为。

大多数概览实施都使用以下模式：

* 用户在网站上激活用户界面元素。例如，单击 **[!UICONTROL 概览]** 按钮。
* 如果需要，网站会向后端发送Ajax请求以加载概览数据或内容。
* 概览数据会转换为内容，以准备在网页上渲染。
* 最后，前端代码以可视方式将此类内容呈现在屏幕上。

然后，方法是访问实施了快速视图功能的现有网站的不同区域，触发快速视图并捕获由网页发送的Ajax URL，以加载快速视图数据或内容。

通常，您无需使用任何专门的调试工具。 现代的Web浏览器配备了Web检查器，可以做到充分的工作。 以下是一些包括Web检查器的Web浏览器示例：

* 要在Google Chrome中查看所有传出HTTP请求，请按F12以打开 **[!UICONTROL 开发人员工具]** ，然后单击 **[!UICONTROL 网络]** 选项卡。

   在Mac上，按 **[!UICONTROL Command+Option+I]** 打开 **[!UICONTROL 开发人员工具]** 面板，然后单击“网络”选项卡。

* 在Firefox中，您可以通过按F12并使用其“网络”选项卡来激活Firebug插件，也可以使用内置 **[!UICONTROL 检查员]** 工具及其 **[!UICONTROL 网络]** 选项卡。

   在Mac上，按 **[!UICONTROL Command+Option+I]** 打开 **[!UICONTROL 开发人员工具]** 面板，然后单击 **[!UICONTROL 检查员]** 选项卡。

在浏览器中打开网络监控时，会触发页面上的概览。

现在，在网络日志中找到Quickview Ajax URL，并复制记录的URL以供将来分析。 在大多数情况下，当您触发概览时，会向服务器发送大量请求。 通常，Quickview Ajax URL是列表中最先使用的URL之一。 它具有复杂的查询字符串部分或路径，其响应MIME类型为 `text/html`, `text/xml`或 `text/javascript`.

在此过程中，访问网站中具有不同产品类别和类型的不同区域非常重要。 原因是概览URL的某些部分可能与给定网站类别相同，但只有在您访问网站的其他区域时才会发生更改。

在最简单的情况下，概览URL中唯一的变量部分是产品SKU。 在这种情况下，SKU值是您在将热点添加到横幅图像时唯一需要的数据块。

但是，在复杂的情况下，除SKU之外，快速视图URL还具有不同的可变元素，例如类别ID、颜色代码、大小代码等。 在这种情况下，在AEM Assets的交互式购物图像功能中，每个元素都是热点数据定义中的一个单独变量。

请考虑以下概览URL及其生成的热点变量示例：

<table> 
     <tbody> 
      <tr> 
       <td><p>单个SKU，位于查询字符串中。</p> </td> 
       <td><p>记录的概览URL包括：</p> 
        <ul> 
         <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
        </ul> <p>URL中唯一的变量部分是productId=查询字符串参数的值，很明显它是SKU值。 因此，我们的热点只需要在SKU字段中填充如下值即可 <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>单个SKU，位于URL路径中。</p> </td> 
       <td><p>记录的概览URL包括：</p> 
        <ul> 
         <li><p><code>https://server/product/6422350843</code></p> </li> 
         <li><p><code>https://server/product/1607745002</code></p> </li> 
         <li><p><code>https://server/product/0086724882</code></p> </li> 
        </ul> <p>变量部分位于路径的最后一部分，它将成为热点的SKU值： <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td> 
      </tr> 
      <tr> 
       <td><p>查询字符串中的SKU和类别ID。</p> </td> 
       <td><p>记录的概览URL包括：</p> 
        <ul> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
        </ul> <p>在这种情况下，URL中有两个不同的部分。 SKU存储在 <code>prodId</code> 参数和类别ID</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**示例**

您可以将上述三个示例中使用的相同方法应用到演示网页：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

演示网页包含多个产品缩略图，每个缩略图中都有一个标有“概览”按钮 **[!UICONTROL 查看更多]**. 如果Web浏览器的调试工具仍处于激活状态，请单击每个按钮并记下记录的概览URL。 激活页面上所有四个可用的产品概览后，您会向后端发出以下概览请求列表：

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

通过查看这些服务器调用，您会发现特定于产品的信息仅存在于请求路径中。 您还注意到查询字符串根本不被使用，并且涉及两种不同类型的数据段：

* 第一类是“男人或女人”。 您可以将此类别称为“产品”。
* 第二种类型是产品名称，如CamoPullover。 您可以假定这是产品SKU。

根据此信息，整个概览URL具有以下模式：

`/datafeed/$categoryId$-$SKU$.json`

根据此类分析，您将使用 `categoryId` 和 `SKU` ，以访问热点。

现在，您可以使用AEM Assets中的交互式购物图像功能上传图像横幅并向其添加热点。

## （可选）创建交互式图像查看器预设 {#optional-creating-an-interactive-image-viewer-preset}

您可以选择使用名为的默认现成交互式图像查看器预设 **[!UICONTROL Shoppable_Banner]** AEM Assets。 或者，您也可以创建自己的自定义查看器预设，以用于交互式图像。

创建自定义交互式图像查看器预设时，您可以确定图像横幅上热点的外观。 在创建查看器预设时，您可以选择使用预定义图像库中的热点图形。

保存查看器预设后，查看器预设会在 **[!UICONTROL 查看器预设]** 列表页面。AEM Assets 此功能意味着无论您何时查看资产，都可以在交互式媒体组件中看到该内容。 但是， *交付* 使用此查看器预设的交互式横幅时，您必须 *发布* 查看器预设（自定义或现成查看器预设也是如此）。

**创建交互式图像查看器预设**:

1. 在左边栏中，点按 **[!UICONTROL 工具>资产>查看器预设]**.
1. 在页面的右上角附近，点按 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL 新查看器预设]** 框中，键入用于描述交互式横幅查看器预设的名称。

   这是将在 **[!UICONTROL 查看器预设]** 列表页面。
1. 在 **[!UICONTROL 富媒体类型]** 下拉菜单，选择 **[!UICONTROL 交互式图像]**.
1. 点按 **创建**.
1. 在 **[!UICONTROL 编辑查看器预设]** 页面，点按 **[!UICONTROL 外观]** 选项卡。
1. 执行下列操作之一：

   * 要上传您自己的热点图像，请点按 **[!UICONTROL 资产选取器]** 图标。 在 **[!UICONTROL 选择内容]** ，导航到要使用的热点图像，将其选中，然后点按 **[!UICONTROL 复选标记]** 图标。
   * 要选择预定义的热点图像，请点按 **[!UICONTROL 热点图库]** 图标。 在热点图库画板上，点按您要使用的热点图像。

1. 在页面的右上角附近，点按 **[!UICONTROL 保存]**.

   确保发布新查看器预设。

   请参阅 [发布已添加的查看器预设](managing-viewer-presets.md#publishing-viewer-presets).

   您现在可以上传图像横幅。

## 上传图像横幅 {#uploading-an-image-banner}

如果您已上传要使用的图像，请前进到下一步， [将热点添加到图像横幅](#adding-hotspots-to-an-image-banner).

**上传图像横幅**:

1. 上传要进行交互的图像横幅。

   请参阅 [上传资产](managing-assets-touch-ui.md#uploading-assets).

   现在，您可以向图像横幅中添加热点；请参阅下面的下一项任务。

## 将热点添加到图像横幅 {#adding-hotspots-to-an-image-banner}

您可以使用 **[!UICONTROL 热点管理]** 页面。

添加热点时，您可以将热点定义为“概览”弹出显示、超链接或体验片段。

请参阅 [体验片段](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>请注意，在体验片段中嵌入查看器时，不支持交互式图像中的社交媒体共享工具。 要解决此问题，您可以使用或创建没有社交媒体共享工具的查看器预设。 通过此类查看器预设，您可以成功将其嵌入到体验片段中。

**[!UICONTROL 撤消]** 和 **[!UICONTROL 重做]** 在当前创建/编辑会话期间，支持页面右上角附近的选项。

创建完交互式图像后，您可以使用 **[!UICONTROL 预览]** 以了解交互式图像在客户面前的显示方式。

请参阅 [（可选）预览交互式图像](#optional-previewing-interactive-images).

>[!NOTE]
>
>在交互式图像或轮播横幅中向图像添加热点时，热点信息会存储在与图像位置相对的相同元数据位置，而不管它是交互式图像还是轮播横幅。 此功能意味着您可以在任意查看器中轻松地重复使用同一图像及其定义的热点数据。
>
>但是，请注意，传送横幅支持图像映射的图像也可能包含热点；交互式图像不会。 如果您打算创建使用相同图像的交互式图像或轮播横幅，请牢记这一点。 您可能希望使用同一图像的不同副本来创建交互式图像和传送横幅。
>
>另请参阅 [传送横幅](carousel-banners.md).

>[!NOTE]
>
>如果您正在使用热点编辑交互式图像并裁剪图像，则热点会被删除。

**向图像横幅添加热点**:

1. 在“资产”视图中，导航到要进行交互的图像横幅。
1. 执行下列操作之一：

   * 将鼠标悬停在图像上，然后点按 **[!UICONTROL 选择]** （复选标记图标）。 在工具栏中，点按 **[!UICONTROL 编辑]**.
   * 将鼠标悬停在图像上，然后点按 **[!UICONTROL 更多操作]** （三个点图标）> **[!UICONTROL 编辑]**.
   * 点按图像以在 **[!UICONTROL 详细信息视图]** 页面。 在工具栏中，点按 **[!UICONTROL 编辑]**.

1. 在页面的左上角附近，点按 **[!UICONTROL 添加热点]** （手指点按图标）以打开 **[!UICONTROL 热点管理]** 页面。
1. 在页面的左上角附近，点按 **[!UICONTROL 热点]**.
1. a.在 **热点管理** 页面，点按 **[!UICONTROL 热点]**.
b.在图像上，点按您希望显示热点的位置。 如有必要，可拖动热点以调整其位置。c.重复步骤a和b，根据需要添加其他热点。d.（可选）要删除热点，请在图像上选择它，然后点按 **[!UICONTROL 删除]** （垃圾箱图标） **[!UICONTROL 热点]** 标题。

1. 在 **[!UICONTROL 名称]** 文本字段中，键入热点的名称。 此名称也会显示在 **[!UICONTROL 选定的热点]** 下拉列表。
1. 执行下列操作之一：

   * 点按 **[!UICONTROL 概览]**.

      * 如果您是AEM Sites或电子商务客户，请点按 **[!UICONTROL 产品选取器]** 图标（放大镜）以打开 **[!UICONTROL 选择产品]** 页面。 点按要使用的产品，然后点按 **[!UICONTROL 选择]** ，以返回 **[!UICONTROL 热点管理]** 页面。
      * 如果您 *not* AEM Sites或电子商务客户

         * 请参阅 [识别热点变量](#optional-identifying-hotspot-variables);您需要定义这些变量。
         * 然后，手动输入SKU值。 在 **[!UICONTROL SKU价值]** 文本字段中，键入产品的SKU（库存单位），即您提供的每个不同产品或服务的唯一标识符。 输入的SKU值会自动填充概览模板的变量部分，以便系统能够将点按的热点与特定SKU的概览相关联。
         * （可选）如果您需要在概览中使用其他变量来进一步识别产品，请点按 **[!UICONTROL 添加常规变量]**. 在文本字段中，指定其他变量。 例如， `category=Mens` 是添加的变量。
   * 点按 **超链接**.

      * 如果您是AEM Sites客户，请点按 **[!UICONTROL 网站选择器]** 图标（文件夹）来导航到URL。 请注意，如果您的交互式内容具有包含相对URL的链接，特别是指向AEM Sites页面的链接，则无法使用基于URL的链接方法。
      * 如果您是独立客户，请在 **[!UICONTROL HREF]** 文本字段，指定链接网页的完整URL路径。

      请确保指定是在新的浏览器选项卡（推荐为默认选项卡）还是在同一选项卡中打开链接。

      请参阅 [使用选择器](working-with-selectors.md) 以了解更多信息。

   * 点按 **体验片段**.

      * 如果您是AEM Sites客户，请点按 **[!UICONTROL 搜索]** 图标（放大镜）以打开 **[!UICONTROL 体验片段]** 页面。 点按您要使用的体验片段，然后点按 **[!UICONTROL 选择]** ，以返回到热点管理页面。

         请参阅 [体验片段](/help/sites-authoring/experience-fragments.md).
         >[!NOTE]
         >请注意，在体验片段中嵌入查看器时，不支持交互式图像中的社交媒体共享工具。 要解决此问题，您可以使用或创建没有社交媒体共享工具的查看器预设。 通过此类查看器预设，您可以成功将其嵌入到体验片段中。

      * 指定将在横幅上显示的体验片段的宽度和高度。



1. 点按 **[!UICONTROL 保存]** 保存您的工作并返回 **[!UICONTROL 浏览]** 页面。
1. 发布交互式图像。 发布后，横幅可通过云进行交付，如果您需要与第三方网站集成，则还会生成嵌入代码。

   请参阅 [发布资产](managing-assets-touch-ui.md#publishing-assets).

   添加热点并发布交互式图像后，您现在可以将其添加到现有网站。

   请参阅 [将交互式图像与您的网站集成](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >如果您正在使用热点编辑交互式图像并裁剪图像，则热点会被删除。

### （可选）预览交互式图像 {#optional-previewing-interactive-images}

您可以使用“预览”来查看交互式图像对客户的呈现效果，并测试图像的热点以确保它们的行为符合预期。

如果您对交互式图像满意，可以发布该图像。\
请参阅 [在网页上嵌入视频查看器或图像查看器](embed-code.md).\
请参阅 [将URL关联到您的Web应用程序](linking-urls-to-yourwebapplication.md). 请注意，如果您的交互式内容具有包含相对URL的链接，特别是指向AEM Sites页面的链接，则无法使用基于URL的链接方法。\
请参阅 [将Dynamic Media Assets添加到页面。](adding-dynamic-media-assets-to-pages.md)

**预览交互式图像**:

1. 在“资产”视图中，导航到您创建的现有交互式图像，然后点按以在预览中打开该图像。
1. 在预览页面的左上角附近， **[!UICONTROL 内容]** 下拉列表中，点按 **[!UICONTROL 查看器]**.
1. 在 **[!UICONTROL 查看器]** 列表，点按 **[!UICONTROL Shoppable_Banner]** 或您创建的交互式图像查看器预设的名称。
1. 点按图像上的热点以测试其关联的操作。

## 发布交互式图像资产 {#publishing-interactive-image-assets}

请参阅 [发布资产](publishing-dynamicmedia-assets.md) 有关如何发布交互式图像资产的详细信息。

## 将交互式图像与您的网站集成 {#integrating-an-interactive-image-with-your-website}

现在，在上传横幅图像、将热点添加到图像并发布交互式图像后，您便可以将其添加到您的网站页面。

如果您是AEM Sites客户，则可以通过将交互式媒体组件拖动到页面上来添加交互式图像。 请参阅 [将Dynamic Media Assets添加到页面。](adding-dynamic-media-assets-to-pages.md)

如果您是独立的AEM Assets客户，则可以按照此部分所述，手动将交互式图像添加到您的网站。

1. 复制已发布的交互式图像的嵌入代码。

   请参阅 [在网页上嵌入视频查看器或图像查看器](embed-code.md).

1. 将复制的嵌入代码添加到网页中的所需位置。

   复制的嵌入代码是为响应式环境设置的，因此它应该自动适合分配的区域。

**示例**

以演示网站为例：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

注意这三个人的照片是静态的 `IMG` 标记：

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

集成过程与删除 `IMG` 标记并将其替换为从AEM Assets复制的嵌入代码。 您可以在以下URL中看到结果，该URL显示页面上具有三个圆形热点的交互式购物图像：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>因此，演示网站交互式购物图像上的热点仅用于显示目的；它们尚未与现有概览相集成。

要为响应式环境将裁剪应用于交互式购物图像，您可以包含交互式图像配置属性 `ZoomView.iscommand` 到路径 — 其中 `ZoomView` 是要调用的组件和 `iscommand` 是您应用的裁剪图像服务命令。

请参阅 [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) 配置属性。

请参阅 [农作物](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) 图像提供命令。

现在，您可以将交互式图像与网站上的现有概览相集成。

## 将交互式图像与现有概览集成 {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>此任务仅在您是独立的AEM Assets客户时才适用。

此过程的最后一步是，将交互式图像与您网站上的现有概览实施相集成。 没有适用于所有情况的集成解决方案。 每个概览实施都是独一无二的，需要一种特定的方法，最可能需要前端IT人员的协助。

现有的概览实施通常表示在网页上发生的一系列相互关联的操作，这些操作按以下顺序发生：

1. 用户在网站的用户界面中触发一个元素。
1. 前端代码根据在步骤1中触发的用户界面元素来获取概览URL。
1. 前端代码使用步骤2中获取的URL发送Ajax请求。
1. 后端逻辑会将相应的概览数据或内容返回到前端代码。
1. 前端代码加载概览数据或内容。
1. 或者，前端代码会将加载的概览数据转换为HTML表示。
1. 前端代码显示一个模态对话框或面板，并在屏幕上为最终用户呈现HTML内容。

这些调用可能不代表独立的公共API调用，网页逻辑可以从任意步骤调用这些调用。 相反，它是一个链式调用，其中每个后续步骤都会隐藏在上一步的最后一个阶段（回调）中。

在交互式购物图像替换第1步和第2步部分内容的同时，当用户单击购物图像中的热点时，查看器会处理此类用户交互。 查看器会向网页返回一个事件，其中包含之前添加到AEM Assets的所有热点数据。

在此类事件处理程序中，前端代码会执行以下操作：

* 监听交互式购物图像发出的事件。
* 根据热点数据构建概览URL。
* 触发从后端加载概览并在屏幕上呈现概览以供显示的过程。

由AEM Assets返回的嵌入代码已拥有一个可供使用的事件处理程序，该处理程序已被注释掉，如以下高亮显示的代码片段所示：

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : { 
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({ 
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 }, 
             });
        */
        s7interactiveimageviewer.init();
```

因此，只需取消代码注释，并将虚拟处理程序主体替换为特定网页的代码即可。

构建概览URL的过程与之前介绍的用于识别热点变量的过程基本上相反。

请参阅 [识别热点变量](#optional-identifying-hotspot-variables).

使用我们之前的概览URL示例，您可以在以下示例中查看每种情况下概览URL的构建方式：

<table> 
 <tbody> 
  <tr> 
   <td><p>单个SKU，位于查询字符串中</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>单个SKU，位于URL路径中</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>查询字符串中的SKU和类别ID</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td> 
  </tr> 
 </tbody> 
</table>

触发概览URL并激活概览面板的最后一步，很可能需要IT部门的前端IT人员的协助。 他们深知如何通过正确的步骤准确触发概览实施，从而拥有现成的概览URL。

您可以了解如何将这些步骤应用到演示网站，以便将交互式购物图像与概览代码完全集成。 以前，概览URL的结构如下所示：

```xml
/datafeed/$categoryId$-$SKU$.json
```

在 `quickViewActivate` 处理程序中，您可以使用 `categoryId` 和 `SKU` 字段 `inData` 由查看器代码传递到处理程序的对象：

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

演示网站使用一个简单的 `loadQuickView()` 函数调用。 此函数仅采用一个参数，即概览数据URL。 因此，集成交互式购物图像所需的最后一步是，将下面一行代码添加到 `quickViewActivate` 处理程序：

```xml
loadQuickView(quickViewUrl);
```

以下是完整的源代码：

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : { 
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({ 
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    }, 
   });
 s7interactiveimageviewer.init();
```

具有完全集成的交互式图像的最终演示网站如下所示：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html)

## 使用概览创建自定义弹出窗口 {#using-quickviews-to-create-custom-pop-ups}

请参阅 [使用概览创建自定义弹出窗口](custom-pop-ups.md).
