---
title: 在AEM中搜索资产
description: 了解如何使用“过滤器”面板在AEM中查找所需的资产，以及如何使用在搜索中显示的资产。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a43a972b8ff5ce5603f0fdaa999558cdf3cbb0e
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# 在AEM {#search-assets-in-aem}中搜索资产

了解如何使用“过滤器”面板在AEM中查找所需的资产，以及如何使用在搜索中显示的资产。

使用“过滤器”面板可搜索资产、文件夹、标记和元数据。 可以使用通配符星号搜索字符串的部分。

“过滤器”面板提供了多种选项，可以通过多种方式（而非通用分类顺序）搜索资产和文件夹。

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

您可以自定义“过滤器”面板，并使用[搜索彩块化](search-facets.md)添加／删除搜索谓词。 要显示“过滤器”面板，请执行以下步骤：

1. 在“资产”用户界面中，点按／单击工具栏中的![search_icon](assets/search_icon.png)以显示“搜索”框。
1. 输入您的搜索词并按Enter。 或者，只需按Enter键，无需输入任何搜索词。 请勿输入任何前导空格，否则搜索无效。

1. 点按／单击GlobalNav图标。 将显示过滤器面板。

   ![过滤器面板1](assets/filters_panel-1.png)

   根据您搜索的项目类型，搜索结果顶部会指示匹配项数。

   ![number_of_searches](assets/number_of_searches.png)

## 搜索文件类型{#search-for-file-types}

“过滤器”面板有助于为搜索体验添加更多粒度，并使搜索功能更具通用性。 您可以轻松展开到所需的详细级别。

例如，如果要查找图像，请使用&#x200B;**[!UICONTROL 文件类型]**&#x200B;谓词选择是要位图图像还是矢量图像。

![image_type](assets/image_type.png)

您可以通过指定图像的MIME类型进一步缩小搜索范围。

![mime_type](assets/mime_type.png)

同样，在搜索文档时，可以指定格式，例如PDF或MS Word。

![文档](assets/documents.png)

## 根据文件大小{#search-based-on-file-size}进行搜索

使用&#x200B;**文件大小**&#x200B;谓词，根据资产的大小搜索资产。 您可以指定大小范围的下限和上限以缩小搜索范围。 您还可以指定度量单位，如千字节、兆字节等。

![unit_of_measure](assets/unit_of_measure.png)

## 根据上次修改资产的时间进行搜索{#search-based-on-when-assets-are-last-modified}

如果您管理进行中的资产或监视审核工作流，则可以根据准确的时间戳搜索资产的上次修改时间。 例如，指定修改资产的前后日期。

![last_modified_dates](assets/last_modified_dates.png)

您还可以使用以下选项在搜索中实现更高级别的粒度：

![时间戳](assets/timestamp.png)

## 根据状态{#search-based-on-status}进行搜索

使用&#x200B;**状态**&#x200B;谓词，根据各种类型的状态（如发布、批准、结帐和过期）搜索资产。

![状态](assets/status.png)

例如，在监视资产发布时，您可以使用相应的选项搜索要发布的资产。

![发布](assets/publish.png)

在监视资产的审核状态时，请使用适当的选项来查找已批准的资产或待批准的资产。

![批准](assets/approval.png)

## 根据Insights数据{#search-based-on-insights-data}进行搜索

使用&#x200B;**Insights**&#x200B;谓词，根据从各种Creative应用程序获取的资产使用情况统计信息搜索资产。 使用数据按以下类别进行分组：

* 使用情况得分
* 展示次数
* 点击量
* 显示资产的媒体渠道

![洞察](assets/insights.png)
