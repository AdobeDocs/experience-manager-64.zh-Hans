---
title: 使用社交标记云
seo-title: 使用社交标记云
description: 将社交标记云组件添加到页面
seo-description: 将社交标记云组件添加到页面
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 1%

---


# 使用社交标记云{#using-social-tag-cloud}

## 简介 {#introduction}

`Social Tag Cloud`组件会突出显示社区成员在发布内容时应用的标记。 这是一种识别热门话题并允许网站访客快速找到标记内容的方法。

要了解当前趋势的其他方法，请访问[活动趋势](trends.md)。

本页文档了`Social Tag Cloud`组件对话框设置并描述了用户体验。

有关开发人员的详细信息，请参阅[Tag Essentials](tag.md)。

有关创建和管理标记以及已应用哪些内容标记的信息，请参阅[管理标记](../../help/sites-administering/tags.md)。

## 添加社交标记云{#adding-a-social-tag-cloud}

要在创作模式下将`Social Tag Cloud`组件添加到页面，请使用组件浏览器找到`Communities / Social Tag Cloud`并将其拖动到应显示标记云的页面上。

有关必要的信息，请访问[社区组件基础知识](basics.md)。

当包含[必需的客户端库](tag.md#essentials-for-client-side)时，`Social Tag Cloud`组件的显示方式如下：

![chlimage_1-303](assets/chlimage_1-303.png)

## 配置社交标记云{#configuring-social-tag-cloud}

选择要访问的已放置`Social Tag Cloud`组件，然后选择打开编辑对话框的`Configure`图标。

![chlimage_1-304](assets/chlimage_1-304.png)

在&#x200B;**[!UICONTROL 社交标记云]**&#x200B;选项卡下，指定要显示的标记，如果这些标记是活动链接，则指定页面的搜索结果位置：

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL 要显示的社交]**
标记标识要显示的UGC标记。下拉选项为

   * `From page and child pages`
   * `All tags`

   默认值为`From page and child pages`，其中“page”是指下面的&#x200B;**Page**&#x200B;设置。

* **[!UICONTROL 页面]**
(如果不需要，则为必填 
`All tags)` 页面的UGC路径。如果留空，则默认为当前页面。

* **[!UICONTROL 标记上无链]**
接如果选中，标记将以纯文本形式显示在标记云中。如果未选中，则标记将显示为活动链接，用于搜索应用该标记的所有内容。 默认为未选中，并要求设置**[!UICONTROL 搜索结果路径]**。

* **[!UICONTROL 搜索结]**
果路径指向其 
`Search Result` 已放置组件，配置为引用UGC，该UGC包括页面设置指定的UGC **** 路径。

## 更改社交标记云的显示{#change-display-of-social-tag-cloud}

要编辑&#x200B;**社交标签云**&#x200B;的显示，请输入[设计模式](../../help/sites-authoring/default-components-designmode.md)并多次单击已放置的`Social Tag Cloud`组件以打开一个包含其他选项卡的对话框。

使用&#x200B;**[!UICONTROL 社交标记云（设计）]**&#x200B;选项卡，指定标记的显示方式。 标记可以是简单标记、默认命名空间中的单个单词或分层分类：

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL 显示完整标题]**
路径如果选中，则显示父标记的标题和每个已应用标记的命名空间。

   例如：

   * 已选中: `Geometrixx Media: Gadgets / Cars`
   * 未选中: `Cars`

   简单的标签没有区别。

   默认为未选中。

* **[!UICONTROL 仅显示叶标]**
记如果选中，则仅显示不包含其他标记的已应用标记。

   例如，给定的TagID

   `Geometrixx Media: Gadgets / Cars`

   可应用3个标记：`Geometrixx Media (the namespace)`、`Gadgets`和`Cars`

   * 已检查：如果应用，将仅显示`Cars`
   * 未选中：如果应用，将显示`Geometrixx Media`和`Gadgets`以及`Cars`

   简单的标签是叶标签。

   默认为未选中。

* **[!UICONTROL 链接]**
模板当通过组件编辑对话框启用链接时，用于在标记云中显示链接的模板（默认模板除外）。

* **[!UICONTROL 所有标记的大小]**
相同如果选中，标记云中的所有单词的样式相同。如果不选中，则根据单词的用法设置不同的样式。 默认为未选中。

## 附加信息 {#additional-information}

有关开发人员的详细信息，请参阅[Tag Essentials](tag.md)页面。

有关创建和管理标记的信息，请参阅[标记用户生成的内容](tag-ugc.md)(UGC)。
