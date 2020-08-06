---
title: 自定义视图页面属性
seo-title: 自定义视图页面属性
description: 每个页面都有一组属性，您可以根据需要进行编辑
seo-description: 每个页面都有一组属性，您可以根据需要进行编辑
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
translation-type: tm+mt
source-git-commit: b4fa2d443f43cdfbf5caca4da7dcb935d099b795
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 1%

---


# 自定义视图页面属性{#customizing-views-of-page-properties}

每页都有一套可供 [用户](/help/sites-authoring/editing-page-properties.md) 查看和编辑的属性； 创建页面时需要某些视图(创建视图)，其他页面则可在以后的阶段进行查看和编辑（编辑）。 这些页面属性由相应页面组件的对话框() `cq:dialog`定义并提供。

>[!CAUTION]
>
>自定义页面属性视图在经典UI中不可用。

每个页面属性的默认状态为：

* 隐藏在创建视图中(例 **如创建页面** 向导)

* 在编辑视图中可用(例如 **视图属性**)

如果需要任何更改，则必须明确配置字段。 使用相应的节点属性完成此操作：

* 在创建视图（例如创建页面向导）中可 **用的页面** 属性：

   * 名称: `cq:showOnCreate`
   * 类型: `Boolean`

* 要在编辑视图(例如，“视图/编辑” ****)“属&#x200B;**性**”选 **项中使用的页** 面属性：

   * 名称: `cq:hideOnEdit`
   * 类型: `Boolean`

例如，请参阅基础页面组件“基本” **选项卡的“更多标题** ”和“ **说明** ”下分组的字段的设置。 在创建页面 **向导中** , `cq:showOnCreate` 这些属性已设置为 `true`:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>有关自定义 [页面属性的指南](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) ，请参阅扩展页面属性教程。

## 配置页面属性 {#configuring-your-page-properties}

您还可以通过配置页面组件的对话框并应用相应的节点属性来配置可用字段。

例如，默认情况下，创 [**建页面向导&#x200B;**](/help/sites-authoring/managing-pages.md#creating-a-new-page)，显示在更多标题和**&#x200B;说明下分组的字段&#x200B;**。 要隐藏这些内容，请配置：

1. 在下面创建您的页面组 `/apps`件。
1. 为页面组件的 *部分创建* (使用Sling资 [源合并](/help/sites-developing/sling-resource-merger.md)提供的对话区 `basic` 别差异); 例如：

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >请参阅：
   >
   >
   ```
   >/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog
   >```
   >
   >但是，您 ***不得*** 更改路径中的任 `/libs` 何内容。
   >
   >这是因为下次升级实 `/libs` 例时，内容会被覆盖（而应用修补程序或功能包时，内容很可能会被覆盖）。
   >
   >建议的配置和其他更改方法是：
   >
   >1. 在下面重新创建所需的项(即，当它存在 `/libs`时) `/apps`
   >1. 在 `/apps`


1. 设置 `path` 上的属 `basic` 性以指向基本选项卡的覆盖（另请参阅下一步）。 例如：

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. 在相应路径上 `basic` 创建 `moretitles` -节的覆盖； 例如：

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. 应用相应的节点属性：

   * **名称**: `cq:showOnCreate`
   * **类型**: `Boolean`
   * **值**: `false`

   “创 **建页面”向导中** ，将不再显示“更多标题 **和说明** ”部分。

>[!NOTE]
>
>配置要与Live Copy一起使用的页面属性时，请参 [阅配置页面属性上的MSM锁](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) ，以获取更多详细信息。

## 页面属性配置示例 {#sample-configuration-of-page-properties}

此示例演示了Sling资源合并的对 [话差异技术](/help/sites-developing/sling-resource-merger.md); 包括使用 [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties)。 它还说明了两者的 `cq:showOnCreate` 使用 `cq:hideOnEdit`。

GITHUB上的代码

您可以在GitHub上找到此页面的代码

* [在GitHub上打开aem-authoring-extension-page-dialog项目](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
