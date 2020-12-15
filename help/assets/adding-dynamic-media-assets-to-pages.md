---
title: 将 Dynamic Media 资产添加到页面
seo-title: 将 Dynamic Media 资产添加到页面
description: 如何将Dynamic Media组件添加到AEM中的页面
seo-description: 如何将Dynamic Media组件添加到AEM中的页面
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 34%

---


# 将 Dynamic Media 资产添加到页面 {#adding-dynamic-media-assets-to-pages}

要向您在网站上使用的资产添加Dynamic Media功能，您可以直接在页面上添加&#x200B;**Dynamic Media**&#x200B;或&#x200B;**交互式媒体**&#x200B;组件。 要执行此操作，请进入布局模式并启用Dynamic Media组件。 然后，您可以将这些组件添加到页面，并将资产添加到该组件。 Dynamic Media 组件和交互式媒体组件是智能组件，它们知道您添加的是图像还是视频，并能据此相应地更改提供的选项。

如果您使用AEM作为WCM，则可以直接将Dynamic Media资产添加到页面。 如果您为 WCM 使用第三方，请[链接](linking-urls-to-yourwebapplication.md)或[嵌入](embed-code.md)资产。有关响应式第三方网站，请参阅[将优化的图像交付到响应式网站](responsive-site.md)。

>[!NOTE]
>
>您必须先发布资产，然后才能将其添加到AEM中的页面。 请参阅[发布Dynamic Media资产](publishing-dynamicmedia-assets.md)。

## 将Dynamic Media组件添加到页面{#adding-a-dynamic-media-component-to-a-page}

向页面添加Dynamic Media组件与向任何页面添加组件相同。 以下各节详细介绍了Dynamic Media各组成部分。

>[!NOTE]
>
>如果网页上有一个具有只读权限的用户访问的Dynamic Media组件，则分页符和组件无法正确呈现。 其原因是，重建页面是为了确保组件的属性良好，并且任何引用的资产和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
>  
>要避免此问题，请确保AEM Sites用户具有访问资产的必要权限。

