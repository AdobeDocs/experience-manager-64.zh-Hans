---
title: 创建和添加模板和组件
seo-title: Creating and Adding Templates and Components
description: 可查看本页以了解有关创建模板和组件并将其添加到应用程序的信息。 页面使用Geometrixx Unlimited应用程序作为包含示例应用程序模板和页面模板的应用程序。
seo-description: Follow this page to learn about creating and adding templates and components to your app. The page uses Geometrixx Unlimited App as the app that contains a sample app template and page templates.
uuid: 3a93017c-8094-413f-a01c-9b72025a2b20
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: ec4ada04-e429-4ad4-a060-2dccac847cf0
exl-id: 84eb552c-ba47-46e1-86e3-9460bd77dfbe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 1%

---

# 创建和添加模板和组件 {#creating-and-adding-templates-and-components}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（例如React）的项目使用SPA编辑器。 [了解详情](/help/sites-developing/spa-overview.md).

AEM Mobile On-Demand提供了完全配置的应用程序模板、文章模板和文章组件。

We.Unlimited App是一个示例模板，它代表一个完全可配置且可管理的AEM Mobile On-Demand应用程序的外壳。

创建新应用程序时选择此示例模板可提供AEM Mobile功能丰富的功能板。

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>要从AEM Mobile应用程序控制中心管理您的应用程序和移动设备应用程序内容，请参阅 [AEM Mobile应用程序功能板](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## 创建应用程序模板 {#creating-app-templates}

应用程序模板用于创建新应用程序，并充当页面模板和组件的集合，这些模板和组件表示应用程序的基线或基础。 该模板会标记一些基本属性，以便以适当的方式引导应用程序。 通常，客户总体上不会创建太多应用程序。

应用程序模板提供了一种轻松的方法来利用开发人员创建的现有设计，这些设计用于在AEM中创建新应用程序。

根据其他应用程序的模板创建新应用程序时，您将获得一个具有起点代表的应用程序，该应用程序是从中创建该应用程序的。

基于应用程序模板创建新应用程序的步骤：

1. 导航到AEM Mobile应用程序目录： *&lt;server-url>/aem/apps.html/content/mobileapps*
1. 选择 **创建** —> **应用程序** 如下所示

使用此模板创建应用程序后，您可以向应用程序添加文章、横幅和收藏集。 要重新访问、创建文章、横幅和收藏集，请参阅 [内容管理操作](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>或者，您也可以选择示例应用程序模板，例如 **我们，无限制** 应用程序，由AEM开发人员提供给您。 如果将此示例模板用于应用程序，则会获得一些可用的示例文章和收藏集。 您将可以选择使用示例模板和组件、自定义现有模板和组件，或为应用程序创建新模板和组件。

>[!CAUTION]
>
>设置 ***redirectTarget*** 属性
>
>使用其中一个应用程序模板时，开发人员定义应用程序的内容。 但是，开发人员必须了解在jcr中创建应用程序的位置以及的值 ***redirectTarget*** 属性。
>
>的 ***redirectTarget*** 会计算为创建应用程序操作的一部分，并尝试解析路径（如果存在可作为应用程序模板一部分的redirectTarget属性，且redirectTarget的值被定义为相对值）。 当创建应用程序进程在应用程序模板中找到redirectTarget的相对值时，该值会附加到创建应用程序的解析位置。
>
>例如，如果应用程序模板定义了 ***redirectTarget*** 值为“*lanage-masters/en*“ ”，且该应用程序是在“*/content/mobileapps/fooApp*&quot;，创建应用程序后，redirectTarget的最终值将为“*/content/mobileapps/fooApp/language-masters/en*&quot;

## 创建内容模板 {#creating-content-templates}

每个实体类型都有两个现成的模板。 这四个关键原则分别是：

* **默认模板：** 用于创建内容，其中包含适用的默认属性/结构
* **导入的模板：** 用于从AEM Mobile导入内容，且包含适用的默认属性/结构

### 文章模板 {#article-templates}

无限制文章是代表典型AEM Mobile On-Demand文章布局的示例模板。

1. 单击 **+** in **管理文章** 创建新文章。 您可以选择 **无限制文章** 或 **富文本文章**. 下图显示了选项，允许您从这两篇文章模板中的任意模板进行选择。

1. 单击 **下一个** 定义文章元数据，如文章名称/标题、描述、作者、抽象、部门、缩略图、文章访问次数等。
1. 单击 **下一个** 以填写广告属性。
1. 单击 **下一个** 输入文章图像或社交媒体图像
1. 单击 **下一个** 来选择收藏集链接。
1. 单击 **下一个** 以输入社交共享的详细信息。
1. 单击 **创建** 完成使用示例创建文章的过程。 单击 **完成** 或 **编辑文章** 编辑本文的属性。

![chlimage_1-71](assets/chlimage_1-71.png)

### 将组件添加到文章 {#adding-components-to-article}

创建后，作者可以通过添加文本和图像等组件来编辑文章的内容。 文章是AEM页面模板的扩展。

选择要编辑的文章，然后单击 **编辑** 向文章中添加组件。

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

选择“**+**”来向文章添加组件。

![chlimage_1-74](assets/chlimage_1-74.png)

### 创建现成模板 {#creating-out-of-the-box-templates}

没有现成的文章模板，但是自定义模板应该扩展的默认模板，请参阅Geometrixx Unlimited应用程序的 [文章模板示例](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

常规AEM模板以外需要属性的关键属性包括；

***dps-resourceType=&quot;dps:Article&quot;***

此属性可确保将AEM页面识别为AEM Mobile目标文章页面。

根据AEM模板，您可以向模板的 ***jcr:content***.

### 横幅和收藏集模板 {#banner-and-collection-templates}

>[!CAUTION]
>
>横幅和收藏集没有内容，因此其创建不支持自定义模板。

## 创建和添加组件 {#creating-and-adding-components}

组件使用并允许访问小组件，这些组件用于呈现内容。

代码存储库中包含一个简单的组件，其源可在AEM中找到。 随后，也可以在本地以CRXDE Lite打开。

>[!NOTE]
>
>目前没有为AEM Mobile提供现成的组件。

您可以向页面中添加组件。 任何组件都可以在AEM Mobile应用程序中使用，但在应用时，可能无法正确呈现。

但是，如果没有在AEM中呈现的自定义导出内容同步处理程序，自定义组件可能无法正确导出并上传到AEM Mobile On-demand Services。

在AEM页面中包含组件以及其他一些构建基块组件后，您可以向页面添加其他组件或编辑现有组件。

**要向页面添加其他组件，请执行以下操作：**

1. 选择该页面，并通过编辑器标题右上角的下拉菜单确保您处于编辑模式
1. 使用编辑器标题中最左侧的图标切换侧面板
1. 选择 **组件** 选项卡
1. 将其中一个可用组件拖放到页面上

![chlimage_1-75](assets/chlimage_1-75.png)

**要编辑现有组件，请执行以下操作：**

1. 选择该页面，并确保您位于 **编辑** 模式并选择组件
1. 点按扳手图标以配置组件

>[!NOTE]
>
>您可以在AEM中创建组件，并使用 [使用CRXDE Lite进行开发](/help/sites-developing/developing-with-crxde-lite.md). 根据需要自定义现有组件后，可以使用 **编辑** 选项 **管理文章** 如上图所示。

>[!NOTE]
>
>请参阅 [模板和组件开发的最佳实践](/help/mobile/best-practices-aem-mobile.md) 在AEM Mobile。

### 后续步骤 {#the-next-steps}

* [使用内容属性导出内容](/help/mobile/on-demand-content-properties-exporting.md)
* [具有内容同步的移动设备](/help/mobile/mobile-ondemand-contentsync.md)
