---
title: Target与体验片段集成
seo-title: Target Integration with Experience Fragments
description: Target与体验片段集成
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 72%

---

# Target与体验片段集成{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>此功能需要应用 [AEM 6.4 Service Pack 2(6.4.2.0)](/help/release-notes/sp-release-notes.md) 或更晚。

您可以导出 [体验片段](/help/sites-authoring/experience-fragments.md)，在Adobe Experience Manager(AEM)中创建，到Adobe Target。 然后，可以将其用作 Target 活动中的选件以大规模测试和打造个性化体验。这样，您就可以将AEM的易用性和强大功能与Target中强大的自动智能(AI)和机器学习(ML)功能结合使用。

## 前提条件 {#prerequisites}

需要执行各种操作：

1. 您必须将 AEM 与 Target 集成。请参阅 [与Adobe Target集成](/help/sites-administering/target.md) 以了解更多信息。
1. 体验片段是从创作实例导出的，因此您需要 [配置链接外部器](/help/sites-developing/externalizer.md) ，以确保发布实例的所有链接都外部化。

## 添加云配置 {#add-the-cloud-configuration}

在导出片段之前，您需要添加 **云配置** 表示 **Adobe Target** 到片段或文件夹：

1. 导航到&#x200B;**体验片段**&#x200B;控制台。
1. 打开相应的文件夹或片段的&#x200B;**页面属性**。

   >[!NOTE]
   >
   >如果将云配置添加到体验片段父文件夹，则该配置将由所有子级继承。
   >
   >如果将云配置添加到体验片段本身，则该配置将由所有变体继承。

1. 选择&#x200B;**云服务**&#x200B;选项卡。

1. 在 **Cloud Service配置**，选择 **Adobe Target** 从下拉列表中。
1. 在 **Adobe Target**，请选择相应的配置。

1. **保存并关闭**。

## 将体验片段导出到 Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>对于媒体资产（例如图像），仅将引用导出到 Target。资产本身仍存储在 AEM Assets 中，并且从 AEM 发布实例进行交付。
>
>因此，在导出到 Target 之前，需要发布包含所有相关资产的体验片段。

要将体验片段从 AEM 导出到 Target（在指定云配置之后），请执行以下操作：

1. 导航到体验片段控制台。
1. 选择要导出到 Target 的体验片段。

   >[!NOTE]
   >
   >它必须是体验片段 Web 变体。

1. 点按/单击&#x200B;**导出到 Adobe Target**。

   >[!NOTE]
   >
   >如果已导出体验片段，请选择&#x200B;**在 Adobe Target 中更新**。

1. 根据需要点按/单击&#x200B;**导出而不发布**&#x200B;或&#x200B;**发布**。

   >[!NOTE]
   >
   >选择**发布**将立即发布体验片段，并将其发送到Target。

1. 在确认对话框中，点按/单击&#x200B;**确定**。

   您的体验片段现在应在 Target 中。

>[!NOTE]
>
>或者，您可以使用[页面信息](/help/sites-authoring/author-environment-tools.md#page-information)菜单中的类似命令从页面编辑器执行导出。

## 在 Target 中使用体验片段 {#using-your-experience-fragments-in-target}

执行上述任务后，体验片段将显示在 Target 的“选件”页面上。请查看[特定 Target 文档](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html)以了解可以实现的目标。

## 删除已导出到 Target 的体验片段 {#deleting-an-experience-fragment-already-exported-to-target}

如果已在 Target 的选件中使用已导出到 Target 的某个体验片段，则删除该体验片段可能会导致出现问题。由于 AEM 正在交付片段内容，因此，删除片段会导致选件不可用。

避免此类情况：

* 如果体验片段当前未在活动中使用，AEM 将允许用户删除片段而不显示警告消息。
* 如果 Target 中的活动当前正在使用体验片段，则会出现一条错误消息，警告 AEM 用户删除该片段可能给活动带来的后果。

   AEM 中的错误消息不会禁止用户（强制）删除体验片段。如果删除体验片段：

   * 带有 AEM 体验片段的 Target 选件可能会显示意外行为

      * 该选件可能仍会呈现，因为体验片段 HTML 已推送到 Target
      * 如果也从 AEM 中删除了引用的资产，则体验片段中的任何引用都无法正常工作。
   * 当然，由于体验片段在 AEM 中不再存在，因此无法对体验片段进行任何进一步的修改。
