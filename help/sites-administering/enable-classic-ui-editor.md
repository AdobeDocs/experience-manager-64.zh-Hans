---
title: 编辑者
seo-title: 编辑者
description: 了解如何切换回经典UI编辑器。
seo-description: 了解如何切换回经典UI编辑器。
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
translation-type: tm+mt
source-git-commit: 9fa15a44cf83a50538cea3fb37bcccf405f66738
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 5%

---


# 编辑者{#editor}

默认情况下，已禁用从编辑器切换到经典UI的功能。

![chlimage_1-9](assets/chlimage_1-9.png)

要重新启用“页面信 **息”菜单中** 的“在经 **典UI中打开** ”选项，请执行以下步骤。

1. 使用CRXDE Lite，找到以下节点：

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   例如

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. 使用“叠加节点” **选项创建叠** 加； 例如：

   * **路径**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **覆盖位置**: `/apps/`
   * **匹配节点类型**: 活动（选中复选框）

1. 将以下多值文本属性添加到叠加的节点：

   `sling:hideProperties = ["granite:hidden"]`

1. 编辑 **页面时，“页面信息** ”菜单中也 **提供了“在经** 典UI中打开”选项。

   ![chlimage_1-10](assets/chlimage_1-10.png)

