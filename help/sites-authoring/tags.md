---
title: 使用标记
seo-title: Using Tags
description: 标记是对网站中的内容进行分类的一种快速而简便的方法
seo-description: Tags are a quick and easy method of classifying content within a website
uuid: a91f8724-fc35-4f40-b21c-bee90429765b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: d0b0e47b-e68d-407d-9d06-deca2039dede
exl-id: 846a925a-673e-4051-a673-1a9236701f0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 26%

---

# 使用标记 {#using-tags}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

标记是对网站中的内容进行分类的一种快速而简便的方法。 标记可以被视为可附加到页面、资产或其他内容的关键字或标签，以便能够搜索以查找该内容和相关内容。

* 请参阅 [管理标记](/help/sites-administering/tags.md) 有关创建和管理标记以及已对哪些内容应用标记的信息。
* 有关标记框架以及在自定义应用程序中包括和扩展标记的信息，请参阅[针对开发人员的标记](/help/sites-developing/tags.md)。

## 使用标记的十大理由 {#ten-reasons-to-use-tagging}

1. 组织内容：标记使作者的工作更轻松，因为他们可以轻而易举地快速组织内容。

1. 组织标记：标记组织内容时，层次分类/命名空间会组织标记。

1. 深度组织的标记：通过创建标记和子标记的功能，可以表示整个分类系统，其中涵盖术语、子术语及其关系。 这允许您创建与正式内容层次结构平行的第二个（或第三个）内容层次结构。

1. 控制标记：可以通过对标记和/或命名空间应用权限来控制标记的创建和应用来控制标记。

1. 灵活标记：标记有许多名称和面孔：标记、分类术语、类别、标签等。 标记的内容模型和使用方式很灵活；例如，在概括目标人口统计、对内容进行分类或评级，或者创建辅助内容层次结构时，均可使用标记。

1. 改进了搜索：AEM中的默认搜索组件包含大量已创建的标记和已应用的标记，可以对其应用过滤器，以将结果缩小到相关范围。

1. 启用SEO:作为页面属性应用的标记将自动显示在页面的元标记中，以对搜索引擎可见。

1. 化繁为简：标记只需通过单词和触摸按钮即可创建。 之后，可以添加标题、描述和无限数量的标签以向标记提供更多语义。

1. 核心一致性：标记系统是AEM的核心组件，可供所有AEM功能用来对内容分类。 此外，开发人员可以使用标记 API 来创建支持标记的应用程序，以便访问相同的分类。

1. 结构与灵活性相结合：由于对页面和路径的嵌套，AEM非常适合处理结构化信息。 由于内置的全文搜索功能，在处理非结构化信息时，它同样具有强大的功能。 标记结合了结构和灵活性的优势。

在设计网站的内容结构和资产的元数据架构时，请考虑使用标记提供的轻量级易访问方法。

## 应用标记 {#applying-tags}

在创作环境中，作者可以通过访问页面属性并在&#x200B;**标记/关键字**&#x200B;字段中输入一个或多个标记来应用标记。

应用 [预定义标记](/help/sites-administering/tags.md)，在 **页面属性** 窗口使用 **标记** 字段和 **选择标记** 窗口。 **标准标记**&#x200B;选项卡是默认的命名空间，这意味着分类前面没有 `namespace-string:` 前缀。

![chlimage_1-92](assets/chlimage_1-92.png)

### 发布标记 {#publishing-tags}

与页面一样，您可以对标记和命名空间执行以下操作：

**激活**

* 激活单个标记。

   与页面一样，新创建的标记需要先激活，然后才能在发布环境中使用。

>[!NOTE]
>
>激活页面时，会自动打开一个对话框，通过该对话框可以激活属于该页面的未激活标记。

**取消激活**

* 取消激活选定标记。

## 标记云 {#tag-clouds}

标记云会显示一组标记，用于当前页面、整个网站或最常访问的标记。 标记云是突出显示用户感兴趣的问题的一种方法。 用于显示标记的文本大小因标记的用法而异。

的 [标记云](/help/sites-authoring/default-components-foundation.md#tag-cloud) 组件（常规组件组）用于向页面添加标记云。

## 在标记上搜索 {#searching-on-tags}

您可以在创作和发布环境中搜索标记。

### 使用搜索组件 {#using-search-component}

添加 [搜索组件](/help/sites-authoring/default-components-foundation.md#search) 到页面可提供包含标记的搜索功能，该功能可在创作和发布环境中使用。

![chlimage_1-93](assets/chlimage_1-93.png)
