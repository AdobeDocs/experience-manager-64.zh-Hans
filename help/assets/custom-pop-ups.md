---
title: 使用概览创建自定义弹出窗口
seo-title: Using Quickviews to create custom pop-ups
description: 默认的概览用于电子商务体验，其中会显示一个弹出窗口，其中包含产品信息以促进购买。 您可以触发要在弹出窗口中显示的自定义内容。
seo-description: The default Quickview is used in ecommerce experiences whereby a pop-up is displayed with product information to drive a purchase. You can trigger custom content to display in the pop-ups.
uuid: b906cfff-ac44-4989-b6da-8a9bbf02af03
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4bcab3f4-500f-432e-b16b-cdc26b9bab4d
exl-id: 56b070e4-b445-4488-acff-685b7ce5785f
feature: Configuration
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# 使用概览创建自定义弹出窗口 {#using-quickviews-to-create-custom-pop-ups}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

默认的概览用于电子商务体验，其中会显示一个弹出窗口，其中包含产品信息以促进购买。 但是，您可以触发要在弹出窗口中显示的自定义内容。 根据您使用的查看器，此功能允许用户单击热点、缩略图图像或图像映射以查看信息或相关内容。

Dynamic Media中的以下查看器支持概览：

* 交互式图像（可单击的热点）
* 交互式视频（视频播放期间可单击的缩略图图像）
* 轮播横幅（可单击的热点或图像映射）

虽然每个查看器的功能不同，但在所有三个受支持的查看器中，创建概览的过程都是相同的。

**要使用概览创建自定义弹出窗口，请执行以下操作：**

1. 为上传的资产创建概览。

   通常，在编辑资产以用于所使用的查看器的同时，会创建一个概览。

   <table> 
    <tbody> 
    <tr> 
    <td><strong>您使用的查看器</strong></td> 
    <td><strong>完成这些步骤以创建概览</strong></td> 
    </tr> 
    <tr> 
    <td>交互式图像</td> 
    <td><a href="/help/assets/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">将热点添加到图像横幅</a>.</td> 
    </tr> 
    <tr> 
    <td>交互式视频</td> 
    <td><a href="/help/assets/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">为视频添加交互性</a>.</td> 
    </tr> 
    <tr> 
    <td>传送横幅</td> 
    <td><a href="/help/assets/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">将热点或图像映射添加到横幅</a>.<br /> </td> 
    </tr> 
    </tbody> 
   </table>

1. 获取查看器嵌入代码以在您的网站中集成查看器。

   <table> 
    <tbody> 
    <tr> 
    <td><strong>您使用的查看器</strong><br /> </td> 
    <td><strong>完成这些步骤以将查看器与您的网站集成</strong></td> 
    </tr> 
    <tr> 
    <td>交互式图像</td> 
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">将交互式图像与您的网站集成</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>交互式视频<br /> </td> 
    <td><a href="/help/assets/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">将交互式视频与您的网站集成</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>轮播横幅</td> 
    <td><a href="/help/assets/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">将轮播横幅添加到您的网站页面</a>.<br /> </td> 
    </tr> 
    </tbody> 
   </table>

1. 现在，您使用的查看器需要知道如何使用概览。

   为此，查看器使用名为 `QuickViewActive`.

   **示例**
假定您在网页上对交互式图像使用了以下示例嵌入代码：

   ![chlimage_1-291](assets/chlimage_1-291.png)

   处理程序将使用加载到查看器中 `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **使用上面的示例嵌入代码示例，我们具有以下代码：**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   详细了解 `setHandlers()` 方法：

   * 交互式图像查看器： [setHandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * 交互式视频查看器： [setHandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. 您现在需要配置 `quickViewActivate` 处理程序。

   quickViewActivate处理程序控制查看器中的概览。 处理程序包含变量列表和函数调用以与概览一起使用。 嵌入代码为概览中设置的SKU变量提供了映射，并提供了loadQuickView函数调用的示例。

   **变量映射**
将网页中使用的变量映射到概览中包含的SKU值和通用变量：

   `var *variable1*= inData.*quickviewVariable*`

   提供的嵌入代码具有SKU变量的示例映射：

   `var sku=inData.sku`

   也从概览中映射其他变量，如下所示：

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i> 
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **函数调用**
处理程序还需要函数调用，以便概览正常工作。 假定您的主机页面可以访问该函数。 嵌入代码提供了一个示例函数调用：

   `loadQuickView(sku)`

   示例函数调用假定函数 `loadQuickView()` 存在且可访问。

   请在以下网站了解有关quickViewActivate方法的更多信息：

   * 交互式图像查看器 —  [事件回调](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * 交互式视频查看器 —  [事件回调](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * 交互式视频查看器中的交互式数据支持 —  [交互式数据支持](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. 执行以下操作：

   * 取消对嵌入代码的setHandlers部分的注释。
   * 映射概览中包含的任何其他变量。

      * 更新 `loadQuickView(sku,*var1*,*var2*)` 调用。
   * 在查看器外的页面上创建一个简单的loadQuickView()函数。

      例如，以下内容会将SKU的值写入浏览器控制台：

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * 将测试HTML页面上传到Web服务器并打开。

      在映射概览中的变量并就地调用函数后，浏览器控制台会使用提供的示例函数将变量值写入浏览器控制台。



1. 您现在可以使用函数在概览中调用一个简单的弹出窗口。 以下示例使用 `DIV` 来访问Advertising Cloud。
1. 设置弹出窗口的样式 `DIV` 以下方式。 根据需要添加您自己的其他样式。

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. 放置弹出窗口 `DIV` 在HTML页面的正文中。

   其中一个元素会设置一个ID，当用户调用概览时，该ID会随SKU值进行更新。 该示例还包含一个简单按钮，用于在弹出窗口可见后再次隐藏该弹出窗口。

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. 添加函数以更新弹出窗口中的SKU值；通过替换在步骤5中创建的简单函数，使弹出窗口可见。 ，具有以下特点：

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. 将测试HTML页面上传到Web服务器并打开。 查看器会显示弹出窗口 `DIV` 用户调用概览时。
1. **如何以全屏模式显示自定义弹出窗口**

   某些查看器（例如交互式视频查看器）支持以全屏模式显示。 但是，如果按照前面步骤中所述使用弹出窗口，则在全屏模式下，该弹出窗口会显示在查看器后面。

   要在标准模式和全屏模式下显示弹出窗口，请将弹出窗口附加到查看器容器。 要实现此目的，可使用第二个处理程序方法， `initComplete`.

   的 `initComplete` 查看器初始化后，将调用处理程序。

   ```xml
   "initComplete":function() { code block }
   ```

   详细了解 `init()` 方法：

   * 交互式图像查看器 —  [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * 交互式视频查看器 —  [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. 要将上述步骤中描述的弹出窗口附加到查看器，请使用以下代码：

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   在上面的代码中，我们已执行以下操作：

   * 已识别我们的自定义弹出窗口。
   * 已从DOM中将其删除。
   * 已识别查看器容器。
   * 已将弹出窗口附加到查看器容器。

1. 现在，您的整个setHandlers代码应当类似于以下内容（使用了交互式视频查看器）：

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. 加载处理程序后，可以初始化查看器：

   `*viewerInstance.*init()`

   **示例**
此示例使用交互式图像查看器。

   `s7interactiveimageviewer.init()`

   将查看器嵌入到主机页面后，请确保已创建查看器实例并加载处理程序，然后才能使用调用查看器 `init()`.
