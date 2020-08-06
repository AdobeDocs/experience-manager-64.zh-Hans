---
title: 管理Dynamic Media图像预设
description: 了解Dynamic Media图像预设并了解如何创建、修改和管理图像预设
uuid: 087e6c32-82d5-4645-8dba-0a22c62f891f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e401816d-eba5-4833-a3bd-e2e45bc3b19e
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/image-presets
translation-type: tm+mt
source-git-commit: a3a160a0281c1ea2ca050c2c747d6a5ec1d952b3
workflow-type: tm+mt
source-wordcount: '3851'
ht-degree: 19%

---


# Managing Dynamic Media image presets {#managing-image-presets}

图像预设使AEM Assets能够动态地传送不同大小、不同格式或具有动态生成的其他图像属性的图像。 每个图像预设都代表一组预定义的大小调整和格式设置命令，以用于显示图像。在创建图像预设时，您需要选择图像传送的大小。此外，还需要选择格式设置命令，以确保传送供查看的图像时，显示优化的图像外观。

管理员可以创建用于导出资产的预设。 在导出图像时，用户可以选择预设，此操作也会根据管理员指定的规范重新设置图像的格式。

您还可以创建响应式图像预设。如果对资产应用响应式图像预设，则资产会根据查看资产时所使用的设备或屏幕大小而相应发生更改。除了RGB或灰色外，您还可以将图像预设配置为在色彩空间中使用CMYK。

本节介绍如何创建、修改图像预设，以及一般管理图像预设。 无论您何时预览图像，都可以对图像应用图像预设。See [Applying Image Presets](image-presets.md).

>[!NOTE]
>
>智能成像可以与现有图像预设配合使用，并在投放的最后一毫秒使用智能功能根据浏览器或网络连接速度进一步减小图像文件大小。 有关更 [多信息](imaging-faq.md) ，请参阅智能成像。

## Understanding Dynamic Media image presets {#understanding-image-presets}

与软件宏一样，图像预设是一组预定义的大小调整和格式设置命令，这些命令以名称保存。 为了解图像预设的工作方式，假定您的网站要求每个产品图像在桌面设备和移动设备上传送时均以不同的大小和格式显示。

You could create two Image Presets: one with 500 x 500 pixels for desktop version and 150 x 150 pixels for the mobile version. You create two Image Presets, one called *Enlarge* to display images at 500x500 pixels and one called *Thumbnail* to display images at 150 x 150 pixels. To deliver images at the Enlarge and Thumbnail size, AEM looks up the definition of the Enlarge Image Preset and Thumbnail Image Preset. 然后，AEM会根据每个图像预设的大小和格式规范动态生成图像。

如果图像在动态传送时大小大幅缩减，图像可能会丢失锐化和细节。由于这一原因，每个图像预设中都包含格式控制，以在传送图像时将其优化为特定大小。这些控制可确保图像在传送到网站或应用程序时具有锐化、清晰的效果。

管理员可以创建图像预设。要创建图像预设，您可以从头开始创建，也可以通过现有图像预设创建，然后使用新名称对其保存。

## Managing Dynamic Media image presets {#managing-image-presets-1}

要在AEM中管理图像预设，请点按AEM徽标以访问全局导航控制台，然后点按工具图标并导航到资产>图 **[!UICONTROL 像预设]**。

![chlimage_1-494](assets/chlimage_1-494.png)

