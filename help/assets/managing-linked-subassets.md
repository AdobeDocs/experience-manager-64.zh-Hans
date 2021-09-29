---
title: 管理复合资产并生成子资产。
description: 了解如何从InDesign、Adobe Illustrator和Photoshop文件中创建对 [!DNL Experience Manager] 资产的引用。 另外，了解如何使用页面查看器功能查看多页面文件的各个页面。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 1%

---

# 使用子资产管理复合资产 {#managing-compound-assets}

Adobe Experience Manager Assets可以识别上传的文件是否包含对存储库中已存在资产的引用。 此功能仅适用于支持的文件格式。 如果上传的资产包含对[!DNL Experience Manager]资产的任何引用，则会在上传的资产和引用的资产之间创建双向链接。

除了消除冗余外，在Adobe Creative Cloud应用程序中引用[!DNL Experience Manager]资产还可以增强协作，并提高用户的效率和工作效率。

[!DNL Experience Manager] 资产支持 **双向引用**。您可以在上传文件的资产详细信息页面中找到引用的资产。 此外，您还可以在引用资产的资产详细信息页面中查看[!DNL Experience Manager]资产的引用文件。

引用会根据引用资产的路径、文档ID和实例ID进行解析。

## Adobe Illustrator:将资产添加为引用 {#refai}

您可以从Adobe Illustrator文件中引用现有[!DNL Experience Manager]资产。

