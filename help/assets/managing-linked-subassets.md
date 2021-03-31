---
title: 管理复合资产并生成子资产。
description: 了解如何从InDesign、Adobe Illustrator和Photoshop文件中创建对AEM资产的引用。 还了解如何使用页面查看器功能来视图多页文件的各个页面，包括PDF、INDD、PPT、PPTX和AI文件。
contentOwner: AG
feature: 资产管理
role: 业务从业者，管理员
translation-type: tm+mt
source-git-commit: e46a27a1ba11b4a5973eb1ece02c8594b2ae0fc9
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 5%

---


# 使用子资产{#managing-compound-assets}管理复合资产

Adobe Experience Manager(AEM)资产可以识别上传的文件是否包含对存储库中已存在资产的引用。 此功能仅适用于支持的文件格式。 如果上传的资产包含对AEM资产的任何引用，则会在上传的资产和引用的资产之间创建双向链接。

除了消除冗余外，在Adobe Creative Cloud应用程序中引用AEM资产还可增强协作并提高用户的效率和工作效率。

AEM Assets支持&#x200B;**双向引用**。 您可以在已上传文件的资产详细信息页面中查找引用的资产。 此外，您还可以在被引用资产的资产详细信息页面中视图AEM资产的引用文件。

引用会根据引用资产的路径、文档ID和实例ID进行解析。

## Adobe Illustrator:将资产添加为引用{#refai}

您可以从 Adobe Illustrator 文件中引用现有的 AEM Assets。

