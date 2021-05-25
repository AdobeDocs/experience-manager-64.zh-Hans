---
title: AEM 和 Web 辅助功能规范
seo-title: AEM 和 Web 辅助功能规范
description: 了解如何使用AEM创建无障碍网站和内容。
seo-description: 了解如何使用AEM创建无障碍网站和内容。
uuid: b68281af-3e8a-4842-b762-1c59f9132795
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility, introduction
content-type: reference
discoiquuid: 13c7e0bd-54af-49f3-9743-075ce6f3314d
exl-id: f0ccdeae-3dbb-4dba-89cf-4c8b759da22b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 47%

---

# AEM 和 Web 辅助功能规范{#aem-and-the-web-accessibility-guidelines}

出于许多社会、经济和法律动因，需要确保 Web 内容尽可能设计地能够让任何目标受众访问，而无论他们具有任何缺陷或限制。因此，Web 辅助功能在良好的 Web 设计中越来越重要。

创建具有AEM影响的无障碍网站和内容：

* 管理员负责配置 Adobe Experience Manager (AEM) 以确保正确启用辅助功能。
* 作者使用这些功能创建支持WCAG 2.0中关键准则的网站。

   创建无障碍内容是一个过程。虽然 AEM 提供了一些功能，但内容作者需要确保遵循创建无障碍内容所要求的技术。

* 在实施网站设计时，模板开发人员还应注意到此类问题。

## 更多信息 {#further-information}

以下页面和部分提供了相关信息和准则：

* [配置富文本编辑器以创建无障碍站点](/help/sites-administering/rte-accessible-content.md)

   关于管理员如何配置AEM以制作无障碍内容的准则。

* [创建无障碍内容（WCAG 2.0 合规性）](/help/sites-authoring/creating-accessible-content.md)

   WCAG 2.0准则提供了符合A级和AA级的成功标准列表。 本页详细介绍AEM涵盖的成功标准，以及如何在生成内容时满足这些标准。

* [WCAG 2.0快速指南](/help/managing/qg-wcag.md)

   有关WCAG 2.0的背景信息。

* [创建无障碍的自适应Forms](/help/forms/using/creating-accessible-adaptive-forms.md)

   Adobe Experience Manager(AEM)包含许多特性和功能，可增强具有不同功能的用户自适应表单的可用性。 该解决方案还帮助表单作者创建无障碍的自适应表单。

## 万维网联盟和WCAG 2.0 {#world-wide-web-consortium-and-wcag}

[万维网联盟 (W3C)](https://www.w3.org/) 是一个致力于开发 Web 标准的国际社区。为帮助Web设计人员和开发人员制作无障碍网站，[Web无障碍倡议(WAI)](https://www.w3.org/WAI/)于2008年12月发布了[Web内容无障碍准则(WCAG)2.0](https://www.w3.org/TR/WCAG20/)（更新了1999年发布的原始版本）。

>[!NOTE]
>
>目前正在开发[更新版本的准则](https://www.w3.org/TR/WCAG21/)，但此版本的AEM不考虑更新版本。

使用Adobe Experience Manager，内容作者和/或网站所有者可以创建符合WCAG 2.0 A级和AA级成功标准的Web内容。

[WCAG 2.0 快速入门指南](/help/managing/qg-wcag.md)中重点介绍了 WCAG 2.0 的特定方面。

### WCAG 2.0无障碍合规性级别{#wcag-accessibility-conformance-levels}

WCAG 2.0提供了涵盖无障碍级别](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html)的[准则（包含相关成功标准）。

与AEM相关的这些项目在[A级和AA符合性](/help/sites-authoring/creating-accessible-content.md)中涵盖。 在创建站点时，您应该大体上确定希望自己的站点符合哪个等级。

>[!NOTE]
>
>由于某些类型的内容无法满足所有 AAA 级成功标准，因此不建议将其作为必需的符合级别。

## Adobe 辅助功能 {#accessibility-at-adobe}

有关其他信息，请访问 [Adobe 辅助功能资源中心](https://www.adobe.com/accessibility/)。
