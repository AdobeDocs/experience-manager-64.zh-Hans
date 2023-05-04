---
title: 智能内容服务培训准则
description: 培训AI服务以将智能标记应用于资产
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 11%

---

# 智能内容服务培训准则 {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

为了能够有效地标记您的品牌图像，智能内容服务要求培训图像符合特定准则。

## 培训准则 {#guidelines-for-training}

为获得最佳结果，培训集中的图像应符合以下准则：

**数量和大小：** 最小 **每个标记30张图像**. 长边至少 500 像素。

**一致性**:标记的图像应当看起来类似。

例如，将所有这些图像标记为 *我的派对* （用于培训），因为它们在视觉上并不相似。

![示例图像以说明培训准则](assets/do-not-localize/coherence.png)

**覆盖**:培训中的图像应该有足够的多样性。 我们的想法是提供一些比较多样化的例子，以便 [!DNL Experience Manager] 学会专注于正确的事情。 如果您对视觉上不相似的图像应用相同的标记，请至少包含每种类型的五个示例。

例如，对于标记 *模型 — 下姿态*，为服务包含更多与下面突出显示的图像类似的培训图像，以便在标记期间更准确地识别类似图像。

![示例图像以说明培训准则](assets/do-not-localize/coverage_1.png)

**干扰/阻碍**:该服务能够更好地训练分散注意力的图像（突出的背景、不相关的伴奏，如主题的物体/人）。

例如，对于标记 *休闲鞋*&#x200B;第二张图像不是好的训练候选者。

![示例图像以说明培训准则](assets/do-not-localize/distraction.png)

**完整性：**&#x200B;如果图像符合多个标记的条件，请在包含培训图像之前添加所有适用的标记。例如，对于 *Raincoat* 和 *model-side-view* 等标记，在将其加入培训之前，在符合条件的资产上添加这两个标记。

![示例图像以说明培训准则](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增强型智能标记基于品牌图像及其标记的学习模型。 这些模型并非总能很好地识别标记。 智能内容服务的当前版本具有以下限制：

* 无法识别图像中的细微差异。 例如，纤薄的衬衫与普通的衬衫。
* 无法根据图像的微小模式/部分来识别标记。 例如，T恤上的徽标。
* 区域设置支持标记 [!DNL Experience Manager] 支持。 有关语言列表，请参阅 [智能内容服务发行说明](/help/release-notes/smart-content-service-release-notes.md).

要使用智能标记（常规或增强）搜索资产，请使用资产全屏搜索（全文搜索）。 智能标记没有单独的搜索谓词。

>[!NOTE]
>
>智能内容服务是否能够在您的标记上进行培训并将其应用于其他图像，取决于您用于培训的图像质量。
>
>为获得最佳结果，Adobe建议您使用视觉上相似的图像来为每个标记培训服务。