1. 在 AEM 中，打开您要添加 Dynamic Media 组件的页面。
1. 在页面左侧的面板中（可能需要切换侧面板的显示），单击&#x200B;**[!UICONTROL 组件]**&#x200B;图标。
1. 在&#x200B;**[!UICONTROL 组件]**&#x200B;标题下，在下拉列表下，选择&#x200B;**[!UICONTROL Dynamic Media]**。 如果没有可用的列表Dynamic Media组件，您可能需要启用要使用的Dynamic Media组件。 请参阅[启用Dynamic Media组件](#enabling-dynamic-media-components)。

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 将要使用的Dynamic Media组件拖动到所需位置的页面上。
1. 将鼠标指针直接悬停在组件上。 当组件被蓝色框包围时，点按一次以显示组件的工具栏。 点按&#x200B;**[!UICONTROL 配置]**（扳手）图标。
1. [根据需](#dynamic-media-components) 要编辑组件，然后单击复选标记以保存更改。

### 启用Dynamic Media组件{#enabling-dynamic-media-components}

如果没有可添加到页面的Dynamic Media组件，则可能意味着您需要首先启用要使用的组件。

1. 在 AEM 中，打开您要添加 Dynamic Media 组件的页面。
1. 在工具栏左侧，点按页面顶部附近的页面信息图标，然后点按下拉列表中的&#x200B;**[!UICONTROL 编辑模板]**。

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. 在工具栏右侧页面顶部附近的下拉列表中，点按&#x200B;**[!UICONTROL 结构]**。

   ![策略](/help/assets/assets-dm/structure-mode.png)

1. 在页面底部附近，点按&#x200B;**[!UICONTROL 布局容器]**&#x200B;以打开其工具栏，然后点按策略图标。
1. 在&#x200B;**[!UICONTROL 布局容器]**&#x200B;页面的&#x200B;**[!UICONTROL 属性]**&#x200B;标题下，确保选中了&#x200B;**[!UICONTROL 允许的组件]**&#x200B;选项卡。

   ![允许的组件](/help/assets/assets-dm/allowed-components.png)

1. 滚动直到您看到&#x200B;**[!UICONTROL Dynamic Media]**。
1. 点按&#x200B;**[!UICONTROL Dynamic Media]**&#x200B;左侧的>图标以展开列表，选择要启用的Dynamic Media组件。

   ![Dynamic Media部件列表](/help/assets/assets-dm/dm-components-select.png)

1. 在&#x200B;**[!UICONTROL 布局容器]**&#x200B;页面的右上角附近，点按完成（复选标记）图标。

1. 在工具栏右侧页面顶部附近的下拉列表中，点按&#x200B;**[!UICONTROL 初始内容]**，然后按[将Dynamic Media组件按常规方式添加到页面](#adding-a-dynamic-media-component-to-a-page)。

## 将Dynamic Media组件定位{#localizing-dynamic-media-components}

您可以通过以下两种方式之一本地化Dynamic Media组件：

* 在“站点”的网页中，打开“属 **[!UICONTROL 性]** ”，然后选择“ **[!UICONTROL 高级]** ”选项卡。 选择所需的本地化语言。

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 从站点选择器中，选择所需的页面或页面组。 点按&#x200B;**[!UICONTROL 属性]**&#x200B;并选择&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡。 选择所需的本地化语言。

   >[!NOTE]
   >
   >请注意，**[!UICONTROL 语言]**&#x200B;菜单中并非所有可用语言当前都分配了令牌。

## Dynamic Media组件{#dynamic-media-components}

Dynamic Media和交互式媒体位于[!UICONTROL 组件]中的[!UICONTROL Dynamic Media]选项卡下。 对于任何交互式资产（例如交互式视频、交互式图像或传送集），请使用[!UICONTROL 交互式媒体]组件。对于所有其他 Dynamic Media 资产，请使用 Dynamic Media 组件。

>[!NOTE]
>
>这些组件默认不可用，在使用之前需要通过模板编辑器使用。 [在模板编辑](/help/sites-authoring/templates.md#editing-templates-template-authors) 器中使组件可用后，您可以像添加任何其他AEM组件一样将组件添加到页面。

![chlimage_1-539](assets/chlimage_1-539.png)

### Dynamic Media 组件 {#dynamic-media-component}

Dynamic Media组件是智能的——根据您添加的是图像还是视频，您有各种选项。 该组件支持图像预设、基于图像的查看器（例如图像集、旋转集、混合媒体集）和视频。此外，查看器具有响应性。 也就是说，屏幕的大小会根据屏幕大小自动更改。 所有查看器都是 HTML5 查看器。

>[!NOTE]
>
>如果具有只读权限的用户访问的网页上存在Dynamic Media组件、交互式媒体组件或两者，则分页符和组件将无法正确呈现。 其原因是，重建页面是为了确保组件的属性良好，并且任何引用的资产和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
>  
>要避免此问题，请确保AEM Sites用户具有访问资产的必要权限。

>[!NOTE]
>
>添加 Dynamic Media 组件时，如果 **[!UICONTROL Dynamic Media 设置]**&#x200B;为空或无法正常添加资产，请检查以下各项：
>
>* 您已经[启用了 Dynamic Media](config-dynamic.md)。默认情况下，Dynamic Media 处于禁用状态。
>* 图像具有金字塔 TIFF 文件。在启用 Dynamic Media 之前导入的图像没有金字塔 TIFF 文件。

>



#### 处理图像时  {#when-working-with-images}

Dynamic Media 组件允许您添加动态图像，包括图像集、旋转集和混合媒体集。您可以缩放图像，并在适当的情况下在旋转集内旋转图像，或从其他类型的集合中选择图像。

您还可以直接在组件中配置查看器预设、图像预设或图像格式。要使图像成为响应式图像，您可以设置断点，或应用响应式图像预设。

必须单击组件中的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标，然后单击&#x200B;**[!UICONTROL Dynamic Media设置]**，以编辑以下Dynamic Media设置。

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>默认情况下，Dynamic media图像组件是自适应的。 如果要使其具有固定大小，请在&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡的组件中，使用&#x200B;**[!UICONTROL 宽度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;设置进行设置。

* **[!UICONTROL 查看]**
器预设从下拉菜单中选择现有的查看器预设。如果未显示您要查找的查看器预设，则可能需要将其显示出来。请参阅管理查看器预设。如果您正在使用图像预设，则无法选择查看器预设，反之亦然。如果您查看的是图像集、旋转集或混合媒体集，这是唯一可用的选项。显示的查看器预设也是智能的 - 仅显示相关的查看器预设。

* **[!UICONTROL 查看]**
器修饰符查看器修饰符采用名称=值对和分隔符的形式，允许您根据查看器参考指南中的概述更改查看器。查看器修饰符的示例为posterimage=img.jpg&amp;caption=text.vtt,1，它为视频缩略图设置不同的图像并将隐藏字幕／子标题文件与视频相关联。

* **[!UICONTROL 图]**
像预设从下拉菜单中选择现有的图像预设。如果未显示您要查找的图像预设，则可能需要将其显示出来。请参阅管理图像预设。如果您正在使用图像预设，则无法选择查看器预设，反之亦然。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 图像修]**
饰符通过提供其他图像命令，可以应用图像效果。这些内容在图像预设和图像服务命令参考中进行了介绍。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 断]**
点如果您在响应式站点上使用此资产，则需要添加图像断点。图像断点之间需要使用逗号 (,) 进行分隔。当图像预设中未定义高度或宽度时，可以使用此选项。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。单击组件中的**[!UICONTROL 编辑]**&#x200B;可编辑以下高级设置。

