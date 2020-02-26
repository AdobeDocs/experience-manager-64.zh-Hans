---
title: 管理控制台
seo-title: 管理控制台
description: 了解如何使用AEM中提供的管理控制台。
seo-description: 了解如何使用AEM中提供的管理控制台。
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# 管理控制台{#admin-consoles}

默认情况下，通过管理控制台切换到经典UI的功能已被禁用。 因此，当将鼠标悬停在某些控制台图标上时看到的弹出图标（允许访问经典UI）不再显示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

在中具有经典UI版本的每个控制台都可 `/libs/cq/core/content/nav` 以单独重新启用，这样，将鼠标移过控制台图标时， **经典UI** 选项会再次弹出。

在此示例中，我们将为站点控制台重新启用经典UI。

1. 使用CRXDE Lite，找到与您要为其重新启用经典UI的管理控制台对应的节点。 它们位于：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 选择与要为其重新启用经典UI的控制台对应的节点。 对于我们的示例，我们将为站点控制台重新启用经典UI。

   `/libs/cq/core/content/nav/sites`

1. 使用“叠加节点” **选项创建叠加** ;例如：

   * **路径**: `/apps/cq/core/content/nav/sites`
   * **覆盖位置**: `/apps/`
   * **匹配节点类型**:活动（选中复选框）

1. 将以下布尔属性添加到叠加的节点：

   `enableDesktopOnly = {Boolean}true`

1. “经 **典UI** ”选项在管理控制台中再次作为弹出窗口选项可用。

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

对要重新启用对经典UI版本访问权限的每个控制台重复这些步骤。
