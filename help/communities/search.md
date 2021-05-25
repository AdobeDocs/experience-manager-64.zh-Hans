---
title: 搜索功能
seo-title: 搜索功能
description: 向社区站点添加和配置搜索
seo-description: 向社区站点添加和配置搜索
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# 搜索功能{#search-feature}

搜索功能可与各种其他功能（如论坛）配合使用，以便能够搜索内容。

添加搜索社区成员输入的帖子(称为用户生成内容(UGC))的功能时，有两个组件：[ `Search`](#search-features)和[ `Search Results`](#search-results)。

包含`Search Results`组件的页面支持搜索和显示结果。

包含`Search`组件的页面提供了启动搜索的位置，搜索结果显示在`Search Results`页面上。

搜索功能可与任何其他功能一起使用，该功能允许网站访客和成员查看内容。

## 搜索 {#search-features}

### 将搜索添加到页面{#add-search-to-a-page}

要在创作模式下将`Search`组件添加到页面，请使用组件浏览器找到`Communities / Search`并将其拖动到页面上的位置。 使用`Search`需要为`Search Results.`再添加一页

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含所需的客户端库`cq.social.hbs.search`时，将显示`Search`组件。

![chlimage_1-373](assets/chlimage_1-373.png)

### 配置添加的搜索{#configure-the-added-search}

选择要访问的已放置的`Search`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-374](assets/chlimage_1-374.png)

在&#x200B;**[!UICONTROL 搜索设置]**&#x200B;选项卡下，指定访客输入查询时搜索的路径。

![chlimage_1-376](assets/chlimage_1-375.png)

* **[!UICONTROL 搜索]**
路径通过使用“添加项目”按钮添加搜索路径，内容搜索受到限制。例如，要将搜索限制为特定论坛，请选择置于页面内的论坛组件：

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL 结果]**
页面使用浏览器选择包含 
`Search Results` 组件.

## 搜索结果 {#search-results}

### 将搜索结果添加到页面{#add-search-results-to-a-page}

要在创作模式下向页面添加`Search Results`组件，请使用组件浏览器找到

* `Communities / Search Results`

并将其拖动到页面上的位置。 与搜索组件不同，由于结果将显示在同一页面上，因此无需再添加第二页。

如果在网站的其他位置使用搜索，则此具有`Search Results`的页面可配置为`Result Page`，适用于`Search`的任何或所有实例。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含所需的客户端库`cq.social.hbs.search`时，将显示`Search Result`组件的方式：

![chlimage_1-376](assets/chlimage_1-376.png)

### 配置添加的搜索结果{#configure-the-added-search-result}

选择要访问的已放置的`Search Results`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-377](assets/chlimage_1-377.png)

在&#x200B;**[!UICONTROL 搜索结果设置]**&#x200B;选项卡下，可以指定访客输入查询时搜索中包含的路径。

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL 每页搜索结]**
果定义每页显示的主题/帖子数。默认值为10。

* **[!UICONTROL 搜索]**
路径通过使用“添加项目”按钮添加搜索路径，内容搜索受到限制。

## 附加信息 {#additional-information}

有关更多信息，请参阅[Search Essentials](search-implementation.md)页面，供开发人员使用。