* **[!UICONTROL 标]**
题更改图像的标题。

* **[!UICONTROL 替]**
代文本为关闭了图形的用户添加图像标题。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL URL，打开]**
位置您可以设置资产以打开链接。设置 URL，并在打开方式中指示是要在同一窗口中还是在新窗口中打开该 URL。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 宽]** 度高 ****
度如果希望图像具有固定大小，请输入以像素为单位的值。将这两个值留空会使资产成为自适应资产。

#### 处理视频时 {#when-working-with-video}

使用Dynamic Media组件将动态视频添加到网页。 编辑该组件时，您可以选择使用预定义的视频查看器预设，以在页面上播放视频。

![chlimage_1-541](assets/chlimage_1-540.png)

必须通过单击组件中的&#x200B;**[!UICONTROL 编辑]**&#x200B;来编辑以下Dynamic Media设置。

>[!NOTE]
>
>默认情况下，Dynamic Media 视频组件为自适应组件。如果要使其具有固定大小，请在组件中使用[!UICONTROL 高级]选项卡中的&#x200B;**[!UICONTROL 宽度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;进行设置。

* **[!UICONTROL 查看]**
器预设从下拉菜单中选择现有的视频查看器预设。如果未显示您要查找的查看器预设，则可能需要将其显示出来。请参阅管理查看器预设。

