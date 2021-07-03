---
title: 在AEM中搜索资产
description: 了解如何使用“过滤器”面板在AEM中查找所需的资产，以及如何使用搜索中显示的资产。
contentOwner: AG
feature: 搜索，元数据
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# 在AEM中搜索资产 {#search-assets-in-aem}

了解如何使用“过滤器”面板在AEM中查找所需的资产，以及如何使用搜索中显示的资产。

使用“过滤器”面板可搜索资产、文件夹、标记和元数据。 您可以使用通配符星号搜索字符串的部分内容。

“过滤器”面板提供了多种选项，可用于以多种方式（而不是通用分类顺序）搜索资产和文件夹。

您可以根据以下选项（谓词）进行搜索：

* 文件类型
* 文件大小
* 字段名称
* 上次修改时间
* 状态
* 方向
* 样式
* 分析

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

您可以使用[搜索彩块化](search-facets.md)自定义“过滤器”面板，并添加/删除搜索谓词。 要显示“过滤器”面板，请执行以下步骤：

1. 在Assets用户界面中，点按/单击工具栏中的![search_icon](assets/search_icon.png) ，以显示Omnisearch框。
1. 输入搜索词并按Enter。 或者，只需按Enter键，而不输入任何搜索词。 请勿输入任何前导空格，否则搜索将不起作用。

1. 点按/单击GlobalNav图标。 此时将显示“过滤器”面板。

   ![filters_panel-1](assets/filters_panel-1.png)

   根据您搜索的项目类型，匹配项的数量会显示在搜索结果的顶部。

   ![number_of_searches](assets/number_of_searches.png)

## 搜索文件类型 {#search-for-file-types}

“过滤器”面板有助于为您的搜索体验添加更多粒度，并使搜索功能更加通用。 您可以轻松地向下展开到所需的详细级别。

例如，如果要查找图像，请使用&#x200B;**[!UICONTROL 文件类型]**&#x200B;谓词选择要位图图像还是矢量图像。

![image_type](assets/image_type.png)

您可以通过为图像指定MIME类型来进一步缩小搜索范围。

![mime_type](assets/mime_type.png)

同样，在搜索文档时，您可以指定格式，例如PDF或MS Word。

![文档](assets/documents.png)

## 根据文件大小进行搜索 {#search-based-on-file-size}

使用&#x200B;**文件大小**&#x200B;谓词，可根据资产的大小搜索资产。 您可以为大小范围指定下限和上限，以缩小搜索范围。 您还可以指定度量单位，例如千字节、兆字节等。

![unit_of_measure](assets/unit_of_measure.png)

## 根据上次修改资产的时间进行搜索 {#search-based-on-when-assets-are-last-modified}

如果您管理正在进行的资产或监控审核工作流，则可以搜索资产的上次修改时间（基于准确的时间戳）。 例如，指定修改资产之前或之后的日期。

![last_modified_dates](assets/last_modified_dates.png)

您还可以使用以下选项在搜索中实现更高级别的粒度：

![timestamp](assets/timestamp.png)

## 基于状态搜索 {#search-based-on-status}

使用&#x200B;**状态**&#x200B;谓词，可根据各种类型的状态（如发布、批准、结帐和到期）搜索资产。

![状态](assets/status.png)

例如，在监控资产发布时，您可以使用相应的选项来搜索已发布的资产。

![发布](assets/publish.png)

在监控资产的审核状态时，请使用相应的选项来查找已批准的资产或待批准的资产。

![审批](assets/approval.png)

## 根据分析数据进行搜索 {#search-based-on-insights-data}

使用&#x200B;**分析**&#x200B;谓词，根据从各种创意应用程序获取的资产使用情况统计信息来搜索资产。 使用情况数据按以下类别分组：

* 使用分数
* 展示次数
* 点击量
* 显示资产的媒体渠道

![洞察](assets/insights.png)
