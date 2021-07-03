---
title: 支持IPTC元数据
description: 了解Adobe Experience Manager(AEM)Assets如何支持通过Adobe Bridge和其他创意应用程序添加到资产中的IPTC元数据、创意评级和关键词。
contentOwner: AG
feature: 元数据
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 7%

---

# 支持IPTC元数据 {#support-for-iptc-metadata}

了解Adobe Experience Manager(AEM)Assets如何支持通过Adobe Bridge和其他创意应用程序添加到资产中的IPTC元数据、创意评级和关键词。

Adobe Experience Manager(AEM)Assets支持广泛用于描述资产的IPTC元数据标准。 这样，AEM Assets就可以在包括摄影师、创意机构、图书馆、博物馆等在内的各方中增强对其图像的接受。

资产的默认元数据架构现在整合了IPTC核心和IPTC扩展元数据架构，以定义全面的元数据属性，从而让用户能够添加有关图像中显示的人员、位置和产品的准确可靠数据。 它还支持有关创建图像的日期、名称和标识符，以及灵活的权限信息表达方式。

资产的“属性”页面现在包含单独的选项卡，用于在可编辑的字段中显示IPTC核心和IPTC扩展元数据。

1. 从Assets用户界面中，选择一个图像。
1. 单击或点按工具栏中的&#x200B;**[!UICONTROL 属性]**&#x200B;图标。
1. 在属性页面中，单击/点按&#x200B;**[!UICONTROL IPTC]**&#x200B;选项卡，以查看资产的IPTC元数据。
1. 根据需要编辑IPTC元数据属性。

   ![iptc_tab](assets/iptc_tab.png)

1. 单击/点按 **[!UICONTROL IPTC 扩展]**&#x200B;选项卡，查看用于资产的 IPTC 扩展元数据。
1. 根据需要编辑ITPC扩展元数据属性。
1. 点按/单击&#x200B;**[!UICONTROL 保存并关闭]**&#x200B;以保存更改。

## 创意评分支持 {#creative-rating-support}

除了显示单个用户评级和聚合评级之外，“属性”页面现在还显示通过Adobe Bridge和其他创意应用程序为资产分配的评级

这些评级位于&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡的&#x200B;**[!UICONTROL 创意评分]**&#x200B;部分下。

此评级为只读属性，范围为1到5。 您可以从“搜索”面板中根据资产的创作评分来搜索资产。

但是，此属性当前没有编入索引，以避免与用户所做的自定义更改发生任何冲突。

## 关键词支持 {#keyword-support}

属性页面的&#x200B;**[!UICONTROL IPTC]**&#x200B;选项卡还显示通过Adobe Bridge和其他创意应用程序添加到资产的关键词。 您还可以编辑这些关键词，并从&#x200B;**[!UICONTROL IPTC]**&#x200B;选项卡添加更多关键词。

![关键词](assets/keywords.png)