* **[!UICONTROL 查看]**
器修饰符查看器修饰符采用名称=值对和分隔符的形式，允许您根据《Adobe查看器参考指南》中的概述更改查看器。查看器修饰符的示例为posterimage=img.jpg&amp;caption=text.vtt,1

   例如，通过查看器修饰符，您可以执行以下操作：

   * 将题注文件与视频[题注关联。](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 将导航文件与视频[导航关联。](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

单击组件中的&#x200B;**[!UICONTROL 编辑]**&#x200B;可编辑以下[!UICONTROL 高级设置]。

* **[!UICONTROL 标]**
题更改视频的标题。

* **[!UICONTROL 宽]** 度高 ****
度如果希望视频具有固定大小，请输入以像素为单位的值。将这两个值留空会使视频成为自适应资产。

#### 使用智能裁剪{#when-working-with-smart-crop}时

使用Dynamic Media组件将智能裁剪图像资产添加到您的网页。 编辑该组件时，您可以选择使用预定义的视频查看器预设，以在页面上播放视频。

另请参阅[图像用户档案](image-profiles.md)。

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

单击组件中的&#x200B;**[!UICONTROL 编辑]**&#x200B;可编辑以下[!UICONTROL Dynamic Media设置]。

>[!NOTE]
>
>默认情况下，Dynamic media图像组件是自适应的。 如果要使其变为固定大小，请在“高级”选项卡的组件中设置 [!UICONTROL 它] ，并使用“宽度”和“高 **** 度” ****。

* **[!UICONTROL 图像修]**
饰符通过提供其他图像命令，可以应用图像效果。这些内容在图像预设和图像服务命令参考中进行了介绍。
如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

单击组件中的&#x200B;**[!UICONTROL 编辑]**&#x200B;可编辑以下&#x200B;**[!UICONTROL 高级]**&#x200B;设置。

* **[!UICONTROL 标]**
题更改智能裁剪图像的标题。

* **[!UICONTROL 替]**
代文本为关闭了图形的用户添加智能裁剪图像的标题。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL URL，打开]**
位置您可以设置资产以打开链接。设置 URL，并在打开方式中指示是要在同一窗口中还是在新窗口中打开该 URL。如果您查看的是图像集、旋转集或混合媒体集，则此选项不可用。

* **[!UICONTROL 高]** 度和宽 ****
度如果希望智能裁剪图像具有固定大小，请输入以像素为单位的值。将这两个值留空会使视频成为自适应资产。

### 交互式媒体组件{#interactive-media-component}

交互式媒体组件适用于具有交互功能的资产，例如热点或图像映射。如果您具有交互式图像、交互式视频或传送横幅，请使用交互式媒体组件。

交互式媒体组件是智能的——根据您添加的是图像还是视频，您有各种选项。 此外，查看器是响应式的 - 其屏幕大小可根据设备屏幕大小自动进行更改。所有查看器都是 HTML5 查看器。

>[!NOTE]
>
>如果具有只读权限的用户访问的网页上存在Dynamic Media组件、交互式媒体组件或两者，则分页符和组件将无法正确呈现。 其原因是，重建页面是为了确保组件的属性良好，并且任何引用的资产和配置都可访问。 然后，页面会再次呈现，导致组件中断；由于用户的只读访问权限，无法重新呈现页面上的相应组件代码。
> 
>要避免此问题，请确保AEM Sites用户具有访问资产的必要权限。

![chlimage_1-540](assets/chlimage_1-541.png)

您可以通过在组件中单击&#x200B;**[!UICONTROL 编辑]**，来编辑以下&#x200B;**[!UICONTROL 常规]**&#x200B;设置。

* **[!UICONTROL 查看]**
器预设从下拉菜单中选择现有的查看器预设。如果未显示您要查找的查看器预设，则可能需要将其显示出来。查看器预设必须先发布，然后才能使用。请参阅管理查看器预设。

* **[!UICONTROL 标]**
题更改视频的标题。

* **[!UICONTROL 宽]** 度高 ****
度如果希望视频具有固定大小，请输入以像素为单位的值。将这两个值留空会使视频成为自适应资产。

您可以通过在组件中单击&#x200B;**[!UICONTROL 编辑]**，来编辑以下&#x200B;**[!UICONTROL 添加到购物车]**&#x200B;设置。

* **[!UICONTROL 显示产]**
品资产默认情况下，此值处于选中状态。产品资产会按“商务”模块中的定义显示产品的图像。清除复选标记不会显示产品资产。

* **[!UICONTROL 显示产]**
品价格默认情况下，此值处于选中状态。产品价格会按“商务”模块中的定义显示项目的价格。清除复选标记不会显示产品价格。

* **[!UICONTROL 显示产]**
品表单默认情况下，此值未选中。产品表单包含所有产品变量，例如大小和颜色。清除复选标记不会显示产品变量。

### 全景媒体组件{#panoramic-media-component}

全景媒体组件适用于那些球面全景图像的资源。 这些图像提供房间、房产、位置或风景的360°查看体验。 要使图像成为球面全景图，它必须具有以下任一或两项：

* 宽高比为2:1。
* 用关键字&quot;equirectangular&quot;或(&quot;spherical&quot; + &quot;panorama&quot;)或(&quot;spherical&quot; + &quot;panoramic&quot;)进行标记。 请参阅[使用标记](/help/sites-authoring/tags.md)。

长宽比和关键字条件均适用于资产详细信息页面和“全景媒体”WCM组件的全景资产。

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

通过点按组件中的&#x200B;**[!UICONTROL 配置]**，可以编辑以下设置。

* **[!UICONTROL 查看]**
器预设从查看器预设下拉菜单中选择现有查看器。

如果未显示您要查找的查看器预设，请检查以确保其已发布。 您必须先发布查看器预设，然后才能使用它们。 请参阅[管理查看器预设](managing-viewer-presets.md)。

### 使用HTTP/2投放Dynamic Media资源{#using-http-to-delivery-dynamic-media-assets}

HTTP/2是新的、经过更新的Web协议，它改进了浏览器和服务器的通信方式。 它提供更快的信息传输，并减少所需的处理能力。 Dynamic Media资源的投放现在可以通过HTTP/2，从而提供更好的响应和加载时间。

有关使用Dynamic Media帐户HTTP/2入门的完整详细信息，请参阅[内容](http2.md)的HTTP2投放。

>[!MORELIKETHIS]
>
>* [借助AEMDynamic Media了解色彩管理](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [将自定义视频缩略图与AEM Dynamic Media一起使用](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [借助AEMDynamic Media了解资产查看器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [与AEMDynamic Media使用交互式视频](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [在AEMDynamic Media使用视频播放器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [在AEMDynamic Media中使用图像锐化](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

