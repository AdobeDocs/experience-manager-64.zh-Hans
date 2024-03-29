---
title: 为 AEM 开发 SPA
seo-title: Developing SPAs for AEM
description: 本文介绍了在让前端开发人员开发AEM的SPA时应考虑的重要问题，并概述了在部署AEM上开发的SPA时要记住的AEM与SPA的架构。
seo-description: This article presents important questions to consider when engaging a front-end developer to develop a SPA for AEM as well as gives an overview of the architecture of AEM with respect to SPAs to keep in mind when deploying a developed SPA on AEM.
uuid: c77b37be-6acc-4cb4-9ae3-ba09583e6fff
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 3f4c17cf-6f77-4a87-b27b-f13a6a976523
exl-id: 7b9f21eb-22f6-42f7-8dc7-770601ef51fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2185'
ht-degree: 5%

---

# 为 AEM 开发 SPA{#developing-spas-for-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

单页应用程序 (SPA) 可以为网站用户提供引人入胜的良好体验。开发人员希望能够使用 SPA 框架构建站点，而作者则希望能够在 AEM 中顺畅地为使用此类框架构建的站点编辑内容。

本文介绍了在让前端开发人员开发SPA for AEM时应考虑的重要问题，并概述了AEM在AEM上部署SPA的架构。

>[!NOTE]
>
>单页应用程序(SPA)编辑器功能需要AEM 6.4 Service Pack 2或更高版本。
>
>对于需要基于SPA框架的客户端渲染(例如，React或Angular)的项目，推荐使用SPA编辑器解决方案。

## AEM 项目原型 {#aem-project-archetype}

任何 AEM 项目都应使用 [AEM 项目原型](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)，它支持使用 React 或 Angular 的 SPA 项目并利用 SPA SDK。

## SPA的AEM开发原则 {#spa-development-principles-for-aem}

在 AEM 上开发单页应用程序时，假定前端开发人员在创建 SPA 时遵循标准最佳实践。如果您作为前端开发人员，遵循以下一般最佳实践以及一些特定于AEM的原则，则您的SPA将能够在 [AEM及其内容创作功能](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa).

