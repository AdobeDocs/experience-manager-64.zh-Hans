---
title: 视频
seo-title: 视频
description: 了解如何在Dynamic Media中处理视频
seo-description: 了解如何在Dynamic Media中处理视频
uuid: 15e89f88-2787-472d-bbb6-d370bbab9228
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
discoiquuid: b721dc7c-b056-47f5-9489-9f4db45b68a0
translation-type: tm+mt
source-git-commit: a3a160a0281c1ea2ca050c2c747d6a5ec1d952b3
workflow-type: tm+mt
source-wordcount: '10507'
ht-degree: 24%

---


# 视频 {#video}

本节介绍如何在 Dynamic Media 中处理视频。

## 快速开始: 视频 {#quick-start-videos}

以下工作流分步说明旨在帮助您快速设置并运行Dynamic Media中的自适应视频集。 每个步骤之后都会交叉引用主题标题，您可以从中找到更多信息。

>[!NOTE]
>
>在Dynamic Media中处理视频之前，请确保AEM管理员已启用并配置Dynamic MediaCloud Services。
>
>* 请参 [阅配置Dynamic Media —— 混合模式中的配置Dynamic MediaCloud Services。](/help/assets/config-dynamic.md)
>* 请参 [阅配置Dynamic Media -Scene7模式](config-dms7.md)[和Dynamic Media -Scene7模式疑难解答](troubleshoot-dms7.md)

>



