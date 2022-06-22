---
title: 图像集
seo-title: Image Sets
description: 了解如何在Dynamic Media中处理图像集
seo-description: Learn how to work with image sets in dynamic media
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
exl-id: af3f95aa-a162-4212-a20a-68b5a0e72d6d
feature: Image Sets
role: User
source-git-commit: 5d4d0c86a9d9e3eaaaca1e795260e8e49567ea73
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 40%

---

# 图像集 {#image-sets}

借助图像集，用户可以通过单击缩略图来查看项目的不同视图，从而为用户提供集成式查看体验。图像集使您可以展示同一项目的替换视图，并且查看器提供了可用于仔细检查图像的缩放工具。

图像集由带有单词的横幅来指定 **[!UICONTROL 图像集]**. 此外，如果图像集已发布，则横幅上会显示由 **[!UICONTROL World]** 图标指示的发布日期以及由铅笔图标指示的上次修改日期 **** 。

![chlimage_1-339](assets/chlimage_1-339.png)

在图像集中，您还可以通过创建图像集并添加缩略图来创建样本。

当您希望以不同的颜色、模式或外表显示某个项目时，此应用程序尤其有用。要创建带有颜色样本的图像集，您要向用户展示的每种不同的颜色、模式或外表都需要有一个图像。每种颜色、模式或外表还需要有一个颜色、模式或外表样本。

例如，假定您要展示帽檐颜色各异的帽子图像，且帽檐分别为红色、绿色和蓝色。在这种情况下，您需要准备同一款帽子的三张拍照。这三张拍照分别对应红色、绿色和蓝色的帽檐。您还需要准备红色、绿色和蓝色三种颜色的样本。颜色色板用作用户在色板集查看器中单击的缩略图，以查看红色、绿色或蓝色的帽子。

>[!NOTE]
>
>有关Assets用户界面的信息，请参阅 [使用触屏UI管理资产](managing-assets-touch-ui.md).

在创建图像集时，Adobe会推荐以下最佳实践，并实施以下限制：

| 资产 — 限制类型 | 最佳实践 | 已实施的限制 | 对2022年12月31日上限的更改 |
| --- | --- | --- | --- |
| **图像集**  — 每个集的重复资产数 | 无重复项 | 100 | 20 |
| **图像集**  — 每组图像的最大数量 | 每组5-10张图像 | 1000 |

另请参阅 [Dynamic Media限制](/help/assets/limitations.md).

## 快速入门：图像集 {#quick-start-image-sets}

要快速设置并运行图像集，请执行以下操作：

