---
title: 在We.Retail中尝试内容片段
seo-title: Trying out Content Fragments in We.Retail
description: 在We.Retail中尝试内容片段
seo-description: null
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
exl-id: d93bec03-c651-4329-b220-4ac1ea189de1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 20%

---

# 在We.Retail中尝试内容片段{#trying-out-content-fragments-in-we-retail}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

内容片段允许您创建渠道中性内容，以及各种（特定于渠道的）变量。**We.Retail** (在AEM的现成实例中可用)提供片段 **洛福滕的北极冲浪** 作为基本示例。 这说明：

* Adobe Experience Manager (AEM) 内容片段[作为独立于页面的资产而创建和管理](/help/assets/content-fragments.md)。这允许您创建渠道中性内容，以及各种（特定于渠道的）变体。

   * 请参阅 [在We.Retail中的何处查找内容片段资产](#where-to-find-content-fragments-in-we-retail)

* 然后，您可以 [在创作时使用这些片段及其变量](/help/sites-authoring/content-fragments.md) 您的内容页面。

   * 请参阅 [在We.Retail中使用内容片段的位置](#where-content-fragments-are-used-in-we-retail)

有关创建、管理、使用和开发内容片段的完整文档：

* 请参阅 [更多信息](#further-information)

>[!NOTE]
>
>**内容片段**&#x200B;和&#x200B;**[体验片段](/help/sites-authoring/experience-fragments.md)**&#x200B;是 AEM 中的两个不同功能：
>
>* **内容片段**&#x200B;是可编辑内容，主要为文本和相关图像。它们是纯内容，无需设计和布局。
>* **体验片段**&#x200B;是经过充分布局的内容；例如，网页的一个片段。
>
>体验片段可以包含内容片段形式的内容，反之则不行。

## 在We.Retail中的何处查找内容片段 {#where-to-find-content-fragments-in-we-retail}

We.Retail中有几个示例内容片段；导航 **资产**, **文件**, **We.Retail**, **英语**, **体验**.

这包括 **洛福滕的北极冲浪**，片段以及相关的可视化资产：

* 导航方式 **资产**, **文件**, **We.Retail**, **英语**, **体验**, **罗福腾的艺术冲浪**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![cf-44](assets/cf-44.png)

您可以选择和编辑 **洛福滕的北极冲浪** 片段：

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

在这里，您可以 [编辑和管理](/help/assets/content-fragments.md) 使用选项卡（左侧面板）生成片段：

![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png)

* **[变体](/help/assets/content-fragments-variations.md)** 包括 [Markdown](/help/assets/content-fragments-markdown.md)

* **[关联的内容](/help/assets/content-fragments-assoc-content.md)**
* **[元数据](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## 在We.Retail中使用内容片段的位置 {#where-content-fragments-are-used-in-we-retail}

举例说明 [使用内容片段进行页面创作](/help/sites-authoring/content-fragments.md) 下面提供了多个示例页面，例如：

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

例如， **洛福滕的北极冲浪** 内容片段在站点页面中引用：

* 导航方式 **站点**, **We.Retail**, **语言母版**, **英语**, **体验**. 然后打开 **洛福滕的北极冲浪** 进行编辑：

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## 更多信息 {#further-information}

有关更多详细信息，请参阅：

* [使用内容片段](/help/assets/content-fragments.md)

   * 了解如何创建、编辑和管理内容片段资产。

* [使用内容片段进行页面创作](/help/sites-authoring/content-fragments.md)

   * 在创作页面时使用内容片段。

* [开发AEM — 内容片段的组件](/help/sites-developing/components-content-fragments.md)

   * 内容片段的组件概述。

* [开发和扩展内容片段](/help/sites-developing/customizing-content-fragments.md)

   * 此信息可帮助您开发和扩展内容片段。
