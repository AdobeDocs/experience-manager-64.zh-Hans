---
title: Admin Console
seo-title: Admin Console
description: 了解如何使用AEM中提供的Admin Console。
seo-description: 了解如何使用AEM中提供的Admin Console。
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 1%

---

# Admin Console{#admin-consoles}

默认情况下，通过管理控制台切换到经典UI的功能已被禁用。 因此，将鼠标悬停在某些控制台图标上时显示的允许访问经典UI的弹出图标将不再显示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

每个在`/libs/cq/core/content/nav`中具有经典UI版本的控制台都可以单独重新启用，以便将鼠标悬停在控制台图标上时，再次弹出&#x200B;**经典UI**&#x200B;选项。

在此示例中，我们将为站点控制台重新启用经典UI。

1. 使用CRXDE Lite，找到与要为其重新启用经典UI的管理控制台对应的节点。 它们位于：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 选择与要为其重新启用经典UI的控制台对应的节点。 例如，我们将为站点控制台重新启用经典UI。

   `/libs/cq/core/content/nav/sites`

1. 使用&#x200B;**覆盖节点**&#x200B;选项创建覆盖；例如：

   * **路径**: `/apps/cq/core/content/nav/sites`
   * **覆盖位置**: `/apps/`
   * **匹配节点类型**:活动（选中复选框）

1. 将以下布尔属性添加到所覆盖的节点：

   `enableDesktopOnly = {Boolean}true`

1. **经典UI**&#x200B;选项在管理控制台中再次作为弹出窗口选项可用。

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

对要为其重新启用经典UI版本访问权限的每个控制台重复这些步骤。
