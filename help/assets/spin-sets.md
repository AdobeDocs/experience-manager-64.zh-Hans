---
title: 旋转集
description: 了解如何在Dynamic Media中使用旋转集。 旋转集模拟旋转对象的真实动作，以从任何角度检查对象。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 47cb6d40-a5c4-4f6a-9794-bd2eddfaa7d0
feature: Spin Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1959'
ht-degree: 6%

---

# 旋转集 {#spin-sets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

旋转集模拟旋转对象的真实动作，以对其进行检查。 旋转集允许从任意角度查看项目，从而从任意角度获取关键的可视细节。

旋转集模拟360度的查看体验。 Dynamic Media提供单轴旋转集，查看器可在其中旋转项目。 此外，用户只需单击几下鼠标即可“自由”缩放和平移任何视图。 这样，用户可以从特定的角度更仔细地检查项目。

旋转集由带有单词的横幅来指定 **[!UICONTROL 旋转集]**. 此外，如果旋转集已发布，则发布日期(由 **[!UICONTROL 世界]** 图标，以及上次修改日期(由 **[!UICONTROL 铅笔]** 图标。

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>有关Assets用户界面的信息，请参阅 [使用触屏UI管理资产](managing-assets-touch-ui.md).

在创建旋转集时，Adobe建议遵循以下最佳实践，并强制实施以下限制：

| 限制类型 | 最佳实践 | 规定的限制 |
| --- | --- | --- |
| 每个2D集的最大行/列数 | 每套12-18页图片 | 1000 |

另请参阅 [Dynamic Media限制](/help/assets/limitations.md).

## 快速入门：旋转集 {#quick-start-spin-sets}

要快速设置并运行旋转集，请遵循以下工作流：

1. [为多个视图上传图像。](#uploading-assets-for-spin-sets)

   对于一维旋转集，您至少需要一个项目8-12张拍照；对于二维旋转集，您至少需要16-24张拍照。 必须定期拍摄这些照片，以给人以项目正在旋转和被翻动的印象。 例如，如果一维旋转集包含12张照片，则对于每张照片，将项目旋转30度(360/12)。

1. [创建旋转集。](#creating-spin-sets)

   要创建旋转集，请选择 **[!UICONTROL 创建>旋转集]** 然后命名该集，选择资产，然后按图像显示顺序对图像进行排序。

   请参阅 [使用选择器](working-with-selectors.md).

   >[!NOTE]
   >
   >您还可以通过 [批次集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*批量集由IPS（图像生产系统）作为资产摄取的一部分创建，并且只能在Dynamic Media - Scene7模式下使用*.

1. 设置 [旋转集查看器预设](managing-viewer-presets.md)，根据需要。

   管理员可以创建或修改旋转集查看器预设。 要查看带有查看器预设的旋转集，请选择旋转集，然后在左边栏下拉菜单中，选择 **[!UICONTROL 查看器]**.

   请参阅 **[!UICONTROL 工具>资产>查看器预设]** 创建或编辑查看器预设。

   请参阅 [添加和编辑查看器预设。](managing-viewer-presets.md)

1. [查看旋转集](#viewing-spin-sets).

   您可以通过三种不同方式查看和访问通过批集预设方式创建的集。 (使用批集预设创建的集，可以 *not* 显示在用户界面中。)

1. [预览旋转集。](previewing-assets.md)

   选择旋转集，您便可以对其进行预览。 旋转旋转集。 您可以从 **[!UICONTROL 查看器]** 菜单（可从左边栏下拉菜单中访问）。

1. [发布旋转集。](publishing-dynamicmedia-assets.md)

   发布旋转集会激活图像在旋转集中的显示顺序。 请务必对其进行排序，以便旋转是一个360度的平滑视图。**[!UICONTROL URL]** 和 **[!UICONTROL 嵌入]** 字符串。 此外，您还必须 [发布查看器预设](managing-viewer-presets.md).

1. [将URL关联到您的Web应用程序](linking-urls-to-yourwebapplication.md) 或 [嵌入视频查看器或图像查看器](embed-code.md).

   AEM Assets会为旋转集创建URL调用，并在您发布旋转集后将其激活。 您可以在预览资产时复制这些URL。 或者，您也可以将它们嵌入到您的网站上。

   选择旋转集，然后在左边栏下拉菜单中选择&#x200B;**[!UICONTROL 查看器]**。

   请参 [阅将旋转集关联到网页](linking-urls-to-yourwebapplication.md)[和嵌入视频查看器或图像查看器](embed-code.md)。

如果需要，您可以 [编辑旋转集](#editing-spin-sets). 此外，您还可以查看和编辑 [旋转集属性](managing-assets-touch-ui.md#editing-properties).

## 为旋转集上传资产 {#uploading-assets-for-spin-sets}

对于一维旋转集，您至少需要一个项目8-12张拍照；对于二维旋转集，您至少需要16-24张拍照。 必须定期拍摄这些照片，以给人以项目正在旋转和被翻动的印象。 例如，如果一维旋转集包含12张照片，则对于每张照片，将项目旋转30度(360/12)。

您可以像上传一样上传旋转集的图像 [上传AEM Assets中的任何其他资产](managing-assets-touch-ui.md).

### 旋转集图像拍摄准则 {#guidelines-for-shooting-spin-set-images}

以下是有关旋转集图像的一些最佳实践。 通常，旋转集中的图像越多，图像的旋转效果越好。 但是，在图像集中包含许多图像也会增加加载图像所花费的时间。 AEM建议为拍摄图像以在旋转集中使用遵循以下准则：

* 在一维旋转集中至少使用8-12幅图像，在二维旋转集中至少使用16-24幅图像。 必须至少8幅图像才能旋转360度。 一维旋转集比较常见，因为创建二维旋转集非常繁琐。
* 使用无损格式；建议使用TIFF和PNG。
* 对所有图像设置蒙版，以便项目显示在纯白色或其他高对比度背景上。 （可选）添加阴影。
* 确保充分突出产品细节并集中注意。
* 用模特道具或模特拍摄时装的旋转图像。 通常，模特人道模型会被完全遮罩（使用玻璃模型模型），或者图像中会显示风格化的模型模型/裁缝。 您可以通过定义角度数来创建模型内旋转集。 用胶带在地板上标出每个角度，以引导模型步进并朝每次拍摄的方向看。

## 创建旋转集 {#creating-spin-sets}

图像在旋转集中的显示顺序很重要。 请务必对其进行排序，以便旋转是一个360度的平滑视图。

>[!NOTE]
>
>您还可以通过[批量集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)自动创建旋转集。
>
>批量集由IPS（图像生产系统）作为资产摄取的一部分创建，并且只能在Dynamic Media - Scene7模式下使用。
>
>请参阅 [配置Dynamic Media - Scene7模式](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

在创建旋转集时，Adobe建议遵循以下最佳实践，并强制实施以下限制：

| 限制类型 | 最佳实践 | 规定的限制 |
| --- | --- | --- |
| 每个2D集的最大行/列数 | 每套12-18页图片 | 1000 |

另请参阅 [Dynamic Media限制](/help/assets/limitations.md).

**要创建旋转集，请执行以下操作：**

1. 在资产中，导航到要创建旋转集的位置，点按 **[!UICONTROL 创建]**，然后选择 **[!UICONTROL 旋转集]**. 您还可以从包含资产的文件夹中创建旋转集。

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. 在 **[!UICONTROL 旋转集编辑器]** 页面，在 **[!UICONTROL 标题]** 字段，输入旋转集的名称。 该名称会显示在旋转集的横幅中。 （可选）输入说明。

   ![chlimage_1-382](assets/chlimage_1-382.png)

   创建旋转集时，您可以更改旋转集缩略图，或允许AEM根据旋转集中的资产自动选择缩略图。 要选择缩略图，请点按 **[!UICONTROL 更改缩略图]**.选择任意图像（您也可以导航到其他文件夹以查找图像）。 如果您选择了缩略图，然后决定让AEM从旋转集中生成缩略图，请选择 **[!UICONTROL 切换到自动缩略图]**.

1. 执行以下任一操作：

   * 在 **[!UICONTROL 旋转集编辑器]** 页面，点按 **[!UICONTROL 添加资产]**.
   * 在 **[!UICONTROL 旋转集编辑器]** 页面，点按 **[!UICONTROL 点按以打开资产选择器]**.

   点按以选择要包含在旋转集中的资产。 选定资产上有一个复选标记图标。完成后，在页面的右上角附近，点按 **[!UICONTROL 选择]**.

   借助资产选择器，您可以通过键入关键字并点按&#x200B;**[!UICONTROL 返回]**&#x200B;来搜索资产。您还可以应用过滤器来优化搜索结果。您可以按路径、收藏集、文件类型和标记进行过滤。选择过滤器，然后点按工具栏上的&#x200B;**[!UICONTROL 过滤器]**&#x200B;图标。要更改视图，请点按页面右上角附近的 **[!UICONTROL 查看]** 图标，然后点按 **[!UICONTROL 列视图]**, **[!UICONTROL 卡片视图]**&#x200B;或 **[!UICONTROL 列表视图]**.

   请参阅 [使用选择器](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 在将资产添加到资产集时，资产会按字母数字顺序自动添加。 您可以在添加资产后手动对资产重新排序或排序。 如有必要，请拖动资产的 **[!UICONTROL 重新排序]** 图标，以在设置列表中对图像进行重新排序。

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. （可选）执行以下任一操作：

   * 要删除图像，请选择图像，然后点按 **[!UICONTROL 删除资产]**.
   * 要应用预设，请点按页面右上角附近的 **[!UICONTROL 预设]**，然后选择要同时应用于所有资产的预设。

1. 点按 **[!UICONTROL 保存]**. 您新创建的旋转集将显示在创建该旋转集的文件夹中。

## 查看旋转集 {#viewing-spin-sets}

您可以在用户界面中创建旋转集，也可以使用 [批次集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). 但是，使用批集预设创建的集，请执行 *not* 显示在用户界面中。 您可以通过三种不同方式访问通过批集预设方式创建的集。 （即使您在用户界面中创建旋转集，这些方法也可用）。

您还可以通过用户界面查看集，如 [编辑旋转集](#editing-spin-sets).

**要查看旋转集，请执行以下操作：**

1. 打开单个资产的属性时。 属性指示所选资产是的成员集(在 **[!UICONTROL 集成员]**)。 点按集的名称可查看整个集。

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. 来自任何集的成员图像。选择 **[!UICONTROL 集]** 菜单，以显示资产所属的集。

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. 从搜索中，您可以选择 **[!UICONTROL 过滤器]**，然后展开 **[!UICONTROL Dynamic Media]** 选择 **[!UICONTROL 集]**.

   搜索会返回在用户界面中手动创建的匹配集，或通过批集预设自动创建的匹配集。 对于自动集，使用 **[!UICONTROL 开始于]** 搜索标准与AEM搜索不同，后者基于使用 **[!UICONTROL 包含]** 搜索标准。 将过滤器设置为 **[!UICONTROL 集]** 是搜索自动集的唯一方法。

   ![chlimage_1-386](assets/chlimage_1-386.png)

## 编辑旋转集 {#editing-spin-sets}

您可以对旋转集执行多种编辑任务，如：

* 向旋转集添加图像。
* 对旋转集中的图像重新排序。
* 删除旋转集中的资产。
* 应用查看器预设。
* 删除旋转集。

**要编辑旋转集，请执行以下操作：**

1. 执行以下任一操作：

   * 将鼠标悬停在旋转集资产上，然后点按 **[!UICONTROL 编辑]** （铅笔图标）。
   * 将鼠标悬停在旋转集资产上，点按 **[!UICONTROL 选择]** （复选标记图标），然后点按 **[!UICONTROL 编辑]** 中。
   * 点按旋转集资产，然后点按 **[!UICONTROL 编辑]** （铅笔图标）。

1. 要编辑旋转集，请执行以下任一操作：

   * 要对图像重新排序，请将图像拖到新位置（选择重新排序图标以移动项目）。
   * 要按升序或降序对项目排序，请点按列标题。
   * 要添加资产或更新现有资产，请点按 **[!UICONTROL 添加资产]**. 导航到资产，选择该资产，然后点按 **[!UICONTROL 选择]** 在右上角附近。
如果您通过将AEM用作缩略图的图像替换为其他图像来删除该图像，则仍会显示原始资产。
   * 要删除资产，请选择该资产，然后点按 **[!UICONTROL 删除资产]**.
   * 要应用预设，请点按 **[!UICONTROL 预设]** 图标，然后选择预设。
   * 要删除整个旋转集，请导航到旋转集，将其选中，然后选择 **[!UICONTROL 删除]**

      >[!NOTE]
      >* 您可以导航到旋转集，点按，以编辑该旋转集中的图像 **[!UICONTROL 设置成员]** ，然后点按 **[!UICONTROL 编辑]** （铅笔图标）来打开编辑窗口。


1. 单击 **[!UICONTROL 保存]** 完成编辑时。

## 预览旋转集 {#previewing-spin-sets}

请参阅 [预览资产](previewing-assets.md).

## 发布旋转集 {#publishing-spin-sets}

请参阅 [发布资产](publishing-dynamicmedia-assets.md).