1. 使用[AEM桌面应用程序](https://helpx.adobe.com/cn/experience-manager/desktop-app/aem-desktop-app.html)将AEM Assets存储库作为驱动器装载到本地计算机上。 在已装载的驱动器中，导航到要引用的资产所在的位置。
1. 将资产从安装的驱动器拖到 Illustrator 文件。
1. 将Illustrator文件保存到已装载的驱动器，或将[upload](managing-assets-touch-ui.md#uploading-assets)上载到AEM存储库。
1. 完成该工作流后，请转到资产的详细信息页面。 对现有AEM资产的引用列在&#x200B;**[!UICONTROL 引用]**&#x200B;列的&#x200B;**[!UICONTROL 依赖项]**&#x200B;下。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 在&#x200B;**[!UICONTROL Dependencies]**&#x200B;下显示的引用资产也可由当前资产以外的文件引用。 要视图引用资产文件的列表，请单击&#x200B;**[!UICONTROL 依赖项]**&#x200B;下方的资产。

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 单击工具栏中的&#x200B;**[!UICONTROL 视图属性]**&#x200B;图标。 在“属性”页中，引用当前资产的文件的列表显示在&#x200B;**[!UICONTROL 基本]**&#x200B;选项卡的&#x200B;**[!UICONTROL 引用]**&#x200B;列下。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign:将资产添加为引用{#add-aem-assets-as-references-in-adobe-indesign}

要从InDesign文件中引用AEM资源，请将AEM资源拖动到InDesign文件或将InDesign文件导出为ZIP文件。

AEM Assets中已存在引用的资产。 您可以通过[配置InDesign服务器](indesign.md)提取子资产。 InDesign文件中的嵌入式资产会提取为子资产。

>[!NOTE]
>
>如果InDesign服务器被代理，则InDesign文件的预览将嵌入到其XMP元数据中。 在这种情况下，缩略图提取不是显式必需的。 但是，如果InDesign服务器未代理，则必须显式提取InDesign文件的缩略图。

上传INDD文件时，通过查询存储库中具有`xmpMM:InstanceID`和`xmpMM:DocumentID`属性的资产来获取引用。

### 通过拖动资产{#create-references-by-dragging-aem-assets}创建引用

此过程类似于[将资产作为引用添加到Adobe Illustrator](#refai)中。

### 通过导出ZIP文件{#create-references-to-aem-assets-by-exporting-a-zip-file}创建对资产的引用

1. 执行[创建工作流模型](/help/sites-developing/workflows-models.md)中的步骤以创建新工作流。
1. 使用Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html)的[包功能导出文档。Adobe InDesign可以将文档和链接的资源作为包导出。 在这种情况下，导出的文件夹包含一个`Links`文件夹，其中包含InDesign文件中的子资产。 `Links`文件夹与INDD文件位于同一文件夹中。
1. 创建 ZIP 文件并将其上传到 AEM 存储库。
1. 启动 Unarchiver 工作流。
1. 该工作流完成后，“链接”文件夹中的引用会自动作为子资产进行引用。要视图引用的资产的列表，请导航到InDesign资产的资产详细信息页面，然后关闭[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

## Adobe Photoshop:将资产添加为引用{#refps}

1. 使用WebDav客户端，将AEM Assets作为驱动器安装。
1. 要在 Photoshop 文件中创建 AEM Assets 引用，请使用 Photoshop 中的“放置链接”功能，导航到已安装驱动器中的相应资产。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 将Photoshop文件保存到已装载的驱动器或将[上载](managing-assets-touch-ui.md#uploading-assets)到AEM存储库。
1. 该工作流完成后，对现有AEM资产的引用会列在资产详细信息页面中。

   要视图引用的资产，请关闭资产详细信息页面中的[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

1. 引用的资产还包含引用这些资产的资产的列表。要视图引用的资产的列表，请导航到资产详细信息页面，然后关闭[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

>[!NOTE]
>
>复合资产中的资产也可以根据其文档ID和实例ID进行引用。 此功能仅在Adobe Illustrator和Adobe Photoshop版本中可用。 对于其他人，与AEM早期版本中一样，引用基于主复合资产中关联资产的相对路径完成。

## 创建子资产{#generate-subassets}

对于多页格式(PDF文件、AI文件、Microsoft PowerPoint和Apple Keynote文件以及Adobe InDesign文件)的受支持资产，AEM可以生成与原始资产的每个单独页面对应的子资产。 这些子资产会链接到&#x200B;*父资产*，以便于多页视图。 出于所有其他目的，子资产都会像AEM中的普通资产一样处理。

默认情况下，子资产生成处于禁用状态。 要启用子资产生成，请执行以下步骤：

1. 以管理员身份登录Experience Manager。 访问&#x200B;**[!UICONTROL 工具>工作流>模型]**。
1. 选择&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流，然后单击&#x200B;**[!UICONTROL 编辑]**。
1. 单击&#x200B;**[!UICONTROL 切换侧面板]**&#x200B;并找到&#x200B;**[!UICONTROL 创建子资产]**&#x200B;步骤。 将步骤添加到工作流。 单击&#x200B;**[!UICONTROL 同步]**。

要生成子资产，请执行以下操作之一：

* 新资产：[!UICONTROL  DAM更新资产]工作流对上传到AEM的任何新资产执行。 子资产是为新的多页资产自动生成的。
* 现有多页资产：按照以下任一步骤手动执行[!UICONTROL  DAM更新资产]工作流：

   * 选择资产，然后单击[!UICONTROL 时间轴]以打开左面板。 或者，使用键盘快捷键`alt + 3`。 单击[!UICONTROL 开始工作流]，选择[!UICONTROL DAM更新资产]，单击[!UICONTROL 开始]，然后单击[!UICONTROL 继续]。
   * 选择资产，然后单击工具栏中的[!UICONTROL 创建>工作流]。 在弹出对话框中，选择[!UICONTROL DAM更新资产]工作流，单击[!UICONTROL 开始]，然后单击[!UICONTROL 继续]。

特别是对于Microsoft Word文档，请执行&#x200B;**[!UICONTROL DAM分析Word文档]**&#x200B;工作流。 它从Microsoft Word文档的内容生成`cq:Page`组件。 从文档提取的图像引用自`cq:Page`组件。 即使禁用了子资产生成功能，也会提取这些图像。

## 视图子资产{#viewing-subassets}

仅当生成了子资产并且这些子资产可用于选定的多页资产时，才会显示子资产。 要视图生成的子资产，请打开多页资产。 在页面的左上角区域，单击![左边栏图标](assets/do-not-localize/aem_leftrail_contentonly.png)，然后单击列表中的&#x200B;**[!UICONTROL 子资产]**。 从列表中选择&#x200B;**[!UICONTROL 子资产]**&#x200B;时。 或者，使用键盘快捷键`alt + 5`。

![视图多页资产的子资产](assets/view_subassets_simulation.gif)

## 视图多页文件{#view-pages-of-a-multi-page-file}的页面

您可以使用AEM Assets的页面查看器功能视图多页文件，如PDF、INDD、PPT、PPTX和AI文件。 打开多页资产，然后单击页面左上角的&#x200B;**[!UICONTROL 视图页面]**。 打开的页面查看器显示资产的页面以及用于浏览和缩放每个页面的控件。

![视图和查看多页资产的页面](assets/view_multipage_asset_fmr.gif)

对于InDesign，您可以使用InDesign服务器提取页面。 如果在创建InDesign文件时保存了预览页面，则页面提取不需要InDesign Server。

以下选项位于工具栏、左边栏和页面查看器控件中：

* **[!UICONTROL 桌面]** 操作，以使用AEM桌面应用程序打开或显示特定的子资产。如果您使用AEM桌面应用程序，请参阅如何[配置桌面操作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2)。

* **[!UICONTROL “属]** 性”选项会打  开特定子资产的“属性”页。

* **[!UICONTROL “注]** 释”选项允许您对特定子资产进行注释。打开父资产进行查看时，您在单独的子资产上使用的注释会一起收集和显示。

* **[!UICONTROL “页]** 面概述”选项同时显示所有子资产。

* **[!UICONTROL 单]** 击“左边栏”图标后，左边 ![栏中](assets/do-not-localize/aem_leftrail_contentonly.png) 的时间线选项显示文件的活动流。

## 最佳实践和限制{#best-practice-limitation-tips}

* 子资产生成可能会对任何Experience Manager部署造成非常大的资源密集。 如果您是在上传复杂资产时生成子资产，请在DAM更新资产工作流中添加该步骤。 如果您要按需生成子资产，请创建单独的工作流以生成子资产。 专用工作流允许您跳过DAM更新资产工作流中的其他步骤并保存计算资源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