1. 通过执行以下操作，**上传 Dynamic Media 视频**：

   * 创建您自己的视频编码用户档案。 或者，您只需使用Dynamic Media附带的预定义“自适应视频编码”用户档案。

      * [创建视频编码用户档案](video-profiles.md)。
      * Learn more about [Best practices for video encoding](#best-practices-for-encoding-videos).
   * 将视频处理用户档案关联到要上传主控视频的一个或多个文件夹。

      * [将视频用户档案应用到文件夹](video-profiles.md#applying-a-video-profile-to-folders)。
      * 了解有关[组织数字资产以使用处理配置文件的最佳实践](organize-assets.md#organize-using-folders)的更多信息。
      * 了解有关[组织数字资产](organize-assets.md)的更多信息。
   * 将主控视频上传到文件夹。 您可以上传每个高达15 GB的视频文件。 向文件夹添加视频时，会根据您为文件夹分配的视频处理用户档案对视频进行编码。

      * [上传视频](managing-video-assets.md#uploading-and-previewing-video-assets)。
      * Learn more about [Supported input file formats](assets-formats.md#supported-multimedia-formats).
   * 监视视 [频编码在资产](#monitoring-video-encoding-and-youtube-publishing-progress) 或工作流视图中的进展情况。




1. 通过执行以下任意操作，**管理 Dynamic Media 视频**：

   * 组织、浏览和搜索视频资产

      * [组织数字资产](organize-assets.md)

         Learn more about [Best practices for organizing your digital assets for using processing profiles](organize-assets.md#organize-using-folders)

      * [搜索视频资产](search-video-assets.md) 或搜 [索资产](managing-assets-touch-ui.md#searching-assets)
   * 预览和发布视频资产

      * 视图源视频和视频的编码演绎版及其关联的缩略图：

         [预览视频](managing-video-assets.md#uploading-and-previewing-video-assets) 或预 [览资产](previewing-assets.md)

         [查看视频演绎版](video-renditions.md)

         [管理视频演绎版](managing-assets-touch-ui.md#managing-renditions)

      * [管理查看器预设](managing-viewer-presets.md)
      * [发布资产](publishing-dynamicmedia-assets.md)
   * 处理视频元数据

      * 视图编码视频演绎版的属性，如帧速率、音频和视频比特率以及编解码器：

         [查看视频演绎版属性](video-renditions.md)

      * 编辑视频的属性，如标题、描述和标记、自定义元数据字段：

         [编辑视频属性](managing-assets-touch-ui.md#editing-properties)

      * [管理数字资产的元数据](metadata.md)
      * [元数据架构](metadata-schemas.md)
   * 审核、批准和批注视频

      * [对视频添加注释](managing-video-assets.md#annotating-video-assets) 或对 [资产添加注释](managing-assets-touch-ui.md#annotating)
      * [将工作流应用于资](assets-workflow.md) 产 [或启动资产工作流](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [审核文件夹资产](bulk-approval.md)
      * [项目](/help/sites-authoring/projects.md)




1. 通过执行以下任一操作，**发布 Dynamic Media 视频**：

   * 如果您使用Adobe Experience Manager作为Web内容管理系统，则可以将视频直接添加到网页。

      * [将视频添加到网页](adding-dynamic-media-assets-to-pages.md)。
   * 如果您使用的是第三方Web内容管理系统，则可以将视频链接或嵌入到您的网页。

      * 使用URL集成视频：

         [将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md).
      * 使用网页上的嵌入代码集成视频：

         [将视频查看器嵌入网页](embed-code.md)。
   * [将视频发布到 YouTube](#publishing-videos-to-youtube)。
   * [生成视频报表](#viewing-video-reports)。
   * [为视频添加字幕](#adding-captions-to-video)。



## Working with video in Dynamic Media {#working-with-video-in-dynamic-media}

Dynamic Media中的视频是一款端到端解决方案，它可轻松发布高质量自适应视频以跨多个屏幕（包括桌面、iOS、Android、Blackberry和Windows移动设备）进行流化。 自适应视频集为同一视频的不同版本编码，这些版本以不同的比特率和格式进行编码，如400 kbps、800 kbps和1000 kbps。 桌面计算机或移动设备会检测可用带宽。

例如，在 iOS 移动设备上，设备检测到 3G、4G 或 Wi-Fi 等带宽。设备会随之自动从自适应视频集内的各种视频比特率中选择正确的编码视频。然后，视频会在桌面设备、移动设备或平板电脑上进行流播放。

此外，如果桌面或移动设备上的网络条件发生变化，设备会自动动态地切换视频质量。同时，如果客户在桌面上进入全屏模式，自适应视频集也会做出响应来使用较好的分辨率，从而改善客户的观看体验。使用自适应视频集可为在多个屏幕和设备上播放Dynamic Media视频的客户提供最佳播放方式。

视频播放器用来确定在播放期间要播放或要选择的编码视频的逻辑基于以下算法：

1. 视频播放器根据最接近播放器本身中为“初始比特率”设置的值的比特率来加载初始视频片段。
1. 视频播放器根据带宽速度的变化使用以下条件进行切换：

   1. 播放器选取低于或等于估计带宽的最高带宽流。
   1. 播放器只考虑80%的可用带宽。 但是，如果它在切换，则更保守，只有70%，以避免过高估计，并立即切换回去。

有关该算法的详细技术信息，请参 [阅https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

为了管理单个视频和自适应视频集，支持以下内容：

* 用多种支持的视频格式和音频格式上传视频，并将视频编码为 MP4 H.264 格式，以供在多种屏幕上播放。您可以使用预定义的自适应视频预设或单个视频编码预设，或者自定义您自己的编码，来控制视频的质量和大小。

   * 在生成自适应视频集时，会包括 MP4 视频。
   * **注意**：主/源视频不会添加到自适应视频集。

* 在所有HTML5视频查看器中添加视频字幕。
* 组织、浏览和搜索具有全面元数据支持的视频，以实现高效的视频资产管理。
* 将自适应视频集交付到Web、桌面和移动设备，包括iPhone、iPad、Android、Blackberry和Windows手机。

自适应视频流播放在多种 iOS 平台上受支持。请参阅 [Adobe查看器参考指南](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html)。

Dynamic Media supports mobile video playback for MP4 H.264 video. You can find Blackberry devices that support this video format at the following: [Supported video formats on Blackberry](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

请参阅下面的文档，以了解支持此视频格式的 Windows 设备：[Windows Phone 上支持的视频格式](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)。

* 使用 Dynamic Media 视频查看器预设播放视频，包括以下查看器：

   * 单一视频查看器。
   * 将视频和图像内容组合在一起的混合媒体查看器。

* 配置视频播放器以满足您的品牌需求。
* 使用简单的 URL 或嵌入代码将视频集成到您的网站、移动站点或移动应用程序。

请参阅[动态视频播放](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480)。

另请参阅《Scene7 查看器参考指南》中的“[关于 HTML5 查看器](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html)”。

## Best practice: Using the HTML5 video viewer {#best-practice-using-the-html-video-viewer}

Dynamic Media HTML5视频查看器预设是强大的视频播放器。 您可以使用它们避免许多与HTML5视频播放相关的常见问题以及与移动设备相关的问题，如缺少自适应流投放和桌面浏览器访问能力有限。

在播放器的设计方面，您可以使用标准的 Web 开发工具设计视频播放器的所有功能。例如，您可以使用 HTML5 和 CSS 设计按钮、控件和自定义标识图像背景，从而帮助您向客户展示自定义的外观。

在查看器的播放方面，查看器可以自动检测浏览器的视频功能。然后，它使用HLS流（自适应视频流）提供视频。 或者，如果这些传送方法不可用，则会改用 HTML5 渐进式流播放。

通过将使用 HTML5 和 CSS 设计播放组件的功能、支持嵌入式播放的功能，以及根据浏览器的容量使用自适应和渐进式流播放的功能整合到单一播放器中，您可以扩大富媒体内容可以传送到的桌面和移动用户的范围，并确保简化视频体验。

另请参阅《 查看器参考指南》中的“[关于 HTML5 查看器](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html)”。

### 使用HTML5视频查看器在桌面计算机和移动设备上播放视频 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

对于桌面和移动自适应视频流播放，比特率切换所使用的视频基于自适应视频集中的所有MP4视频。

使用HLS（HTTP实时流）视频流或渐进式视频下载进行视频播放。 在AEM的先前版本（如6.0、6.1和6.2）中，视频通过HTTP进行流化。

但是，在AEM 6.3及更高版本中，视频现在通过HTTPS（即HLS视频流）进行流化，因为DM网关服务URL也始终使用HTTPS。 请注意，此默认行为不会对客户造成任何影响。 也就是说，除非浏览器不支持，否则视频流将始终通过HTTPS进行。 （请参阅下表）。 因此，

* 如果您的HTTPS网站具有HTTPS视频流，则流可以正常进行。
* 如果您有一个HTTP网站，其中包含HTTPS视频流，则流程可以正常进行，并且Web浏览器中不存在混合内容问题。

HLS（HTTP实时流）是自适应视频流播放的Apple标准，可根据网络带宽容量自动调整播放。 它还允许客户“搜索”视频中的任何点，而无需等待视频的其余部分下载（另请参阅HTTP实时流）。

渐进式视频通过下载视频并将其本地存储到用户的桌面屏幕或移动设备来交付。

下表介绍使用Scene7视频查看器在桌面计算机和移动设备上播放视频的设备、浏览器和方法。

<table> 
 <tbody> 
  <tr> 
   <td><strong>设备</strong></td> 
   <td><strong>浏览器</strong></td> 
   <td><strong>视频播放模式</strong></td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>Internate Explorer 9和10</td> 
   <td>渐进式下载。</td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>Internate Explorer 11+</td> 
   <td>在Windows 8和Windows 10上——只要请求HLS，就强制使用HTTPS。 已知限制： HLS上的HTTP在Windows 7上的浏览器／操作系统组合<br /> - <br /> 渐进式下载中不工作。 使用标准逻辑选择HTTP与HTTPS协议。</td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>Firefox 23-44</td> 
   <td>渐进式下载。</td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>Firefox 45或更高版本</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>铬黄</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>桌面设备</td> 
   <td>Safari(Mac)</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>Chrome（Android 6或更早版本）</td> 
   <td>渐进式下载。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>Chrome（Android 7或更高版本）</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>Android（默认浏览器）</td> 
   <td>渐进式下载。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>Safari(iOS)</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>Chrome(iOS)</td> 
   <td>HLS视频流。</td> 
  </tr> 
  <tr> 
   <td>移动设备</td> 
   <td>黑莓</td> 
   <td>HLS视频流。</td> 
  </tr> 
 </tbody> 
</table>

## Architecture of Dynamic Media video solution {#architecture-of-dynamic-media-video-solution}

下图显示了视频创作的整个工作流，在此流程中，视频通过 DMGateway 上传并编码，然后进行发布以供公众观看。

![chlimage_1-427](assets/chlimage_1-427.png)

## 用于视频的混合发布架构 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## 视频编码的最佳实践 {#best-practices-for-encoding-videos}

如果您已启用 Dynamic Media 并设置了视频云服务，则 **[!UICONTROL Dynamic Media 编码视频]**&#x200B;工作流会对视频进行编码。此工作流会捕获工作流进程历史记录和失败信息。请参阅[监视视频编码和 YouTube 发布进度](#monitoring-video-encoding-and-youtube-publishing-progress)。If you have enabled Dynamic Media and set up Video Cloud services, the **[!UICONTROL Dynamic Media Encode Video]** workflow automatically takes effect when you upload a video. (If you are not using Dynamic Media, the **[!UICONTROL DAM Update Asset]** workflow takes effect.)

以下是关于源视频文件编码的最佳实践提示。

有关视频编码的建议，请参阅以下资源：

* 文章：*流播放 101：基础知识 - 编解码器、带宽、数据率和分辨率：*[www.adobe.com/go/learn_s7_streaming101_cn](https://www.adobe.com/go/learn_s7_streaming101_en)。
* 视频：*视频编码基础知识：*[www.adobe.com/go/learn_s7_encoding_cn](https://www.adobe.com/go/learn_s7_encoding_en)。

### 源视频文件 {#source-video-files}

在对视频文件进行编码时，请尽可能使用最高质量的源视频文件。避免使用先前已编码的视频文件，因为这样的文件已经压缩，进一步编码会导致创建的视频质量不佳。

下表说明了在编码之前，源视频文件应具有的建议大小、宽高比和最低比特率。

| 大小 | 宽高比 | 最低比特率 |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 4500 kbps，适用于大部分视频。 |
| 1280 X 720 | 16:9 | 3000 - 6000 kbps，具体取决于视频中的动作数量。 |
| 1920 X 1080 | 16:9 | 6000 - 8000 kbps，具体取决于视频中的动作数量。 |

### 获取文件的元数据 {#obtaining-a-file-s-metadata}

获取文件元数据的方法如下：通过使用视频编辑工具查看文件的元数据，或者使用专门为获取元数据而设计的应用程序。下面说明了如何使用第三方应用程序 MediaInfo 获取视频文件的元数据：

1. 转到此网页： [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo)。
1. 选择并下载所使用的GUI版本的安装程序，然后按照安装说明操作。
1. After installation, either right-click the video file (Windows only) and select **[!UICONTROL MediaInfo]**, or open **[!UICONTROL MediaInfo]** and drag your video file into the application. You see all metadata associated with your video file, including its width, height, and fps.

### 宽高比 {#aspect-ratio}

在为主视频文件选择或创建视频编码预设时，请确保预设的宽高比与主视频文件的宽高比相同。宽高比是视频的宽度与高度的比率。

要确定视频文件的长宽比，请获取该文件的元数据并记录该文件的宽度和高度（请参阅上面的“获取文件的元数据”）。 然后，使用此公式确定宽高比：

*宽度/高度 = 宽高比*

下表说明了公式结果如何转换成常见的宽高比选项：

| 公式结果 | 宽高比 |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

例如，如果一个视频的宽度为 1440，高度为 1080，则其宽高比为 1440/1080，也就是 1.33。在这种情况下，要对该视频文件进行编码，您需要选择宽高比为 4:3 的视频编码预设。

### 比特率 {#bitrate}

比特率是为组成一秒钟的视频播放而编码的数据量。 比特率以千比特／秒(Kbps)为单位。

由于所有编解码器都使用有损压缩，因此比特率是影响视频质量的最重要因素。 使用有损压缩时，对视频文件的压缩程度越大，质量就降低得越多。因此，所有其他特性（分辨率、帧速率和编解码器）相等，比特率越低，压缩文件的质量就越低。

在选择比特率编码时，您可以选择两种类型：

* **恒定比特率编码** (CBR)-在CBR编码过程中，在整个编码过程中，比特率或每秒的比特数保持不变。 CBR编码在整个视频中将设置的数据速率保持为您的设置。 此外，CBR编码不会为质量优化媒体文件，但会节省存储空间。

   如果视频在整个视频中包含类似的运动级别，则使用CBR。 CBR最常用于流式视频内容。 另请参 [阅使用自定义添加的视频编码参数](video-profiles.md#using-custom-added-video-encoding-parameters)。

* **可变比特率编码** (VBR)- VBR编码根据压缩程序所需的数据，将数据率调低并调整到您设置的上限。 这意味着在VBR编码过程中，媒体文件的比特率会根据媒体文件的比特率需求动态地增加或减少。

   VBR编码时间较长，但生成的结果最为有利； 媒体文件的质量优越。 VBR最常用于视频内容的http渐进投放。

**您何时应使用VBR与CRB?**
在选择VBR与CBR时，几乎始终建议您对媒体文件使用VBR。 VBR以竞争比特率提供更高质量的文件。 使用VBR时，请确保使用两遍编码，并将最大比特率设置为目标视频比特率的1.5倍。

在选择视频编码预设时，请考虑目标最终用户的连接速度。所选预设的数据率应该是目标最终用户连接速度的 80%。例如，如果目标最终用户的连接速度是 1000 Kbps，则最佳预设就是视频数据率为 800 Kbps 的预设。

下表说明了典型连接速度的数据率。

| 速度 (Kbps) | 连接类型 |
|--- |--- |
| 256 | 拨号连接。 |
| 800 | 典型移动连接。对于此类连接，3G 体验的目标数据率范围为 400 至最高 800。 |
| 2000 | 典型宽带桌面连接。 对于此连接，目标数据率范围为800-2000 Kbps，大多数目标的平均速率为1200-1500 Kbps。 |
| 5000 | 典型高宽带连接。不建议在此较高范围下进行编码，因为大多数用户并不具备此速度的视频传送条件。 |

### 分辨率 {#resolution}

**分辨率**&#x200B;以像素为单位描述视频文件的高度和宽度。大多数源视频以高分辨率存储（例如，1920 x 1080）。出于流播放目的，源视频会压缩至较低分辨率（640 x 480 或更低）。

分辨率和数据率是两个相互关联、密不可分的因素，它们决定着视频质量。为保持同等的视频质量，视频文件的像素数越高（分辨率越高），数据率就必须越高。例如，考虑分辨率分别为 320 x 240 和 640 x 480 的视频文件的每帧像素数：

| 分辨率 | 每帧像素数 |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

对于分辨率为 640 x 480 的文件，其每帧像素数高出四倍。为使这两个示例分辨率的文件实现同等的数据率，您需要对分辨率为 640 x 480 的文件应用四倍的压缩，而这会降低视频的质量。因此，如果视频数据率为 250 Kbps，则在 320 x 240 分辨率下观看时质量会很高，但在 640 x 480 分辨率下观看时质量则不高。

总的来说，您使用的数据率越高，视频的画质就越好；您使用的分辨率越高，您保持画质所需的数据率就越高（与较低分辨率相比）。

由于分辨率与数据率相关联，在对视频进行编码时，有两种选择：

* 选择一个数据率，然后使用在选定数据率下看起来效果不错的最高分辨率进行编码。
* 选择一个分辨率，然后使用在选定分辨率下获得高质量视频所需的数据率进行编码。

在为主视频文件选择（或创建）视频编码预设时，请使用此表来确定正确的分辨率：

| 分辨率 | 高度（像素） | 屏幕大小 |
|--- |--- |--- |
| 240p | 240 | 微型屏幕 |
| 300p | 300 | 通常用于移动设备的小型屏幕 |
| 360p | 360 | 小型屏幕 |
| 480p | 480 | 中型屏幕 |
| 720p | 720 | 大型屏幕 |
| 1080p | 1080 | 高清晰度大型屏幕 |

### Fps (Frames per second) {#fps-frames-per-second}

在美国和日本，大多数视频以 29.97 帧/秒 (fps) 的速率拍摄；在欧洲，大多数视频以 25 fps 的速率拍摄。电影是以 24 fps 的速率拍摄。

选择的视频编码预设应与主视频文件的 fps 速率相匹配。例如，如果您的主视频采用 25 fps，则应选择 25 fps 的编码预设。默认情况下，所有自定义编码均采用主视频文件的 fps。鉴于这一原因，您在创建视频编码预设时不需要明确指定 fps 设置。

### 视频编码尺寸 {#video-encoding-dimensions}

为实现最佳效果，请选择相应编码尺寸，使源视频成为所有编码视频的整数倍数。

要计算此比率，请用源宽度除以编码宽度，得出宽度比。然后，用源高度除以编码高度，得出高度比。

如果计算得出的比率是整数，就意味着视频已得到最佳缩放。如果计算得出的比率不是整数，则会影响视频质量，使显示屏上出现残留像素伪影。当视频含有文本时，这种影响最为明显。

例如，假定源视频的分辨率为 1920 x 1080。在下表中，这三个编码视频提供了可使用的最佳编码设置。

<table> 
 <tbody> 
  <tr> 
   <th><p>视频类型</p> </th> 
   <th><p>宽度 x 高度</p> </th> 
   <th><p>宽度比</p> </th> 
   <th><p>高度比</p> </th> 
  </tr>
  <tr> 
   <td><p>源</p> </td> 
   <td><p>1920 x 1080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>编码</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>编码</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>3</p> </td> 
  </tr> 
  <tr> 
   <td><p>编码</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### 编码视频文件格式 {#encoded-video-file-format}

Dynamic Media 建议使用 MP4 H.264 视频编码预设。由于 MP4 文件使用 H.264 视频编解码器，因此 MP4 可以提供高质量的视频，但需要压缩文件大小。

## 将视频发布到 YouTube {#publishing-videos-to-youtube}

您可以将内部部署AEM视频资产直接发布到您之前创建的YouTube渠道。

要将视频资产发布到YouTube，您需要设置带有标记的AEM Assets。 将这些标记与YouTube渠道关联。 如果视频资产的标签与YouTube渠道的标签匹配，则视频将发布到YouTube。 如果视频资产没有标记，则不会将其发布到YouTube。

发布到YouTube会绕过AEM中的处理用户档案系统，因此也会绕过视频编码用户档案。 这种旁路之所以发生，是因为YouTube有其自己的编码，因此不需要视频处理用户档案。 但是，在大多数情况下，预计您的视频资产已通过视频处理用户档案。 当您绕过视频处理用户档案并直接发布到YouTube时，这只意味着AEM资产中的视频资产没有可查看的缩略图。 这也意味着，如果您以动态媒体运行模式运行，则未编码的视频将不能用于任何Dynamic Media资产类型。

将视频资产发布到YouTube服务器需要完成以下任务，以确保使用YouTube进行安全、安全的服务器到服务器身份验证：

1. [配置Google Cloud设置](#configuring-google-cloud-settings)
1. [创建YouTube渠道](#creating-a-youtube-channel)
1. [添加用于发布的标记](#adding-tags-for-publishing)
1. [启用YouTube发布复制代理](#enabling-the-youtube-publish-replication-agent)
1. [在AEM中设置YouTube](#setting-up-youtube-in-aem)
1. [（可选）自动设置已上传视频的默认YouTube属性](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [将视频发布到您的 YouTube 频道](#publishing-videos-to-your-youtube-channel)
1. [（可选）验证已发布到 YouTube 上的视频](video.md#optional-verifying-the-published-video-on-youtube)
1. [将 YouTube URL 关联到您的 Web 应用程序](#linking-youtube-urls-to-your-web-application)

您还可以[取消发布视频以将其从 YouTube 中删除](#unpublishing-videos-to-remove-them-from-youtube)。

### 配置Google Cloud设置 {#configuring-google-cloud-settings}

要发布到YouTube，您需要一个Google帐户。 如果您有GMAIL帐户，那么您已经有Google帐户。 如果您没有Google帐户，您可以轻松创建一个。 您需要此帐户，因为您需要凭据才能将视频资产发布到YouTube。 如果已创建帐户，请跳过此任务并继 [续创建YouTube渠道](#creating-a-youtube-channel)。

>[!NOTE]
>
>编写本文时，以下步骤是准确的。 不过，谷歌会定期更新其网站，恕不另行通知。 因此，这些步骤可能略有不同。

**配置Google Cloud设置**:

1. 创建新的Google帐户。

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   如果您已经有Google帐户，请跳到下一步。

1. 请访问 [https://cloud.google.com/](https://cloud.google.com/)。
1. 在Google云平台页面顶部附近，点按控 **[!UICONTROL 制台]**。 您可能需 **要使用** Google帐户凭据登录。
1. 在仪表板 **[!UICONTROL 页]** ，点按创 **[!UICONTROL 建项目]**。
1. 在“新 **[!UICONTROL 建项目]** ”对话框中，输入项目名称。

   请注意，您的项目ID基于您的项目名称。 因此，请仔细选择项目名称； 创建后无法更改它。 此外，稍后在Adobe Experience Manager设置YouTube时，您需要再次输入同一项目ID。 您可能需要写下项目的ID。
1. 点按&#x200B;**[!UICONTROL 创建]**。

1. 在项目的 **[!UICONTROL 仪表板]**，在入 **[!UICONTROL 门卡]** ，点按启用 **[!UICONTROL API并]**&#x200B;获取密钥等凭据。
1. 在仪表板页顶部 **[!UICONTROL 附近]** ，点 **[!UICONTROL 按启用API]**。
1. 在“ **[!UICONTROL 库]** ”页面的YouTube API下，点 **[!UICONTROL 击YouTube Data API]**。
1. 在YouTube数据API v3] **页面顶部附近** ，点按 **[!UICONTROL 启]** 用以打开它。
1. 要使用API，您可能需要凭据。 如有必要，请点按 **[!UICONTROL 创建凭据]**。
1. 从 **[!UICONTROL Where will the API?]** 下拉列表，选 **[!UICONTROL 择“Web服务器”（例如node.js、Tomcat）]**。
1. 在“ **[!UICONTROL 将访问哪些数据”下？]** 选择 **[!UICONTROL 用户数据]**。
1. 点击 **[!UICONTROL 我需要哪些凭据？]** 按钮.
1. 在“创 **[!UICONTROL 建OAuth 2.0客户端ID”标题]** 下，输入唯一名称。
1. 在“已授权的Javascript来源 **[!UICONTROL ”标题下的文本字段中，输入以下路径，在路径中替换您自己的域和端口号，然后]** 按Enter **** 以将路径添加到列表:

   `https://<servername.domain>:<port_number>`

   例如，`https://1a2b3c.mycompany.com:4321`

   **注意**: 以上路径示例仅供说明。

1. 在“已授权重定 **[!UICONTROL 向URI”标题下的文本字段中]** ，输入以下内容，在路径中替换您自己的域和端口号，然后按Enter以添加列表的路径：

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   例如，`https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **注意**: 以上路径示例仅供说明。

1. 点按 **[!UICONTROL 创建客户端ID]**。
1. On the Credentials page, under the **[!UICONTROL Set up the OAuth 2.0 consent screen]** heading, select the Gmail address that you are currently using.
1. 在向用户显示的产 **[!UICONTROL 品名称标题下的文本字]** 段中，输入您希望在同意屏幕上显示的内容。

   AEM管理员在YouTube上进行身份验证时，会显示同意屏幕； AEM将与YouTube联系以获得许可。

1. 点按 **[!UICONTROL 继续]**。
1. 在“下载 **[!UICONTROL 凭据]** ”标题下， **[!UICONTROL 点按下载]**。
1. 保存文 `client_id.json` 件。

   稍后在Adobe Experience Manager设置YouTube时，您将需要此下载的json文件。

1. 点按&#x200B;**[!UICONTROL 完成]**。

   现在您将创建一个YouTube渠道。

### 创建YouTube渠道 {#creating-a-youtube-channel}

将视频发布到YouTube需要您拥有一个或多个渠道。 如果已创建YouTube渠道，可跳过此任务，转至“添加用 **于发布的标记”**。

>[!CAUTION]
>
>请确保已在YouTube &amp;ast;before&amp;ast；中设置一个或多个渠道 您可以在AEM的“YouTube设置”下添加渠道(请参 [阅下面的AEM中设](#setting-up-youtube-in-aem) 置YouTube)。 如果您未能这样做，则系统不会对任何现有渠道发出警告。 但是，添加渠道时仍会发生Google身份验证，但无法选择发送视频的渠道。

**要创建YouTube渠道**:

1. 转到 [https://www.youtube.com](https://www.youtube.com/) ，然后使用您的Google帐户凭据登录。
1. 在YouTube页面的右上角，点按用户档案图片（也可能以纯色圆圈中的字母显示），然后点 **[!UICONTROL 按YouTube设置]** （圆齿轮图标）。
1. 在“概 **[!UICONTROL 述]** ”页面的“其他功 **[!UICONTROL 能”标题下]** ，点按 **[!UICONTROL 查看所有渠道或创建新渠道]**。
1. 在渠道 **[!UICONTROL 页面中]** ，点 **[!UICONTROL 按创建新渠道]**。
1. 在“品 **[!UICONTROL 牌帐户]** ”页面的“品牌 **[!UICONTROL 帐户名称”字段中，输入业务名称或您选择的要发布视频资产的任何其他渠道名，然后点按创]** 建 ****。

   记住在此处输入的名称，因为在AEM中设置YouTube时，您需要再次输入该名称。

1. （可选）如有必要，请添加更多渠道。

   现在，您将添加用于发布的标记。

### 添加用于发布的标记 {#adding-tags-for-publishing}

要将视频发布到YouTube,AEM会将标记关联到一个或多个YouTube渠道。 要添加用于发布的标记，请参阅 [管理标记](/help/sites-administering/tags.md)。

或者，如果您打算在AEM中使用默认标记，则可以跳过此任务并转 [到启用YouTube发布复制代理](#enabling-the-youtube-publish-replication-agent)。

### 启用YouTube发布复制代理 {#enabling-the-youtube-publish-replication-agent}

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Deployment > Replication > Agents on Author]**.
1. 在“作 **[!UICONTROL 者代理]** ”页面上， **[!UICONTROL 点按YouTube发布(youtube)]**。
1. 在工具栏的设置右侧，点按编 **[!UICONTROL 辑]**。
1. 选中“ **[!UICONTROL 启用]** ”复选框以打开复制代理。
1. 点按 **[!UICONTROL 确定]**。

   现在你将在AEM建立YouTube。

### Setting up YouTube in AEM {#setting-up-youtube-in-aem}

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Deployment > Cloud Services]**.
1. 在“第 **[!UICONTROL 三方服务]** ”标题下，点按 **[!UICONTROL 立即配置]**。
1. 在“创 **建配置”** 对话框中，在相应的字段中输入标题（必填）和名称（可选）。
1. 点按&#x200B;**[!UICONTROL 创建]**。
1. In the **[!UICONTROL YouTube Account Settings]** dialog box, in the **[!UICONTROL Application Name]** field, enter the Google Project ID.

   您最初在之前配置Google Cloud设置时指定了项目ID。

   保持“ **[!UICONTROL YouTube帐户设置]** ”对话框打开； 你马上就会回来。

1. 使用纯文本编辑器，打开之前在“配置Google Cloud”设置中下载并保存的JSON文件。
1. 选择并复制整个JSON文本。
1. Return to the **[!UICONTROL YouTube Account Settings]** dialog box. 在 **[!UICONTROL JSON 配置]**&#x200B;字段中，粘贴 JSON 文本。
1. 点按 **[!UICONTROL 确定]**。

   您现在将在AEM中设置YouTube渠道。

1. 在&#x200B;**[!UICONTROL 可用渠道]**&#x200B;右侧，点按 **[!UICONTROL +]**（加号图标）。
1. In the **[!UICONTROL YouTube Channel Settings]** dialog box, in the **[!UICONTROL Title]** field, enter the name of the channel that you created in the task **C[!UICONTROL reating a YouTube channel ]**earlier.

   您可以根据需要选择添加描述。

1. 点按 **[!UICONTROL 确定]**。
1. 将显示YouTube/Google身份验证。 如果您尚未登录Google Cloud帐户，请跳过此步骤。

   * 输入与上述Google项目ID和JSON文本关联的Google用户名和密码。
   * 根据您的帐户拥有的渠道数，您会看到两个或更多项目。 选择渠道。 请勿选择电子邮件地址。
   * 在下一页，点按接 **[!UICONTROL 受]** ，以允许访问此渠道。

1. 点 **按[!UICONTROL允许**。

   您现在将设置用于发布的标记。

1. **设置要发布的标记** -在 **[!UICONTROL Cloud Services> YouTube页]** 面上，点 **[!UICONTROL 击铅笔图]** 标，以编辑要使用的标记列表。
1. 点按下拉列表图标（倒转插入符号）以显示AEM中可用标记的列表。
1. 点击一个或多个标记以添加它们。

   To delete a tag you have added, select the tag, and tap **[!UICONTROL X]**.

1. 添加完所需标记后，点按确 **[!UICONTROL 定]**。

   现在，您可以将视频发布到YouTube渠道。

### （可选）自动设置已上传视频的默认YouTube属性 {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

您可以在上传视频时自动设置YouTube属性。 要完成此操作，请在AEM中创建元数据处理用户档案。

要创建元数据处理配置文件，您首先需要从&#x200B;**[!UICONTROL 字段标签]**、**[!UICONTROL 映射到属性]**&#x200B;和&#x200B;**[!UICONTROL 选择]**&#x200B;字段中复制值，所有这些字段均位于视频的元数据架构中。然后，您可以通过向处理配置文件添加这些值来构建您的 YouTube 视频元数据处理配置文件。

**（可选）自动设置已上传视频的默认YouTube属性**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Metadata Schemas]**.
1. 点按 **[!UICONTROL 默认]**。 （请勿在“default”左侧的选择框中添加复选标记。）
1. On the **[!UICONTROL default]** page, check the box to the left of **[!UICONTROL video]**, then tap **[!UICONTROL Edit]**.
1. 在元数 **[!UICONTROL 据模式编辑]** 器页面上，点 **[!UICONTROL 按高级]** 选项卡。
1. Under the YouTube Publishing heading, tap **[!UICONTROL YouTube Category]**. (请勿点击YouTube类别下拉列表。)
1. 在页面右侧的设置选项卡 **[!UICONTROL 下]** ，执行以下操作：

   * 在“字 **[!UICONTROL 段标签]** ”文本字段中，选择并复制值。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

   * 在映射到 **[!UICONTROL 属性文本字段]** ，选择并复制值。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

   * 在“ **[!UICONTROL 选择]**”下，选择并复制您要使用的默认值（如“人物和博客”或“科学与技术”）。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

1. Under the YouTube Publishing heading, tap **[!UICONTROL YouTube Privacy]**. (请勿点击YouTube隐私下拉列表。)
1. 在页面右侧的设置选项卡 **[!UICONTROL 下]** ，执行以下操作：

   * 在“字 **[!UICONTROL 段标签]** ”文本字段中，选择并复制值。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

   * 在映射到 **[!UICONTROL 属性文本字段]** ，选择并复制值。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

   * 在“ **[!UICONTROL 选择]**”下，选择并复制要使用的默认值。 请注意，“选择”按两对进行分组。 对中的底部字段是要复制的默认值，如公共、未列出或私有。

      将复制的值粘贴到打开的文本编辑器中。 您以后在创建元数据处理用户档案时将需要此值。 使文本编辑器保持打开状态。

1. 在“元数据模式编辑器”页 **[!UICONTROL 面的右上角]** ，点按 **[!UICONTROL 取消]**。
1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Metadata Profiles]**.

1. 在[ **!UICONTROL元用户档案** ，在页面的右上角附近，点按 **[!UICONTROL创建**。 In the **[!UICONTROL Add Metadata Profile** dialog box, in the **[!UICONTROL Profile title]** text field, enter the name `YouTube Video`.
1. 在元数 **[!UICONTROL 据用户档案编辑]** 器页面上，点 **[!UICONTROL 按高级]** 选项卡。
1. 通过执行以下操作，将复制的YouTube发布值添加到用户档案:

   * 在页面的右侧，点按构建表 **[!UICONTROL 单选项卡]** 。
   * 将标记为Section **[!UICONTROL Header的组件]** 拖到左侧，并将其放置到表单区域中。
   * Tap **[!UICONTROL Field Label]** to select the component.
   * 在页面右侧的“设置”选 **[!UICONTROL 项卡]** 的“字段标 **[!UICONTROL 签”文本字]** 段中 `YouTube Publishing`，输入。
   * Tap the **[!UICONTROL Build Form]** tab, then drag the component labeled **[!UICONTROL Single Line Text]** and drop it below the **[!UICONTROL YouTube Publishing]** heading that you just created.
   * Tap **[!UICONTROL Field Label]** to select the component.
   * 在页面右侧的“设置”选 **[!UICONTROL 项]** 卡下，将您之前复制的 **[!UICONTROL YouTube Publishing]** (字段标签&#x200B;**[!UICONTROL 值和映射到属性]****** 值的映射)粘贴到表单中各自的字段中。 将“选 **[!UICONTROL 择]** ”值粘贴 **[!UICONTROL 到“默认值]** ”字段。

1. 通过执行以下操作，将复制的YouTube隐私值添加到用户档案:

   * 在页面的右侧，点按构建表 **[!UICONTROL 单选项卡]** 。
   * 将标记为Section **[!UICONTROL Header的组件]** 拖到左侧，并将其放置到表单区域中。
   * Tap **[!UICONTROL Field Label]** to select the component.
   * 在页面右侧的“设置”选项卡的“字段标签”文本字段中，输入 `YouTube Privacy`。
   * Tap the **[!UICONTROL Build Form]** tab, then drag the component labeled **[!UICONTROL Single Line Text]** and drop it below the **[!UICONTROL YouTube Privacy]** heading you just created.
   * Tap **[!UICONTROL Field Label]** to select the component.
   * 在页面右侧的“设置”选 **[!UICONTROL 项]** 卡下，将您之前复制的 **[!UICONTROL YouTube Publishing]** (字段标签&#x200B;**[!UICONTROL 值和映射到属性]****** 值的映射)粘贴到表单中各自的字段中。 将[! **UICONTROL Choices值粘贴** ，到“ **[!UICONTROL 默认值]** ”字段。

1. 在页面的右上角附近，点按&#x200B;**[!UICONTROL 保存]**。
1. 将YouTube发布元数据用户档案应用于要上传视频的文件夹。 您需要同时设置元数据用户档案和视频用户档案。

   请参阅 [元数据配置文件](metadata-profiles.md) 和视 [频配置文件](video-profiles.md)。

### 将视频发布到您的 YouTube 频道 {#publishing-videos-to-your-youtube-channel}

现在，您可以关联之前添加到视频资产的标记。 此过程可让AEM知道要发布到YouTube渠道的资产。

要从YouTube发布内容，AEM使用“ **[!UICONTROL 发布到YouTube]** ”工作流程，它允许您监视进度并视图任何故障信息。
请参阅[监视视频编码和 YouTube 发布进度](#monitoring-video-encoding-and-youtube-publishing-progress)。

**要将视频发布到您的YouTube渠道**:

1. 在AEM中，导航到要发布到YouTube渠道的视频资产。
1. 选择视频资产。

   无论您选择的视频资产（如原始源视频或其编码演绎版）如何，原始源视频始终会上传。

1. On the toolbar, tap **[!UICONTROL Properties]**.
1. 在“基 **[!UICONTROL 本]** ”选项卡的“元数据”标题下，点 **[!UICONTROL 按]** “标记 **[!UICONTROL ”字段右]** 侧的“浏览”。
1. 在“选 **[!UICONTROL 择标记]** ”页面上，导览至要使用的标记，然后选择一个或多个标记。
1. 在页面的右上角，点按确认 **[!UICONTROL 图标]** 。
1. In the upper-right corner of the video&#39;s properties page, tap **[!UICONTROL Save]**.
1. 在工具栏中，点按&#x200B;**[!UICONTROL 发布 > 发布]**。

   您可以选择验证已发布到YouTube渠道上的视频。

### （可选）验证已发布到 YouTube 上的视频{#optional-verifying-the-published-video-on-youtube}

您可以监视YouTube发布（或取消发布）的进度。

请参阅[监视视频编码和 YouTube 发布进度](#monitoring-video-encoding-and-youtube-publishing-progress)。

发布视频所需的时间可能会因诸多因素而有很大不同，这些因素包括主视频的格式、文件大小和上传流量。发布过程所需的时间少则几分钟，多则几小时，这些情况都有可能出现。另请注意，分辨率较高的格式渲染起来会慢很多。例如，分辨率分别为 720p 和 1080p 的视频在渲染时所需的时间会比 480p 的视频显著更长。

如果在八小时后，状态消息仍然显示&#x200B;**[!UICONTROL 已上传（正在处理，请稍候）]**，请尝试从我们的站点中删除视频，然后重新上传。

### 将 YouTube URL 关联到您的 Web 应用程序 {#linking-youtube-urls-to-your-web-application}

您可以在发布视频后获取Dynamic Media生成的YouTube URL字符串。 在复制该 YouTube URL 时，它会进入“剪贴板”，以便您能够视需要将其粘贴到网站或应用程序中的页面。

只有在将视频资产发布到 YouTube 后，才可复制其 YouTube URL。

**要将YouTube URL关联到您的Web应用程序**:

1. 导航到要复 *制其* URL的YouTube已发布视频资产，然后选择它。

   Remember that YouTube URLs are only available to copy *after* you have first *published* the video assets to YouTube.

1. On the toolbar, tap **[!UICONTROL Properties]**.
1. 点按&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡。
1. Under the **[!UICONTROL YouTube Publishing]** heading, in the **[!UICONTROL YouTube URL]** List, select and copy the URL text to your web browser to preview the asset or to add to your web content page.

### 取消发布视频以将其从 YouTube 中删除 {#unpublishing-videos-to-remove-them-from-youtube}

在AEM中取消发布视频资产时，该视频会从YouTube中删除。

>[!CAUTION]
>
>如果您直接从YouTube中删除视频，AEM不会察觉并继续表现出视频仍发布到YouTube的样子。 始终通过AEM从YouTube取消发布视频资产。

要从YouTube中删除内容，AEM使 **[!UICONTROL 用从YouTube中取消发布]** ，该工作流允许您监视进度并视图任何故障信息。
请参阅[监视视频编码和 YouTube 发布进度](#monitoring-video-encoding-and-youtube-publishing-progress)。

**要取消发布视频以将其从YouTube中删除，请执行以下操作**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets]**.
1. 导航到要从YouTube渠道取消发布的视频资产。
1. 在资产选择模式下，选择一个或多个已发布的视频资产。
1. 在工具栏中，点按取 **[!UICONTROL 消发布>取消发布]**。

## Monitoring video encoding and YouTube publishing progress {#monitoring-video-encoding-and-youtube-publishing-progress}

将新视频上传到应用了视频编码的文件夹或将视频发布到youtube时，您可以通过多种方式监控视频编码/youtube发布的进展（或失败）。 实际的YouTube发布进度仅通过日志可用，但是失败还是成功会通过以下过程描述的其他方式列出。 此外，当YouTube发布工作流或视频编码完成或中止时，您可能会收到电子邮件通知。

### 监视进度 {#monitoring-progress}

要监视进度（包括编码失败/YouTube发布），请执行以下操作：

1. 视图资产文件夹中的视频编码进度：

   * 在卡 **[!UICONTROL 片视图]**，视频编码进度会按百分比显示在资产上。 如果出现错误，此信息也会显示在资产上。

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * In **[!UICONTROL List View]**, video encoding progress displays in the **[!UICONTROL Processing Status]** column. 如果出现错误，则同一列中将显示此消息。

      ![chlimage_1-430](assets/chlimage_1-430.png)

      默认情况下，此列不显示。To enable the column, select **[!UICONTROL View Settings]** from the **[!UICONTROL Views]** drop-down menu, and add the **[!UICONTROL Processing Status]** column and tap **[!UICONTROL Update]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. 视图资产详细信息中的进度。 点按资产时，请打开下拉菜单并选择时 **[!UICONTROL 间轴]**。 要将其缩小为工作流活动（如编码或YouTube发布），请选择 **[!UICONTROL 工作流]**。

   ![chlimage_1-432](assets/chlimage_1-432.png)

   任何工作流信息（如编码）都会显示在时间轴中。 对于YouTube发布，工 **[!UICONTROL 作流]** 时间轴还包括YouTube渠道和YouTube视频URL的名称。 此外，您还可以在工作流时间轴中看到任何 **[!UICONTROL 失败]** 通知。

   >[!NOTE]
   >
   >It may take a long time for failure/error messages to finally be recorded due to multiple workflow configurations on **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, and **[!UICONTROL timeout]** from [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), for example:
   >
   >* Apache Sling作业队列配置
   >* AdobeGranite工作流外部进程作业处理程序
   >* Granite工作流超时队列

   > 
   >在这些配置中 **[!UICONTROL ，您可以调]**&#x200B;整重试 **[!UICONTROL 、]**&#x200B;重试延迟 **[!UICONTROL ,]** 以及超时。

1. For workflows in progress, see **Workflow Instances** available from **[!UICONTROL Tools > Workflow > Instances]**.

   >[!NOTE]
   >
   >您可能需要管理权限才能访问“工 **[!UICONTROL 具]** ”菜单。

   ![chlimage_1-433](assets/chlimage_1-433.png)

   选择实例，然后点按打 **[!UICONTROL 开历史记录]**。

   ![chlimage_1-434](assets/chlimage_1-434.png)

   从“工 **[!UICONTROL 作流实例]** ”区域，您还可以暂停、终止或重命名工作流。 有关更 [多信息](/help/sites-administering/workflows-administering.md) ，请参阅管理工作流。

1. For failed jobs, see **Workflow Failures** available from **[!UICONTROL Tools > Workflow > Failures]**. **[!UICONTROL 工作流失败]**&#x200B;列出所有失败的工作流活动。

   >[!NOTE]
   >
   >您可能需要管理权限才能访问“ **[!UICONTROL 工具]** ”菜单。

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >It may take a long time for the error message to finally be recorded due to multiple workflow configurations on **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, and **[!UICONTROL timeout]** from [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), for example:
   >
   >* Apache Sling作业队列配置
   >* AdobeGranite工作流外部进程作业处理程序
   >* Granite工作流超时队列

   >
   >在这些配置中 **[!UICONTROL ，您可以调]**&#x200B;整重试 **[!UICONTROL 、]**&#x200B;重试延迟 **[!UICONTROL ,]** 以及超时。

1. For completed workflows, see **[!UICONTROL Workflow Archive]** available from **[!UICONTROL Tools > Workflow > Archive]**. **[!UICONTROL 工作流存档]**&#x200B;列出了所有已完成的工作流活动。

   您可能需要管理权限才能访问“工 **[!UICONTROL 具]** ”菜单。

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. 您可能会收到有关中止或失败的工作流作业的电子邮件通知。 管理员可以配置这些电子邮件通知。
See [Configuring email notifications](#configuring-e-mail-notifications).

#### 配置电子邮件通知 {#configuring-e-mail-notifications}

您可能需要管理权限才能访问“ **[!UICONTROL 工具]** ”菜单。

如何配置通知取决于您是希望通知用于编码作业还是YouTube发布作业：

* 对于编码作业，您可以通过搜索Day CQ Workflow Email Notification Service访问所有AEM工 **[!UICONTROL 作流电子邮件通知的配置页]** ，该页位于“工具”>“操 **[!UICONTROL 作”>“Web控制台”]**。 请参阅 [在AEM中配置电子邮件通知](/help/sites-administering/notification.md)。 您可以相应地选中或清除“中止时 **[!UICONTROL 通知”或]** “ **[!UICONTROL 完成时通知]** ”复选框。

* 对于YouTube发布作业，请执行以下操作：

1. 在AEM中，选择“工 **[!UICONTROL 具”>“工作流”>“模型]**”。
1. 选择发 **[!UICONTROL 布到YouTube工作流]** ，然后点按 **[!UICONTROL 编辑]**。
1. 右键单击“YouTube **[!UICONTROL 上传”工作流]** ，然后点按 **[!UICONTROL 编辑]**。
1. 点按参 **数&#x200B;**选项卡。
1. 您可以选中或清除以下复选框：

   * **[!UICONTROL 发布开始]**
   * **[!UICONTROL 发布失败]**
   * **[!UICONTROL 发布完成]**，包括有关渠道和URL的信息

   清除复选框意味着您不会从YouTube发布工作流接收指定的电子邮件通知。

   >[!NOTE]
   >
   >这些电子邮件特定于YouTube，是通用工作流电子邮件通知的补充。 因此，您可能会收到两组电子邮件通知- Day CQ Workflow Email Notification Service中提供的 **通用通知** ，另一组特定于YouTube，具体取决于您的配置设置。

## 查看视频报表 {#viewing-video-reports}

运行Dynamic Media —— 混合模式时，视频报告可用； 运行Dynamic Media -Scene7模式时，报告不可用。

视频报表显示指定时间段内的多个聚合量度，帮助您监控*已发布*单个和聚合视频是否按预期效果呈现。 以下顶级指标数据是整个网站中所有已发布视频的汇总数据：

* 视频开始
* 完成率
* 视频花费的平均时间
* 视频花费的总时间
* 每次访问的视频数

报表中还会列出包含所有&#x200B;*已发布*&#x200B;视频的表格，以便您能够根据视频开始的总次数，跟踪您网站上最常观看的视频。

在您点按列表中的视频名称时，系统会以折线图向您显示该视频的受众保留（流失）报表。该图表显示了视频播放期间任意给定时刻的查看次数。当您播放视频时，垂直条与播放器中的时间指示器同步进行跟踪。折线图数据中的下降趋势表示受众因不感兴趣而停止观看。

如果视频是在 Adobe Experience Manager Dynamic Media 外部编码的，就不会提供受众保留（流失）图表和表中的播放比例数据。

另请参 [阅配置Dynamic MediaCloud Services](/help/assets/config-dynamic.md)。

>[!NOTE]
>
>只有在使用 Dynamic Media 自带的视频播放器及关联的视频播放器预设时，才可跟踪并报告数据。因此，对于通过其他视频播放器播放的视频，您无法进行跟踪和报告。

默认情况下，在您首次进入视频报表时，报表会显示从当月的第一个开始到当月的当日结束的视频数据。 但是，您可以通过指定您自己的日期范围来覆盖默认日期范围。 下次输入视频报表时，将使用您指定的日期范围。

For video reports to work correctly, a Report Suite ID is automatically created when Dynamic Media Cloud Services is configured. At the same time, the Report Suite ID is pushed to the Publish server so that it is available for the Copy URL feature when you preview assets. However, this requires that the Publish server be already set up. If the Publish server is not set up, you can still publish to see the video report, however, you will need to return to the Dynamic Media Cloud Configuration and tap **OK**.

**要视图视频报表**:

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools > Assets > Video Reports]**.
1. 在“视频报表”页面中，执行以下任一操作：

   * 在右上角附近，点按&#x200B;**[!UICONTROL 刷新视频报表]**图标。


      如果报表的结束日期是当日，您只需使用“刷新”。这可确保您查看自上次运行报告以来发生的视频跟踪。

   * Near the upper-right corner, tap the **[!UICONTROL Date Picker]** icon.

      指定您要查看的视频数据的开始日期和结束日期范围，然后点按&#x200B;**[!UICONTROL 运行报表]**。
   The **[!UICONTROL Top Metrics]** group box identifies various aggregate measurements for all *published* videos across your site.

1. 在列出顶级已发布视频的表中，点按视频名称以播放视频，还可以查看该视频的受众保留（流失）报表。

### 查看基于使用 Scene7 HMTL5 查看器 SDK 创建的视频查看器的视频报表 {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

如果您使用的是Dynamic Media提供的现成视频查看器，或者您基于现成视频查看器创建了自定义查看器预设，则无需执行任何其他步骤即可视图视频报告。 但是，如果您基于Scene7HTML5查看器SDK创建了自己的视频查看器，请使用以下步骤确保视频查看器将跟踪事件发送到Dynamic Media视频报表。

使用 Scene7 查看器参考和 Scene7 HTML5 查看器 SDK 创建您自己的视频查看器。

请参阅《[Scene7 查看器参考指南](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html)》。

从 Adobe Developer Connection 下载 Scene7 HTML 查看器 SDK。

请参阅 [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html)。

要查看基于使用 Scene7 HMTL5 查看器 SDK 创建的视频查看器的视频报表，请执行以下操作：

1. 导航到任意已发布的视频资产。
1. 在资产页面的左上角附近，从下拉列表中选择&#x200B;**[!UICONTROL 查看器]**。
1. 选择任意视频查看器预设，并复制嵌入代码。
1. 在嵌入代码中，找到包含以下内容的代码行：

   `videoViewer.setParam("config2", "<value>");`

   The `config2` parameter enables tracking in HTML5 Viewers. 它还是一个特定于公司的预设，其中包含视频报告的配置信息以及特定于客户的Adobe Analytics配置。

   config2 参数的正确值可在&#x200B;**[!UICONTROL 嵌入代码]**&#x200B;和复制 **[!UICONTROL URL]** 函数中找到。在复制 **[!UICONTROL URL]** 命令的 URL 中，要查找的参数为 `&config2=<value>`。该值几乎总是 `companypreset`，但在某些情况下，也可以是 `companypreset-1`、`companypreset-2` 等。

1. 在您的自定义视频查看器代码中，通过执行以下操作，将 AppMeasurementBridge.jsp 添加到查看器页面：

   * First, determine if you need the `&preset` parameter.

      If the `config2` parameter is `companypreset`, you do *not* need `&preset=parameter`.

      If `config2` is anything else, set the preset parameter the same as the `config2` parameter. For example, if `config2=companypreset-2`, add `&param2=companypreset-2` to the AppMeasurmentBridge.jsp URL.

   * 然后，添加AppMeasurementBridge.jsp脚本：

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. 通过执行以下操作，创建 TrackingManager 组件：

   * After calling `s7sdk.Utils.init();` create a TrackingManager instance to track events by adding the following:

      `var trackingManager = new s7sdk.TrackingManager();`

   * 通过执行以下操作，将组件连接到TrackingManager:

      在事件 `s7sdk.Event.SDK_READY` 处理函数中，将要跟踪的组件附加到TrackingManager。

      例如，如果组件为， `videoPlayer`则添加

      `trackingManager.attach(videoPlayer);`

      将组件附加到trackingManager。 要在一个页面上跟踪多个查看器，可使用多个跟踪管理器组件。

   * 通过添加以下内容创建AppMeasurementBridge对象：

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * 通过添加以下内容添加跟踪功能：

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   appMeasurementBridge对象具有内置的跟踪功能。 但是，您可以提供自己的功能来支持多个跟踪系统或其他功能。

   For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).

## 为视频添加字幕 {#adding-captions-to-video}

您可以通过向单个视频或自适应视频集添加字幕，将视频的触及范围扩展到全球市场。 通过添加题注，您无需对音频进行混音，或使用母语者为每种不同的语言重新录制音频。 视频以录制的语言播放。 显示外语字幕，使不同语言的用户仍可了解音频部分。

字幕功能还允许对耳聋或听力欠佳的用户使用隐藏式字幕，从而提高辅助功能。

>[!NOTE]
>
>您使用的视频播放器必须支持字幕的显示。

Dynamic Media能够将题注文件转换为JSON（JavaScript对象表示法）格式。 此转换意味着您可以将JSON文本作为视频的隐藏但完整的记录嵌入到网页中。 然后，搜索引擎可以爬网和索引内容，使视频更容易被发现，并为客户提供有关视频内容的更多详细信息。

有 [关在URL中使用JSON函数](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html) ，请参 *阅“Scene7图像服务API帮助”中的* “服务静态（非图像）内容”。

**要向视频添加字幕或字幕**:

1. 使用第三方应用程序或服务创建您的视频字幕／子标题文件。

   确保您创建的文件符合WebVTT（Web视频文本轨道）标准。 字幕文件扩展名为。vtt。 您可以了解有关WebVTT字幕标准的更多信息。

   请参 [阅WebVTT: Web视频文本跟踪格式](https://dev.w3.org/html5/webvtt/)。

   您可以使用免费和高级工具及服务在Dynamic Media外创作字幕／子标题文件。 例如，要创建不带样式的简单视频题注文件，您可以使用以下免费的在线题注创作和编辑工具：

   [WebVTT字幕制作器](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   为获得最佳效果，请使用Internet Explorer 9或更高版本、Google Chrome或Safari中的工具。

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then tap **[!UICONTROL Load]**. 请参阅[获取资产的 URL](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)，以获取视频文件的 URL，然后您可以将该 URL 粘贴到&#x200B;**[!UICONTROL 输入视频文件的 URL 字段]**。随后，Internet Explorer、Chrome 或 Safari 可以本机播放视频。

   现在，请按照站点屏幕上的说明创作和保存WebVTT文件。 完成后，复制题注文件内容并将其粘贴到纯文本编辑器中，并以。vtt文件扩展名保存它。

   >[!NOTE]
   >
   >要全局支持多语言视频字幕，请注意，WebVTT标准要求您为要支持的每种语言创建单独的。vtt文件和调用。

   通常，您希望将字幕VTT文件命名为与视频文件同名，并附加语言区域设置，如-EN、-FR或-DE等。 通过这样做，它可以帮助您使用现有Web内容管理系统自动生成视频URL。

1. 在AEM中，将您的WebVTT题注文件上传到DAM。
1. 导航到要 *与上* 传的题注文件关联的已发布视频资产。

   请注意，只有在首次&#x200B;*发布*&#x200B;资产&#x200B;*后*，才可复制 URL。

   请参阅[发布资产](publishing-dynamicmedia-assets.md)。

1. 执行下列操作之一：

   * 要获得弹出式视频查看器体验，请点 **[!UICONTROL 击URL]**。 在“URL”对话框中，选择URL并将其复制到剪贴板，然后将URL传到简单的文本编辑器中。 在复制的视频URL后面附加以下语法：

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      请注意 `,1` 题注路径末尾的。 紧随路径中。vtt文件扩展名的后面，您可以选择分别设置为或启用（打开）或禁用（关闭）视频播放器栏上的隐藏 `,1` 字幕 `,0`按钮。

   * 要获得嵌入式视频查看器体验，请点 **[!UICONTROL 按嵌入代码]**。 在“嵌入代码”对话框中，选择嵌入代码并将其复制到剪贴板，然后将该代码粘贴到简单的文本编辑器中。 在复制的嵌入代码后附加以下语法：

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      请注意 `,1` 题注路径末尾的。 紧随路径中。vtt文件扩展名的后面，您可以选择分别设置为或启用（打开）或禁用（关闭）视频播放器栏上的隐藏 `,1` 字幕 `,0`按钮。

## 向视频添加章节标记 {#adding-chapter-markers-to-video}

您可以通过向单个视频或自适应视频集添加章节标记，使长形视频更易于观看和导航。 当用户播放视频时，他们可以点击视频时间线上的章节标记（也称为视频浏览条），轻松导航到自己感兴趣的点，或立即跳到新内容、演示、教程等。

>[!NOTE]
>
>使用的视频播放器必须支持使用章节标记。 Dynamic Media视频播放器确实支持章节标记，但使用第三方视频播放器可能不支持。

如果需要，您可以使用章节而不是使用视频查看器预设创建自定义视频查看器并为其添加品牌。 有关创建具有章节导航的自己HTML5查看器的说明，请参阅《Adobe Scene7查看器SDK for HTML5指南》中的类和下方的标题“使用修饰符自定义行为 `s7sdk.video.VideoPlayer` ” `s7sdk.video.VideoScrubber`。 可从Adobe Scene7下载Adobe Developer Connection查看器 [SDK](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html)。

为视频创建章节列表的方法与创建字幕的方法非常相似。 即，创建一个WebVTT文件。 但是，请注意，此文件必须与您也可能使用的任何WebVTT题注文件分开； 不能将字幕和章节合并到一个WebVTT文件中。

您可以将以下示例用作创建具有章节导航的WebVTT文件所使用格式的示例：

### 带有视频章节导航的WebVTT文件 {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

在上例中，提示 `Chapter 1` 标识符是可选的。 提示时间以 `00:00:000 --> 01:04:364` 格式指定章节的开始时间和结束 `00:00:000` 时间。 最后三位数字是毫秒，如果需要，可 `000`以保留为。 章标题 `The bicycle store behind it all` 是本章内容的实际描述。 当用户将鼠标指针悬停在视频时间轴中的可视提示点上时，提示标识符、开始提示时间和章节标题都显示在视频播放器的弹出窗口中。

由于您使用的是HTML5视频查看器，请确保您创建的章节文件符合WebVTT（Web视频文本轨道）标准。 章节文件扩展名为。vtt。 您可以了解有关WebVTT字幕标准的更多信息。

请参 [阅WebVTT: Web视频文本轨道格式](https://dev.w3.org/html5/webvtt/)

**要向视频添加章节标记，请执行以下操作：**

1. 使用AEM外的简单文本编辑器创建视频章节文件。

   要全局支持非英语语言的视频章节，请注意，WebVTT标准要求您为要支持的每种语言分别创建单独的。vtt文件和调用。

1. 以UTF8 `.vtt` 编码保存文件，以避免章节标题文本中的字符再现问题。

   通常，您希望将章节VTT文件命名为与视频文件同名，并在其后添加章节。 通过这样做，它可以帮助您使用现有Web内容管理系统自动生成视频URL。
1. 在AEM中，上传您的WebVTT章节文件。

   请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

1. 执行下列操作之一：

   <table> 
     <tbody> 
      <tr> 
       <td>要获得弹出式视频查看器体验</td> 
       <td> 
       <ol> 
       <li>导航到要 <i>与 </i>您上传的章节文件关联的已发布视频资产。 请注意，只有在首次<i>发布</i>资产<i>后</i>，才可复制 URL。请参阅<a href="/help/assets/publishing-dynamicmedia-assets.md">发布资产</a>。</li> 
       <li>从下拉菜单中，点按查 <strong>看器</strong>。</li> 
       <li>在左边栏中，点按视频查看器预设名称。 视频的预览将在单独的页面中打开。</li> 
       <li>In the left rail, at the bottom, tap <strong>URL</strong>.</li> 
       <li>在“URL”对话框中，选择URL并将其复制到剪贴板，然后将URL传到简单的文本编辑器中。</li> 
       <li>在视频的复制URL后面附加以下语法，将其与复制的URL关联到您的章节文件：<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>对于嵌入式视频查看器体验<br /> </td> 
       <td> 
       <ol> 
       <li>导航到要 <i>与 </i>您上传的章节文件关联的已发布视频资产。 请注意，只有在首次<i>发布</i>资产<i>后</i>，才可复制 URL。请参阅<a href="/help/assets/publishing-dynamicmedia-assets.md">发布资产</a>。</li> 
       <li>从下拉菜单中，点按查 <strong>看器</strong>。</li> 
       <li>在左边栏中，点按视频查看器预设名称。 视频的预览将在单独的页面中打开。</li> 
       <li>In the left rail, at the bottom, tap <strong>Embed</strong>.</li> 
       <li>在“嵌入代码”对话框中，选择整个代码并将其复制到剪贴板，然后将其粘贴到简单的文本编辑器中。</li> 
       <li>在视频的嵌入代码后面附加以下语法，将其与复制的URL关联到您的章节文件：<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## 关于视频缩略图 {#about-video-thumbnails}

您可以从Dynamic Media自动生成的十张缩略图中选择一张，以将其添加到视频中。 在AEM Sites、AEM Mobile或AEM Screens的创作环境中，当视频资产与Dynamic Media组件一起使用时，视频播放器会显示您选择的缩略图。 缩略图用作最能代表整个视频内容的静态图片，并进一步鼓励用户点击“播放”按钮。

根据视频的总时间，Dynamic Media将以1%、11%、21%、31%、41%、51%、61%、71%、81%和91%的比例捕获十张（默认）缩略图图像。 十个缩览图将保留，这意味着如果您稍后决定选择其他缩略图，则无需重新生成该系列。 您预览十个缩略图图像，然后选择要用于视频的图像。 如果要更改为默认值，则可以使用CRXDE Lite配置生成缩略图的时间间隔。 例如，如果您只想从视频中生成一系列四张均匀间隔的缩略图，可以将间隔时间配置为24%、49%、74%和99%。

理想情况下，在上传视频后但在网站上发布视频之前，您可以随时添加视频缩略图。

如果您愿意，您可以选择上传自定义缩略图来代表您的视频，而不是使用Dynamic Media生成的缩略图。 例如，您可以创建自定义缩略图图像，该图像具有视频的标题、引人注目的开始图像或从视频捕获的非常特定的图像。 您上传的自定义视频缩略图图像的最大分辨率应为1280 x 720像素（最小宽度为640像素）且不应大于2MB。

>[!NOTE]
>
>自定义视频缩略图仅在运行Dynamic Media —— 混合模式时可用。

### 添加视频缩略图 {#adding-a-video-thumbnail}

1. 导航到要添加视频缩略图的已上传视频资产。
1. In asset selection mode either from the **[!UICONTROL List View]** or the **[!UICONTROL Card View]**, tap the video asset.
1. 在工具栏中，点按 **[!UICONTROL 视图属性]** 图标（其中带有“i”的圆圈）。
1. 在视频的“属性” **[!UICONTROL 页面]** ，点按 **[!UICONTROL 更改缩略图]**。
1. 在“更 **[!UICONTROL 改缩略图]** ”页面的工具栏中，点按 **[!UICONTROL 选择框架]**。

   Dynamic Media根据您自定义的默认时间间隔或时间间隔，从您的视频生成系列缩略图图像。

1. 预览生成的缩略图图像，然后选择要添加到视频的缩略图。
1. 点按 **[!UICONTROL 保存更改]**。

   视频的缩略图图像将更新为使用您选择的缩略图。 如果您稍后决定更改缩略图图像，则可返回“更改 **[!UICONTROL 缩略图]** ”页面并选择新缩略图。

   如果您配置了新的默认时间间隔，或者上传了新视频以替换现有视频，则需要Dynamic Media重新生成缩略图。

   请参 [阅配置生成视频缩略图的默认时间间隔](#configuring-the-default-time-interval-that-video-thumbnails-are-generated)。

#### 配置生成视频缩略图的默认时间间隔 {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

当您配置并保存新的默认时间间隔时，所做的更改将仅自动应用于您将来上传的视频。 它不会自动将新默认值应用于您之前上传的视频。 对于现有视频，必须重新生成缩略图。

请参 [阅添加视频缩略图](#adding-a-video-thumbnail)。

要配置生成视频缩略图的默认时间间隔，

1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。

1. 在CRXDE Lite页面左侧的目录面板中，导航到 `o etc/dam/imageserver/configuration/jcr:content/settings.`

   如果目录面板不可见，则可能需要点按“主页”选项卡左侧的>>图标。

1. 在右下方的面板中，在“属 **[!UICONTROL 性]** ”选项卡中，多次点 `thumbnailtime`击。
1. 在“编辑缩览图时间”对话框中，使用文本字段以百分比形式输入间隔值。

   * 点按加号(+)图标以添加一个或多个间隔值字段。 您可能需要滚动到对话框底部才能看到该图标。
   * 点按间隔值字段右侧的减号(-)图标，将其从列表中删除。
   * 点按向上箭头图标和向下箭头图标以重新排序间隔值。

1. 点按 **[!UICONTROL 确]** 定以返回“属 **[!UICONTROL 性]** ”选项卡。
1. 在CRXDE Lite页面的左上角附近，点 **[!UICONTROL 按全部保]**&#x200B;存，然后点 **[!UICONTROL 按左上角的]** “返回主页”图标以返回AEM。

   请参 [阅添加视频缩略图。](#adding-a-video-thumbnail)

### 添加自定义视频缩略图 {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>此功能仅在运行Dynamic Media —— 混合模式时可用。

1. 导航到要添加视频缩略图的已上传视频资产。
1. In asset selection mode either from the **[!UICONTROL List View]** or the **[!UICONTROL Card View]**, tap the video asset.
1. 在工具栏中，点按 **[!UICONTROL 视图属性]** 图标（其中带有“i”的圆圈）。
1. 在视频的“属性” **[!UICONTROL 页面]** ，点按 **[!UICONTROL 更改缩略图]**。
1. 在“更 **[!UICONTROL 改缩略图]** ”页面的工具栏中，点按上 **[!UICONTROL 传新缩略图]**。
1. 导航到要使用的缩略图图像，选择它，然后点按打 **[!UICONTROL 开]** ，开始将图像上传到AEM
1. 成功上传图像后，在更改缩略图 **[!UICONTROL 页面中]** ，点按 **[!UICONTROL 保存更改]**。

   自定义缩略图会添加到您的视频中。

