---
title: Admin Console
seo-title: Admin Consoles
description: 了解如何使用AEM中提供的Admin Console。
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 3%

---

# Admin Console{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

默认情况下，通过管理控制台切换到经典UI的功能已被禁用。 因此，将鼠标悬停在某些控制台图标上时显示的允许访问经典UI的弹出图标将不再显示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

在中具有经典UI版本的每个控制台 `/libs/cq/core/content/nav` 可以单独重新启用，以便 **经典UI** 将鼠标悬停在控制台图标上时，选项会再次弹出。

在此示例中，我们将为站点控制台重新启用经典UI。

1. 使用CRXDE Lite，找到与要为其重新启用经典UI的管理控制台对应的节点。 它们位于：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 选择与要为其重新启用经典UI的控制台对应的节点。 例如，我们将为站点控制台重新启用经典UI。

   `/libs/cq/core/content/nav/sites`

1. 使用创建叠加 **覆盖节点** 选项；例如：

   * **路径**: `/apps/cq/core/content/nav/sites`
   * **覆盖位置**: `/apps/`
   * **匹配节点类型**:活动（选中复选框）

1. 将以下布尔属性添加到所覆盖的节点：

   `enableDesktopOnly = {Boolean}true`

1. 的 **经典UI** 选项在管理控制台中再次作为弹出选项可用。

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

对要为其重新启用经典UI版本访问权限的每个控制台重复这些步骤。
