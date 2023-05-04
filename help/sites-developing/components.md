---
title: 组件概述
seo-title: Components
description: 组件是模块化单元，可实施特定功能以在您的网站上展示您的内容
seo-description: Components are modular units which realize specific functionality to present your content on your website
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
exl-id: 3444d7df-fc43-4383-87b0-0f00fef116bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 49%

---

# 组件概述{#components-overview}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

此页面概述了 Adobe Experience Manager (AEM) 组件，例如那些[用于页面创作](/help/sites-authoring/default-components-foundation.md)的组件。

## 什么是组件？ {#what-exactly-is-a-component}

* 模块化单元，可实施特定功能以在您的网站上展示您的内容。
* 可重用的。
* 作为存储库的一个文件夹中的独立单元开发。
* 没有隐藏的配置文件。
* 可以包含其他组件。
* 可以在任何AEM系统内的任何位置运行。 这些组件也可限制在特定组件下运行。
* 拥有标准化的用户界面。
* 具有可配置的编辑行为。
* 使用基于Granite UI组件使用子元素构建的对话框
* 使用 [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) （推荐）或JSP。
* 可以开发以创建扩展默认功能的自定义组件。

由于组件是模块化的，因此您可以：

* 在本地实例上开发新组件。
* 将它部署到测试环境。
* 将它部署到实时创作环境，作者和/或管理员可在该环境中添加和配置内容。
* 将它部署到实时发布环境，它在该环境中用于为您网站的访客呈现内容。某些组件（例如，社区组件）也接受用户的输入。

每个 AEM 组件：

* 是一种资源类型。
* 是一个完全实施特定功能的脚本的集合。
* 可以在中运行 *隔离*，即在AEM或门户中。

## AEM中的现成组件 {#out-of-the-box-components-within-aem}

AEM附带多种 [开箱即用的组件](/help/sites-authoring/default-components.md) 提供全面功能，包括：

* 段落系统 ( `parsys`)
* 页面( `responsivegrid`  — 仅限触屏优化UI)
* 文本
* 图像，带有随附的文本
* 工具栏

提供的组件及其在 [示例We.Retail网站](/help/sites-developing/we-retail.md) 提供了如何实施和使用组件的说明。 这些组件随所有源代码一起提供，可以按原样使用或用作已修改或扩展的组件的起点。

### 核心组件和基础组件 {#core-components-and-foundation-components}

提供了两组Adobe提供的AEM组件：

* [核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hans)
* [基础组件](/help/sites-authoring/default-components-foundation.md)

**核心组件** 已在AEM 6.3中引入，并提供了灵活且功能丰富的创作功能。 的 [We.Retail参考网站](/help/sites-developing/we-retail.md) 说明核心组件的使用方式，并代表组件开发的当前最佳实践。

**基础组件** 已在许多版本的AEM中提供，并且在标准AEM安装中现成可用。 尽管仍受支持，但大多数已弃用，不再进行增强，并且基于旧版技术。

>[!NOTE]
>
>[核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hans) 代表组件设计和开发的当前最佳实践，并用作参考实施。
>
>[AEM现代化工具](modernization-tools.md) 有助于迁移到核心组件。

### 查看可用组件 {#viewing-available-components}

有关 AEM 实例中的所有可用组件的概述，请使用[组件控制台](/help/sites-authoring/default-components-console.md)。

或者，您也可以使用 CRXDE Lite 获取存储库中所有可用组件的列表。

1. 在 **[!UICONTROL CRXDE Lite]** 中，从工具栏中选择&#x200B;**[!UICONTROL 工具]**，然后选择&#x200B;**[!UICONTROL 查询]**，这将打开&#x200B;**[!UICONTROL 查询]**&#x200B;选项卡。

1. 在&#x200B;**[!UICONTROL 查询]**&#x200B;选项卡中，选择 `XPath` 作为&#x200B;**[!UICONTROL 类型]**。

1. 在&#x200B;**[!UICONTROL 查询]**&#x200B;输入字段中，输入以下字符串：

   `//element(*, cq:Component)`

1. 单击&#x200B;**[!UICONTROL 执行]**，这将列出组件。

## 其他资源 {#further-reading}

以下页面提供了有关开发这些组件和其他组件的更多详细信息：

* [AEM组件 — 基础知识](/help/sites-developing/components-basics.md)
* [开发AEM组件](/help/sites-developing/developing-components.md)
* [开发AEM组件 — 代码示例](/help/sites-developing/developing-components-samples.md)
* [配置多个就地编辑器](/help/sites-developing/multiple-inplace-editors.md)
* [开发人员模式](/help/sites-developing/developer-mode.md)
* [测试您的UI](/help/sites-developing/hobbes.md)
* [内容片段的组件](/help/sites-developing/components-content-fragments.md)
* [以JSON格式获取页面信息](/help/sites-developing/pageinfo.md)
* [组件国际化](/help/sites-developing/i18n.md)
* [核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hans)
* [使用隐藏条件](/help/sites-developing/hide-conditions.md)
* 经典 UI

   * [AEM组件（经典UI）](/help/sites-developing/developing-components-classic.md)
   * [使用和扩展小组件（经典UI）](/help/sites-developing/widgets.md)
   * [使用xtype（经典UI）](/help/sites-developing/xtypes.md)
   * [开发Forms（经典UI）](/help/sites-developing/developing-forms.md)