>[!NOTE]
>
>在您预览或传送资产时，您创建的任何图像预设也可作为动态演绎版使用。
>
>在 *Dynamic Media -Scene7模式*，您 *无需发* 布图像预设，因为图像预设会自动发布。
>
>在 *Dynamic Media —— 混合模式中*，您需要手动发布图像预设。
>
>See [Publishing Image Presets.](#publishing-image-presets)

>[!NOTE]
>
>当您在资产的详细信息视图中选择 **[!UICONTROL 演绎]** 版时，系统会显示 **[!UICONTROL 各种演绎版]** 。 您可以增加或减少显示的图像预设数。 See [Increasing the number of image presets that display](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式 {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

如果您希望支持摄取AI、EPS和PDF文件，以便生成这些文件格式的动态演绎版，您可能需要在创建图像预设之前查看以下信息。

Adobe Illustrator的文件格式是PDF的变体。 在AEM Assets方面，主要区别是：

* Adobe Illustrator文档由一页多层组成。 每个层都被提取为主Illustrator资源下的PNG子资产。
* PDF文档由一个或多个页面组成。 每页都会在主多页PDF文档下提取为单页PDF子资产。

子资产由整个工作流 `Create Sub Asset process` 中的组件创 `DAM Update Asset` 建。 要在工作流中查看此流程组件，请点 **[!UICONTROL 按工具>工作流>模型> DAM更新资产>编辑]**。

另请参 [阅查看多页文件的页面](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file)。

您可以在打开资产时视图子资产或页面，点按内容菜单，然后选择子 **[!UICONTROL 资产]** 或 **[!UICONTROL 页面]**。 子资产是真实资产。 即，PDF页面由工作流组件 `Create Sub Asset` 提取。 然后，它们会 `page1.pdf`作为 `page2.pdf`、等存储在主资产下。 存储资产后，DAM更新 **[!UICONTROL 资产工作流会处理]** 这些资产。

要使用Dynamic Media预览和生成AI、EPS或PDF文件的动态演绎版，需要执行以下处理步骤：

1. 在DAM更 **[!UICONTROL 新资产工作流中]** ，栅格化 **[!UICONTROL PDF/AI图像预览再现流程组件会使用配置的分辨率将原始资产的第一页栅格化为再]**`cqdam.preview.png` 现。

1. 然后 `cqdam.preview.png` ，该再现会通过工作流中的Dynamic Media Process **[!UICONTROL 图像资产流程组件优化]** ，为PTIFF格式。

>[!NOTE]
>
>In the **[!UICONTROL DAM Update Asset]** workflow, the **[!UICONTROL EPS thumbnails]** step generates thumbnails for EPS files.

### PDF/AI/EPS资产元数据属性 {#pdf-ai-eps-asset-metadata-properties}

| **元数据属性** | **描述** |
|---|---|
| dam：物理窗口 | 文档宽度（英寸）。 |
| dam：物理高度英寸 | 文档高度（英寸）。 |

您可以 **[!UICONTROL 通过DAM更新资产工作流访问“栅格化]** PDF/AI图像预览再现 **[!UICONTROL ”流程]** 组件选项。

点按左上角的Adobe Experience Manager，导航到工 **[!UICONTROL 具>工作流>模型]**。 在“工 **[!UICONTROL 作流模型]** ”页面 **[!UICONTROL 上，选择DAM更新资产]**，然后在工具栏点 **[!UICONTROL 按编辑]**。 在“DAM更 **[!UICONTROL 新资产工作流]** ”页面上，多次点 **[!UICONTROL 按“栅格化PDF/AI图像预览再现”]** 流程组件以打开其“步 **[!UICONTROL 骤属性]** ”对话框。

### Rasterize PDF/AI image preview rendition options {#rasterize-pdf-ai-image-preview-rendition-options}

![栅格化PDF或AI工作流程的参数](assets/rasterize_pdf_ai_image_preview.png)

**栅格化PDF或AI工作流程的参数**

<table> 
 <tbody> 
  <tr> 
   <td><strong>进程参数</strong></td> 
   <td><strong>默认设置</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>Mime 类型</td> 
   <td><p>application/pdf</p> <p>application/postscript</p> <p>application/illustrator<br /> </p> </td> 
   <td>列表被视为PDF或Illustrator文档的文档mime类型。<br /> </td> 
  </tr> 
  <tr> 
   <td>最大宽度</td> 
   <td>2048</td> 
   <td>生成的预览再现的最大宽度（以像素为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td>最大高度</td> 
   <td>2048</td> 
   <td>生成的预览再现的最大高度（以像素为单位）。<br /> </td> 
  </tr> 
  <tr> 
   <td>分辨率</td> 
   <td>72</td> 
   <td>分辨率，以ppi为单位栅格化第一页（每英寸像素数）。</td> 
  </tr> 
 </tbody> 
</table>

使用默认处理参数，PDF/AI文档的第一页以72 ppi栅格化，生成的预览图像的大小为2048 x 2048像素。 对于典型部署，您可能希望将分辨率提高到至少150 ppi或更高。 例如，300 ppi的美国字母大小文档要求最大宽度和高度分别为2550 x 3300像素。

**[!UICONTROL “最大宽]** 度” **[!UICONTROL 和“最大高度]** ”限制栅格化的分辨率。 例如，如果最大值未更改，且“分辨率”设置为300 ppi，则美国字母文档将栅格化为186 ppi。 即，文档为1581 x 2046像素。

栅 **[!UICONTROL 格化PDF/AI图像预览再现处理组件]** ，定义了最大值，以确保它不会在内存中创建过大的图像。 这样的大映像可能会溢出提供给JVM（Java虚拟机）的内存。 必须注意向JVM提供足够的内存来管理已配置的并行工作流数，每个并行都有可能以最大配置大小创建映像。

### InDesign(INDD)文件格式 {#indesign-indd-file-format}

如果要支持摄取INDD文件，以便生成此文件格式的动态演绎版，您可能需要在创建图像预设之前查看以下信息。

对于InDesign文件，仅当Adobe InDesign服务器与AEM集成时，才会提取子资源。 引用的资产会根据其元数据进行链接。 InDesign Server不是链接必需的。 但是，在处理InDesign文件之前，AEM中必须存在引用的资产，才能在InDesign文件和引用的资产之间创建链接。

See [Integrating AEM Assets with InDesign Server](indesign.md).

DAM更新资产工作流中的媒体 **[!UICONTROL 提取流程组]** 件会运行多个预 **[!UICONTROL 配置的扩展脚]** 本，以处理InDesign文件。

![媒体提取过程参数中的扩展脚本路径](assets/media_extraction_arguments.png)

在 **[!UICONTROL DAM更新资]** 产工作流中 **[!UICONTROL ，媒体提取]** 流程组件 **[!UICONTROL 的参数]** 中的扩展脚本路径。

Dynamic Media集成使用以下脚本：

<table> 
 <tbody> 
  <tr> 
   <td><strong>扩展脚本名称</strong></td> 
   <td><strong>默认</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>ThumbnailExport.jsx</td> 
   <td>是</td> 
   <td>生成经过优化 <code>thumbnail.jpg</code> 的300 ppi再现，并按流程组件转换为PTIFF <code>Dynamic Media Process Image Assets</code> 再现。<br /> </td> 
  </tr> 
  <tr> 
   <td>JPEGPagesExport.jsx</td> 
   <td>是</td> 
   <td>为每页生成一个300 ppi的JPEG子资产。 JPEG子资产是存储在InDesign资产下的实际资产。 它还经过优化，并通过工作流转换为 <code>DAM Update Asset</code> PTIFF。<br /> </td> 
  </tr> 
  <tr> 
   <td>PDFPagesExport.jsx</td> 
   <td>否</td> 
   <td>为每个页面生成一个PDF子资产。 PDF子资产将按照前面所述进行处理。 由于PDF仅包含单页，因此不会生成子资产。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 配置图像缩略图大小 {#configuring-image-thumbnail-size}

您可以通过在DAM更新资产工作流中配置这些设置来 **[!UICONTROL 配置缩略图的大小]** 。 在工作流中，您可以通过两个步骤配置图像资产的缩略图大小。 尽管动态图&#x200B;**[!UICONTROL 像资产使用一个(Dynamic Media Process Image]** Assets)，静态缩略图生成使用另一个(**[!UICONTROL Process Thumbnails]**)，或者当所有其他进程无法生成缩略图时，这两个进程 *应具有相同* 的设置。

在 **[!UICONTROL Dynamic Media 流程图像资产]**&#x200B;步骤中，缩略图由图像服务器生成，此配置与应用于&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤的配置无关。通过&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤生成缩略图是创建缩览图最耗时、内存占用最多的方法。

缩览图大小按以下格式定义： **width:height:center**，例如 *80:80:false*。 宽度和高度决定缩略图的大小（以像素为单位）; 中心值为false或true，如果设置为true，则表示缩略图的大小与配置中指定的大小完全相同。 如果调整大小的图像较小，则图像将居中在缩略图中。

>[!NOTE]
>
>* Thumbnail size for EPS files are configured in the **[!UICONTROL EPS thumbnails]** step, in the **[!UICONTROL Arguments]** tab under **[!UICONTROL Thumbnails]**.
   >
   >
* 可在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡下的&#x200B;**[!UICONTROL 流程]**&#x200B;选项卡中，通过 **[!UICONTROL FFmpeg 缩略图]**&#x200B;步骤配置视频的缩略图大小。

>



**配置缩略图大小**:

1. 点按 **[!UICONTROL 工具>工作流>模型> DAM更新资产>编辑]**。
1. 点按Dynamic **[!UICONTROL Media Process图像资产]** ，然后点按缩略图 **[!UICONTROL 选项卡]** 。 根据需要更改缩略图大小，然后点按&#x200B;**[!UICONTROL 确定]**。

   ![step_properties_thumbnailarguments](assets/step_properties_thumbnailarguments.png)

1. 点按&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤，然后点按&#x200B;**[!UICONTROL 缩略图]**&#x200B;选项卡。Change the thumbnail size, as needed, and tap **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >**[!UICONTROL 流程缩略图]**&#x200B;步骤的缩略图参数中的值必须与 **[!UICONTROL Dynamic Media 流程图像资产]**&#x200B;步骤中的缩略图参数相匹配。

1. 点按 **[!UICONTROL 保存]** ，以保存对工作流所做的更改。

### 增加或减少显示的Dynamic Media图像预设数 {#increasing-or-decreasing-the-number-of-image-presets-that-display}

在预览资产时，您创建的图像预设可以作为动态演绎版使用。 AEM在从详细信息视图>演绎版查看资产时显示 **[!UICONTROL 各种动态演绎版]**。 您可以增加或减少显示的演绎版限制。

**要增加或减少显示的Dynamic Media图像预设数**:

1. 导航到 **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 导航到位于的图像预设列表节点 `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![increase_deximenteumberofimages显示](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. In the **[!UICONTROL limit]** property, change the **[!UICONTROL value]**, which is set to 15 by default, to the desired number.
1. 导航到图像预设数据源： `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. 在limit属性中，将数字更改为所需的数字，例如 `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 点按 **[!UICONTROL 全部保存]**。

### Creating Dynamic Media image presets {#creating-image-presets}

通过创建Dynamic Media图像预设，您可以在预览或发布图像时将这些设置应用到任何图像。

>[!NOTE]
>
>如果您使用Internet Explorer 9，创建的预设在保存后不会立即显示在预设列表中。 要解决此问题，请禁用 IE9 的缓存。

如果您希望支持摄取AI、PDF和EPS文件，以便生成这些文件格式的动态再现，您可能需要在创建图像预设之前查看以下信息。\
请参 [阅Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)。

如果要支持摄取INDD文件，以便生成此文件格式的动态演绎版，您可能需要在创建图像预设之前查看以下信息。  请参 [阅InDesign(INDD)文件格式](#indesign-indd-file-format)。

>[!NOTE]
>
>要创建Dynamic Media图像预设，您必须具有AEM管理员或Admin Console管理员的管理员权限。

**要创建Dynamic Media图像预设，请执行以下操作**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按工 **[!UICONTROL 具图]** 标，然后导航到 **[!UICONTROL 资产>图像预设]**。
1. 点按&#x200B;**[!UICONTROL 创建]**。

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >要使此图像预设具有响应性，请擦除&#x200B;**[!UICONTROL 宽度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;字段中的值，并将其留空。

1. 在“编 **[!UICONTROL 辑图像预设]** ”页面上，根据需要在“基 **[!UICONTROL 本”和“高级]** ”选 **[!UICONTROL 项卡中输入值，包括]** 名称。 图像预设选项中概 [述了这些选项](#image-preset-options)。 预设显示在左窗格中，并可以与其他资产一起动态使用。

   ![chlimage_1-497](assets/chlimage_1-497.png)

1. 单击&#x200B;**[!UICONTROL 保存]**。

### Creating a responsive image preset {#creating-a-responsive-image-preset}

To create a responsive image preset, perform the steps in [Creating Image Presets](#creating-image-presets). When entering the height and width in the **[!UICONTROL Edit Image Preset]** window, erase the values and leave them blank.

将它们留空会告知AEM此图像预设是响应式的。 您可以根据需要调整其他值。

![chlimage_1-498](assets/chlimage_1-498.png)

>[!NOTE]
>
>要在将图像预设应用到资产时显示 **[!UICONTROL URL]** 和 **[!UICONTROL RESS]** 按钮，必须先发布资产。
>
>在Dynamic Media -Scene7模式中，图像预设和图像资产会自动发布。
>
>在Dynamic Media —— 混合模式中，您必须手动发布图像预设和图像资产。

### Image Preset options {#image-preset-options}

在创建或编辑图像预设时，您可以使用本节介绍的几种选项。此外，Adobe还建议对开始采 *用以下* 三种最佳做法选项：

* **[!UICONTROL 格式]** (**[!UICONTROL 基本]** 选项卡)-选 **[!UICONTROL 择JPEG]** 或其他符合要求的格式。 所有Web浏览器都支持JPEG图像格式； 它可以在小文件大小和图像质量之间实现良好的平衡。 但是，JPEG格式图像使用有损压缩方案，如果压缩设置太低，会引入不需要的图像伪影。 因此，Adobe 建议将压缩质量设置为 75。此设置在图像质量和小文件大小之间提供了良好的平衡。
* **[!UICONTROL 启用简单锐化]** -请勿选择启 **[!UICONTROL 用简单锐化]** (此锐化滤镜优惠的控制比USM锐化设置少)。
* **[!UICONTROL 锐化： 重新取样模]** 式——选 **[!UICONTROL 择“双三次”]**。

#### “基本”选项卡选项{#basic-tab-options}

<table> 
 <tbody> 
  <tr> 
   <td><strong>字段</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td><strong>名称</strong></td> 
   <td>输入一个描述性名称，不加任何空格。在名称中包含图像大小规格可帮助用户识别此图像预设。</td> 
  </tr> 
  <tr> 
   <td><strong>宽度和高度</strong></td> 
   <td>输入传送图像时所用的像素大小。宽度和高度必须大于 0 像素。如果任一值为 0，则无法创建预设。如果两个值均为空，则表示已经创建了响应式图像预设。</td> 
  </tr> 
  <tr> 
   <td><strong>格式</strong></td> 
   <td><p>从菜单中选择一个格式。</p> <p>选择 <strong>JPEG</strong> 可提供以下更多选项。</p> 
    <ul> 
     <li><strong>质量</strong> -控制JPEG压缩级别。 此设置会影响文件大小和图像质量。 JPEG质量比例为1-100。拖动滑块时，比例可见。</li> 
     <li><strong>启用JPG色度缩减采样</strong> -由于眼睛对高频颜色信息的敏感程度低于高频亮度，因此JPEG图像将图像信息分为明亮度和颜色分量。 当压缩JPEG图像时，明亮度分量将保留为全分辨率，而颜色分量则通过平均一组像素进行缩减采样。 缩减像素采样可将数据量减少一半或三分之一，几乎不会影响感知质量。 缩减像素采样不适用于灰度图像。 此技术可减少对对比度高的图像（例如，叠加有文本的图像）有用的压缩量。</li> 
    </ul> 
    <div>
      选择 <strong>GIF</strong> 或<strong>带有 Alpha 的 GIF</strong> 可提供以下更多 <strong>GIF 颜色量化</strong>选项： 
    </div> 
    <ul> 
     <li><strong>类 </strong>型——选 <strong>择</strong> Adaptive <strong>（默认）、</strong>Web <strong>或</strong>Macintosh。 如果您选 <strong>择带有Alpha的GIF</strong>，则Macintosh选项不可用。</li> 
     <li><strong>仿色</strong> -选 <strong>择扩</strong> 散或 <strong>关闭</strong>。</li> 
     <li><strong>颜色数目</strong> - 输入介于 2 到 256 之间的一个数字。</li> 
     <li><strong>颜色列表</strong> - 输入一个以逗号分隔的列表。例如，对于白色、灰色和黑色，输入 000000,888888,ffffff。</li> 
    </ul> 
    <div>
      选择 <strong>PDF</strong>、<strong>TIFF</strong> 或<strong>带有 Alpha 的 TIFF</strong> 可提供以下更多选项： 
    </div> 
    <ul> 
     <li><strong>压缩</strong> - 选择一种压缩算法。“PDF”的算法选项有<strong>无</strong>、<strong>Zip</strong> 和 <strong>Jpeg</strong>；对于“TIFF”，压缩算法选项有<strong>无</strong>、<strong>LZW</strong>、<strong>Jpeg</strong> 和 <strong>Zip</strong>；对于“带有 Alpha 的 TIFF”，压缩算法选项有<strong>无</strong>、<strong>LZW</strong> 和 <strong>Zip</strong>。</li> 
    </ul> <p>如果选择 <strong>PNG</strong>、<strong>带有 Alpha 的 PNG</strong>，或者选择 <strong>EPS</strong>，则不提供其他选项。</p> </td> 
  </tr> 
  <tr> 
   <td><strong>锐化</strong></td> 
   <td>Select the <strong>Enable Simple Sharpening</strong> option to apply a basic sharpening filter to the image after all scaling takes place. Sharpening can help compensate for blurriness that can result when you display an image at a different size. </td> 
  </tr> 
 </tbody> 
</table>

#### “高级”选项卡选项{#advanced-tab-options}

<table> 
 <tbody> 
  <tr> 
   <td><strong>字段</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td><strong>色彩空间</strong></td> 
   <td>Select <strong>RGB, CMYK,</strong> or <strong>Grayscale</strong> for the color space.</td> 
  </tr> 
  <tr> 
   <td><strong>颜色配置文件</strong></td> 
   <td>如果资产与工作用户档案不同，请选择应将其转换为的输出色彩空间用户档案。</td> 
  </tr> 
  <tr> 
   <td><strong>渲染方法</strong></td> 
   <td>您可以覆盖默认的渲染方法。 渲染意图确定在目标颜色用户档案（溢色）中无法再现的颜色会发生什么情况。 如果渲染方法与ICC用户档案不兼容，则将忽略它。 
    <ul> 
     <li>选择 <strong>“感知</strong> ”，当原始图像中的一种或多种颜色超出目标色彩空间的色域时，将一个色彩空间的总色域压缩为另一个色彩空间。</li> 
     <li>当当 <strong>前颜色空间中</strong> 的颜色超出目标颜色空间中的色域时，选择“相对比色”，并希望将其映射到目标颜色空间的色域中最接近的可能颜色，而不影响任何其他颜色。 </li> 
     <li>选择 <strong>“饱和</strong> ”以在转换为目标色彩空间时重现原始图像色彩饱和度。 </li> 
     <li>选 <strong>择“绝对比色</strong> ”以精确匹配颜色，而不调整会改变图像亮度的白点或黑点。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>黑场补偿</strong></td> 
   <td>如果输出用户档案支持此功能，请选择此选项。 如果黑点补偿与指定的ICC用户档案不兼容，则忽略黑点补偿。</td> 
  </tr> 
  <tr> 
   <td><strong>仿色</strong></td> 
   <td>选择此选项可避免或减少色带伪像。 </td> 
  </tr> 
  <tr> 
   <td><strong>锐化类型</strong></td> 
   <td><p>Select <strong>None</strong>, <strong>Sharpen</strong>, or <strong>Unsharp Mask</strong>. </p> 
    <ul> 
     <li>选择<strong>无</strong>可禁用锐化。</li> 
     <li>Select <strong>Sharpen </strong>to apply a basic sharpening filter to the image after all scaling takes place. Sharpening can help compensate for blurriness that can result when you display an image at a different size. </li> 
     <li>Select<strong> Unsharp mask</strong> to fine-tune a sharpening filter effect on the final downsampled image. You can control intensity of effect, radius of the effect (measured in pixels) and a threshold of contrast that will be ignored. This effect uses the same options as Photoshop’s “Unsharp Mask” filter.</li> 
    </ul> <p>在 <strong>USM 锐化</strong>中，您可以设置以下选项：</p> 
    <ul> 
     <li><strong>数量</strong> -控制应用于边缘像素的对比度数量。 默认的实数值为1.0。对于高分辨率图像，最高可将其增加到5.0。可以考虑使用“数量”来衡量滤镜强度。</li> 
     <li><strong>半径</strong> -确定边缘像素周围影响锐化的像素数。 对于高分辨率图像，输入1到2的实数。 低值仅锐化边缘像素； 高值锐化较宽范围的像素。 正确的值取决于图像大小。</li> 
     <li><strong>阈值</strong> -确定应用USM锐化滤镜时要忽略的对比度范围。 换句话说，此选项确定锐化的像素与周围区域必须存在多大的不同，才能被视为边缘像素并进行锐化。 为避免引入杂色，请尝试2到20之间的整数值。 </li> 
     <li><strong>应用于</strong> -确定是否将取消锐化应用于每种颜色或亮度。</li> 
    </ul> 
    <div>
      有关“锐化”的信息，请参阅<a href="https://docs.adobe.com/content/help/en/experience-manager-64/assets/dynamic/assets/s7_sharpening_images.pdf">锐化图像</a>。 
    </div> </td> 
  </tr> 
  <tr> 
   <td><strong>重新取样模式</strong></td> 
   <td>选择一个<strong>重新取样模式</strong>选项。在缩减像素采样时，这些选项会锐化图像： 
    <ul> 
     <li><strong>双线性</strong> -最快速的重新取样方法。 会出现一些锯齿伪像。</li> 
     <li><strong>两次立方</strong> -提高CPU使用率，但生成较锐利的图像，出现的锯齿伪像较少。</li> 
     <li><strong>锐化2</strong> —— 可以生成比两次立方效果更锐利的结果，但CPU成本更高。</li> 
     <li><strong>Bi-Sharp</strong> —— 选择Photoshop默认重新取样器以减小图像大小，在Adobe Photoshop <strong>称为</strong> “双立方”。</li> 
     <li><strong>每种颜色</strong>和<strong>亮度</strong> - 每种方法均可基于颜色或亮度。默认情况下将选择<strong>每种颜色</strong>。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>打印分辨率</strong></td> 
   <td>选择此图像的打印分辨率；默认值为 72 像素。</td> 
  </tr> 
  <tr> 
   <td><strong>图像修饰符</strong></td> 
   <td><p>除了UI中提供的常见图像设置之外，Dynamic Media还支持许多可在图像修饰符字段中指定的高 <strong>级图像修</strong> 改。 这些参数在图像服务器协 <a href="https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html">议命令参考中定义</a>。</p> <p>重要： 不支持API中列出的以下功能：</p> 
    <ul> 
     <li>基本模板和文本渲染命令： <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> 和 <code>textPs=</code></li> 
     <li>本地化命令： <code>locale=</code> 和 <code>req=xlate</code></li> 
     <li><code>req=set</code> 不可用于一般用途。</li> 
     <li><code>req=mbrset</code></li> 
     <li><code>req=saveToFile</code></li> 
     <li><code>req=targets</code></li> 
     <li><code>template=</code></li> 
     <li>非核心Dynamic Media服务： SVG、图像渲染和Web到打印</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Defining Image Preset options with image modifiers {#defining-image-preset-options-with-image-modifiers}

Besides the options available in the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs, you can define image modifiers to give you more options when you define image presets. 图像渲染依赖于Dynamic Media图像渲染API。 API在《HTTP协议参考》中有 [详细定义](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/c-http-protocol-reference.html)。

下面是一些基本示例，说明了可以使用图像修饰符进行哪些操作。

>[!NOTE]
>
>某些图像修 [饰符不能用于AEM](#advanced-tab-options)。

* [op_invert](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html) —— 反转每个颜色分量以获得负片图像效果。

   ```xml
   &op_invert=1
   ```

   ![chlimage_1-499](assets/chlimage_1-499.png)

* [op_blur](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html) - 向图像应用模糊滤镜。

   ```xml
   &op_blur=25
   ```

   ![chlimage_1-500](assets/chlimage_1-500.png)

* 组合命令 - op_blur 和 op-invert

   ```xml
   &op_invert=1&op_blur=25
   ```

   ![chlimage_1-501](assets/chlimage_1-501.png)

* [op_brightness](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html) —— 降低或增加亮度。

   ```xml
   &op_brightness=75
   ```

   ![chlimage_1-502](assets/chlimage_1-502.png)

* [opac](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html) - 调整图像不透明度。可用于降低前景不透明度。

   ```xml
   opac=50
   ```

   ![chlimage_1-503](assets/chlimage_1-503.png)

## 编辑图像预设 {#modifying-image-presets}

**要编辑图像预设，请执行以下操作**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按工 **[!UICONTROL 具图]** 标，然后导航到 **[!UICONTROL 资产>图像预设]**。

   ![chlimage_1-504](assets/chlimage_1-504.png)

1. 选择一个预设，然后点按 **[!UICONTROL 编辑]**。
1. 在“编 **[!UICONTROL 辑图像预设]** ”页面上，进行所需的更改，然后点按 **[!UICONTROL 保存]**。

## Publishing Dynamic Media image presets {#publishing-image-presets}

如果运行的是Dynamic Media —— 混合模式，则必须手动发布图像预设。

如果您运行的是Dynamic Media -Scene7模式，则图像预设将自动为您发布； 您无需完成这些步骤。

**要在Dynamic Media —— 混合模式中发布图像预设，请执行以下操作**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按工 **[!UICONTROL 具图]** 标，然后导航到 **[!UICONTROL 资产>图像预设]**。
1. 从图像预设列表中选择图像预设或多个图像预设，然后点按发 **[!UICONTROL 布]**。
1. 图像预设发布后，状态将从未发布更改为已发布。

   ![chlimage_1-505](assets/chlimage_1-505.png)

## Deleting Dynamic Media image presets {#deleting-image-presets}

**要删除Dynamic Media图像预设，请执行以下操作**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按工 **[!UICONTROL 具图]** 标，然后导航到 **[!UICONTROL 资产>图像预设]**。
1. 选择一个预设，然后点按 **[!UICONTROL 删除]**。 Dynamic Media会确认您是否要删除它。 点按 **[!UICONTROL 删除]**。

