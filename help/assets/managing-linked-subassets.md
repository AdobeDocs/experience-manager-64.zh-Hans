---
title: 管理复合资产并生成子资产。
description: 了解如何创建对 [!DNL Experience Manager] InDesign、Adobe Illustrator和Photoshop文件中的资产。 另外，了解如何使用页面查看器功能查看多页面文件的各个页面。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# 使用子资产管理复合资产 {#managing-compound-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets可以识别上传的文件是否包含对存储库中已存在资产的引用。 此功能仅适用于支持的文件格式。 如果上传的资产包含对 [!DNL Experience Manager] 资产时，会在上传的资产和引用的资产之间创建双向链接。

除了消除冗余外，还引用 [!DNL Experience Manager] Adobe Creative Cloud应用程序中的资产可增强协作，并提高用户的效率和工作效率。

[!DNL Experience Manager] 资产支持 **双向引用**. 您可以在上传文件的资产详细信息页面中找到引用的资产。 此外，您还可以查看的引用文件 [!DNL Experience Manager] 资产。

引用会根据引用资产的路径、文档ID和实例ID进行解析。

## Adobe Illustrator:将资产添加为引用 {#refai}

您可以引用现有 [!DNL Experience Manager] 资产。

1. 使用 [[!DNL Experience Manager] 桌面应用程序](https://helpx.adobe.com/cn/experience-manager/desktop-app/aem-desktop-app.html)，装载 [!DNL Experience Manager] 资产存储库作为本地计算机上的驱动器。 在已装载的驱动器中，导航到要引用的资产的位置。
1. 将资产从已装载的驱动器拖到Illustrator文件。
1. 将Illustrator文件保存到已装载的驱动器，或 [上传](managing-assets-touch-ui.md#uploading-assets) 到 [!DNL Experience Manager] 存储库。
1. 工作流完成后，转到资产的资产详细信息页面。 对现有 [!DNL Experience Manager] 资产列于 **[!UICONTROL 依赖关系]** 在 **[!UICONTROL 引用]** 列。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 在 **[!UICONTROL 依赖关系]** 也可以被当前文件以外的文件引用。 要查看资产的引用文件列表，请在 **[!UICONTROL 依赖关系]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 单击 **[!UICONTROL 查看属性]** 图标。 在属性页面中，引用当前资产的文件列表显示在 **[!UICONTROL 引用]** 列 **[!UICONTROL 基本]** 选项卡。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign:将资产添加为引用 {#add-aem-assets-as-references-in-adobe-indesign}

引用 [!DNL Experience Manager] 从InDesign文件中拖动资产 [!DNL Experience Manager] 资产导出到InDesign文件，或将InDesign文件导出为ZIP文件。

中已存在引用的资产 [!DNL Experience Manager] 资产。 您可以通过 [配置InDesign服务器](indesign.md). InDesign文件中的嵌入资产将作为子资产进行提取。

>[!NOTE]
>
>如果InDesign服务器已代理，则InDesign文件的预览会嵌入到其XMP元数据中。 在这种情况下，并非明确需要缩略图提取。 但是，如果InDesign服务器未代理，则必须为InDesign文件显式提取缩略图。

上传INDD文件后，通过查询具有 `xmpMM:InstanceID` 和 `xmpMM:DocumentID` 属性。

### 通过拖动资产创建引用 {#create-references-by-dragging-aem-assets}

此过程类似于 [在Adobe Illustrator中将资产添加为引用](#refai).

### 通过导出ZIP文件创建对资产的引用 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. 执行 [创建工作流模型](/help/sites-developing/workflows-models.md) 创建新工作流。
1. 使用 [Adobe InDesign的包功能](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) 以导出文档。 Adobe InDesign可以将文档和链接的资产作为包导出。 在这种情况下，导出的文件夹包含 `Links` 文件夹中包含子资产。 的 `Links` 文件夹与INDD文件位于同一文件夹中。
1. 创建ZIP文件并将其上传到 [!DNL Experience Manager] 存储库。
1. 启动Unarchiver工作流。
1. 工作流完成后，Links文件夹中的引用会自动作为子资产进行引用。 要查看引用的资产列表，请导航到InDesign资产的资产详细信息页面，然后关闭 [边栏](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop:将资产添加为引用 {#refps}

1. 使用WebDav客户端，装载 [!DNL Experience Manager] 资产作为驱动器。
1. 创建对的引用 [!DNL Experience Manager] 在Photoshop文件中，使用Photoshop中的“置入链接”功能，导航到已装载驱动器中的相应资产。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 将Photoshop文件保存到已装载的驱动器或 [上传](managing-assets-touch-ui.md#uploading-assets) 到 [!DNL Experience Manager] 存储库。
1. 工作流完成后，对现有 [!DNL Experience Manager] 资产会在资产详细信息页面中列出。

   要查看引用的资产，请关闭 [边栏](/help/sites-authoring/basic-handling.md#rail-selector) （位于资产详细信息页面）。

1. 引用的资产还包含引用这些资产的资产列表。 要查看引用的资产列表，请导航到资产详细信息页面并关闭 [边栏](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>复合资产中的资产还可以根据其文档ID和实例ID进行引用。 此功能仅在Adobe Illustrator和Adobe Photoshop版本中可用。 对于其他资产，则会按照主复合资产中链接资产的相对路径进行引用，这与在AEM早期版本中一样。

## 创建子资产 {#generate-subassets}

对于支持的多页格式资产 — PDF文件、AI文件、Microsoft PowerPoint和Apple Keynote文件，以及Adobe InDesign文件 —  [!DNL Experience Manager] 可以生成与原始资产的每个单独页面对应的子资产。 这些子资产与 *父项* 并促进多页面查看。 出于所有其他目的，子资产会像在AEM中处理常规资产一样处理。

默认情况下，子资产生成处于禁用状态。 要启用子资产生成，请执行以下步骤：

1. 以管理员身份登录Experience Manager。 访问 **[!UICONTROL 工具>工作流>模型]**.
1. 选择 **[!UICONTROL DAM更新资产]** 工作流和单击 **[!UICONTROL 编辑]**.
1. 单击 **[!UICONTROL 切换侧面板]** 并找到 **[!UICONTROL 创建子资产]** 中。 将步骤添加到工作流。 单击&#x200B;**[!UICONTROL 同步]**。

要生成子资产，请执行以下操作之一：

* 新资产：的 [!UICONTROL DAM更新资产] 工作流会对上传到AEM的任何新资产执行。 子资产会为新的多页面资产自动生成。
* 现有的多页资产：手动执行 [!UICONTROL DAM更新资产] 工作流执行以下任一步骤：

   * 选择资产并单击 [!UICONTROL 时间轴] 打开左侧面板。 或者，使用键盘快捷键 `alt + 3`. 单击 [!UICONTROL 启动工作流]，选择 [!UICONTROL DAM更新资产]，单击 [!UICONTROL 开始]，然后单击 [!UICONTROL 继续].
   * 选择资产并单击 [!UICONTROL 创建>工作流] 中。 从弹出对话框中，选择 [!UICONTROL DAM更新资产] 工作流，单击 [!UICONTROL 开始]，然后单击 [!UICONTROL 继续].

特别是对于Microsoft Word文档，请执行 **[!UICONTROL DAM解析Word文档]** 工作流。 它会生成 `cq:Page` 组件。 从文档提取的图像将从 `cq:Page` 组件。 即使禁用子资产生成，也会提取这些图像。

## 查看子资产 {#viewing-subassets}

只有在生成子资产并且该子资产可用于选定的多页面资产时，才会显示子资产。 要查看生成的子资产，请打开多页面资产。 在页面的左上角，单击 ![左边栏图标](assets/do-not-localize/aem_leftrail_contentonly.png) 单击 **[!UICONTROL 子资产]** 列表。 选择 **[!UICONTROL 子资产]** 列表。 或者，使用键盘快捷键 `alt + 5`.

![查看多页面资产的子资产](assets/view_subassets_simulation.gif)

## 查看多页文件的页面 {#view-pages-of-a-multi-page-file}

您可以使用的页面查看器功能查看多页文件，如PDF、INDD、PPT、PPTX和AI文件 [!DNL Experience Manager] 资产。 打开多页面资产并单击 **[!UICONTROL 查看页面]** 的上角。 打开的页面查看器会显示资产的页面以及用于浏览和缩放每个页面的控件。

![查看和查看多页面资产的页面](assets/view_multipage_asset_fmr.gif)

对于InDesign，您可以使用InDesign服务器提取页面。 如果在InDesign文件创建期间保存了页面的预览，则在页面提取时不需要InDesign Server。

以下选项在工具栏、左边栏和“页面查看器”控件中可用：

* **[!UICONTROL 桌面操作]** 使用打开或显示特定子资产 [!DNL Experience Manager] 桌面应用程序。 了解如何 [配置桌面操作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) 如果您使用 [!DNL Experience Manager] 桌面应用程序。

* **[!UICONTROL 属性]** 选项 [!UICONTROL 属性] 页面。

* **[!UICONTROL 注释]** 选项允许您在特定子资产中添加批注。 打开父资产进行查看时，系统会收集并显示您在单独的子资产上使用的注释。

* **[!UICONTROL 页面概述]** 选项可同时显示所有子资产。

* **[!UICONTROL 时间轴]** 选项 ![左边栏图标](assets/do-not-localize/aem_leftrail_contentonly.png) 显示文件的活动流。

## 最佳实践和限制 {#best-practice-limitation-tips}

* 子资产生成在任何Experience Manager部署上都会占用大量资源。 如果您在上传复杂资产时生成子资产，请在DAM更新资产工作流中添加该步骤。 如果要按需生成子资产，请创建单独的工作流以生成子资产。 利用专用工作流，可跳过DAM更新资产工作流中的其他步骤并保存计算资源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

