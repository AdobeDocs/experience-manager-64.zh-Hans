---
title: 应用程序模板和组件
seo-title: App Templates and Components
description: 可查看本页以了解应用程序模板和组件。 它提供了有关模板结构的详细信息。
seo-description: Follow this page to learn about App Templates and Components. It provides detailed information on the structure of templates.
uuid: ba2fd91b-de5a-4f39-a976-5455f9983669
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 7f31c6a7-92d5-4a87-a9f0-68a82b834d5a
exl-id: 5480ac38-f651-4211-94f6-c588fb44ad55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---

# 应用程序模板和组件{#app-templates-and-components}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（例如React）的项目使用SPA编辑器。 [了解详情](/help/sites-developing/spa-overview.md).

模板用于创建页面并定义可在所选范围内使用的组件。 模板是节点的层次结构，其结构与要创建的页面相同，但没有任何实际内容。

每个模板都将为您提供一系列可供使用的组件。

* 模板由 [组件](/help/sites-developing/components.md);
* 组件使用和允许访问小组件，这些组件用于呈现内容。

>[!NOTE]
>
>要了解如何使用CRXDE Lite开发AEM应用程序，请参阅 [使用CRXDE Lite进行开发](/help/sites-developing/developing-with-crxde-lite.md).

模板是页面的基础。

要创建页面，必须复制模板（节点树） **/apps/&lt;myapp>/templates/&lt;mytemplate>**)到站点树中的相应位置：如果使用 **网站** 选项卡。

此复制操作还会为页面提供其初始内容（通常仅限顶级内容）和属性sling:resourceType，用于呈现页面的页面组件的路径（子节点jcr:content中的所有内容）。

## 模板的结构 {#structure-of-a-template}

需要考虑两个方面：

* 模板本身的结构
* 使用模板时生成的内容的结构

在类型的节点下创建模板 **cq：模板**.

可以设置各种属性，特别是：

* **jcr:title**  — 模板的标题；创建页面时，会显示在对话框中。
* **jcr:description**  — 模板描述；创建页面时，会显示在对话框中。

此节点包含 *jcr:content(cq:PageContent)* 节点，用作生成页面内容节点的基础；此参考，使用 *sling:resourceType*，用于呈现新页面实际内容的组件。

>[!NOTE]
>
>要了解AEM中模板和组件的基础知识，请参阅以下资源：
>
>* [模板](/help/sites-developing/templates.md)
>* [组件](/help/sites-developing/components.md)
>


在您基本了解模板和组件后，请参阅以下资源：

* [创建和添加模板和组件](/help/mobile/mobile-ondemand-app-templates.md)
* [使用内容属性导出内容](/help/mobile/on-demand-content-properties-exporting.md)
* [最佳实践](/help/mobile/best-practices-aem-mobile.md)
* [开发AEM Mobile内容服务](/help/mobile/developing-content-services.md)

### 其他资源 {#additional-resources}

要了解有关移动设备应用程序的其他主题，请参阅以下链接：

* [具有内容同步的移动设备](/help/mobile/mobile-ondemand-contentsync.md)
* [测试移动设备应用程序](/help/mobile/develop-mobile-apps-testing.md)
