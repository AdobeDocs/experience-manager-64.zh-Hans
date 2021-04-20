---
title: 智能内容服务培训指南
description: 培训AI服务以将智能标签应用于资产
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 11%

---


# 智能内容服务培训指南{#smart-content-service-training-guidelines}

为了能够有效地标记您的品牌图像，智能内容服务要求培训图像符合某些准则。

## 培训准则{#guidelines-for-training}

为获得最佳效果，培训集中的图像应符合以下准则：

**数量和大小：每** 个标 **签至少30张图像**。长边至少 500 像素。

**一致**:标签的图像应当看上去相似。

例如，将所有这些图像标记为&#x200B;*my-party*（用于培训）并不是个好主意，因为它们在视觉上并不相似。

![说明性图像以说明培训准则](assets/do-not-localize/coherence.png)

**覆盖**:培训中的图像应该有足够的多样性。我们的想法是提供一些比较多样的例子，以便AEM学会专注于正确的事情。 如果要对视觉上不同的图像应用相同的标签，请至少包含每种类型的五个示例。

例如，对于标签&#x200B;*model-down-pose*，包含更多与下面突出显示的图像相似的培训图像，以便服务在标记期间更准确地识别类似图像。

![说明性图像以说明培训准则](assets/do-not-localize/coverage_1.png)

**分散注意力/妨碍**:该服务对分散注意力的图像（突出的背景、不相关的伴奏，如与主题有关的物体/人）进行了更好的培训。

例如，对于标签&#x200B;*休闲鞋*，第二幅图像不是好的培训候选者。

![说明性图像以说明培训准则](assets/do-not-localize/distraction.png)

**完整性：**&#x200B;如果图像符合多个标记的条件，请在包含培训图像之前添加所有适用的标记。例如，对于 *Raincoat* 和 *model-side-view* 等标记，在将其加入培训之前，在符合条件的资产上添加这两个标记。

![说明性图像以说明培训准则](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增强的智能标签基于品牌图像及其标签的学习模型。 这些模型并不总是能够完美地识别标签。 智能内容服务的当前版本具有以下限制：

* 无法识别图像中的细微差异。 比如，修身与普通衬衫。
* 无法根据图像的微小图案/部分识别标记。 例如，T恤上的徽标。
* 在支持AEM的区域设置中支持标记。 有关语言列表，请参阅[智能内容服务发行说明](/help/release-notes/smart-content-service-release-notes.md)。

要使用智能标记（常规或增强）搜索资产，请使用资产全屏搜索（全文搜索）。 智能标记没有单独的搜索谓词。

>[!NOTE]
>
>智能内容服务是否能够对您的标签进行培训并将它们应用于其他图像，这取决于您用于培训的图像质量。
>
>为获得最佳效果，Adobe建议您使用视觉上相似的图像来针对每个标签培训服务。

