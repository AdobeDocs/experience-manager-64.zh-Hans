---
title: 在AEM中搜索资产
description: 了解如何在 [!DNL Experience Manager] ，以及如何使用搜索中显示的资产。
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 3%

---

# 在 [!DNL Experience Manager] 中搜索资源 {#search-assets-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

了解如何在 [!DNL Experience Manager] ，以及如何使用搜索中显示的资产。

使用“过滤器”面板可搜索资产、文件夹、标记和元数据。 您可以使用通配符星号搜索字符串的部分内容。

“过滤器”面板提供了多种选项，可用于以多种方式而不是按常规分类顺序搜索资产和文件夹。

您可以根据以下选项（谓词）进行搜索：

* 文件类型
* 文件大小
* 字段名称
* 上次修改时间
* 状态
* 方向
* 样式
* 见解

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

您可以使用自定义过滤器面板和添加/删除搜索谓词 [搜索彩块化](search-facets.md). 要显示“过滤器”面板，请执行以下步骤：

1. 在Assets用户界面中，点按/单击 ![search_icon](assets/search_icon.png) 来显示Omnisearch框。
1. 输入搜索词并按Enter。 或者，只需按Enter键，而不输入任何搜索词。 请勿输入任何前导空格，否则搜索将不起作用。

1. 点按/单击GlobalNav图标。 此时将显示“过滤器”面板。

   ![filters_panel-1](assets/filters_panel-1.png)

   根据您搜索的项目类型，匹配项的数量会显示在搜索结果的顶部。

   ![number_of_searches](assets/number_of_searches.png)

## 搜索文件类型 {#search-for-file-types}

“过滤器”面板有助于为您的搜索体验添加更多粒度，并使搜索功能更加通用。 您可以轻松地向下展开到所需的详细级别。

例如，如果您要查找图像，请使用 **[!UICONTROL 文件类型]** 此谓词用于选择是要位图图像还是矢量图像。

![image_type](assets/image_type.png)

您可以通过为图像指定MIME类型来进一步缩小搜索范围。

![mime_type](assets/mime_type.png)

同样，在搜索文档时，可以指定格式，例如PDF或MS Word。

![文档](assets/documents.png)

## 根据文件大小进行搜索 {#search-based-on-file-size}

使用 **文件大小** 此谓词用于根据资产的大小搜索资产。 您可以为大小范围指定下限和上限，以缩小搜索范围。 您还可以指定度量单位，例如千字节、兆字节等。

![unit_of_measure](assets/unit_of_measure.png)

## 根据上次修改资产的时间进行搜索 {#search-based-on-when-assets-are-last-modified}

如果您管理正在进行的资产或监控审核工作流，则可以搜索资产的上次修改时间（基于准确的时间戳）。 例如，指定修改资产之前或之后的日期。

![last_modified_dates](assets/last_modified_dates.png)

您还可以使用以下选项在搜索中实现更高级别的粒度：

![timestamp](assets/timestamp.png)

## 基于状态搜索 {#search-based-on-status}

使用 **状态** 此谓词用于根据各种类型的状态（如发布、批准、结帐和到期）搜索资产。

![状态](assets/status.png)

例如，在监控资产发布时，您可以使用相应的选项来搜索已发布的资产。

![发布](assets/publish.png)

在监控资产的审核状态时，请使用相应的选项来查找已批准的资产或待批准的资产。

![审批](assets/approval.png)

## 根据分析数据进行搜索 {#search-based-on-insights-data}

使用 **分析** 此谓词用于根据从各种创意应用程序获取的资产使用情况统计信息来搜索资产。 使用情况数据按以下类别分组：

* 使用分数
* 展示次数
* 单击次数
* 显示资产的媒体渠道

![洞察](assets/insights.png)
