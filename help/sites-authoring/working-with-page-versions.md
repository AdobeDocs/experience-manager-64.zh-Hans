---
title: 处理页面版本
seo-title: Working with Page Versions
description: 创建、比较和恢复页面版本
seo-description: Create, compare, and restore versions of a page
uuid: b0328431-c2cf-48f4-b358-261238338241
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: fa331c03-5587-452d-ab96-ac2926ae0da3
exl-id: 2df7c08f-db17-4666-ba39-e81cc2e656d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 53%

---

# 处理页面版本{#working-with-page-versions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

版本控制可创建页面在特定时间点的“快照”。 通过版本控制，您可以执行以下操作：

* 创建页面版本。
* 将页面恢复到之前的版本，以撤消您对页面所做的更改，例如。
* 将页面的当前版本与之前版本进行比较，并突出显示文本和图像中的差异。

## 创建新版本 {#creating-a-new-version}

您可以通过以下方式创建某个版本的资源：

* the [时间轴边栏](#creating-a-new-version-timeline)
* the [创建](#creating-a-new-version-create-with-a-selected-resource) 选项（在选择资源时）

### 创建新版本 – 时间线 {#creating-a-new-version-timeline}

1. 导航以显示要为其创建版本的页面。
1. 在[选择模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中选择页面。
1. 打开 **时间轴** 列。
1. 单击/点按评论字段旁边的箭头以显示以下选项：

   ![screen_shot_2018-03-21at155035](assets/screen_shot_2018-03-21at155035.png)

1. 选择&#x200B;**保存为版本**。
1. 输入 **标签** 和 **注释** （如果需要）。

   ![chlimage_1-398](assets/chlimage_1-398.png)

1. 通过&#x200B;**创建**&#x200B;确认新版本。

   时间线中的信息将进行更新以指示该新版本。

### 创建新版本 – 通过选定的资源创建 {#creating-a-new-version-create-with-a-selected-resource}

1. 导航以显示要为其创建版本的页面。
1. 在[选择模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中选择页面。
1. 选择 **创建** 选项。
1. 此时将打开一个对话框。您可以输入 **标签** 和 **注释** （如果需要）：

   ![screen_shot_2012-02-15at105050am](assets/screen_shot_2012-02-15at105050am.png)

1. 通过&#x200B;**创建**&#x200B;确认新版本。

   将会打开时间线，并且其信息会更新以指示新版本。

## 还原到某个页面版本 {#reverting-to-a-page-version}

创建了版本之后，即可以根据需要还原到该版本。

>[!NOTE]
>
>恢复页面时，创建的版本将包含在新分支中。
>
>举例说明：
>
>* 为任意页面创建版本。
>* 初始的标签和版本节点名称将表示为 1.0、1.1、1.2，以此类推。
>* 恢复第一个版本；即1.0。
>* 再次创建新版本。
>* 生成的标签和节点名称现在将为1.0.0、1.0.1、1.0.2等。
>


还原到之前的版本：

1. 导航以显示要还原到之前版本的页面。
1. 在[选择模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中选择页面。
1. 打开“ **时间线** ”列，然后选择“ **显示全部** ”或“ **版本**”。 将列出所选页面的页面版本。
1. 选择要还原到的版本。 将显示可能的选项：

   ![screen_shot_2018-03-21at155246](assets/screen_shot_2018-03-21at155246.png)

1. 选择 **还原到此版本**. 将恢复到所选版本，并在时间线中更新信息。

## 预览版本 {#previewing-a-version}

您可以预览特定版本：

1. 导航以显示要比较的页面。
1. 在[选择模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中选择页面。
1. 打开&#x200B;**时间线**&#x200B;列，然后选择&#x200B;**显示全部**&#x200B;或&#x200B;**版本**。
1. 将列出页面版本。 选择要预览的版本：

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. 选择 **预览**. 该页面将显示在新选项卡中。

   >[!CAUTION]
   >
   >如果页面已移动，则无法再对移动前创建的任何版本执行预览。
   >
   >如果您遇到问题，请检查页面的[时间线](/help/sites-authoring/basic-handling.md#timeline)以查看页面是否已被移动。

## 将页面的某个版本与当前版本进行比较 {#comparing-a-version-with-current-page}

要将之前的版本与当前页面进行比较，请执行以下操作：

1. 导航以显示要比较的页面。
1. 在[选择模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中选择页面。
1. 打开&#x200B;**时间线**&#x200B;列，然后选择&#x200B;**显示全部**&#x200B;或&#x200B;**版本**。
1. 将列出页面版本。 选择要比较的版本：

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. 选择 **与当前比较**. 的 [页面差异](/help/sites-authoring/page-diff.md) 将打开并显示差异。

## 时间扭曲 {#timewarp}

时间扭曲是一项功能，旨在模拟过去特定时间某个页面的&#x200B;*已发布*&#x200B;状态。

其目的是允许您跟踪在选定时间点发布的网站。 它使用页面版本来确定发布环境的状态。

要执行此操作：

* 系统会查找在选定时间处于活动状态的页面版本。
* 这表示显示的版本已创建/激活 *之前* 在时间扭曲中选择的时间点。
* 当导航到已删除的页面时，也会呈现该页面 — 只要该页面的旧版本仍然位于存储库中即可。
* 如果没有找到发布的版本，则时间扭曲会还原到该页面在创作环境中的当前状态（这是为了防止出现错误/404 页面，此页面将阻止您进行浏览）。

### 使用时间扭曲 {#using-timewarp}

时间扭曲是 [模式](/help/sites-authoring/author-environment-tools.md#page-modes) 页面编辑器的页面编辑器。 要启动该模式，只需像切换任何其他模式一样切换该模式即可。

1. 为要启动时间扭曲的页面启动编辑器，然后选择 **时间扭曲** 中。

   ![screen_shot_2018-03-21at155416](assets/screen_shot_2018-03-21at155416.png)

1. 在对话框中设置目标日期和时间，然后单击或点按设 **置日期**。 如果不选择时间，则当前时间将默认。

   ![screen_shot_2018-03-21at155513](assets/screen_shot_2018-03-21at155513.png)

1. 将根据设置的日期显示页面。 时间扭曲模式通过窗口顶部的蓝色状态栏来指示。 使用状态栏中的链接选择新的目标日期或退出时间扭曲模式。

   ![screen_shot_2018-03-21at155544](assets/screen_shot_2018-03-21at155544.png)

### 时间扭曲限制

时间扭曲会尽量在选定的时刻重现页面。但是，由于在 AEM 中连续创作内容的过程非常复杂，并非总能实现这一点。在使用时间扭曲时，应牢记以下限制。

* **时间扭曲基于已发布的页面工作** – 仅当您之前已发布页面时，时间扭曲才会完全正常工作。如果没有，时间扭曲将在创作环境显示当前页面。
* **时间扭曲使用页面版本** – 当您浏览到的页面已从存储库删除时，如果该页面的旧版本仍然位于存储库中，则该页面将会正常呈现。
* **已删除的版本会影响时间扭曲** – 如果从存储库从删除了版本，那么时间扭曲无法显示正确的视图。
* **时间扭曲为只读** – 您无法编辑页面的旧版本。旧版本仅供查看。如果要恢复旧版本，则必须使用恢复功能手动恢复。
* **时间扭曲仅基于页面内容** – 如果呈现网站的元素（如代码、css、资产/图像等）发生更改，则视图将与它原来的样子不同，因为这些项目不在存储库中进行版本控制。

>[!CAUTION]
>
>时间扭曲旨在作为一种工具，帮助作者理解和创建其内容。 而不是用作审查日志或用于法律目的。
