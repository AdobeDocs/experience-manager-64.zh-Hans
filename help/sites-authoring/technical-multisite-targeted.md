---
title: 如何构建目标内容的多站点管理
seo-title: How Multisite Management for Targeted Content is Structured
description: 图表显示了如何构建目标内容的多站点支持
seo-description: A diagram shows how multisite support for targeted content is structured
uuid: 2d30cdf0-ab77-490d-aac0-db3a0d417a58
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 7dd851ab-3fa7-426e-89cb-08b67e9b5999
exl-id: 28c45577-e5cd-4706-b5b2-227279126ad9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 32%

---

# 如何构建目标内容的多站点管理{#how-multisite-management-for-targeted-content-is-structured}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

下图显示了如何构建目标内容的多站点支持。

**/content/campaigns/&lt;brand>** 下方显示了区域，默认情况下，每个品牌都有一个自动创建的主区域。每个区域都包含自身的一组活动、体验和选件。

![chlimage_1-268](assets/chlimage_1-268.png)

要查找目标内容，页面或网站可以映射到某个区域。 如果未配置区域，则AEM会返回到此特定品牌的主控区域。

下图是该逻辑如何为三个站点（名为 site1、site2 和 site3）工作的示例。

![chlimage_1-269](assets/chlimage_1-269.png)

* site1根据区域映射查找brand1的myarea1和brand2的otherarea2。
* site2查找brand1的myarea1和brand2的主控区域，因为只定义了brand1的区域映射。
* site3查找brand1和brand2的主控区域，因为根本没有为此网站定义其他区域映射。
