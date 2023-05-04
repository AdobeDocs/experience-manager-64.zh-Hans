---
title: 个性化和内容定位
seo-title: Personalization and Content Targeting
description: 了解 AEM 如何创建个性化内容
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 34%

---

# 个性化和内容定位 {#personalization}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 个性化和内容定位 {#personalization-and-content-targeting}

AEM提供了一个工具框架，用于创作目标内容和呈现个性化体验。

## 定位模式 {#targeting-mode}

可使用 AEM 的定位模式[创作目标内容](/help/sites-authoring/content-targeting-touch.md)。定位模式和 Target 组件提供了一些工具，用于为您的营销活动体验创建内容。

## 活动 {#activities}

活动定义并组织您的营销工作。 活动包括您定位的受众以及应用定位的时间段。

例如，We.Retail产品目录包含关注季节性产品的Teaser。 夏季体育活动定义Teaser在夏季月份定位的营销区段。

活动还会识别 [定位引擎](/help/sites-authoring/personalization.md#targeting-engine) 页面所使用的。

使用 [“活动”控制台](/help/sites-authoring/activitylib.md) 创建和管理品牌的活动。 您还可以在[创作目标内容](/help/sites-authoring/content-targeting-touch.md)时创建活动。

## 体验 {#experiences}

对于每个活动，您可以定义一个或多个体验来识别要定位的受众。AEM 使您能够控制包含每个体验的内容。

受众基于在AEM或Adobe Target中创建的营销区段。 当访客打开网页时，页面逻辑会确定访客所属的受众，并显示您为该受众创建的内容。

例如，某项活动定义了针对两类不同受众的体验：30 岁以上的女性和 30 岁以下的女性。We.Retail网站的“女性”页面针对每个体验显示不同的产品。

您可以为活动定义体验。 您可以使用 [活动控制台](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) 或 [定位模式](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) 向活动添加体验。

## 选件 {#offers}

选件是指显示在某个体验页面上某个位置的内容。 对不同的体验使用不同的选件，以最大限度地提高受众内容的有效性。

例如，We.Retail示例网站的“女士”页面可以使用选件作为显示在页面顶部的Teaser图像。 “30岁以上女性”体验和“30岁以下女性”体验的Teaser会使用不同的选件。

使用 [“选件”控制台](/help/sites-authoring/offerlib.md) 以创建可在多个体验中使用的选件。 在 [创作目标内容](/help/sites-authoring/content-targeting-touch.md).

## 定位引擎 {#targeting-engine}

定位引擎是驱动目标内容逻辑的机制。 [活动](/help/sites-authoring/activitylib.md)会配置为使用以下两个可用的定位引擎之一：AEM 和 Adobe Target。

### AEM {#aem}

AEM提供了一个内置定位引擎，用于处理页面请求并确定要显示的内容。 使用 AEM 定位引擎时，您仅可使用在 AEM 中创建的区段来定义体验受众。

### Adobe Target {#adobe-target}

Adobe Target 定位引擎允许从 Adobe Target 中跟踪的页面访问收集信息。

* 使用此定位引擎时，您可以使用从Adobe Target导入的区段来定义体验的受众。
* 使用Adobe Target引擎的活动包括 [已同步到Target](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

[与 Adobe Target 集成后](/help/sites-administering/opt-in.md)，您便可以使用此引擎。
