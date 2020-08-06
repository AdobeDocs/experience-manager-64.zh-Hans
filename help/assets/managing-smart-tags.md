---
title: 管理智能标记
description: 更新或删除不准确的智能标记，以提高标记的相关性
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# 管理智能标记 {#managing-smart-tags}

您可以创建智能标记来删除可能分配给您的品牌图像的任何不准确标记，以便只显示最相关的标记。

调节智能标签还可确保图像显示在最相关标签的搜索结果中，从而帮助优化基于标签的图像搜索。 从根本上说，它有助于消除不相关图像在搜索结果中出现的可能性。

您还可以为标记指定更高的等级，以增加与图像相关的相关性。 提升图像的标记可提高当基于特定标记执行搜索时在搜索结果中出现图像的可能性。

1. 在OmniSearch框中，根据标记搜索资产。
1. Inspect搜索结果，以识别与搜索不相关的图像。
1. 选择图像，然后单击／点按工 **[!UICONTROL 具栏中的]** “管理标记”图标。
1. 从“管 **[!UICONTROL 理标记]** ”页面检查标记。 如果不希望根据特定标记搜索图像，请选择标记，然后单击／点按工具栏中 **[!UICONTROL 的]** “删除”图标。 或者，单击／点按标签&#x200B;**[!UICONTROL 旁边]**&#x200B;显示的(X)符号。
1. 要为标记分配更高的等级，请选择标记，然后单击／点按工 **[!UICONTROL 具栏]** 中的提升图标。 您提升的标记将移到“标记 **[!UICONTROL ”部]** 分。
1. 单击／点按 **[!UICONTROL 保存]**，然后单击／点按确 **[!UICONTROL 定]** ，关闭成功对话框。
1. 导航到图像的属性页面。 请注意，您提升的标记具有较高的相关性，因此在搜索结果中显示得更高。

## 使用智能标签了解AEM搜索结果 {#understand-search-results-with-smart-tags}

默认情况下，AEM搜索将搜索词与子句 `AND` 组合。 使用智能标记不会更改此默认行为。 使用智能标记可添加 `OR` 一个附加子句，以在应用智能标记中查找任何搜索词。 For example, consider searching for `woman running`. 默认情况下， `woman` 元数据 `running` 中仅包含关键字的资产不会显示在搜索结果中。 但是，在此类搜索查询中， `woman` 会显 `running` 示带有或使用智能标记的资产。 搜索结果是，

* 同时包含关键字 `woman` 和元 `running` 数据的资产。
* 使用任一关键字标记的资产智能。

首先显示与元数据字段中所有搜索词匹配的搜索结果，然后显示与智能标记中任何搜索词匹配的搜索结果。 在上例中，搜索结果的近似显示顺序为：

1. 的匹配 `woman running` 项。
1. 智能标 `woman running` 记中的匹配项。
1. 智能标 `woman` 签的 `running` 匹配项或匹配项。
