---
title: 管理Dynamic Media图像预设
description: 了解Dynamic Media图像预设，并了解如何创建、修改和管理图像预设
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/image-presets
exl-id: 3a666efe-1592-4425-82f5-c4d9343f65da
feature: Image Presets
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3871'
ht-degree: 7%

---

# 管理Dynamic Media图像预设 {#managing-image-presets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

图像预设使AEM Assets能够动态地传送不同大小、不同格式或具有其他动态生成的图像属性的图像。 每个图像预设都代表一组预定义的大小调整和格式设置命令，用于显示图像。 在创建图像预设时，您可以选择图像交付的大小。 您还可以选择格式设置命令，以便在传送图像以供查看时优化图像的外观。

管理员可以创建用于导出资产的预设。 用户在导出图像时可以选择预设，这也会按照管理员指定的规范来重新设置图像的格式。

您还可以创建响应式图像预设。 如果您将响应式图像预设应用于资产，则资产会根据查看资产时所使用的设备或屏幕大小而发生更改。 除了“RGB”或“灰色”之外，您还可以将图像预设配置为在色彩空间中使用CMYK。

本节将介绍如何创建、修改和通常管理图像预设。 无论您何时预览图像，都可以将图像预设应用到图像。 请参阅 [应用图像预设](image-presets.md).

>[!NOTE]
>
>智能成像可与您现有的图像预设配合使用，并在交付的最后一毫秒内使用智能功能，根据浏览器或网络连接速度进一步减小图像文件大小。 请参阅 [智能成像](imaging-faq.md) 以了解更多信息。

## 了解Dynamic Media图像预设 {#understanding-image-presets}

与软件宏一样，图像预设是一组预定义的大小调整和格式设置命令，这些命令以名称保存。 为了了解图像预设的工作方式，假定您的网站要求每个产品图像在桌面和移动设备交付中以不同的大小、不同格式和压缩率显示。

您可以创建两个图像预设：一个适用于桌面版的500 x 500像素，而适用于移动版的150 x 150像素。 您可以创建两个图像预设，一个称为 *放大* 以500x500像素显示图像，称为 *缩略图* 以150 x 150像素显示图像。 要传送大图和缩略图大小的图像，AEM会查找“放大图像预设”和“缩略图图像预设”的定义。 然后，AEM会根据每个图像预设的大小和格式规范动态生成图像。

如果图像在动态传送时大小减小，则图像可能会丢失锐化和细节。 因此，每个图像预设都包含格式控件，用于在以特定大小传送图像时优化图像。 这些控件可确保在将图像传送到您的网站或应用程序时，图像清晰明了。

管理员可以创建图像预设。 要创建图像预设，您可以从头开始，也可以从现有图像预设开始，然后使用新名称保存。

## 管理Dynamic Media图像预设 {#managing-image-presets-1}

您可以在AEM中管理图像预设，方法是点按AEM徽标以访问全局导航控制台，然后点按工具图标并导航到 **[!UICONTROL 资产>图像预设]**.

![chlimage_1-494](assets/chlimage_1-494.png)

