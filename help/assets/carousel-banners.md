---
title: 传送横幅
seo-title: Carousel Banners
description: 了解如何在Dynamic Media中使用轮播横幅
seo-description: Learn how to work with carousel banners in dynamic media
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
exl-id: d2fdad3f-513b-4147-a7c6-a3c1b64dd6e3
feature: Carousel Banners
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4771'
ht-degree: 4%

---

# 传送横幅 {#carousel-banners}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过创建交互式旋转促销内容并将其交付到任何屏幕，轮播横幅使营销人员能够推动转化。

创建和修改促销横幅中特有的内容可能非常耗时，这会限制您快速发布新内容或使其更具针对性的能力。 传送横幅可让您快速创建或修改旋转横幅，添加与产品详细信息或相关资源链接的热点等交互性，并将这些交互性传送到任何屏幕，从而让您更快地将新促销内容推向市场。

传送横幅由带有单词的横幅来指定 **卡鲁塞**:

![chlimage_1-438](assets/chlimage_1-438.png)

在您的网站上，轮播横幅可以如下所示：

![chlimage_1-439](assets/chlimage_1-439.png)

在此，您可以导航浏览图像（通过单击数字）。 此外，幻灯片会根据您可以自定义的时间间隔自动旋转。 您在轮播横幅中添加的图像同时支持热点和图像映射，用户可以在其中点按或转到超链接或访问概览窗口。

在此示例中，用户点按或单击了图像映射，并访问了手套的“概览”窗口：

![chlimage_1-440](assets/chlimage_1-440.png)

## 观看如何创建轮播横幅 {#watch-how-carousel-banners-are-created}

观看10分钟33秒的演练 [轮播横幅的创建方式](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). 您还将了解如何预览、编辑和传送传送传送横幅。

>[!NOTE]
>
>非管理用户必须添加到 **dam-users** 组，以便能够创建或编辑传送横幅。 如果您在创建或编辑时遇到问题，请咨询系统管理员，该管理员可将您添加到 **dam-users** 群组。

## 快速入门：传送横幅 {#quick-start-carousel-banners}

要快速启动并运行，请执行以下操作：

