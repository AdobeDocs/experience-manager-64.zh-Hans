---
title: 管理智能标记
description: 更新或删除不准确的智能标记，以提高标记的相关性
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 3%

---

# 管理智能标记 {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以策划智能标记，以删除可能分配给品牌图像的任何不准确标记，以便仅显示最相关的标记。

审核智能标记还可确保图像显示在最相关标记的搜索结果中，从而帮助优化基于标记的图像搜索。 从本质上讲，这有助于消除不相关图像在搜索结果中出现的可能性。

您还可以为标记分配更高的排名，以增加与图像相关的相关性。 提升图像的标记，在基于特定标记执行搜索时，增加了在搜索结果中出现图像的可能性。

1. 在OmniSearch框中，根据标记搜索资产。
1. Inspect搜索结果来识别您找不到与搜索相关的图像。
1. 选择图像，然后单击/点按 **[!UICONTROL 管理标记]** 图标。
1. 从 **[!UICONTROL 管理标记]** ，检查标记。 如果您不希望根据特定标记搜索图像，请选择标记，然后单击/点按 **[!UICONTROL 删除]** 图标。 或者，单击/点按(**[!UICONTROL X]**)符号。
1. 要为标记分配更高的排名，请选择标记，然后单击/点按 **[!UICONTROL 提升]** 图标。 您提升的标记将移至 **[!UICONTROL 标记]** 中。
1. 单击／点按 **[!UICONTROL 保存]**，然后单击／点按确 **[!UICONTROL 定]** ，关闭成功对话框。
1. 导航到图像的属性页面。 请注意，为您提升的标记分配了高相关性，因此，在搜索结果中显示的较高。

## 了解 [!DNL Experience Manager] 使用智能标记搜索结果 {#understand-search-results-with-smart-tags}

默认情况下， [!DNL Experience Manager] 搜索将搜索词与 `AND` 子句。 使用智能标记不会更改此默认行为。 使用智能标记可添加 `OR` 子句来查找应用智能标记中的任何搜索词。 例如，请考虑搜索 `woman running`. 仅包含 `woman` 或 `running` 默认情况下，元数据中的关键字不会显示在搜索结果中。 但是，标有以下任一项的资产 `woman` 或 `running` 在此类搜索查询中会显示使用智能标记。 所以搜索结果是，

* 同时具有两个关键字的资产， `woman` 和 `running` 元数据中。
* 使用任一关键字标记的资产智能。

首先显示与元数据字段中的所有搜索词匹配的搜索结果，然后显示与智能标记中的任意搜索词匹配的搜索结果。 在上例中，搜索结果的显示大致顺序为：

1. 匹配 `woman running` 在各种元数据字段中。
1. 匹配 `woman running` 在智能标记中。
1. 匹配 `woman` 或 `running` 在智能标记中。