>[!NOTE]
>
>在预览或传送资产时，您创建的任何图像预设也可用作动态演绎版。
>
>在 *Dynamic Media -Scene7模式*, *not* 在图像预设自动发布时，需要发布图像预设。
>
>在 *Dynamic Media — 混合模式*，则需要手动发布图像预设。
>
>请参阅 [发布图像预设。](#publishing-image-presets)

>[!NOTE]
>
>当您选择 **[!UICONTROL 演绎版]** 资产的 **[!UICONTROL 详细信息]** 查看。 您可以增加或减少显示的图像预设数。 请参阅 [增加显示的图像预设数](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式 {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

如果您打算支持摄取AI、EPS和PDF文件，以便生成这些文件格式的动态呈现，则在创建图像预设之前，您可能需要查看以下信息。

Adobe Illustrator的文件格式是PDF的变体。 在AEM Assets，主要区别如下：

* Adobe Illustrator文档由包含多层的单个页面组成。 每个层都作为PNG子资产提取，位于主Illustrator资产下。
* PDF文档由一个或多个页面组成。 每个页面都将作为主多页PDF文档下的单个页面PDF子资产进行提取。

子资产由 `Create Sub Asset process` 组件 `DAM Update Asset` 工作流。 要在工作流中查看此流程组件，请点按 **[!UICONTROL 工具>工作流>模型> DAM更新资产>编辑]**.

另请参阅 [查看多页文件的页面](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file).

您可以在打开资产时查看子资产或页面，点按内容菜单，然后选择 **[!UICONTROL 子资产]** 或 **[!UICONTROL 页面]**. 子资产是真实资产。 即，PDF页面由 `Create Sub Asset` 工作流组件。 然后，它们将存储为 `page1.pdf`, `page2.pdf`，等等。 存储后， **[!UICONTROL DAM更新资产]** 工作流会处理它们。

要使用Dynamic Media预览AI、EPS或PDF文件并生成动态演绎版，需要执行以下处理步骤：

1. 在 **[!UICONTROL DAM更新资产]** 工作流， **[!UICONTROL 栅格化PDF/AI图像预览呈现版本]** 流程组件使用配置的分辨率将原始资产的第一页栅格化为 `cqdam.preview.png` 演绎版。

1. 的 `cqdam.preview.png` 然后，演绎版会由 **[!UICONTROL Dynamic Media处理图像资产]** 工作流中的流程组件。

>[!NOTE]
>
>在 **[!UICONTROL DAM更新资产]** 工作流， **[!UICONTROL EPS缩略图]** 步骤为EPS文件生成缩略图。

### PDF/AI/EPS资产元数据属性 {#pdf-ai-eps-asset-metadata-properties}

| **元数据属性** | **描述** |
|---|---|
| dam:Physicalwidthininch | 文档宽度（英寸）。 |
| dam：物理高度英寸 | 文档高度（英寸）。 |

您有权访问 **[!UICONTROL 栅格化PDF/AI图像预览呈现版本]** 流程组件选项(通过 **[!UICONTROL DAM更新资产]** 工作流。

点按左上角的Adobe Experience Manager，导航到 **[!UICONTROL 工具>工作流>模型]**. 在 **[!UICONTROL 工作流模型]** 页面，选择 **[!UICONTROL DAM更新资产]**，然后在工具栏中点按 **[!UICONTROL 编辑]**. 在 **[!UICONTROL DAM更新资产工作流]** ，请双击 **[!UICONTROL 栅格化PDF/AI图像预览呈现版本]** 进程组件打开其 **[!UICONTROL 步骤属性]** 对话框。

### 栅格化PDF/AI图像预览呈现版本选项 {#rasterize-pdf-ai-image-preview-rendition-options}

![用于栅格化PDF或AI工作流的参数](assets/rasterize_pdf_ai_image_preview.png)

**用于栅格化PDF或AI工作流的参数**

<table> 
 <tbody> 
  <tr> 
   <td><strong>进程参数</strong></td>
   <td><strong>默认设置</strong></td>
   <td><strong>描述</strong></td>
  </tr> 
  <tr> 
   <td>Mime 类型</td>
   <td><p>application/pdf</p> <p>application/postscript</p> <p>application/illustrator<br/> </p> </td>
   <td>被视为PDF或Illustrator文档的文档mime类型列表。<br/> </td>
  </tr> 
  <tr> 
   <td>最大宽度</td>
   <td>2048</td>
   <td>生成的预览呈现版本的最大宽度（以像素为单位）。<br/> </td>
  </tr> 
  <tr> 
   <td>最大高度</td>
   <td>2048</td>
   <td>生成的预览呈现版本的最大高度（以像素为单位）。<br/> </td>
  </tr> 
  <tr> 
   <td>解决方法</td>
   <td>72</td>
   <td>分辨率以ppi为单位栅格化第一页（每英寸像素）。</td>
  </tr>
 </tbody>
</table>

使用默认的处理参数，PDF/AI文档的第一页以72 ppi进行光栅化，并且生成的预览图像的大小为2048 x 2048像素。 对于典型部署，您可能希望将分辨率提高到至少150 ppi或更高。 例如，300 ppi的美国字母大小文档要求最大宽度和高度分别为2550 x 3300像素。

**[!UICONTROL 最大宽度]** 和 **[!UICONTROL 最大高度]** 限制光栅化的分辨率。 例如，如果最大值保持不变，并且分辨率设置为300 ppi，则美国信件文档将以186 ppi光栅化。 即，文档为1581 x 2046像素。

的 **[!UICONTROL 栅格化PDF/AI图像预览呈现版本]** 进程组件定义了最大值，以确保它不会在内存中创建过大的图像。 此类大映像可能会使提供给JVM（Java虚拟机）的内存溢出。 必须小心为JVM提供足够的内存来管理已配置的并行工作流数量，每个工作流都有可能以已配置的最大大小创建映像。

### InDesign(INDD)文件格式 {#indesign-indd-file-format}

如果您打算支持摄取INDD文件以便生成此文件格式的动态演绎版，则可能需要在创建图像预设之前查看以下信息。

对于InDesign文件，仅当Adobe InDesign服务器与AEM集成时，才会提取子资产。 引用的资产会根据其元数据进行关联。 InDesign Server不是链接所必需的。 但是，在为要在AEM文件和引用的资产之间创建的链接处理InDesign文件之前，InDesign中必须存在引用的资产。

请参阅 [将AEM Assets与InDesign Server集成](indesign.md).

中的媒体提取流程组件 **[!UICONTROL DAM更新资产]** 工作流运行多个预配置的 **[!UICONTROL 扩展脚本]** 以处理InDesign文件。

![媒体提取流程参数中的扩展脚本路径](assets/media_extraction_arguments.png)

的 **[!UICONTROL 扩展脚本]** 参数中的路径 **[!UICONTROL 媒体提取]** 流程组件 **[!UICONTROL DAM更新资产]** 工作流。

以下脚本供Dynamic Media集成使用：

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
   <td>生成300 ppi <code>thumbnail.jpg</code> 已优化并通过 <code>Dynamic Media Process Image Assets</code> 进程组件。<br/> </td>
  </tr> 
  <tr> 
   <td>JPEGPagesExport.jsx</td> 
   <td>是</td> 
   <td>为每个页面生成300 ppiJPEG子资产。 JPEG子资产是存储在InDesign资产下的实际资产。 它还会通过 <code>DAM Update Asset</code> 工作流。<br/> </td>
  </tr> 
  <tr> 
   <td>PDFPagesExport.jsx</td>
   <td>否</td>
   <td>为每个页面生成PDF子资产。 将按照前面所述处理PDF子资产。 由于PDF仅包含单个页面，因此不会生成子资产。<br/> </td>
  </tr> 
 </tbody> 
</table>

## 配置图像缩略图大小 {#configuring-image-thumbnail-size}

您可以通过在 **[!UICONTROL DAM更新资产]** 工作流。 在工作流中，您可以通过两个步骤来配置图像资产的缩略图大小。 尽管有一个(**[!UICONTROL Dynamic Media处理图像资产]**)用于动态图像资产，而其他(**[!UICONTROL 流程缩略图]**)生成静态缩略图，或者当所有其他进程无法生成缩略图时， *both* 应具有相同的设置。

在 **[!UICONTROL Dynamic Media 流程图像资产]**&#x200B;步骤中，缩略图由图像服务器生成，此配置与应用于&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤的配置无关。通过&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤生成缩略图是创建缩览图最耗时、内存占用最多的方法。

缩略图大小按以下格式定义： **宽度:height:中心**，例如 *80:80:false*. 宽度和高度决定缩略图的大小（以像素为单位）；中心值为false或true，如果设置为true，则表示缩略图的大小与配置中给定的大小完全相同。 如果调整大小的图像较小，则该图像将居中在缩略图中。

>[!NOTE]
>
>* EPS文件的缩略图大小在 **[!UICONTROL EPS缩略图]** 步骤 **[!UICONTROL 参数]** 选项卡 **[!UICONTROL 缩略图]**.
>
>* 可在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡下的&#x200B;**[!UICONTROL 流程]**&#x200B;选项卡中，通过 **[!UICONTROL FFmpeg 缩略图]**&#x200B;步骤配置视频的缩略图大小。
>


**配置缩略图大小**:

1. 点按 **[!UICONTROL 工具>工作流>模型> DAM更新资产>编辑]**.
1. 点按 **[!UICONTROL Dynamic Media处理图像资产]** 步骤，然后点按 **[!UICONTROL 缩略图]** 选项卡。 根据需要更改缩略图大小，然后点按&#x200B;**[!UICONTROL 确定]**。

   ![step_properties_thumbnailarguments](assets/step_properties_thumbnailarguments.png)

1. 点按&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤，然后点按&#x200B;**[!UICONTROL 缩略图]**&#x200B;选项卡。根据需要更改缩略图大小，然后点按 **[!UICONTROL 确定]**.

   >[!NOTE]
   >
   >**[!UICONTROL 流程缩略图]**&#x200B;步骤的缩略图参数中的值必须与 **[!UICONTROL Dynamic Media 流程图像资产]**&#x200B;步骤中的缩略图参数相匹配。

1. 点按 **[!UICONTROL 保存]** 以保存对工作流所做的更改。

### 增加或减少显示的Dynamic Media图像预设数 {#increasing-or-decreasing-the-number-of-image-presets-that-display}

在预览资产时，您创建的图像预设可以作为动态演绎版使用。 AEM在从以下位置查看资产时，会显示各种动态演绎版 **[!UICONTROL 详细信息视图>演绎版]**. 您可以增加或减少显示的演绎版限制。

**要增加或减少显示的Dynamic Media图像预设数**:

1. 导航到 **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 导航到位于的图像预设列表节点 `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![increase_deximentumberofimagpresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. 在 **[!UICONTROL 限制]** 属性，请更改 **[!UICONTROL 值]**，默认情况下，该值设置为15，即为所需的数字。
1. 导航到位于的图像预设数据源 `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. 在limit属性中，将数字更改为所需的数字，例如 `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 点按 **[!UICONTROL 全部保存]**.

### 创建Dynamic Media图像预设 {#creating-image-presets}

通过创建Dynamic Media图像预设，您可以在预览或发布图像时将这些设置应用到任何图像。

>[!NOTE]
>
>如果您使用Internet Explorer 9，则创建的预设在保存后不会立即显示在预设列表中。 要解决此问题，请禁用IE9的缓存。

如果您打算支持摄取AI、PDF和EPS文件，以便生成这些文件格式的动态呈现版本，则可能需要在创建图像预设之前查看以下信息。\
请参阅 [Adobe Illustrator(AI)、Postscript(EPS)和PDF文件格式](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

如果您打算支持摄取INDD文件以便生成此文件格式的动态演绎版，则可能需要在创建图像预设之前查看以下信息。  请参阅 [InDesign(INDD)文件格式](#indesign-indd-file-format).

>[!NOTE]
>
>要创建Dynamic Media图像预设，您必须以AEM管理员或Admin Console管理员的身份拥有管理员权限。

**创建Dynamic Media图像预设**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按 **[!UICONTROL 工具]** 图标，然后导航到 **[!UICONTROL 资产>图像预设]**.
1. 点按 **[!UICONTROL 创建]**.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >要使此图像预设具有响应性，请擦除&#x200B;**[!UICONTROL 宽度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;字段中的值，并将其留空。

1. 在 **[!UICONTROL 编辑图像预设]** ，在 **[!UICONTROL 基本]** 和 **[!UICONTROL 高级]** 选项卡，包括名称。 图像预设选项中概 [述了这些选项](#image-preset-options)。 预设显示在左窗格中，并可以与其他资产一起动态使用。

   ![chlimage_1-497](assets/chlimage_1-497.png)

1. 单击“**[!UICONTROL 保存]**”。

### 创建响应式图像预设 {#creating-a-responsive-image-preset}

要创建响应式图像预设，请执行 [创建图像预设](#creating-image-presets). 在 **[!UICONTROL 编辑图像预设]** 窗口中，拭除这些值并将其留空。

将它们留空会告知AEM此图像预设是响应式的。 您可以根据需要调整其他值。

![chlimage_1-498](assets/chlimage_1-498.png)

>[!NOTE]
>
>为了查看 **[!UICONTROL URL]** 和 **[!UICONTROL RESS]** 按钮时，必须发布资产。
>
>在Dynamic Media - Scene7模式下，图像预设和图像资产会自动发布。
>
>在Dynamic Media — 混合模式下，您必须手动发布图像预设和图像资产。

### “图像预设”选项 {#image-preset-options}

创建或编辑图像预设时，您可以使用此部分中描述的选项。 此外，Adobe还建议使用以下三个 *最佳实践* 选项选择开始：

* **[!UICONTROL 格式]** (**[!UICONTROL 基本]** 选项卡) — 选择 **[!UICONTROL JPEG]** 或其他符合您要求的格式。 所有 Web 浏览器都支持 JPEG 图像格式；它可以在小文件大小和图像质量之间实现良好的平衡。但是，JPEG 格式图像使用有损压缩方案，如果压缩设置太低，则会引入不需要的图像伪影。因此，Adobe 建议将压缩质量设置为 75。此设置在图像质量和小文件大小之间提供了良好的平衡。
* **[!UICONTROL 启用简单锐化]**  — 不选择 **[!UICONTROL 启用简单锐化]** （此锐化滤镜提供的控件比“USM锐化”设置少。）
* **[!UICONTROL 锐化：重新取样模式]**  — 选择 **[!UICONTROL 锐化2]**.

#### 基本选项卡选项 {#basic-tab-options}

<table> 
 <tbody> 
  <tr> 
   <td><strong>字段</strong></td>
   <td><strong>描述</strong></td>
  </tr> 
  <tr> 
   <td><strong>名称</strong></td>
   <td>请输入一个描述性名称，且不含任何空格。在名称中包含图像大小规格可帮助用户识别此图像预设。</td>
  </tr>
  <tr> 
   <td><strong>宽度和高度</strong></td>
   <td>输入传送图像的大小（以像素为单位）。 宽度和高度必须大于0像素。 如果任一值为0，则不会创建预设。 如果两个值均为空，则会创建响应式图像预设。</td>
  </tr> 
  <tr> 
   <td><strong>格式</strong></td>
   <td><p>从菜单中选择格式。</p> <p>选择 <strong>JPEG</strong> 提供了以下其他选项：</p>
    <ul> 
     <li><strong>质量</strong>  — 控制JPEG压缩级别。 此设置会影响文件大小和图像质量。 JPEG质量比例尺为1-100。 拖动滑块时，可看到缩放比例。</li> 
     <li><strong>启用JPG色度缩减采样</strong>  — 由于眼睛对高频颜色信息的敏感程度低于高频亮度，JPEG图像将图像信息分为亮度和颜色分量。 当JPEG图像被压缩时，亮度分量将保留全分辨率，而颜色分量则通过将像素组平均在一起来缩减采样。 缩减采样会将数据量减少一半或三分之一，几乎不会影响感知质量。 缩减采样不适用于灰度图像。 此技术可减少对对比度高的图像（例如，叠加有文本的图像）有用的压缩量。</li>
    </ul>
    <div>
      选择
     <strong>GIF</strong> 或
     <strong>GIFAlpha</strong> 提供这些附加
     <strong>GIF颜色量化</strong> 选项：
    </div>
    <ul> 
     <li><strong>类型 </strong> — 选择 <strong>自适应</strong> （默认）、 <strong>Web</strong>或 <strong>Macintosh</strong>. 如果您选择 <strong>GIFAlpha</strong>，则“ Macintosh”选项不可用。</li>
     <li><strong>Dither</strong>  — 选择 <strong>扩散</strong> 或 <strong>关闭</strong>.</li>
     <li><strong>颜色数量 </strong> — 输入一个介于2到256之间的数字。</li>
     <li><strong>颜色列表</strong>  — 输入以逗号分隔的列表。 例如，对于白色、灰色和黑色，输入000000,888888,ffffff。</li>
    </ul> 
    <div>
      选择
     <strong>PDF</strong>,
     <strong>TIFF</strong>或
     <strong>TIFFAlpha</strong> 提供了以下其他选项：
    </div>
    <ul>
     <li><strong>压缩</strong>  — 选择压缩算法。 PDF的算法选项包括 <strong>无</strong>, <strong>Zip</strong>和 <strong>Jpeg</strong>;TIFF <strong>无</strong>, <strong>LZW</strong>, <strong>Jpeg</strong>和 <strong>Zip</strong>;和AlphaTIFF <strong>无</strong>, <strong>LZW</strong>和 <strong>Zip</strong>.</li>
    </ul> <p>选择 <strong>PNG</strong>, <strong>带Alpha的PNG，</strong> 或 <strong>EPS</strong> 不提供其他选项。</p> </td>
  </tr>
  <tr>
   <td><strong>锐化</strong></td>
   <td>选择 <strong>启用简单锐化</strong> 选项，以在进行所有缩放后对图像应用基本锐化滤镜。锐化有助于弥补在以不同大小显示图像时可能产生的模糊。 </td>
  </tr>
 </tbody>
</table>

#### 高级选项卡选项 {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>字段</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>色彩空间</strong></td>
   <td>选择 <strong>RGB, CMYK，</strong> 或 <strong>灰度</strong> 的颜色。</td>
  </tr>
  <tr>
   <td><strong>颜色配置文件</strong></td>
   <td>如果资产与工作配置文件不同，请选择资产应转换到的输出色彩空间配置文件。</td>
  </tr>
  <tr>
   <td><strong>渲染方法</strong></td>
   <td>您可以覆盖默认的渲染意图。 渲染意图决定了目标颜色配置文件中无法重现的颜色（超出色域）会发生什么情况。 如果“渲染意图”与ICC配置文件不兼容，则将忽略该“渲染意图”。
    <ul> 
     <li>选择 <strong>知觉</strong> 当原始图像中的一个或多个颜色超出目标色彩空间的色域时，将一个色彩空间的总色域压缩为另一个色彩空间。</li>
     <li>选择 <strong>相对比色</strong> 当当前色彩空间中的颜色在目标色彩空间中超出色域时，您希望将其映射到目标色彩空间色域中最接近的可能颜色，而不影响任何其他颜色。 </li>
     <li>选择 <strong>饱和度</strong> 在转换为目标色彩空间时重现原始图像色彩饱和度。 </li>
     <li>选择 <strong>绝对比色</strong> 以完全匹配颜色，而不调整会改变图像亮度的白点或黑点。</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>黑场补偿</strong></td>
   <td>如果输出配置文件支持此功能，请选择此选项。 如果黑点补偿与指定的ICC配置文件不兼容，则忽略该补偿。</td>
  </tr>
  <tr>
   <td><strong>仿色</strong></td>
   <td>选择此选项可能会避免或减少色带伪影。 </td>
  </tr>
  <tr>
   <td><strong>锐化类型</strong></td>
   <td><p>选择 <strong>无</strong>, <strong>锐化</strong>或 <strong>钝化蒙版</strong>. </p>
    <ul>
     <li>选择 <strong>无</strong> 禁用锐化。</li>
     <li>选择 <strong>锐化 </strong>在进行所有缩放后，对图像应用基本锐化滤镜。 锐化有助于弥补在以不同大小显示图像时可能产生的模糊。 </li>
     <li>选择<strong> 钝化蒙版</strong> 对最终的缩减采样图像微调锐化滤镜效果。 您可以控制效果的强度、效果的半径（以像素为单位）以及将被忽略的对比度阈值。 此效果使用与 Photoshop 的“钝化蒙蔽”滤镜相同的选项。</li>
    </ul> <p>在 <strong>钝化蒙版</strong>，您可以使用以下选项：</p>
    <ul> 
     <li><strong>金额</strong>  — 控制对边缘像素应用的对比度量。 默认的实数值为1.0。对于高分辨率图像，最高可将其增加到5.0。请考虑使用“数量”来测量滤镜强度。</li>
     <li><strong>半径</strong>  — 确定边缘像素周围影响锐化的像素数。 对于高分辨率图像，请输入一个介于1到2之间的实数。 低值仅锐化边缘像素；高值可锐化较宽范围的像素。 正确的值取决于图像的大小。</li>
     <li><strong>阈值</strong>  — 确定在应用USM锐化滤镜时要忽略的对比度范围。 换句话说，此选项确定锐化的像素与周围区域必须有多大的不同，才会被视为边缘像素并进行锐化。 为避免引入杂色，请尝试使用2到20之间的整数值。 </li>
     <li><strong>应用于</strong>  — 确定钝化是否适用于每种颜色或亮度。</li>
    </ul>
    <div>
      有关锐化的描述，请参阅  
     <a href="https://experienceleague.adobe.com/docs/experience-manager-64/assets/sharpening_images.pdf">Adobe Dynamic Media Classic图像质量和锐化最佳实践</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>重新取样模式</strong></td>
   <td>选择 <strong>重新取样模式</strong> 选项。 在缩减像素采样时，以下选项会锐化图像：
    <ul>
     <li><strong>双线性</strong>  — 最快的重新取样方法。会出现一些锯齿伪像。</li>
     <li><strong>两次立方</strong>  — 提高CPU使用率，但生成较锐利的图像，出现的锯齿伪像较少。</li>
     <li><strong>锐化2</strong>  — 生成的结果比两次立方比较锐利，但CPU成本更高。</li>
     <li><strong>双锐</strong>  — 选择Photoshop默认重采样器以减小图像大小，该方法称为 <strong>双比克锐化</strong> 在Adobe Photoshop。</li>
     <li><strong>每种颜色</strong> 和 <strong>亮度</strong>  — 每种方法都可以基于颜色或亮度。 默认情况下 <strong>每种颜色</strong> 中。</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>打印分辨率</strong></td>
   <td>选择打印此图像的分辨率；默认为72像素。</td>
  </tr>
  <tr>
   <td><strong>图像修饰符</strong></td>
   <td><p>除了UI中提供的常见图像设置之外，Dynamic Media还支持您在 <strong>图像修饰符</strong> 字段。 这些参数在 <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html">图像服务器协议命令参考</a>.</p> <p>重要信息：API中列出的以下功能不受支持：</p>
    <ul>
     <li>基本模板和文本渲染命令： <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> 和 <code>textPs=</code></li>
     <li>本地化命令： <code>locale=</code> 和 <code>req=xlate</code></li>
     <li><code>req=set</code> 不可用于常规用法。</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>非核心Dynamic Media服务：SVG、图像渲染和Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## 使用图像修饰符定义图像预设选项 {#defining-image-preset-options-with-image-modifiers}

除了 **[!UICONTROL 基本]** 和 **[!UICONTROL 高级]** 选项卡上，您可以定义图像修饰符，以便在定义图像预设时提供更多选项。 图像渲染依赖于Dynamic Media图像渲染API。 API在 [HTTP协议参考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/c-http-protocol-reference.html).

以下是一些使用图像修饰符可以执行的操作的基本示例。

>[!NOTE]
>
>一些图像修饰符 [无法在AEM中使用](#advanced-tab-options).

* [op_invert](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html)  — 反转每个颜色分量以获得负图像效果。

   ```xml
   &op_invert=1
   ```

   ![chlimage_1-499](assets/chlimage_1-499.png)

* [op_blur](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html)  — 对图像应用模糊滤镜。

   ```xml
   &op_blur=25
   ```

   ![chlimage_1-500](assets/chlimage_1-500.png)

* 组合命令 — op_blur和op-invert

   ```xml
   &op_invert=1&op_blur=25
   ```

   ![chlimage_1-501](assets/chlimage_1-501.png)

* [op_brightness](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html)  — 降低或增加亮度。

   ```xml
   &op_brightness=75
   ```

   ![chlimage_1-502](assets/chlimage_1-502.png)

* [opac](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html)  — 调整图像不透明度。 用于降低前景不透明度。

   ```xml
   opac=50
   ```

   ![chlimage_1-503](assets/chlimage_1-503.png)

## 编辑图像预设 {#modifying-image-presets}

**编辑图像预设**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按 **[!UICONTROL 工具]** 图标，然后导航到 **[!UICONTROL 资产>图像预设]**.

   ![chlimage_1-504](assets/chlimage_1-504.png)

1. 选择预设，然后点按 **[!UICONTROL 编辑]**.
1. 在 **[!UICONTROL 编辑图像预设]** ，然后点按 **[!UICONTROL 保存]**.

## 发布Dynamic Media图像预设 {#publishing-image-presets}

如果您运行的是Dynamic Media — 混合模式，则必须手动发布图像预设。

如果您运行的是Dynamic Media - Scene7模式，则图像预设将自动发布；您无需完成这些步骤。

**要在Dynamic Media中发布图像预设 — 混合模式**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按 **[!UICONTROL 工具]** 图标，然后导航到 **[!UICONTROL 资产>图像预设]**.
1. 从图像预设列表中选择一个或多个图像预设，然后点按 **[!UICONTROL 发布]**.
1. 发布图像预设后，状态将从未发布更改为已发布。

   ![chlimage_1-505](assets/chlimage_1-505.png)

## 删除Dynamic Media图像预设 {#deleting-image-presets}

1. 在AEM中，点按AEM徽标以访问全局导航控制台。
1. 点按 **[!UICONTROL 工具]** 图标，然后导航到 **[!UICONTROL 资产>图像预设]**.
1. 选择预设，然后点按 **[!UICONTROL 删除]**. Dynamic Media会向您确认是否要删除它。 点按 **[!UICONTROL 删除]**.
