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
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Target与体验片段的集成{#target-integration-with-experience-fragments}

>[!NOTE]
>
>此功能需要应用[AEM 6.4 Service Pack 2(6.4.2.0)](/help/release-notes/sp-release-notes.md)或更高版本。

您可以将在Adobe Experience Manager(AEM)中创建的[体验片段](/help/sites-authoring/experience-fragments.md)导出到Adobe Target。 然后，即可在Target活动中将这些体验用作选件，以便测试和个性化大量体验。 这样，您就可以将AEM的易用性和强大功能与Target中强大的自动智能(AI)和机器学习(ML)功能结合使用。

## 前提条件 {#prerequisites}

需要执行各种操作：

1. 您必须将AEM与Target集成。 有关更多信息，请参阅[与Adobe Target集成](/help/sites-administering/target.md) 。
1. 体验片段是从创作实例导出的，因此您需要在创作实例上[配置链接外部器](/help/sites-developing/externalizer.md)，以确保发布实例的所有链接都外部化。

## 添加云配置{#add-the-cloud-configuration}

在导出片段之前，您需要将&#x200B;**Adobe Target**&#x200B;的&#x200B;**云配置**&#x200B;添加到片段或文件夹中：

1. 导航到&#x200B;**体验片段**&#x200B;控制台。
1. 打开相应文件夹或片段的&#x200B;**页面属性** 。

   >[!NOTE]
   >
   >如果将云配置添加到体验片段父文件夹，则该配置将由所有子文件夹继承。
   >
   >如果将云配置添加到体验片段本身，则该配置将由所有变量继承。

1. 选择&#x200B;**Cloud Services**&#x200B;选项卡。

1. 在&#x200B;**Cloud Service配置**&#x200B;下，从下拉列表中选择&#x200B;**Adobe Target**。
1. 在&#x200B;**Adobe Target**&#x200B;下，选择相应的配置。

1. **保存并关闭**.

## 将体验片段导出到Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>对于媒体资产（如图像），只会将引用导出到Target。 资产本身将保留在AEM Assets中，并从AEM发布实例交付。
>
>因此，需要先发布体验片段（包含所有相关资产），然后再导出到Target。

要将体验片段从AEM导出到Target（在指定云配置后），请执行以下操作：

1. 导航到体验片段控制台。
1. 选择要导出到target的体验片段。

   >[!NOTE]
   >
   >它必须是体验片段Web变量。

1. 点按/单击&#x200B;**导出到Adobe Target**。

   >[!NOTE]
   >
   >如果体验片段已导出，请选择&#x200B;**在Adobe Target中更新**。

1. 根据需要，点按/单击不发布&#x200B;**或**&#x200B;发布&#x200B;**的导出。**

   >[!NOTE]
   >
   >选择**发布**将立即发布体验片段，并将其发送到Target。

1. 点按/单击确认对话框中的&#x200B;**确定**。

   您的体验片段现在应该位于Target中。

>[!NOTE]
>
>或者，您也可以使用[Page Information](/help/sites-authoring/author-environment-tools.md#page-information)菜单中的类似命令从页面编辑器执行导出。

## 在Target {#using-your-experience-fragments-in-target}中使用您的体验片段

执行上述任务后，体验片段会显示在Target的“选件”页面上。 请查看[特定Target文档](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) ，了解您在该文档中可以实现的目标。

## 删除已导出到Target的体验片段{#deleting-an-experience-fragment-already-exported-to-target}

如果删除已导出到Target的体验片段，则该片段已在Target的选件中使用，则该体验片段可能会导致问题。 删除片段会导致选件在AEM交付片段内容时不可用。

为避免出现这种情况：

* 如果活动中当前未使用体验片段，则AEM允许用户删除片段，而不显示警告消息。
* 如果Target中的活动当前正在使用体验片段，则会显示一条错误消息，警告AEM用户删除片段对活动可能产生的影响。

   AEM中的错误消息不禁止用户（强制）删除体验片段。 如果删除了体验片段：

   * 包含AEM体验片段的Target选件可能显示不希望的行为

      * 由于体验片段HTML已推送到Target，因此选件很可能仍会呈现
      * 如果还在AEM中删除了引用的资产，则体验片段中的任何引用可能无法正常工作。
   * 当然，对体验片段进行任何进一步的修改都是不可能的，因为体验片段不再存在于AEM中。
