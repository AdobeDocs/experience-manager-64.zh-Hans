---
title: Target与体验片段集成
seo-title: Target与体验片段集成
description: Target与体验片段集成
seo-description: Target与体验片段集成
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb

---


# Target与体验片段集成{#target-integration-with-experience-fragments}

>[!NOTE]
>
>此功能需要应用 [AEM 6.4 Service Pack 2(6.4.2.0)或更高版本](/help/release-notes/sp-release-notes.md) 。

您可以将 [在Adobe Experience Manager](/help/sites-authoring/experience-fragments.md)(AEM)中创建的Experience Fragments导出到Adobe Target。 然后，可在Target活动中将其用作选件，以大规模测试和个性化体验。 这使您能够将AEM的易用性和强大功能与Target中强大的自动智能(AI)和机器学习(ML)功能相结合。

## 前提条件 {#prerequisites}

需要执行各种操作：

1. 您必须将AEM与Target集成。 See [Integrating with Adobe Target](/help/sites-administering/target.md) for more information.
1. 体验片段从创作实例中导出，因此您需要在创作实例上配置 [Link Externalizer](/help/sites-developing/externalizer.md) ，以确保发布实例的所有链接都外部化。

## 添加云配置 {#add-the-cloud-configuration}

在导出片段之前，您需要将 **Adobe Target的云配置****** 添加到片段或文件夹：

1. 导航到“体 **验片段** ”控制台。
1. 打开 **相应文件夹** 或片段的页面属性。

   >[!NOTE]
   >
   >如果将云配置添加到Experience Fragment父文件夹，则此配置将由所有子文件夹继承。
   >
   >如果将云配置添加到体验片段本身，则所有变量都会继承该配置。

1. 选择“ **云服务** ”选项卡。

1. 在“ **云服务配置**”下，从下 **拉列表中选择Adobe Target** 。
1. 在 **Adobe Target下**，选择相应的配置。

1. **保存并关闭**.

## 将体验片段导出到目标 {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>对于媒体资产（如图像），只有引用会导出到Target。 资产本身将保留在AEM资产中，并从AEM发布实例中传送。
>
>因此，需要先发布包含所有相关资产的体验片段，然后再导出到Target。

要将体验片段从AEM导出到Target（在指定云配置后），请执行以下操作：

1. 导航到体验片段控制台。
1. 选择要导出到目标的体验片段。

   >[!NOTE]
   >
   >它必须是体验片段Web变量。

1. 点按／单 **击导出至Adobe Target**。

   >[!NOTE]
   >
   >如果体验片段已导出，请在Adobe Target中 **选择更新**。

1. 根据需要点按／单 **击导出** ，不发 **布或** 发布。

   >[!NOTE]
   >
   >选择**发布**将立即发布体验片段并将其发送到Target。

1. 点按／单击确 **认对话框** 中的确定。

   您的体验片段现在应位于Target中。

>[!NOTE]
>
>或者，您也可以使用“页面信息”菜单中的类似命令从页面编辑器 [执行导出](/help/sites-authoring/author-environment-tools.md#page-information) 。

## 在Target中使用体验片段 {#using-your-experience-fragments-in-target}

执行上述任务后，体验片段会显示在Target的“选件”页面上。 请查看特定Target文 [档](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) ，了解您可以在其中实现什么。

## 删除已导出到Target的体验片段 {#deleting-an-experience-fragment-already-exported-to-target}

如果删除已导出到Target的体验片段，则该片段已在Target中的选件中使用，则可能会导致问题。 删除片段会使选件在AEM传送片段内容时无法使用。

要避免此类情况，请执行以下操作：

* 如果活动中当前未使用体验片段，则AEM允许用户删除片段，但不显示警告消息。
* 如果Target中的活动当前正在使用体验片段，则会显示一条错误消息，警告AEM用户删除片段对活动可能产生的后果。

   AEM中的错误消息不会禁止用户（强制）删除体验片段。 如果体验片段被删除：

   * 包含AEM体验片段的Target选件可能显示不期望的行为

      * 随着体验片段HTML被推送到Target，选件可能仍会呈现
      * 如果引用的资产也在AEM中被删除，则体验片段中的任何引用可能无法正常工作。
   * 当然，由于体验片段在AEM中已不存在，因此无法对体验片段进行任何进一步修改。


