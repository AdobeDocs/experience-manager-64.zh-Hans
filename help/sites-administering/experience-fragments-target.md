---
title: 目标与体验片段集成
seo-title: 目标与体验片段集成
description: 目标与体验片段集成
seo-description: 目标与体验片段集成
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# 目标与体验片段集成{#target-integration-with-experience-fragments}

>[!NOTE]
>
>此功能需要[AEM 6.4 Service Pack 2(6.4.2.0)](/help/release-notes/sp-release-notes.md)或更高版本的应用程序。

您可以将在Adobe Experience Manager(AEM)创建的[体验片段](/help/sites-authoring/experience-fragments.md)导出到Adobe Target。 然后，它们可用作目标活动的优惠，以大规模测试和个性化体验。 这使您能够将AEM的易用性和强大功能与目标中强大的自动智能(AI)和机器学习(ML)功能相结合。

## 前提条件 {#prerequisites}

需要执行各种操作：

1. 您必须将AEM与目标集成。 有关详细信息，请参阅[与Adobe Target集成](/help/sites-administering/target.md)。
1. 体验片段从创作实例中导出，因此您需要在创作实例中[配置链接外部化器](/help/sites-developing/externalizer.md)，以确保发布实例的所有链接都外部化。

## 添加云配置{#add-the-cloud-configuration}

在导出片段之前，您需要将&#x200B;**Adobe Target**&#x200B;的&#x200B;**云配置**&#x200B;添加到片段或文件夹：

1. 导航到&#x200B;**体验片段**&#x200B;控制台。
1. 打开相应文件夹或片段的&#x200B;**页面属性**。

   >[!NOTE]
   >
   >如果将云配置添加到体验片段父文件夹，则所有子级都会继承该配置。
   >
   >如果将云配置添加到体验片段本身，则所有变量都会继承该配置。

1. 选择&#x200B;**Cloud Services**&#x200B;选项卡。

1. 在&#x200B;**Cloud Service配置**&#x200B;下，从下拉列表中选择&#x200B;**Adobe Target**。
1. 在&#x200B;**Adobe Target**&#x200B;下，选择相应的配置。

1. **保存并关闭**.

## 将体验片段导出到目标{#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>对于媒体资产（如图像），只会导出引用到目标。 资产本身仍存储在AEM Assets，并通过AEM发布实例传送。
>
>因此，需要先发布包含所有相关资产的体验片段，然后再导出到目标。

要将体验片段从AEM导出到目标（在指定云配置后），请执行以下操作：

1. 导航到体验片段控制台。
1. 选择要导出到目标的体验片段。

   >[!NOTE]
   >
   >它必须是体验片段Web变体。

1. 点按／单击&#x200B;**导出到Adobe Target**。

   >[!NOTE]
   >
   >如果体验片段已导出，请选择“在Adobe Target **中更新”。**

1. 根据需要点按／单击&#x200B;**导出而不发布**&#x200B;或&#x200B;**发布**。

   >[!NOTE]
   >
   >选择**发布**将立即发布体验片段并将其发送到目标。

1. 点按／单击确认对话框中的&#x200B;**确定**。

   您的体验片段现在应处于目标。

>[!NOTE]
>
>或者，也可以使用[页面信息](/help/sites-authoring/author-environment-tools.md#page-information)菜单中的类似命令从页面编辑器执行导出。

## 在目标{#using-your-experience-fragments-in-target}中使用您的体验片段

执行上述任务后，体验片段显示在优惠页面的目标中。 请查看[特定目标文档](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html)，了解您可以在那里实现什么。

## 删除已导出到目标{#deleting-an-experience-fragment-already-exported-to-target}的体验片段

如果删除已导出到目标的体验片段在目标的优惠中已使用，则可能会导致问题。 删除片段将导致优惠不可用，因为AEM正在传送片段内容。

要避免此类情况：

* 如果活动中当前未使用体验片段，AEM允许用户删除片段，而不显示警告消息。
* 如果目标中的活动当前正在使用体验片段，则会显示一条错误消息，警告AEM用户删除片段对活动可能造成的后果。

   AEM中的错误消息不禁止用户（强制）删除体验片段。 如果体验片段被删除：

   * 具有AEM体验片段的目标优惠可能显示不期望的行为

      * 优惠可能仍会呈现，因为体验片段HTML已推送到目标
      * 如果在AEM中也删除了引用的资产，则体验片段中的任何引用可能也无法正常工作。
   * 当然，体验片段的任何进一步修改都不可能，因为体验片段在AEM中已不存在。


