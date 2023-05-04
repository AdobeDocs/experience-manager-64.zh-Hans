---
title: 编辑器
seo-title: Editor
description: 了解如何切换回经典UI编辑器。
seo-description: Learn how to switch back to the Classic UI Editor.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
exl-id: 04a9c595-9a73-4a8a-99ae-c2292882338f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 8%

---

# 编辑器{#editor}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

默认情况下，从编辑器切换到经典UI的功能已被禁用。

![chlimage_1-9](assets/chlimage_1-9.png)

重新启用选项 **在经典UI中打开** 在 **页面信息** 菜单，请按照以下步骤操作。

1. 使用CRXDE Lite，找到以下节点：

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   例如

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. 使用创建叠加 **覆盖节点** 选项；例如：

   * **路径**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **覆盖位置**: `/apps/`
   * **匹配节点类型**:活动（选中复选框）

1. 将以下多值文本属性添加到叠加的节点：

   `sling:hideProperties = ["granite:hidden"]`

1. 的 **在经典UI中打开** 选项在 **页面信息** 菜单。

   ![chlimage_1-10](assets/chlimage_1-10.png)
