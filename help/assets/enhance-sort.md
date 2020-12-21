---
title: AEM中资源的增强排序
description: 了解AEM Assets如何部署服务器端排序来对文件夹资产或搜索查询进行一次排序，而不是在客户端进行批量排序。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 3%

---


# AEM {#enhanced-sorting-of-assets-in-aem}中资源的增强排序

了解AEM Assets如何部署服务器端排序来对文件夹资产或搜索查询进行一次排序，而不是在客户端进行批量排序。

Adobe Experience Manager(AEM)资产的搜索功能得到增强，可以高效地对文件夹列表视图和搜索结果页面中的大量资产进行排序。 您还可以对时间轴条目进行排序。

AEM Assets部署服务器端排序，一次对文件夹或搜索查询中的整个资产集（无论大小）进行排序，而不是在客户端批量对它们进行排序。 这样，预取的结果可以快速显示在用户界面上，从而使排序操作更快速、响应更快。

## 在列表视图{#sorting-assets-in-list-view}中对资产排序

AEM Assets允许您根据以下字段对文件夹资产进行排序：

* 区域设置
* 状态
* 类型
* 大小
* 评级
* 修改日期
* 发布日期
* 使用
* 点击量
* 展示次数
* 已签出

1. 导航到包含大量资产的文件夹。
1. 单击／点按布局图标，然后切换到列表视图。

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. 单击／点按资产列表中任意列标题旁边的排序图标。

   ![chlimage_1-395](assets/chlimage_1-395.png)

   资产列表会根据字段值进行排序。

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>要对`Name`或`Title`列中的值进行排序，请叠加`/libs/dam/gui/content/commons/availablecolumns`并将`sortable`的值更改为`True`。

## 在搜索结果{#sorting-assets-in-search-results}中对资产进行排序

您可以根据以下字段对搜索结果进行排序：

* 标题
* 状态
* 类型
* 大小
* 修改日期
* 发布日期

1. 从OmniSearch框中，根据所需条件搜索资产。

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. 单击／点按布局图标，然后切换到列表视图。 如果搜索结果已显示在列表视图中，请跳过此步骤。
1. 单击／点按资产列表中任意列标题旁边的排序图标。 资产列表会根据字段值进行排序。

   ![chlimage_1-398](assets/chlimage_1-398.png)

## 在时间轴{#sorting-assets-in-timeline}中对资产进行排序

AEM Assets允许您按时间顺序对时间轴条目进行排序，如批注、版本、工作流和活动。

1. 在资产UI中，选择要显示其时间轴的资产。
1. 单击／点按GolbalNav图标，然后选择&#x200B;**[!UICONTROL 时间轴]**。

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. 在时间轴中，从列表中选择一个条目。 例如，选择&#x200B;**[!UICONTROL 注释]**&#x200B;以显示与资产关联的注释的列表。

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. 单击／点按&#x200B;**[!UICONTROL Date]**&#x200B;标签旁的&#x200B;**[!UICONTROL 排序]**&#x200B;图标。 根据您的选择，注释会按时间顺序／时间顺序排列，按时间顺序或相反的时间顺序添加到资产中。

   ![chlimage_1-481](assets/chlimage_1-401.png)