1. [识别热点和图像映射变量](#identifying-hotspot-and-image-map-variables) (仅适用于使用AEM Assets + Dynamic Media的客户)

   首先，识别现有概览实施所使用的动态变量，以便您在AEM Assets的轮播横幅创建过程中能够正确输入热点和图像映射数据。

   >[!NOTE]
   >
   >如果您是AEM Sites或Ecommerce客户，则可以使用内置功能导航到产品页面并查找产品目录中的现有SKU。 您无需手动输入热点或图像映射变量。 请参阅 [设置电子商务](/help/sites-administering/generic.md).
   >
   >如果您是AEM Assets和Dynamic Media客户，则将手动输入热点和图像映射的数据，然后将已发布的URL或嵌入代码与第三方内容管理系统相集成。

1. 可选：根据需要[创建轮播集查看器预设](managing-viewer-presets.md)。

   如果您是管理员，则可以通过创建自己的轮播查看器预设来自定义轮播的行为和外观。 主要优势在于，您可以对多个轮播重复使用此自定义查看器预设。 但是，用户也可以选择在创作轮播时直接自定义轮播的行为和外观。 当您想要为给定轮播设计非常具体的设计时，这是首选方法。

1. [上传图像横幅](#uploading-image-banners).

   上传要进行交互的图像横幅。

1. [创建轮播集](#creating-carousel-sets).

   在轮播集中，用户在横幅图像中导航，并点按热点或图像映射以访问相关内容。

   要在 Assets 中创建轮播集，请点按&#x200B;**[!UICONTROL 创建]**，然后选择&#x200B;**[!UICONTROL 轮播集]**。将资产添加到幻灯片，然后点按&#x200B;**[!UICONTROL 保存]**。您还可以直接在编辑器中编辑轮播集的外观和行为。

1. [将热点或图像映射添加到图像横幅。](#adding-hotspots-or-image-maps-to-an-image-banner)

   向图像横幅中添加一个或多个热点或图像映射，并将每个热点或图像映射与链接、概览或体验片段之类的操作相关联。 添加热点或图像映射后，可通过发布轮播集来完成此任务。 发布后会创建嵌入代码，您可以使用该代码复制嵌入代码并将其应用于网站登录页面。

   请参阅 [（可选）预览传送横幅](#optional-previewing-carousel-banners)  — 可选。 如果需要，您可以查看轮播集的表示形式并测试其交互性。

1. [发布传送横幅。](#publishing-carousel-banners)

   与发布任何资产一样，您也可以发布轮播集。 在资产中，导航到轮播集，然后选择它，然后点按或点按 **[!UICONTROL 发布]**. 发布轮播集时，会激活URL和嵌入字符串。

1. 执行下列操作之一：

   * [将轮播横幅添加到您的网站页面](#adding-a-carousel-banner-to-your-website-page) 您可以将复制的轮播横幅URL或嵌入代码添加到网站页面。

      * [将轮播横幅与现有概览相集成](#integrating-the-carousel-banner-with-an-existing-quickview). 如果您使用的是第三方Web内容管理系统，则需要将新的轮播横幅与网站上的现有概览实施相集成。
   * [在AEM中将轮播横幅添加到您的网站](adding-dynamic-media-assets-to-pages.md) 如果您是AEM Sites客户，则可以使用交互式媒体组件将轮播集直接添加到AEM中的页面。


如果需要编辑传送集，请参阅 [编辑轮播集](#editing-carousel-sets). 此外，您还可以查看和编辑 [轮播集属性](/help/assets/managing-assets-touch-ui.md#editing-properties).

## 识别热点和图像映射变量 {#identifying-hotspot-and-image-map-variables}

首先，识别现有概览实施所使用的动态变量，以便您在AEM Assets的轮播集创建过程中能够输入适当的热点或图像映射数据。

在AEM Assets中将热点或图像映射添加到横幅图像时，您需要为每个热点或图像映射分配一个SKU和可选的其他变量。 这些变量稍后会用于将热点或图像映射与概览内容进行匹配。

>[!NOTE]
>
>如果您是AEM Sites和/或AEM Ecommerce客户，请跳过此步骤。 您无需手动识别热点或图像映射变量；您可以将与电子商务的集成用于产品集成。 请参阅 [设置电子商务](/help/sites-administering/generic.md). 此外，您还可以使用交互组件并将其添加到网页中。
>
>如果您是AEM Assets或媒体客户，则需要发布URL或嵌入代码，然后与第三方内容管理系统集成，并手动识别热点和图像映射。

必须正确识别要与热点或图像映射数据关联的变量数量和类型。 添加到横幅图像的每个热点或图像映射都必须包含足够的信息，以便在现有的后端系统中明确地识别产品。 同时，每个热点或图像映射不应包含所需的更多数据。 原因是这样会使数据输入过程过于复杂，并且会使正在进行的热点或图像映射管理更容易出错。

有不同的方法来识别一组用于热点或图像映射数据的变量。

有时，与负责现有概览实施的IT专家进行咨询可能已足够，因为他们可能知道在系统中识别概览所需的最少数据集。 但是，在大多数情况下，也可以简单地分析前端代码的现有行为。

大多数概览实施都使用以下模式：

* 用户在网站上激活用户界面元素。例如，单击 **[!UICONTROL 概览]** 按钮。
* 如果需要，网站会向后端发送Ajax请求以加载概览数据或内容。
* 概览数据会转换为内容，以准备在网页上渲染。
* 最后，前端代码以可视方式将此类内容呈现在屏幕上。

然后，方法是访问实施了快速视图功能的现有网站的不同区域，触发快速视图并捕获由网页发送的Ajax URL，以加载快速视图数据或内容。

通常，您无需使用任何专门的调试工具。 现代的Web浏览器配备了Web检查器，可以做到充分的工作。 以下是一些包括Web检查器的Web浏览器示例：

* 要在Google Chrome中查看所有传出的HTTP请求，请按F12(Windows)或Command-Option-I(Mac)以打开“开发人员工具”面板，然后点按 **[!UICONTROL 网络]** 选项卡。
* 在Firefox中，您可以通过按F12(Windows)或Command-Option-I(Mac)并使用其“网络”选项卡来激活Firebug插件，也可以使用内置的检查器工具及其“网络”选项卡。

在浏览器中打开网络监控时，会触发页面上的概览。

现在，在网络日志中找到Quickview Ajax URL，并复制记录的URL以供将来分析。 在大多数情况下，当您触发概览时，会向服务器发送大量请求。 通常，Quickview Ajax URL是列表中最先使用的URL之一。 它具有复杂的查询字符串部分或路径，其响应MIME类型为 `text/html`, `text/xml`或 `text/javascript`.

在此过程中，访问网站中具有不同产品类别和类型的不同区域非常重要。 原因是概览URL的某些部分可能与给定网站类别相同，但只有在您访问网站的其他区域时才会发生更改。

在最简单的情况下，概览URL中唯一的变量部分是产品SKU。 在这种情况下，SKU值是您在将热点或图像映射添加到横幅图像时需要的唯一数据块。

但是，在复杂的情况下，除SKU之外，快速视图URL还具有不同的可变元素，例如类别ID、颜色代码、大小代码等。 在这种情况下，在热点或轮播横幅功能的图像映射数据定义中，每个元素都是一个单独的变量。

请考虑以下概览URL示例及其生成的热点或图像映射变量：

<table> 
 <tbody> 
  <tr> 
   <td>单个SKU，位于查询字符串中。</td> 
   <td><p>记录的概览URL包括：</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>URL中唯一的变量部分是 <code>productId=</code> 查询字符串参数，很明显它是SKU值。 因此，我们的热点或图像映射只需要在SKU字段中填充如下值即可 <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>单个SKU，位于URL路径中。</td> 
   <td><p>记录的概览URL包括：</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>变量部分位于路径的最后一部分，它将成为热点/图像映射的SKU值：<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>查询字符串中的SKU和类别ID。</td> 
   <td><p>记录的概览URL包括：</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>在这种情况下，URL中有两个不同的部分。 SKU存储在 <code>prodId</code> 参数和类别ID存储在 <code>category=</code>参数。</p> <p>因此，热点/图像映射定义是成对存在的。 即，一个SKU值和一个名为 <code>categoryId</code>. 结果对如下所示：</p> 
    <ul> 
     <li><p>SKU是 <strong><code>305466</code></strong> 和 <code>categoryId</code> is <code>1100004</code>.</p> </li> 
     <li><p>SKU是 <strong><code>310181</code></strong> 和 <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>SKU是 <strong><code>308706</code></strong> 和 <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 上传图像横幅 {#uploading-image-banners}

如果您已上传要使用的图像，请前进到下一步， [创建轮播集](#creating-carousel-sets). 请注意，在启用Dynamic Media后，必须上传轮播中使用的图像。

要上传图像横幅，请参阅 [上传资产](managing-assets-touch-ui.md).

## 创建轮播集 {#creating-carousel-sets}

>[!NOTE]
>
>非管理用户必须添加到 **[!UICONTROL dam-users]** 组，以便能够创建或编辑传送横幅。 如果您在创建或编辑时遇到问题，请咨询系统管理员，该管理员可将您添加到 **dam-users** 群组。

**创建轮播集**:

1. 在Assets中，导航到要创建轮播集的文件夹，然后点按 **[!UICONTROL 创建>轮播集]**.
1. 在 **[!UICONTROL 轮播横幅编辑器]** 页面，点按 **[!UICONTROL 点按以打开资产选择器]** 来选择第一张幻灯片的图像。

   在 **[!UICONTROL 轮播横幅编辑器]** ，请执行以下任一操作：

   * 在页面的左上角附近，点按 **[!UICONTROL 添加幻灯片]** 图标。
   * 在页面中间附近，点按 **[!UICONTROL 点按以打开资产选择器]**.

   点按以选择要包含在轮播集中的资产。选定资产上有一个复选标记图标。完成后，在页面的右上角附近，点按 **[!UICONTROL 选择]**.

   借助资产选择器，您可以通过键入关键字并点按&#x200B;**[!UICONTROL 返回]**&#x200B;来搜索资产。您还可以应用过滤器来优化搜索结果。您可以按路径、收藏集、文件类型和标记进行过滤。选择过滤器，然后点按工具栏上的&#x200B;**[!UICONTROL 过滤器]**&#x200B;图标。通过点按 **[!UICONTROL 查看]** 图标和选择 **[!UICONTROL 列视图]**, **[!UICONTROL 卡片视图]**&#x200B;或 **[!UICONTROL 列表视图]**.

   请参阅 [使用选择器](working-with-selectors.md) 以了解更多信息。

1. 继续添加幻灯片，直到您添加了所有要在轮播集中旋转的图像。
1. （可选）执行以下任一操作：

   * 如有必要，可拖动幻灯片以对设置列表中的图像进行重新排序。
   * 要删除图像，请选择图像，然后点按 **[!UICONTROL 删除幻灯片]** 中。
   * 要应用预设，请点按页面右上角附近的预设下拉列表，然后选择要一次应用于该预设集的预设。

   要删除幻灯片，请点按幻灯片，然后点按 **[!UICONTROL 删除幻灯片]** 中。 要移动幻灯片，请点按订单图标，然后按住并移动到所需位置。

1. 在幻灯片中添加图像后，您可以向图像添加热点和/或图像映射。 请参阅 [添加热点或图像映射](#adding-hotspots-or-image-maps-to-an-image-banner).
1. 您可以通过点按或单击“行为”和“外观”选项卡，并调整轮播横幅的外观或特定组件的行为，来更改轮播集的可视设计和行为。 请参阅 [管理查看器预设](viewer-presets.md) 以了解有关如何使用查看器编辑器的更多信息。

   >[!NOTE]
   >
   >对于传送横幅，您可能需要调整以下内容：
   >* 图像显示的持续时间。 默认情况下，每幅图像显示9秒。
   >* 动画. 默认情况下，每个幻灯片过渡都是渐隐效果。 您可以将其更改为幻灯片过渡。
   >* 按钮的样式。 用户可以通过点按每个圆点或数字来旋转横幅。 您可以更改设置指示器按钮的显示位置（如果是数字或虚线样式）以及其大小。
   >* 更改图像映射的高亮显示样式或用于热点的图标。
   >* 在编辑查看器预设之前，请选择要作为预设基础的样式。 如果不这样做，则在开始编辑查看器预设时，如果您决定更改其他预设，则将丢失所有更改。


   您还可以预览轮播横幅的外观。 请参阅 [（可选）预览传送横幅](#optional-previewing-carousel-banners).

1. 点按 **[!UICONTROL 保存]** 完成。

## 将热点或图像映射到图像横幅 {#adding-hotspots-or-image-maps-to-an-image-banner}

您可以使用轮播集编辑器将热点或图像映射添加到横幅。

添加热点或图像映射时，您可以将热点或图像映射定义为“概览”弹出显示、超链接或体验片段。

请参阅 [体验片段](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>请注意，在体验片段中嵌入查看器时，“轮播横幅”中的社交媒体共享工具不受支持。 要解决此问题，您可以使用或创建没有社交媒体共享工具的查看器预设。 通过此类查看器预设，您可以成功将其嵌入到体验片段中。

在向图像添加热点或图像映射时，请记住保存您的工作。 **[!UICONTROL 撤消]** 和 **[!UICONTROL 重做]** 在当前创建/编辑会话期间，支持页面右上角附近的选项。

创建完轮播横幅后，您可以选择使用 **[!UICONTROL 预览]** 以了解轮播横幅向客户显示的方式。

请参阅 [（可选）预览传送横幅](#optional-previewing-carousel-banners).

>[!NOTE]
>
>在 [交互式图像](interactive-images.md) 或者轮播横幅，热点信息会存储在与图像位置相对的同一元数据位置中，而无论该位置是交互式图像还是轮播横幅。 此功能意味着您可以在任意查看器中轻松重复使用同一图像及其定义的热点数据。
>
>但是，请注意，传送横幅支持图像映射的图像也可能包含热点；交互式图像不会。 如果您打算创建使用相同图像的交互式图像或轮播横幅，请牢记这一点。 您可能希望使用同一图像的不同副本来创建交互式图像和传送横幅。

>[!NOTE]
>
>如果您正在使用热点编辑交互式图像并裁剪图像，则热点会被删除。

**向图像横幅添加热点**:

1. 在资产中，导航到要进行交互的轮播集。
1. 选择轮播集并点按 **[!UICONTROL 编辑]**.
1. 在轮播查看器编辑器中，选择要进行交互的幻灯片。
1. 在页面的左上角附近，点按&#x200B;**[!UICONTROL 热点]**&#x200B;或&#x200B;**[!UICONTROL 图像映射]**。
1. 执行以下任一操作：

   * 对于热点：在图像上，点按您希望显示热点的位置。
   * 对于图像映射：在图像上，点按，然后从左上角拖动到右下角，以创建图像映射区域。 您可以通过拖动角来调整图像映射的大小。

   如有必要，请将热点或图像映射拖到新位置。 根据需要添加其他热点或图像映射。

   要删除热点或图像映射，请点按&#x200B;**[!UICONTROL 操作]**&#x200B;选项卡。在&#x200B;**[!UICONTROL 映射和热点]**&#x200B;标题下，从&#x200B;**[!UICONTROL 选定类型]**&#x200B;下拉菜单中，选择要删除的热点或图像映射的名称。点按菜单旁边的&#x200B;**[!UICONTROL 废纸篓]**&#x200B;图标，然后点按&#x200B;**[!UICONTROL 删除]**。

1. 在“名称”文本字段中，键入热点或图像映射的名称。 此名称也会显示在 **[!UICONTROL 映射和热点]** 下拉列表。 如果您决定在将来对热点或图像映射进行更改，那么提供名称可以让您轻松地识别该热点或图像映射。
1. 在 **[!UICONTROL 操作]** 选项卡：

   * 点按 **[!UICONTROL 概览]**.

      * 如果您是AEM Sites和电子商务客户，请点按 **[!UICONTROL 产品选取器]** 图标（放大镜）以打开 **[!UICONTROL 选择产品]** 页面。 点按要使用的产品，然后点按页面右上角的复选标记，以返回到 **[!UICONTROL 轮播横幅编辑器]**.
      * 如果您不是AEM Sites或Ecommerce客户

         * 请参阅 [识别热点变量](#identifying-hotspot-and-image-map-variables) ，因为您可能想要定义这些变量。
         * 然后，手动输入SKU值。 在 **[!UICONTROL SKU价值]** 文本字段中，键入产品的SKU（库存单位），即您提供的每个不同产品或服务的唯一标识符。 输入的SKU值会自动填充概览模板的变量部分，以便系统能够将点按的热点与特定SKU的概览相关联。
         * （可选）如果您需要在概览中使用其他变量来进一步识别产品，请点按 **[!UICONTROL 添加常规变量]**. 在文本字段中，指定其他变量。 例如， `category=Mens` 是添加的变量。
         * 请参阅 [使用选择器](working-with-selectors.md) 以了解更多信息。
   * 点按 **[!UICONTROL 超链接]**.

      * 如果您是AEM Sites客户，请点按 **[!UICONTROL 网站选择器]** 图标（文件夹）来导航到URL。

         >[!NOTE]
         >如果您的交互式内容具有包含相对URL的链接，特别是指向AEM Sites页面的链接，则无法使用基于URL的链接方法。

      * 如果您是独立客户，请在 **[!UICONTROL HREF]** 文本字段，指定链接网页的完整URL路径。

         请确保指定是在新的浏览器选项卡（推荐为默认选项卡）还是在同一选项卡中打开链接。

         请参阅 [使用选择器](working-with-selectors.md) 以了解更多信息。
   * 点按 **[!UICONTROL 体验片段]**.

      * 如果您是AEM Sites客户，请点按 **[!UICONTROL 搜索]** 图标（放大镜）以打开“体验片段”页面。 点按您要使用的体验片段，然后点按 **[!UICONTROL 选择]** ，以返回到热点管理页面。

         请参阅 [体验片段](/help/sites-authoring/experience-fragments.md).

         **注意**:请注意，在体验片段中嵌入查看器时，“轮播横幅”中的社交媒体共享工具不受支持。 要解决此问题，您可以使用或创建没有社交媒体共享工具的查看器预设。 通过此类查看器预设，您可以成功将其嵌入到体验片段中。

      * 指定将在横幅上显示的体验片段的宽度和高度。

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   您还可以预览轮播横幅的外观。 请参阅 [（可选）预览传送横幅](#optional-previewing-carousel-banners).

1. 点按 **[!UICONTROL 保存]**.
1. 发布轮播集。 发布后会创建可在您的网站页面上使用的嵌入代码或URL。 如果您是AEM Sites客户，则可以将轮播集直接添加到您的网页。

   请参阅 [发布资产](publishing-dynamicmedia-assets.md).

   请参阅 [将轮播集添加到您的网站登录页面](#adding-a-carousel-banner-to-your-website-page)

## 编辑轮播集 {#editing-carousel-sets}

>[!NOTE]
>
>非管理用户必须添加到 **[!UICONTROL dam-users]** 组，以便能够创建或编辑传送横幅。 如果您在创建或编辑时遇到问题，请咨询系统管理员，该管理员可将您添加到 **[!UICONTROL dam-users]** 群组。

您可以对轮播集执行多种编辑任务，如下所示：

* 向轮播集添加幻灯片。 另请参阅 [使用选择器](working-with-selectors.md).
* 在轮播集中对幻灯片重新排序。
* 删除轮播集中的资产。
* 应用查看器预设。
* 删除轮播集。
* 添加或编辑热点和图像映射。 另请参阅 [使用选择器](working-with-selectors.md).

请注意，如果您正在使用热点编辑交互式图像，并裁剪图像，则您的热点会被删除。

**编辑轮播集**:

1. 执行以下任一操作：

   * 将鼠标悬停在轮播集资产上，然后点按 **[!UICONTROL 编辑]** （铅笔图标）。
   * 将鼠标悬停在轮播集资产上，点按 **[!UICONTROL 选择]** （复选标记图标），然后点按 **[!UICONTROL 编辑]** 中。
   * 点按“轮播集”资产，然后点按页面左上角的 **[!UICONTROL 编辑]** （铅笔图标）。

1. 要编辑轮播集，请执行以下任一操作：

   * 要添加幻灯片，请点按 **[!UICONTROL 添加幻灯片]** 图标，然后导航到要添加到该幻灯片的资产，并点按复选标记。
   * 要对幻灯片重新排序，请将幻灯片拖到新位置（选择重新排序图标以移动项目）。
   * 要添加热点或图像映射，请点按热点或图像映射图标，然后参阅 [添加热点和图像映射](#adding-hotspots-or-image-maps-to-an-image-banner).
   * 要编辑轮播集的外观或行为，请点按 **[!UICONTROL 外观]** 选项卡或 **[!UICONTROL 行为]** 选项卡，然后设置所需的选项。
   * 要编辑热点或图像映射，请在相应的幻灯片上选择热点或图像映射，然后根据需要在 **[!UICONTROL 操作]** 选项卡。
   * 要删除幻灯片，请选择它，然后点按 **[!UICONTROL 删除幻灯片]** 中。
   * 要应用预设，请点按页面右上角附近的预设下拉列表，然后选择查看器预设。
   * 要删除整个轮播集，请导航到轮播集，将其选中，然后点按 **[!UICONTROL 删除]**.

## （可选）预览传送横幅 {#optional-previewing-carousel-banners}

您可以使用 **[!UICONTROL 预览]** 要查看您的轮播横幅对客户的外观，并测试轮播横幅热点和图像映射以确保它们按预期行事。

当您对轮播横幅满意时，可以发布该横幅。

* 请参阅 [在网页上嵌入视频查看器或图像查看器](embed-code.md).
* 请参阅 [将URL关联到您的Web应用程序](linking-urls-to-yourwebapplication.md). 请注意，如果您的交互式内容具有包含相对URL的链接，特别是指向AEM Sites页面的链接，则无法使用基于URL的链接方法。
* 请参阅 [将Dynamic Media Assets添加到页面。](adding-dynamic-media-assets-to-pages.md)

您可以从轮播编辑器（首选方法）或 **[!UICONTROL 查看器]** 列表。

**预览传送横幅**:

1. 在 **[!UICONTROL 资产]**，导航到您创建的现有轮播横幅，然后点按以将其打开。
1. 点按 **[!UICONTROL 编辑]**.
1. 在工具栏右角的查看器预设列表中，选择查看器以预览轮播横幅。

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. 点按 **[!UICONTROL 预览]**.
1. 点按图像上的热点或图像映射，以测试其关联的操作。

**从查看器列表预览轮播横幅**:

1. 在 **[!UICONTROL 资产]**，导航到您创建的现有轮播横幅，然后点按以将其打开。
1. 在 **[!UICONTROL 预览]** 页面，点按 **[!UICONTROL 内容]** 图标。
1. 在 **[!UICONTROL 查看器]** 在页面左侧的面板中列出，点按要使用的轮播横幅查看器预设的名称。
1. 点按图像上的热点或图像映射，以测试其关联的操作。

## 发布传送横幅 {#publishing-carousel-banners}

您需要发布轮播才能使用它。 发布轮播集时，会激活URL和嵌入代码。 它还会将轮播发到Dynamic Media云，该云与CDN集成以进行可扩展且性能卓越的交付。

如果您在轮播横幅中使用带有热点的现有交互式图像，则在发布轮播横幅后，必须单独发布该交互式图像。

此外，如果您修改了在轮播横幅中使用的已发布的预先存在的交互式图像，则必须先发布该交互式图像，然后才能将这些更改反映在轮播横幅中。

请参阅 [发布Dynamic Media Assets](publishing-dynamicmedia-assets.md) 有关如何发布传送横幅的信息。

## 将轮播横幅添加到您的网站页面 {#adding-a-carousel-banner-to-your-website-page}

在上传横幅图像以创建轮播、将热点和/或图像映射添加到横幅并发布轮播集后，您现在可以将其添加到现有网站页面。

如果您是AEM Sites客户，则可以通过将交互式媒体组件拖动到页面来直接将轮播横幅添加到您的页面。 请参阅 [将Dynamic Media Assets添加到页面。](adding-dynamic-media-assets-to-pages.md)

但是，如果您是独立的AEM资产客户，则可以按照此部分所述，手动将轮播横幅添加到您的网站登录页面。

1. 复制已发布的轮播集的嵌入代码。

   请参阅 [在网页上嵌入视频查看器或图像查看器](embed-code.md).

1. 将您从AEM Assets复制的嵌入代码添加到您的网页。

   复制的嵌入代码是响应式代码，因此它应该自动适合页面的嵌入区域。

## 将轮播横幅与现有概览集成 {#integrating-the-carousel-banner-with-an-existing-quickview}

此任务仅在您是独立的AEM Assets客户时才适用。

此过程的最后一个步骤是将轮播横幅与您网站上的现有概览实施集成。 每个概览实施都是独一无二的，需要一种特定的方法，最可能需要前端IT人员的协助。

现有的概览实施通常表示在网页上发生的一系列相互关联的操作，这些操作按以下顺序发生：

1. 用户在网站的用户界面中触发一个元素。
1. 前端代码根据在步骤1中触发的用户界面元素来获取概览URL。
1. 前端代码使用步骤2中获取的URL发送Ajax请求。
1. 后端逻辑会将相应的概览数据或内容返回到前端代码。
1. 前端代码加载概览数据或内容。
1. 或者，前端代码会将加载的概览数据转换为HTML表示。
1. 前端代码显示一个模态对话框或面板，并在屏幕上为最终用户呈现HTML内容。

这些调用可能不代表独立的公共API调用，网页逻辑可以从任意步骤调用这些调用。 相反，它是一个链式调用，其中每个后续步骤都会隐藏在上一步的最后一个阶段（回调）中。

在轮播横幅将替换步骤1和部分步骤2的同时，当用户单击轮播横幅中的热点或图像映射时，查看器将处理此类用户交互。 查看器会向网页返回一个事件，其中包含之前添加的所有热点或图像映射数据。

在此类事件处理程序中，前端代码会执行以下操作：

* 监听轮播横幅发出的事件。
* 根据热点或图像映射数据构建概览URL。
* 触发从后端加载概览并在屏幕上呈现概览以供显示的过程。

由AEM Assets返回的嵌入代码已拥有一个现成的事件处理程序，该处理程序已被注释掉。

因此，只需取消代码注释，并将虚拟处理程序主体替换为特定网页的代码即可。

构建概览URL的过程与之前介绍的用于识别热点和图像映射变量的过程基本上相反。

请参阅 [识别热点和图像映射变量](#identifying-hotspot-and-image-map-variables).

触发概览URL并激活概览面板的最后一步，很可能需要IT部门的前端IT人员的协助。 他们深知如何通过正确的步骤准确触发概览实施，从而拥有现成的概览URL。

## 使用概览创建自定义弹出窗口 {#using-quickviews-to-create-custom-pop-ups}

请参阅 [使用概览创建自定义弹出窗口](custom-pop-ups.md).