* **[便携性](/help/sites-developing/spa-architecture.md#portability) -** 与任何组件一样，组件应该构建为尽可能便携。 SPA应使用可移植且可重复使用的组件构建，以避免引用内容结构的静态路径。
* **[AEM驱动器站点结构](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)**  — 前端开发人员创建组件并拥有其内部结构，但依赖AEM来定义网站的内容结构。
* **[动态渲染](/help/sites-developing/spa-architecture.md#dynamic-rendering) -** 所有渲染都应是动态的。
* **[动态路由](#dynamic-routing) -** SPA负责路由，AEM会侦听该路由并基于该路由获取组件数据。 任何路由也应是动态的。

在开发SPA时，如果您牢记这些原则，那么在启用所有受支持的AEM创作功能时，将尽可能灵活地进行未来验证。

如果您不需要支持AEM创作功能，则可能需要考虑其他 [SPA设计模型](/help/sites-developing/spa-architecture.md#spa-design-models).

### 便携性 {#portability}

与开发任何组件一样，您的组件的设计方式应最大限度地提高其可移植性。 任何与组件的可移植性或可重用性相抵触的模式都应避免，以确保今后的兼容性、灵活性和可维护性。

开发人员应避免使用引用内容结构的静态路径，因为内容作者可以随时修改路径。 这也会限制库的可重用性，并且会阻止使用AEM模板编辑器，因为其结构位于内容以外的其他位置。

生成的SPA应使用高度可移植和可重复使用的组件构建。

### AEM驱动器站点结构 {#aem-drives-site-structure}

前端开发人员必须认为自己负责创建用于构建应用程序的SPA组件库。 前端显影器对组件的内部结构具有完全的控制。 [但AEM始终拥有网站的结构。](/help/sites-developing/spa-overview.md)

这意味着前端开发人员可以在组件入口点之前或之后添加客户内容，还可以在组件内进行第三方调用。 但是，前端开发人员并不能完全控制组件的嵌套方式，例如。

### 动态渲染 {#dynamic-rendering}

SPA应仅依赖于内容的动态渲染。 这是AEM获取并呈现内容结构所有子项的默认期望值。

指向特定内容的任何显式渲染都被视为静态渲染，尽管受支持，但将与AEM内容创作功能不兼容。 这也违背了 [便携性](/help/sites-developing/spa-architecture.md#portability).

### 动态路由 {#dynamic-routing}

与渲染一样，所有路由也应是动态的。 在AEM中， [SPA应始终拥有路由](/help/sites-developing/spa-routing.md) 和AEM会侦听数据，并据此获取内容。

任何静态路由都适用于 [便携性原则](/help/sites-developing/spa-architecture.md#portability) 和通过与AEM的内容创作功能不兼容来限制作者。 例如，使用静态路由时，如果内容作者想要更改路由或更改页面，则他/她将必须要求前端开发人员执行此操作。

## SPA设计模型 {#spa-design-models}

如果 [在AEM中开发SPA的原则](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) 之后，您的SPA将能够使用所有受支持的AEM内容创作功能正常工作。

但是，在有些情况下，这并非完全必要。 下表概述了各种设计模型、其优点和缺点。

<table> 
 <tbody>
  <tr>
   <th><strong>设计模型<br /> </strong></th> 
   <th><strong>优点</strong></th> 
   <th><strong>缺点</strong></th> 
  </tr>
  <tr>
   <td>AEM用作无头CMS，而不使用 <a href="/help/sites-developing/spa-reference-materials.md">SPA Editor SDK框架。</a></td> 
   <td>前端开发人员完全控制应用程序。</td> 
   <td><p>内容作者无法利用AEM内容创作体验。</p> <p>如果代码包含静态引用或路由，则该代码既不可移植，也不可重复使用。</p> <p>不允许使用模板编辑器，因此前端开发人员必须通过JCR维护可编辑的模板。</p> </td> 
  </tr>
  <tr>
   <td>前端开发人员使用SPA Editor SDK框架，但只向内容作者打开一些区域。</td> 
   <td>开发人员只允许在应用程序的限制区域中进行创作，从而保持对应用程序的控制。</td> 
   <td><p>内容作者仅受一组有限的AEM内容创作体验的限制。</p> <p>如果代码包含静态引用或路由，则它既不可移植，也不可重复使用。</p> <p>不允许使用模板编辑器，因此前端开发人员必须通过JCR维护可编辑的模板。</p> </td> 
  </tr>
  <tr>
   <td>项目可充分利用SPA Editor SDK，并且前端组件将开发为库，应用程序的内容结构将委派给AEM。</td> 
   <td><p>该应用程序可重复使用且可移植。</p> <p>内容作者可以使用AEM内容创作体验编辑应用程序。<br /> </p> <p>SPA与模板编辑器兼容。</p> </td> 
   <td><p>开发人员无法控制应用程序的结构和委派给AEM的内容部分。</p> <p>开发人员仍可以将应用程序的区域保留为不打算使用AEM创作的内容。</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>尽管AEM中支持所有模型，但只能通过实施第三个模型(从而遵循建议的 [SPA的AEM开发原则](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem))内容作者将能够像往常一样与AEM中的SPA内容进行交互和编辑。

## 将现有SPA迁移到AEM {#migrating-existing-spas-to-aem}

通常，如果您的SPA遵循 [SPA的AEM开发原则](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)，则您的SPA将在AEM中工作，并可使用AEM SPA编辑器进行编辑。

按照以下步骤操作，使现有SPA可以随时使用AEM。

1. **将JS组件设为模块化。**

   使其能够按任意顺序、位置和大小呈现。

1. **使用我们的SDK提供的容器将您的组件放在屏幕上。**

   AEM提供了一个页面和段落系统组件供您使用。

1. **为每个JS组件创建一个AEM组件。**

   AEM组件定义对话框和JSON输出。

## 面向前端开发人员的说明 {#instructions-for-front-end-developers}

让前端开发人员为AEM创建SPA的主要任务是就组件及其JSON模型达成一致。

以下是前端开发人员在开发SPA for AEM时需要遵循的步骤概要。

1. **同意组件及其JSON模型**

   前端开发人员和后端AEM开发人员需要就哪些组件是必需的以及模型达成一致，以便从SPA组件到后端组件之间实现一对一的匹配。

   AEM组件在提供编辑对话框和导出组件模型时仍然是必需的。

1. **在React组件中，通过`this.props.cqModel`**

   在同意组件并且JSON模型到位后，前端开发人员便可以免费开发SPA，只需通过访问JSON模型即可 `this.props.cqModel`.

1. **实施组件的 `render()` 方法**

   前端开发人员实施 `render()` 方法，并可使用 `cqModel` 属性。 这会输出将插入页面的DOM和HTML片段。 这是在React中构建应用程序的标准方式。

1. **通过将组件映射到AEM资源类型`MapTo()`**

   映射存储组件类，并由提供的在内部使用 `Container` 组件来检索和动态实例化基于给定资源类型的组件。

   它用作前端和后端之间的“胶水”，以便编辑器了解反应组件对应的组件。

   的 `Page` 和 `ResponsiveGrid` 是扩展基础的类的好示例 `Container`.

1. **定义组件的 `EditConfig` 作为参数`MapTo()`**

   此参数对于告知编辑器组件在尚未渲染或没有要渲染的内容时应该如何命名。

1. **扩展提供的 `Container` 页面和容器的类**

   页面和段落系统应扩展此类，以便委派到内部组件可以按预期工作。

1. **实施使用HTML5的路由解决方案 `History` API。**

   当 `ModelRouter` 启用，调用 `pushState` 和 `replaceState` 函数将触发对的请求 `PageModelManager` 以获取模型的缺失片段。

   的当前版本 `ModelRouter` 仅支持使用指向Sling模型入口点实际资源路径的URL。 它不支持使用虚URL或别名。

   的 `ModelRouter` 可以禁用或配置为忽略正则表达式列表。

## 与AEM无关 {#aem-agnostic}

这些代码块说明了您的React和Angular组件不需要任何特定于Adobe或AEM的内容。

* JavaScript组件内的所有内容都与AEM无关。
* 但是，AEM的特定功能是，JS组件必须通过MapTo帮助程序映射到AEM组件。

![screen_shot_2018-12-11at144019](assets/screen_shot_2018-12-11at144019.png)

的 `MapTo` 帮助程序是允许后端和前端组件相匹配的“胶水”：

* 它可告知JS容器（或JS段落系统），JS组件负责渲染JSON中存在的每个组件。
* 它会向JS组件呈现的HTML中添加HTML数据属性，以便SPA编辑器知道在编辑组件时要向作者显示的对话框。

有关使用的更多信息 `MapTo` 和一般构建AEM的SPA，请参阅所选框架的快速入门指南。

* [AEM - React中的SPA快速入门](/help/sites-developing/spa-getting-started-react.md)
* [AEM SPA快速入门 — Angular](/help/sites-developing/spa-getting-started-angular.md)

## AEM架构和SPA {#aem-architecture-and-spas}

使用SPA时，AEM的常规架构（包括开发、创作和发布环境）不会发生更改。 但是，了解SPA开发如何融入此架构将会有所帮助。

![screen_shot_2018-12-11at145348](assets/screen_shot_2018-12-11at145348.png)

* **构建环境**

   这是签出SPA应用程序源和组件源的源位置。

   * NPM clientlib生成器从SPA项目创建客户端库。
   * 该库将由Maven获取，并由Maven Build插件以及组件一起部署到AEM Author。

* **AEM Author**

   内容是在AEM作者上创建的，包括创作SPA。

   在创作环境中使用SPA编辑器编辑SPA时：

   1. SPA请求外部HTML。
   1. 将加载CSS。
   1. 将加载SPA应用程序的Javascript。
   1. 执行SPA应用程序时，将请求JSON，以允许应用程序构建页面的DOM，包括 `cq-data` 属性。
   1. 此 `cq-data` 属性允许编辑器加载其他页面信息，以便它知道哪些编辑配置可用于组件。

* **AEM 发布**

   这是发布创作内容和编译的库(包括SPA应用程序对象、clientlib和组件)以供公众使用的地方。

* **Dispatcher/CDN**

   调度程序用作网站访客的AEM缓存层。

   * 处理请求的方式与在AEM作者中类似，但是没有对页面信息提出请求，因为只有编辑者才需要这样做。
   * Javascript、CSS、JSON和HTML已缓存，可优化页面以便快速交付。

>[!NOTE]
>
>在AEM中，无需执行Javascript构建机制或执行Javascript本身。 AEM仅托管SPA应用程序中的已编译工件。

## 后续步骤 {#next-steps}

有关AEM中简单SPA的结构方式及其工作方式的概述，请参阅这两者的入门指南 [React](/help/sites-developing/spa-getting-started-react.md) 和 [Angular](/help/sites-developing/spa-getting-started-angular.md).

有关创建您自己的SPA的分步指南，请参阅 [AEM SPA Editor - WKND事件入门教程](https://helpx.adobe.com/cn/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

有关动态模型到组件映射以及它如何在AEM的SPA中工作的更多详细信息，请参阅文章 [适用于SPA的动态模型到组件映射](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

如果您希望在AEM中为除React或Angular之外的其他框架实施SPA，或者只想深入了解SPA SDK for AEM的工作方式，请参阅 [SPA Blueprint](/help/sites-developing/spa-blueprint.md) 文章。
