---
title: Campaign Management
seo-title: Campaign Management
description: 营销活动管理为数字营销人员提供了交付个性化内容并为访客创建专用体验的机会。 它允许您在Web、电子邮件和Mobile Services中编排营销活动，从而吸引访客。
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: 2980ec6d-cdd4-4fbd-b4a4-5e45e4508903
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 2%

---

# Campaign Management{#campaign-management}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

营销活动管理为数字营销人员提供了交付个性化内容并为访客创建专用体验的机会。

它允许您在Web、电子邮件和Mobile Services中编排营销活动，从而吸引访客。 您可以创建内容、划分访客区段、推送和提升特定用户配置文件的目标内容，以及跨多个渠道管理营销活动。

本文档介绍了构成营销活动的各种元素。 以下文档提供了更多详细信息：

* [Teaser和策略](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [电子邮件营销](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [登录页面](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Target选件](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [使用营销活动管理器](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [了解分段](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [设置营销活动](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

营销活动管理由各种元素组成：

* **品牌**
在AEM中，品牌是顶级单位，并构成 
**营销活动**.

* **促销活动**
营销活动是个人的集合 
**体验**.

* **体验**
重点内容构成了各种体验，呈现给访客的是 
**Touchpoints**. 可用的体验类型有以下几种：

   * **Teaser**
      [Teaser页面/段落](#teasers) 用于控制特定访客的方向 **区段** 关注他们兴趣的内容。

      Teaser页面可以：

      * 提供一系列选项供访客从中进行选择
      * 仅显示一个基于特定访客区段的teaser段落；例如，显示的Teaser段落可能取决于访客的年龄。

      通常，Teaser页面是一个临时操作，将持续特定时间段，直到被下一个Teaser页面替换为止。

   * **新闻稿**

      [电子邮件通信](#emailmarketing) 用于吸引用户并鼓励他们访问您的网站。 这些通常采用新闻稿的形式，将其发送到您的 **潜在客户** (通常分组为 **列表**)。 **注意：** Adobe不打算进一步增强此功能。 建议为 [利用Adobe Campaign和与AEM的集成](/help/sites-administering/campaign.md).

   * **Adobe Target**

      这允许与Adobe Target（以前称为Test&amp;Target）集成，Test&amp;Target为营销人员提供了转化网站优化工具，该工具具备持续使其在线内容和选件与其客户更相关的必要功能，从而产生更大的转化。 Adobe Target提供了一个直观的界面，用于设计和执行测试、创建受众区段和定位内容 — 所有这些都可以从单个应用程序完成。


* **Touchpoints**

   这些是访客与您的营销活动之间的联系点。 触点与您创建的体验相关联。

   例如，对于Teaser，它是Teaser段落所在的内容页面；对于Newsletter，它是邮寄列表。

* **潜在客户**

   您收集的关于访客以及如何与他们联系的信息构成了潜在客户的基础。 **注意：** Adobe不打算进一步增强此功能。

   建议为 [利用Adobe Campaign和与AEM的集成](/help/sites-administering/campaign.md).

* **列表**

   潜在客户通常会分组到列表中，以便您能够对其采取集体行动。 注意： **注意：** Adobe不打算进一步增强此功能。

   建议为 [利用Adobe Campaign和与AEM的集成。](/help/sites-administering/campaign.md)

* **区段**

   网站访客访问网站时的兴趣和目标各不相同。 根据网站上的活动、注册的用户档案信息以及其他网站上的活动等因素进行分析，有助于您定义区段。 然后，可以根据访客匹配的区段，专门针对访客的需求和兴趣。

* **MCM**

   营销活动管理器(MCM)是一个控制台，它允许您访问创建和控制营销活动、品牌、体验、接触点、潜在客户、列表、区段和报表所需的所有功能。

   它可以从多个位置(标记为 **促销活动**)，或使用（例如URL）：

   `http://localhost:4502/libs/mcm/content/admin.html`
