---
title: 提升启动项
seo-title: Promoting Launches
description: 在发布之前，您需要提升启动页面以将内容移回源（生产）。
seo-description: You need to promote launch pages to move the content back into the source (production) before publishing.
uuid: 56483f8f-d66e-4677-a7bd-3b1425625b2b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 977a3dda-4292-4bd2-bfa5-af4d789d9ef9
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 2a790f7d-03a1-4f60-a59e-0a5f15c44fa5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 19%

---

# 提升启动项{#promoting-launches}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在发布之前，您需要提升启动页面以将内容移回源（生产）。 提升启动页面时，源页面的对应页面将被替换为提升页面的内容。 提升启动项页面时，可以使用以下选项：

* 是仅提升当前页面还是提升整个启动项。
* 是否提升当前页面的子页面。
* 是提升完整启动项，还是仅提升已更改的页面。

>[!NOTE]
>
>将启动项页面提升到目标后(**生产**)，您可以激活 **生产** 页面作为实体（以加快处理速度）。 将页面添加到工作流包中，并将其用作激活页面包的工作流的有效负荷。 您需要先创建工作流包，然后再提升启动项。 请参阅 [使用AEM工作流处理提升的页面](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>不能同时提升单个启动项。 这意味着，对同一个启动项同时执行两次提升操作可能会导致出现以下错误：`Launch could not be promoted`（同时还会导致日志中出现冲突错误）。

>[!CAUTION]
>
>提升启动项时 *修改* 页面时，会考虑源分支和启动分支中的修改。

## 提升启动页面 {#promoting-launch-pages}

>[!NOTE]
>
>这包括在只有一个启动级别时提升启动页面的手动操作。 请参阅：
>
>* [提升嵌套启动项](#promoting-a-nested-launch) 当结构中有多个启动项时。
>* [启动项 — 事件的顺序](/help/sites-authoring/launches.md#launches-the-order-of-events) 有关自动升级和发布的更多详细信息。
>


您可以从 **站点** 控制台或 **启动项** 控制台：

1. 打开：

   * the **站点** 控制台：

      1. 打开[引用边栏](/help/sites-authoring/author-environment-tools.md#references)，然后使用[选择模式](/help/sites-authoring/basic-handling.md)选择所需的源页面（或者先进行选择，然后再打开引用边栏，顺序不重要）。此时将显示所有引用。

      1. 选择 **启动项** (例如，启动项(1))以显示特定启动项的列表。
      1. 选择特定的启动项以显示可用的操作。
      1. 选择&#x200B;**提升启动项**&#x200B;以打开向导。
   * the **启动项** 控制台：

      1. 选择启动项（点按/单击缩略图）。
      1. 选择 **提升**.


1. 在第一步中，您可以指定：

   * **提升整个发布内容**
   * **提升已修改的页面**
   * **提升当前页面**
   * **提升当前页面和子页面**

   例如，当选择仅提升已修改的页面时：

   ![chlimage_1](assets/chlimage_1.png)

   >[!NOTE]
   >
   >这涵盖单个启动项，如果您有嵌套的启动项，请参阅 [提升嵌套启动项](#promoting-a-nested-launch).

1. 选择 **下一个** 以继续。
1. 您可以查看要提升的页面，具体页面将取决于您选择的页面范围：

   ![chlimage_1-1](assets/chlimage_1-1.png)

1. 选择 **提升**.

## 编辑时提升启动页面 {#promoting-launch-pages-when-editing}

编辑启动页面时， **提升启动项** 操作也可从 **页面信息**. 这将打开相应向导来收集所需的信息。

![chlimage_1-2](assets/chlimage_1-2.png)

>[!NOTE]
>
>此功能适用于单个和 [嵌套启动项](#promoting-a-nested-launch).

## 提升嵌套启动项 {#promoting-a-nested-launch}

创建嵌套启动项后，您可以将其提升回任何源，包括根源（生产）。

![chlimage_1-3](assets/chlimage_1-3.png)

1. 与 [创建嵌套启动项](/help/sites-authoring/launches-creating.md#creating-a-nested-launch)，在 **启动项** 控制台或 **引用** 边栏。
1. 选择&#x200B;**提升启动项**&#x200B;以打开向导。

1. 输入所需的详细信息：

   * **提升目标**

      您可以向任何来源提升。

   * **范围**
在此，您可以选择是提升整个启动项，还是仅提升已实际编辑的页面。 如果是后者，则可以选择包含/排除子页面。 默认配置是仅提升当前页面的页面更改：

      * **提升整个发布内容**
      * **提升已修改的页面**
      * **提升当前页面**
      * **提升当前页面和子页面**

   ![chlimage_1-4](assets/chlimage_1-4.png)

1. 选择&#x200B;**下一步**。
1. 在选择&#x200B;**提升**&#x200B;之前查看提升详细信息：

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >列出的页面将取决于 **范围** 定义的页面，可能还有实际已编辑的页面。

1. 您的更改将被提升并反映在 **启动项** 控制台：

   ![chlimage_1-6](assets/chlimage_1-6.png)

## 使用 AEM 工作流处理提升的页面 {#processing-promoted-pages-using-aem-workflow}

使用工作流模型对提升的启动项页面执行批量处理：

1. 创建工作流包。
1. 作者提升启动页面时，会将其存储在工作流包中。
1. 使用包作为有效负载，启动工作流模型。

要在提升页面时自动启动工作流， [配置工作流启动器](/help/sites-administering/workflows-starting.md#workflows-launchers) 的子域。

例如，当作者提升启动项页面时，您可以自动生成页面激活请求。 配置工作流启动器，以在修改包节点时启动请求激活工作流。

![chlimage_1-7](assets/chlimage_1-7.png)