1. 使用[[!DNL Experience Manager] 桌面应用程序](https://helpx.adobe.com/cn/experience-manager/desktop-app/aem-desktop-app.html)，将[!DNL Experience Manager]资产存储库作为驱动器装载到本地计算机上。 在已装载的驱动器中，导航到要引用的资产的位置。
1. 将资产从安装的驱动器拖到 Illustrator 文件。
1. 将Illustrator文件保存到已装载的驱动器，或将[上载](managing-assets-touch-ui.md#uploading-assets)到[!DNL Experience Manager]存储库。
1. 工作流完成后，转到资产的资产详细信息页面。 对现有[!DNL Experience Manager]资产的引用列在&#x200B;**[!UICONTROL 引用]**&#x200B;列的&#x200B;**[!UICONTROL 依赖项]**&#x200B;下。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 在&#x200B;**[!UICONTROL Dependencies]**&#x200B;下显示的引用资产也可由当前资产以外的文件引用。 要查看资产引用文件的列表，请单击&#x200B;**[!UICONTROL 依赖项]**&#x200B;下的资产。

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 单击工具栏中的&#x200B;**[!UICONTROL 查看属性]**&#x200B;图标。 在属性页面中，引用当前资产的文件列表显示在&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡的&#x200B;**[!UICONTROL References]**&#x200B;列下。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign:将资产添加为引用 {#add-aem-assets-as-references-in-adobe-indesign}

要从InDesign文件中引用[!DNL Experience Manager]资产，请将[!DNL Experience Manager]资产拖到InDesign文件中，或将InDesign文件导出为ZIP文件。

[!DNL Experience Manager]资产中已存在引用的资产。 您可以通过[配置InDesign服务器](indesign.md)提取子资产。 InDesign文件中的嵌入资产将作为子资产进行提取。

>[!NOTE]
>
>如果InDesign服务器已代理，则InDesign文件的预览会嵌入到其XMP元数据中。 在这种情况下，并非明确需要缩略图提取。 但是，如果InDesign服务器未代理，则必须为InDesign文件显式提取缩略图。

上传INDD文件后，将通过查询存储库中具有`xmpMM:InstanceID`和`xmpMM:DocumentID`属性的资产来获取引用。

### 通过拖动资产创建引用 {#create-references-by-dragging-aem-assets}

此过程与[将资产添加为Adobe Illustrator](#refai)中的引用类似。

### 通过导出ZIP文件创建对资产的引用 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. 执行[创建工作流模型](/help/sites-developing/workflows-models.md)中的步骤，以创建新工作流。
1. 使用Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html)的[包功能导出文档。Adobe InDesign可以将文档和链接的资产作为包导出。 在这种情况下，导出的文件夹包含一个`Links`文件夹，其中包含InDesign文件中的子资产。 `Links`文件夹与INDD文件位于同一文件夹中。
1. 创建ZIP文件并将其上传到[!DNL Experience Manager]存储库。
1. 启动 Unarchiver 工作流。
1. 工作流完成后，Links文件夹中的引用会自动作为子资产进行引用。要查看引用的InDesign列表，请导航到资产的资产详细信息页面，并关闭[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

## Adobe Photoshop:将资产添加为引用 {#refps}

1. 使用WebDav客户端，将[!DNL Experience Manager]资产作为驱动器进行装载。
1. 要在Photoshop文件中创建对[!DNL Experience Manager]资产的引用，请使用Photoshop中的“置入链接”功能导航到已装载驱动器中的相应资产。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 将Photoshop文件保存到已装载的驱动器，或将](managing-assets-touch-ui.md#uploading-assets)上载到[!DNL Experience Manager]存储库。[
1. 工作流完成后，对现有[!DNL Experience Manager]资产的引用将列在资产详细信息页面中。

   要查看引用的资产，请关闭资产详细信息页面中的[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

1. 引用的资产还包含引用这些资产的资产列表。要查看引用的资产列表，请导航到资产详细信息页面并关闭[边栏](/help/sites-authoring/basic-handling.md#rail-selector)。

>[!NOTE]
>
>复合资产中的资产还可以根据其文档ID和实例ID进行引用。 此功能仅在Adobe Illustrator和Adobe Photoshop版本中可用。 对于其他资产，则会按照主复合资产中链接资产的相对路径进行引用，这与在AEM早期版本中一样。

## 创建子资产 {#generate-subassets}

对于多页格式的受支持资产(PDF文件、AI文件、Microsoft PowerPoint和Apple Keynote文件以及Adobe InDesign文件),[!DNL Experience Manager]可以生成与原始资产的每个单独页面对应的子资产。 这些子资产与&#x200B;*父*&#x200B;资产相关联，有助于进行多页面查看。 出于所有其他目的，子资产会像在AEM中处理常规资产一样处理。

默认情况下，子资产生成处于禁用状态。 要启用子资产生成，请执行以下步骤：

1. 以管理员身份登录Experience Manager。 访问&#x200B;**[!UICONTROL 工具>工作流>模型]**。
1. 选择&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流，然后单击&#x200B;**[!UICONTROL 编辑]**。
1. 单击&#x200B;**[!UICONTROL 切换侧面板]**&#x200B;并找到&#x200B;**[!UICONTROL 创建子资产]**&#x200B;步骤。 将步骤添加到工作流。 单击&#x200B;**[!UICONTROL 同步]**。

要生成子资产，请执行以下操作之一：

* 新资产：[!UICONTROL  DAM更新资产]工作流会对上传到AEM的任何新资产执行。 子资产会为新的多页面资产自动生成。
* 现有的多页资产：按照以下任一步骤手动执行[!UICONTROL  DAM更新资产]工作流：

   * 选择资产并单击[!UICONTROL 时间轴]以打开左侧面板。 或者，使用键盘快捷键`alt + 3`。 单击[!UICONTROL 启动工作流]，选择[!UICONTROL DAM更新资产]，单击[!UICONTROL 启动]，然后单击[!UICONTROL 继续]。
   * 选择资产，然后单击工具栏中的[!UICONTROL 创建>工作流]。 在弹出对话框中，选择[!UICONTROL DAM更新资产]工作流，单击[!UICONTROL 启动]，然后单击[!UICONTROL 继续]。

特别是对于Microsoft Word文档，请执行&#x200B;**[!UICONTROL DAM解析Word文档]**&#x200B;工作流。 它从Microsoft Word文档的内容生成`cq:Page`组件。 从文档提取的图像将从`cq:Page`组件中引用。 即使禁用子资产生成，也会提取这些图像。

## 查看子资产 {#viewing-subassets}

只有在生成子资产并且该子资产可用于选定的多页面资产时，才会显示子资产。 要查看生成的子资产，请打开多页面资产。 在页面的左上角区域，单击![左边栏图标](assets/do-not-localize/aem_leftrail_contentonly.png)，然后单击列表中的&#x200B;**[!UICONTROL 子资产]**。 从列表中选择&#x200B;**[!UICONTROL 子资产]**&#x200B;时。 或者，使用键盘快捷键`alt + 5`。

![查看多页面资产的子资产](assets/view_subassets_simulation.gif)

## 查看多页文件的页面 {#view-pages-of-a-multi-page-file}

您可以使用[!DNL Experience Manager] Assets的页面查看器功能查看多页文件，如PDF、INDD、PPT、PPTX和AI文件。 打开多页资产，然后单击页面左上角的&#x200B;**[!UICONTROL 查看页面]** 。 打开的页面查看器会显示资产的页面以及用于浏览和缩放每个页面的控件。

![查看和查看多页面资产的页面](assets/view_multipage_asset_fmr.gif)

对于InDesign，您可以使用InDesign服务器提取页面。 如果在InDesign文件创建期间保存了页面的预览，则在页面提取时不需要InDesign Server。

以下选项在工具栏、左边栏和“页面查看器”控件中可用：

* **[!UICONTROL 桌面]** 操作来使用桌面应用程序打开或显示特定 [!DNL Experience Manager] 的子资产。如果您使用的是[!DNL Experience Manager]桌面应用程序，请参阅如何[配置桌面操作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)。

* **** 属性选项会打开  特定子资产的属性页面。

* **** 注释选项允许您对特定子资产添加注释。打开父资产进行查看时，系统会收集并显示您在单独的子资产上使用的注释。

* **[!UICONTROL 页面]** 概述选项同时显示所有子资产。

* **** 单击左边栏图标后，左边栏中 ![的时](assets/do-not-localize/aem_leftrail_contentonly.png) 间线选项会显示文件的活动流。

## 最佳实践和限制 {#best-practice-limitation-tips}

* 子资产生成在任何Experience Manager部署上都会占用大量资源。 如果您在上传复杂资产时生成子资产，请在DAM更新资产工作流中添加该步骤。 如果要按需生成子资产，请创建单独的工作流以生成子资产。 利用专用工作流，可跳过DAM更新资产工作流中的其他步骤并保存计算资源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

