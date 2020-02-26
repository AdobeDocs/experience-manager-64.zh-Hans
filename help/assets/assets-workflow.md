---
title: 应用工作流来处理您的数字资产
description: 了解如何将工作流应用于AEM资产中的资产、文件夹和收藏集，以处理您的数字资产。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# 将工作流应用于资产 {#applying-workflows-to-assets}

将工作流应用于数字资产与将工作流应用于网站页面相同。 有关如何在AEM中创建和使用工作流的完整指南，请参阅启 [动工作流](../sites-authoring/workflows-participating.md)。

使用数字资产中的工作流来激活资产或创建水印。 资产的许多工作流都会自动打开。 例如，编辑图像后自动创建再现的工作流会自动打开。

如果经典UI中可用的工作流在触屏优化UI中不可用，例如请求激活和请求取消激活，请参阅使工作流模 [型在触屏UI中可用](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)。

## 将工作流应用于AEM资产 {#applying-a-workflow-to-an-aem-asset}

有关将工作流应用到AEM资产的详细信息，请参 [阅在资产上启动工作流](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)。

## 将工作流应用到多个资产 {#applying-a-workflow-to-multiple-assets}

1. 从“资产”控制台中，导航到要为其启动工作流的资产所在的位置，然后选择资产。
1. 单击GlobalNav图标，然后从菜单中选择 **[!UICONTROL 时间轴]** ，以显示时间轴。

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. 单击“ **[!UICONTROL 启动工作流]**”。
1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. （可选）指定工作流的标题，该标题可用于引用工作流实例。
1. 单击 **[!UICONTROL 开始]** ，然后在对话 **[!UICONTROL 框中单击确]** 认。 该工作流会在您选择的所有资产上运行。

## 将工作流应用到多个文件夹 {#applying-a-workflow-to-multiple-folders}

将工作流应用到多个文件夹的过程与将工作流应用到多个资产的过程类似。 在“资产”控制台中选择文件夹，然后执行将工作流应用到多 [个资产过程的步骤2-7](assets-workflow.md#applying-a-workflow-to-multiple-assets)。

## 将工作流应用到集合 {#applying-a-workflow-to-a-collection}

有关将工作流应用到集合的详细信息，请参 [阅在集合上运行工作流](managing-collections-touch-ui.md#running-a-workflow-on-a-collection)。
