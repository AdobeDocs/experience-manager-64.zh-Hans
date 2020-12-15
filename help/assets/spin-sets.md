---
title: 旋转集
seo-title: 旋转集
description: 了解如何在动态媒体中处理旋转集
seo-description: 了解如何在动态媒体中处理旋转集
uuid: a80a0491-6500-463a-83c4-ff4b90a88182
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: afacb3ad-e4ad-4d06-a898-f3f2da8bbb64
translation-type: tm+mt
source-git-commit: f86765084981cda1e255834bf83be0ff8a7a2a02
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 28%

---


# 旋转集 {#spin-sets}

旋转集模拟旋转对象的真实动作，以便于进行检查。通过旋转集，可以从任意角度查看项目，从而获取任意角度的重要可视细节。

旋转集模拟 360 度全方位查看体验。Dynamic Media 提供单轴旋转集，查看者可在该旋转集中旋转项目。另外，用户可以自由缩放和平移任何视图，只需几次简单的鼠标单击操作即可实现。这样，用户就可以从任何特定视角更仔细地检查项目。

旋转集由带有单词&#x200B;**[!UICONTROL SPINSET]**&#x200B;的横幅来指定。此外，如果旋转集已发布，则横幅上会显示由&#x200B;**[!UICONTROL World]**&#x200B;图标指示的发布日期以及上次修改日期，并显示由&#x200B;**[!UICONTROL Pencil]**&#x200B;图标指示。

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>有关资产用户界面的信息，请参阅[使用触屏UI管理资产](managing-assets-touch-ui.md)。

## 快速开始:旋转集{#quick-start-spin-sets}

要快速设置和运行旋转集，请遵循以下工作流：