1. [为多个视图上传主图像。](#uploading-assets-in-image-sets)

   首先为图像集上传图像。由于用户可以在图像集查看器中缩放图像，因此在选择图像时，请考虑缩放因素。确保图像的最大尺寸至少为2000像素，以优化缩放详细信息。 Dynamic Media每幅可渲染多达2500万像素的图像。 例如，您可以使用5000 x 50000万像素图像或任何其他大小组合，最多2500万像素。

   AEM Assets 支持很多种图像文件格式，但建议使用无损的 TIFF、PNG 和 EPS 图像。

1. [创建图像集。](#creating-image-sets)

   在图像集中，用户在图像集查看器中单击缩略图图像。

   要在资产中创建图像集，请点按 **[!UICONTROL 创建>图像集]**. 然后，添加图像并点按 **[!UICONTROL 保存]**.

   您还可以通过 [批次集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

   **重要信息**  — 批量集由IPS（图像生产系统）作为资产摄取的一部分创建，并且仅在Dynamic Media - Scene7模式下可用。

   请参阅 [准备要上传的图像集资产和上传文件](#uploading-assets-in-image-sets).

   请参阅 [使用选择器。](working-with-selectors.md)

1. 添加 [图像集查看器预设](managing-viewer-presets.md)，根据需要。

   管理员可以创建或修改映像 **[!UICONTROL 设置查看器预设]**. 要查看带有查看器预设的图像集，请选择图像集，然后在左边栏下拉菜单中，选择 **[!UICONTROL 查看器]**.

   请参阅 **[!UICONTROL 工具>资产>查看器预设]** 创建或编辑查看器预设。

1. （可选） [查看图像集](image-sets.md#viewing-image-sets) 批次集预设创建的集合。
1. [预览图像集。](previewing-assets.md)

   选择图像集后，您便可以预览该图像集。点按缩略图图标以在选定的查看器中检查图像集。 您可以从 **[!UICONTROL 查看器]** 菜单（可从左边栏下拉菜单中访问）。

1. [发布图像集。](publishing-dynamicmedia-assets.md)

   发布图像集时，将会激活 URL 和嵌入字符串。此外，您还必须 [发布任何自定义查看器预设](managing-viewer-presets.md) 创建的。 现成的查看器预设已发布。

1. [将 URL 关联到您的 Web 应用程序](linking-urls-to-yourwebapplication.md)或者[嵌入视频查看器或图像查看器](embed-code.md)。

   在发布图像集后，AEM Assets 会为该图像集创建 URL 调用并将其激活。预览资产时，您可以复制这些 URL。或者，您也可以将它们嵌入到您的网站上。

   选择图像集，然后在左边栏下拉菜单中选择&#x200B;**[!UICONTROL 查看器]**。

   请参 [阅将图像集链接到网页和嵌入视](linking-urls-to-yourwebapplication.md) 频查看器或图像查看器 [](embed-code.md)。

要编辑图像集，请参阅 [编辑图像集。](#editing-image-sets) 此外，您还可以查看和编辑 [图像集属性](managing-assets-touch-ui.md#editing-properties).

如果您在创建集时遇到问题，请参阅 [Dynamic Media - Scene7模式故障诊断](troubleshoot-dms7.md#images-and-sets).

## 在图像集中上传资产 {#uploading-assets-in-image-sets}

首先为图像集上传图像。由于用户可以在图像集查看器中缩放图像，因此在选择图像时，请考虑缩放因素。确保图像的最大尺寸至少为2000像素。图像集支持很多种图像文件格式，但建议使用无损的 TIFF、PNG 和 EPS 图像。

为图像集上传图像的方法与[在资产中上传任何其他资产](managing-assets-touch-ui.md#uploading-assets)的方法相同。

### 准备要上传的图像集资产 {#preparing-image-set-assets-for-upload}

在创建图像集之前，请确保图像的大小和格式均合适。

要创建多视图的图像集，您需要多个图像，它们要从不同视角显示一个项目或显示同一项目的不同方面。其目标是突出一个项目的各项重要功能，以便查看者能够全面地了解该项目的外观或用途。

由于用户可以缩放图像集中的图像，请确保图像的最大尺寸至少有 2000 像素。资产支持很多种图像文件格式，但建议使用无损的 TIFF、PNG 和 EPS 图像。

>[!NOTE]
>
>此外，如果您使用缩略图指示产品样本，则需要以下各项：
>
>您需要小插图，也就是同一图像的不同拍照，以显示该图像的不同颜色、模式或外表。您还需要与不同颜色、模式或外表相对应的缩略图文件。例如，要通过显示同一款夹克的黑色、咖色和绿色版的图像集展示缩略图，您需要：
>
>* 同一款夹克的黑色、咖色和绿色版拍照。
>* 黑色、咖色和绿色版的缩略图。
>


## 创建图像集 {#creating-image-sets}

您可以通过用户界面或API创建图像集。 本节介绍如何在用户界面中创建图像集。

>[!NOTE]
>
>您还可以通过 [批次集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**重要信息：** 批量集由IPS（图像生产系统）作为资产摄取的一部分创建，并且只能在Dynamic Media - Scene7模式下使用。

在将资产添加到资产集时，资产会按字母数字顺序自动添加。 您可以在添加资产后手动对资产重新排序或排序。

>[!NOTE]
>
>对于具有 `,` （逗号）。

在创建图像集时，Adobe会推荐以下最佳实践，并实施以下限制：

| 资产 — 限制类型 | 最佳实践 | 已实施的限制 | 对2022年12月31日上限的更改 |
| --- | --- | --- | --- |
| **图像集**  — 每个集的重复资产数 | 无重复项 | 100 | 20 |
| **图像集**  — 每组图像的最大数量 | 每组5-10张图像 | 1000 |

另请参阅 [Dynamic Media限制](/help/assets/limitations.md).

**创建图像集**:

1. 在 **资产**，导航到要创建图像集的位置，点按 **[!UICONTROL 创建]**，然后选择 **[!UICONTROL 图像集]**. 您还可以从包含资产的文件夹中创建旋转集。

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. 在“图像集编辑器”页面的 **[!UICONTROL 标题]** 字段，输入图像集的名称。 该名称会显示在图像集的横幅中。（可选）输入说明。

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >创建图像集时，您可以更改图像集缩略图，或允许 AEM 根据图像集中的资产自动选择缩略图。要选择缩略图，请点按 **[!UICONTROL 更改缩略图]** 并选择任意图像（您也可以导航到其他文件夹以查找图像）。 如果您选择了缩略图，然后决定让 AEM 从图像集生成缩略图，请选择&#x200B;**[!UICONTROL 切换到自动缩略图]**。

1. 执行以下操作之一：

   * 在 **[!UICONTROL 图像集编辑器]** 页面，点按 **[!UICONTROL 添加资产]**.
   * 在 **[!UICONTROL 图像集编辑器]** 页面，点按 **[!UICONTROL 点按以打开资产选择器]**.

   点按以选择要包含在图像集中的资产。 选定资产上有一个复选标记图标。完成后，在页面的右上角附近，点按 **[!UICONTROL 选择]**.

   借助资产选择器，您可以通过键入关键字并点按&#x200B;**[!UICONTROL 返回]**&#x200B;来搜索资产。您还可以应用过滤器来优化搜索结果。您可以按路径、收藏集、文件类型和标记进行过滤。选择过滤器，然后点按工具栏上的&#x200B;**[!UICONTROL 过滤器]**&#x200B;图标。通过点按 **[!UICONTROL 查看]** 图标和选择 **[!UICONTROL 列视图]**, **[!UICONTROL 卡片视图]**&#x200B;或 **[!UICONTROL 列表视图]**.

   请参阅 [使用选择器。](working-with-selectors.md)

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. 在将资产添加到资产集时，资产会按字母数字顺序自动添加。 您可以在添加资产后手动对资产重新排序或排序。

   如有必要，请拖动资产的 **[!UICONTROL 重新排序]** 图标，以在设置列表中对图像进行重新排序。

   ![spin_set_assets](assets/spin_set_assets.png)

   如果要更改缩略图或色板，请点按 **[!UICONTROL 缩略图]** 图标，然后导航到所需的缩略图或色板。 选择完所有图像后，点按 **[!UICONTROL 保存]**.

1. （可选）执行以下操作之一：

   * 要删除图像，请选择图像，然后点按 **[!UICONTROL 删除资产]**.
   * 要应用预设，请点按页面右上角附近的 **[!UICONTROL 预设]**，然后选择要同时应用于所有资产的预设。

1. 点按&#x200B;**[!UICONTROL 保存]**。您新创建的图像集会显示在创建时所用的文件夹中。

## 查看图像集 {#viewing-image-sets}

您可以在用户界面中创建图像集，也可以使用 [批次集预设](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**重要信息**  — 批集由IPS创建 [图像生成系统] 作为资产摄取的一部分，且仅在Dynamic Media - Scene7模式下可用。)

但是，使用批集预设创建的集，请执行 *not* 显示在用户界面中。 您可以通过三种不同方式查看这些集。 （即使您是在用户界面中创建图像集，这些方法也可用）。

* 打开单个资产的属性时。 属性指示所选资产是的成员集(在 **[!UICONTROL 集成员]**)。 点按集的名称可查看整个集。

   ![chlimage_1-343](assets/chlimage_1-343.png)

* 来自任何集的成员图像。选择 **[!UICONTROL 集]** 菜单，以显示资产所属的集。

   ![chlimage_1-344](assets/chlimage_1-344.png)

* 从搜索中，您可以选择 **[!UICONTROL 过滤器]**，然后展开 **[!UICONTROL Dynamic Media]** 选择 **[!UICONTROL 集]**.

   搜索会返回在UI中手动创建的匹配集，或通过批集预设自动创建的匹配集。 对于自动集，搜索查询使用“开始于”搜索标准进行，该搜索标准与基于使用“包含”搜索标准的AEM搜索不同。 将过滤器设置为 **[!UICONTROL 集]** 是搜索自动集的唯一方法。

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>您可以通过用户界面查看集，如 [编辑图像集](#editing-image-sets).

## 编辑图像集 {#editing-image-sets}

您可以对图像集执行多种编辑任务，如下所示：

* 向图像集中添加图像。
* 对图像集中的图像重新排序。
* 删除图像集中的资产。
* 应用查看器预设。
* 删除图像集。

**编辑图像集**:

1. 执行以下任一操作：

   * 将鼠标悬停在图像集资产上，然后点按 **[!UICONTROL 编辑]** （铅笔图标）。
   * 将鼠标悬停在图像集资产上，点按 **[!UICONTROL 选择]** （复选标记图标），然后点按 **[!UICONTROL 编辑]** 中。
   * 点按图像集资产，然后点按 **[!UICONTROL 编辑]** （铅笔图标）。

1. 要编辑图像集中的图像，请执行以下任意操作：

   * 要对资产重新排序，请将图像拖到新位置（选择重新排序图标以移动项目）。
   * 要按升序或降序对项目排序，请点按列标题。
   * 要添加资产或更新现有资产，请点按 **[!UICONTROL 添加资产]**. 导航到资产，选择该资产，然后点按 **[!UICONTROL 选择]** 在页面的右上角附近。

   >[!NOTE]
   >如果您通过将AEM用作缩略图的图像替换为其他图像来删除该图像，则仍会显示原始资产。

   * 要删除资产，请选择它，然后点按 **[!UICONTROL 删除资产]**.
   * 要应用预设，请点按页面右上角附近的 **[!UICONTROL 预设]**，然后选择查看器预设。
   * 要添加或更改缩略图，请选择资产右侧的缩略图图标。 导航到新的缩略图或色板资产，将其选中，然后点按 **[!UICONTROL 选择]**.
   * 要删除整个图像集，请导航到图像集，将其选中，然后点按 **[!UICONTROL 删除]**.

   >[!NOTE]
   >
   >您可以导航到图像组，点按左边栏中的&#x200B;**[!UICONTROL 设置成员]**，然后点按单个资产上的“铅笔”图标以打开编辑窗口，来编辑图像。****

1. 点按 **[!UICONTROL 保存]** 完成编辑后。

## 预览图像集 {#previewing-image-sets}

请参阅 [预览资产](previewing-assets.md).

## 发布图像集 {#publishing-image-sets}

请参阅[发布资产](publishing-dynamicmedia-assets.md)。
