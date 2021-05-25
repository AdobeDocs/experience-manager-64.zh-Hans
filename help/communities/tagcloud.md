---
title: 使用Social标签云
seo-title: 使用Social标签云
description: 向页面添加Social标签云组件
seo-description: 向页面添加Social标签云组件
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
exl-id: 3f55a02c-2733-4f69-8112-7c6c4c98938c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 1%

---

# 使用Social标签云{#using-social-tag-cloud}

## 简介 {#introduction}

`Social Tag Cloud`组件会突出显示社区成员在发布内容时应用的标记。 它是识别趋势主题并允许网站访客快速找到标记内容的方法。

有关确定当前趋势的另一种方法，请访问[活动趋势](trends.md)。

本页记录了`Social Tag Cloud`组件对话框设置，并描述了用户体验。

有关开发人员的详细信息，请参阅[Tag Essentials](tag.md)。

请参阅[管理标记](../../help/sites-administering/tags.md) ，以了解有关创建和管理标记以及已对哪些内容应用标记的信息。

## 添加Social标签云{#adding-a-social-tag-cloud}

要在创作模式下将`Social Tag Cloud`组件添加到页面，请使用组件浏览器找到`Communities / Social Tag Cloud`并将其拖动到应显示标记云的页面上。

有关必要信息，请访问[社区组件基础知识](basics.md)。

当包含[所需的客户端库](tag.md#essentials-for-client-side)时，将显示`Social Tag Cloud`组件：

![chlimage_1-303](assets/chlimage_1-303.png)

## 配置Social标签云{#configuring-social-tag-cloud}

选择要访问的已放置的`Social Tag Cloud`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-304](assets/chlimage_1-304.png)

在&#x200B;**[!UICONTROL Social标签云]**&#x200B;选项卡下，指定要显示的标签以及（如果标签为活动链接）搜索结果页面的位置。

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL 要显示的Social]**
标签识别要显示的UGC标签。下拉选项包括

   * `From page and child pages`
   * `All tags`

   默认值为`From page and child pages`，其中“page”是指下面的&#x200B;**Page**&#x200B;设置。

* **[!UICONTROL 页面]**
（如果不需要，则为必填项） 
`All tags)` 页面的UGC路径。如果留空，则默认为当前页面。

* **[!UICONTROL 标记上没有链]**
接如果选中此选项，则标记将以纯文本形式显示在标记云中。如果未选中，则标记将显示为活动链接，用于搜索应用了该标记的所有内容。 默认值未选中，并要求设置**[!UICONTROL 搜索结果路径]**。

* **[!UICONTROL 搜索结]**
果路径 
`Search Result` 组件已放置，配置为引用UGC，其中包含由页面设置指定的UGC **** 路径。

## 更改Social标签云的显示{#change-display-of-social-tag-cloud}

要编辑&#x200B;**Social标签云**&#x200B;的显示，请输入[设计模式](../../help/sites-authoring/default-components-designmode.md)并双击放置的`Social Tag Cloud`组件，以打开一个包含其他选项卡的对话框。

使用&#x200B;**[!UICONTROL Social标签云（设计）]**&#x200B;选项卡，指定标签的显示方式。 标记可以是简单的标记、默认命名空间中的单个词，或分层分类：

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL 显示完整标]**
题路径如果选中此选项，则显示父标记的标题以及每个已应用标记的命名空间。

   例如：

   * 已选中: `Geometrixx Media: Gadgets / Cars`
   * 未选中: `Cars`

   简单的标记没有区别。

   默认为未选中。

* **[!UICONTROL 仅显示叶标]**
记如果选中此选项，则仅显示已应用且不包含其他标记的标记。

   例如，假定TagID为

   `Geometrixx Media: Gadgets / Cars`

   有3个标记可应用：`Geometrixx Media (the namespace)`、`Gadgets`和`Cars`

   * 已选中：如果应用，则只显示`Cars`
   * 未选中：如果应用，将显示`Geometrixx Media`和`Gadgets`以及`Cars`

   简单的标签是叶标签。

   默认为未选中。

* **[!UICONTROL 链接]**
模板通过组件编辑对话框启用链接时，使用的模板（默认模板除外）用于在标记云中显示链接。

* **[!UICONTROL 所有标记的大]**
小相同如果选中此选项，则标记云中的所有词语的样式都相同。如果未选中，则根据词语的用法设置不同的样式。 默认为未选中。

## 附加信息 {#additional-information}

有关更多信息，请参阅[Tag Essentials](tag.md)页面，供开发人员使用。

请参阅[标记用户生成的内容](tag-ugc.md)(UGC)，以了解有关创建和管理标记的信息。