1. [上传多个视图的图像。](#uploading-assets-for-spin-sets)

   对于一维旋转集，一个项目至少需要8-12张照片；对于二维旋转集，一个项目至少需要16-24张照片。拍摄时必须定期进行，以给人以项目正在旋转和翻动的印象。例如，如果一维旋转集包含12个镜头，则对每个镜头将项目旋转30度(360/12)。

1. [创建旋转集。](#creating-spin-sets)

   要创建旋转集，请选择&#x200B;**[!UICONTROL 创建>旋转集]**，然后命名旋转集，选择资产，然后按照图像的显示顺序对图像进行排序。

   请参阅[使用选择器](working-with-selectors.md)。

   >[!NOTE]
   >
   >您还可以通过[批集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)自动创建旋转集。
   >
   >*批集由IPS（图像生产系统）创建，作为资产摄取的一部分，并且仅在Dynamic Media-Scene7模式下可用*。

1. 根据需要设置[旋转集查看器预设](managing-viewer-presets.md)。

   管理员可以创建或修改旋转集查看器预设。 要查看带有查看器预设的旋转集，请选择旋转集，在左边栏下拉菜单中，选择&#x200B;**[!UICONTROL 查看器]**。

   请参阅&#x200B;**[!UICONTROL 工具>资产>查看器预设]**&#x200B;以创建或编辑查看器预设。

   请参阅[添加和编辑查看器预设。](managing-viewer-presets.md)

1. [查看旋转集](#viewing-spin-sets)。

   您可以通过三种不同的方式视图和访问通过批集预设创建的集。 （使用批集预设创建的集合，在用户界面中执行&#x200B;*不*&#x200B;操作。）

1. [预览旋转集。](previewing-assets.md)

   选择旋转集，之后您便可以进行预览。旋转该旋转集。您可以从左边栏下拉菜单中的&#x200B;**[!UICONTROL 查看器]**&#x200B;菜单中选择不同的查看器。

1. [发布旋转集。](publishing-dynamicmedia-assets.md)

   发布旋转集时，将激活图像在旋转集中的显示顺序。 请务必对它们进行排序，使旋转保持360度的平滑视图。**[!UICONTROL URL]** 和 **** 嵌入字符串。此外，您必须[发布查看器预设](managing-viewer-presets.md)。

1. [将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md)或者[嵌入视频查看器或图像查看器](embed-code.md)。

   AEM Assets为旋转集创建URL调用，并在您发布旋转集后将其激活。您可以在预览资产时复制这些URL。或者，您也可以将它们嵌入到您的网站上。

   选择旋转集，然后在左边栏下拉菜单中选择&#x200B;**[!UICONTROL 查看器]**。

   请参 [阅将旋转集关联到网页](linking-urls-to-yourwebapplication.md)[和嵌入视频查看器或图像查看器](embed-code.md)。

如果需要，您可以[编辑旋转集](#editing-spin-sets)。 此外，还可以视图和编辑[旋转集属性](managing-assets-touch-ui.md#editing-properties)。

## 上传旋转集的资产 {#uploading-assets-for-spin-sets}

对于一维旋转集，一个项目至少需要8-12张照片；对于二维旋转集，一个项目至少需要16-24张照片。拍摄时必须定期进行，以给人以项目正在旋转和翻动的印象。例如，如果一维旋转集包含12个镜头，则对每个镜头将项目旋转30度(360/12)。

为旋转集上传图像的方法与[在 AEM Assets 中上传任何其他资产](managing-assets-touch-ui.md)的方法相同。

### 旋转集图像拍摄准则 {#guidelines-for-shooting-spin-set-images}

以下是关于旋转集图像的一些最佳实践。一般而言，旋转集中的图像越多，图像的旋转效果越好。但是，在旋转集中包含很多图像也会使加载图像所需的时间变长。在拍摄用于旋转集的图像时，AEM 建议遵循以下准则：

* 在一维旋转集中至少使用8-12幅图像，在二维旋转集中至少使用16-24幅图像。必须至少使用8张图像才能进行360度旋转。一维旋转集比较常见，因为创建二维旋转集非常繁琐。
* 使用无损格式；建议使用 TIFF 和 PNG。
* 对所有图像使用蒙版，以使项目显示在纯白或其他高对比度的背景中。或者，也可以添加阴影。
* 确保充分突出产品细节，使其成为焦点。
* 拍摄时装的旋转图像时，使用模特道具或真人模特。通常，模特道具会完全遮罩住（使用玻璃材质的模特道具），或者图像中会显示风格化的模特道具/人体模型。您可以通过定义多个角度来创建真人模特展示旋转集。可使用卷尺在地面上标出各个角度，以指导模特行走并目视每个拍摄方向。

## 创建旋转集 {#creating-spin-sets}

旋转集中的图像显示顺序很重要。请务必对它们进行排序，使旋转保持360度的平滑视图。

>[!NOTE]
>
>您还可以通过[批量集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)自动创建旋转集。
>
>批集由IPS（图像生产系统）创建，作为资产摄取的一部分，并且仅在Dynamic Media-Scene7模式下可用。
>
>请参阅[配置Dynamic Media-Scene7模式](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)中的“创建批集预设以自动生成图像集和旋转集”。

**要创建旋转集，请执行以下操作：**

1. 在资产中，导航到要创建旋转集的位置，点按&#x200B;**[!UICONTROL 创建]**，然后选择&#x200B;**[!UICONTROL 旋转集]**。 您还可以从包含资产的文件夹中创建旋转集。

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. 在&#x200B;**[!UICONTROL 旋转集编辑器]**&#x200B;页面的&#x200B;**[!UICONTROL 标题]**&#x200B;字段中，输入旋转集的名称。 该名称会显示在旋转集的横幅中。（可选）输入说明。

   ![chlimage_1-382](assets/chlimage_1-382.png)

   创建旋转集时，您可以更改旋转集缩略图，或允许AEM根据旋转集中的资产自动选择缩略图。 要选择缩略图，请点按&#x200B;**[!UICONTROL 更改缩略图]**。选择任何图像（您也可以导航到其他文件夹以查找图像）。 如果您已选择缩略图，然后决定要AEM从旋转集生成缩略图，请选择&#x200B;**[!UICONTROL 切换到自动缩略图]**。

1. 执行以下操作之一：

   * 在&#x200B;**[!UICONTROL 旋转集编辑器]**&#x200B;页面的左上角附近，点按&#x200B;**[!UICONTROL 添加资产]**。
   * 在&#x200B;**[!UICONTROL 旋转集编辑器]**&#x200B;页面的中间附近，点按&#x200B;**[!UICONTROL 点按以打开资产选择器]**。

   点按以选择要包含在旋转集中的资产。 选定资产上有一个复选标记图标。完成后，在页面右上角附近，点按&#x200B;**[!UICONTROL 选择]**。

   借助资产选择器，您可以通过键入关键字并点按&#x200B;**[!UICONTROL 返回]**&#x200B;来搜索资产。您还可以应用过滤器来优化搜索结果。您可以按路径、收藏集、文件类型和标记进行过滤。选择过滤器，然后点按工具栏上的&#x200B;**[!UICONTROL 过滤器]**&#x200B;图标。要更改视图，请点按页面右上角附近的&#x200B;**[!UICONTROL 视图]**&#x200B;图标，然后点按&#x200B;**[!UICONTROL 列视图]**、**[!UICONTROL 卡视图]**&#x200B;或&#x200B;**[!UICONTROL 列表视图]**。

   请参阅[使用选择器](working-with-selectors.md)。

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 将资产添加到资产集时，资产会按字母数字顺序自动添加。 在添加资产后，您可以手动对资产重新排序或排序。 如有必要，请将资产的&#x200B;**[!UICONTROL Reorder]**&#x200B;图标拖动到资产文件名的右侧，以在设置的列表上或下重新排序图像。

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. （可选）执行以下操作之一：

   * 要删除图像，请选择该图像，然后点按&#x200B;**[!UICONTROL 删除资产]**。
   * 要应用预设，请点按页面右上角附近的&#x200B;**[!UICONTROL 预设]**，然后选择一个预设以一次应用于所有资产。

1. 点按&#x200B;**[!UICONTROL 保存]**。您新创建的旋转集将显示在创建该旋转集的文件夹中。

## 查看旋转集{#viewing-spin-sets}

您可以在用户界面中创建旋转集，也可以使用[批集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)自动创建旋转集。 但是，使用批集预设创建的集合，在用户界面中不显示&#x200B;*。*&#x200B;您可以通过三种不同方式访问通过批集预设创建的集。 （即使您在用户界面中创建了旋转集，这些方法也可用。）

您还可以通过用户界面视图集，如[编辑旋转集](#editing-spin-sets)中所述。

**视图旋转集：**

1. 打开单个资产的属性时。 属性指明所选资产是成员（位于&#x200B;**[!UICONTROL 集成员]**&#x200B;下）的组。 点按集的名称可查看整个集。

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. 来自任何集的成员图像。选择&#x200B;**[!UICONTROL 集]**&#x200B;菜单以显示资产所属的集。

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. 在搜索中，您可以选择&#x200B;**[!UICONTROL 过滤器]**，然后展开&#x200B;**[!UICONTROL Dynamic Media]**&#x200B;并选择&#x200B;**[!UICONTROL 集]**。

   搜索会返回在用户界面中手动创建或通过批集预设自动创建的匹配集。 对于自动集，搜索查询使用具有&#x200B;]**搜索条件的**[!UICONTROL &#x200B;开始进行，该搜索条件不同于基于使用&#x200B;**[!UICONTROL 包含]**&#x200B;搜索条件的AEM搜索。 将过滤器设置为&#x200B;**[!UICONTROL Sets]**&#x200B;是搜索自动集的唯一方法。

   ![chlimage_1-386](assets/chlimage_1-386.png)

## 编辑旋转集 {#editing-spin-sets}

您可以对旋转集执行各种编辑任务，如：

* 向旋转集中添加图像。
* 对旋转集中的图像进行重新排序。
* 删除旋转集中的资产。
* 应用查看器预设。
* 删除旋转集。

**要编辑旋转集，请执行以下操作：**

1. 执行下列任一操作：

   * 将鼠标悬停在旋转集资产上，然后点按&#x200B;**[!UICONTROL 编辑]**（铅笔图标）。
   * 将指针悬停在旋转集资产上，点按&#x200B;**[!UICONTROL 选择]**（复选标记图标），然后点按工具栏上的&#x200B;**[!UICONTROL 编辑]**。
   * 点按旋转集资产，然后点按工具栏上的&#x200B;**[!UICONTROL 编辑]**（铅笔图标）。

1. 要编辑旋转集，请执行以下任意操作：

   * 要对图像重新排序，请将图像拖到新位置（选择重新排序图标以移动项目）。
   * 要按升序或降序对项目排序，请点按列标题。
   * 要添加资产或更新现有资产，请点按&#x200B;**[!UICONTROL 添加资产]**。 导航到资产，选择它，然后点按右上角附近的&#x200B;**[!UICONTROL 选择]**。
如果通过将缩略图替换为其他图像来删除AEM用的缩略图图像，则仍会显示原始资产。
   * 要删除资产，请选择该资产，然后点按&#x200B;**[!UICONTROL 删除资产]**。
   * 要应用预设，请点按&#x200B;**[!UICONTROL 预设]**&#x200B;图标，然后选择预设。
   * 要删除整个旋转集，请导航到该旋转集，将其选中，然后选择&#x200B;**[!UICONTROL 删除]**

      >[!NOTE]
      >* 您可以通过导航到旋转集来编辑旋转集中的图像，点按左边栏中的&#x200B;**[!UICONTROL 设置成员]**，然后点按单个资产上的&#x200B;**[!UICONTROL 编辑]**（铅笔图标）以打开编辑窗口。


1. 完成编辑后，单击&#x200B;**[!UICONTROL 保存]**。

## 预览旋转集 {#previewing-spin-sets}

请参阅[预览资产](previewing-assets.md)。

## 发布旋转集 {#publishing-spin-sets}

请参阅[发布资产](publishing-dynamicmedia-assets.md)。
