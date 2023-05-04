---
title: 适用于SPA的动态模型到组件映射
seo-title: Dynamic Model to Component Mapping for SPAs
description: 本文介绍了在适用于AEM的Javascript SPA SDK中如何进行动态模型到组件的映射。
seo-description: This article describes how the dynamic model to component mapping occurs in the Javascript SPA SDK for AEM.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 2bbbfbaa-b0a1-4f8a-9445-51325d80e368
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 1%

---

# 适用于SPA的动态模型到组件映射{#dynamic-model-to-component-mapping-for-spas}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本文档介绍如何在适用于AEM的Javascript SPA SDK中进行动态模型到组件的映射。

>[!NOTE]
>单页应用程序(SPA)编辑器功能需要AEM 6.4 Service Pack 2或更高版本。
>
>对于需要基于SPA框架的客户端渲染(例如，React或Angular)的项目，推荐使用SPA编辑器解决方案。

## 组件映射模块 {#componentmapping-module}

的 `ComponentMapping` 模块作为NPM包提供到前端项目。 它存储前端组件，并为单页应用程序提供了一种将前端组件映射到AEM资源类型的方法。 这样，在解析应用程序的JSON模型时，就可以动态解析组件。

模型中存在的每个项目都包含 `:type` 公开AEM资源类型的字段。 装载后，前端组件可以使用从基础库收到的模型片段呈现自身。

请参阅 [SPA Blueprint](/help/sites-developing/spa-blueprint.md) 文档，以了解有关模型解析和对模型的前端组件访问的详细信息。

另请参阅npm包： [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## 模型驱动的单页应用程序 {#model-driven-single-page-application}

使用适用于AEM的Javascript SPA SDK的单页应用程序由模型驱动：

1. 前端组件本身注册到 [组件映射存储](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. 然后， [容器](/help/sites-developing/spa-blueprint.md#container)，一经由提供 [模型提供程序](/help/sites-developing/spa-blueprint.md#the-model-provider)，迭代其模型内容( `:items`)。

1. 对于页面，其子项( `:children`)首先从获取组件类 [组件映射](/help/sites-developing/spa-blueprint.md#componentmapping) 然后实例化它。

## 应用程序初始化 {#app-initialization}

通过 [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). 因此，初始化采用以下一般形式：

1. 每个模型提供程序自行初始化，并侦听对与其内部组件对应的模型段所做的更改。
1. 的 [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) 必须初始化，如 [初始化流程](/help/sites-developing/spa-blueprint.md).

1. 存储后，页面模型管理器会返回应用程序的完整模型。
1. 然后，此模型将传递到前端根 [容器](/help/sites-developing/spa-blueprint.md#container) 组件。
1. 模型段最终会传播到每个单独的子组件。

![app_model_initialization](assets/app_model_initialization.png)
