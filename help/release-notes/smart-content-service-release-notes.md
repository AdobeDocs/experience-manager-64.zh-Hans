---
title: 智能内容服务发行说明
seo-title: 智能内容服务发行说明
description: 智能内容服务的概述和服务的已知问题。
seo-description: 智能内容服务的概述和服务的已知问题。
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 8%

---


# 智能内容服务发行说明{#smart-content-service-release-notes}

智能内容服务的概述和服务的已知问题。

组织需要根据员工、合作伙伴和客户引用和搜索数字资产时所使用的分类标记其数字资产。 与通用标记相比，基于业务分类标记的资产更容易识别和检索，而基于标记的搜索则更容易。

智能内容服务使用您的AEM Assets分类法自动标记数字资产，从而确保最相关的资产出现在搜索中。

您必须对AEM资产和标记的精选集合进行智能内容服务培训，以识别您的业务分类。 经过培训后，服务可以将这些标记应用于类似的资产集。

智能内容服务由Adobe Sensei平台提供支持，该平台使您能够针对您的业务分类培训图像识别算法。 此内容智能随后可用于对类似资产应用相关标记。

## 关键改进{#key-improvements}

智能内容服务包括以下主要改进：

* 进一步提高模型精度、查全值的算法优化
* 支持在租户级别重置所有标记的模型培训
* 支持增强的智能标记命名空间以避免冲突
* 新的模型替换策略可避免再培训导致的降级
* 服务使用情况的租户监控
* 针对群集和连接问题的修复，它们增强了服务的健壮性

## 修复的问题 {#fixed-issues}

此版本中修复了以下问题：

* 如果无法连接到MySQL服务器，标记和培训工作流的工作进程将终止。 CQ-4242886

* 精度偏差得分计算不正确。 CQ-4241797

* 模型的PR计算不正确。 CQ-4241381

* 从队列CQ-4240901处理示例资源时，培训工作流会忽略这些资源

* 精确召回的改进。 CQ-4239895

* 型号替换策略。 CQ-4239886

* 男衬衫的图片上贴着女夹克标签。 CQ-4239650

* 在舞台部署时会错过培训示例。 CQ-4239483

* 应对提交用于培训的一组资产进行培训作业的验证。 CQ-4238834

* 即使标签存在最小的正／负值，模型创建也会因负值筛选而失败。 CQ-4240741

* 培训师日志中负面觅食的误导性条目。 CQ-4240738

* 首次培训如果为培训提交的标记是相互随机的负片，则会出现问题。 CQ-4240118

* 即时修改日志，以监视每个租户的服务使用情况。 CQ-4239781

## 语言 {#languages}

智能内容服务适用于以下区域设置：

* 英语
* 德语
* 法语
* 西班牙语
* 意大利语
* 葡萄牙语
* 日语
* 简体中文
* 韩语

## 链接 {#links}

* [adobe.com 上的 Adobe Experience Manager 产品页面](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [增强的智能标记文档](/help/assets/enhanced-smart-tags.md)

## 产品访问和支持（受限站点）{#product-access-and-support-restricted-sites}

这些网站仅适用于客户。如果您是Adobe并需要访问，请与客户经理联系。

* [产品访问](https://login.marketing.adobe.com)
* [产品下载：licensing.adobe.com](https://licensing.adobe.com/).
* 有关[软件分发](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上其他功能的产品更新、修补程序和软件包。
* [通过Admin Console提供客户支持](https://adminconsole.adobe.com/)。有关详细信息，请参阅[新Adobe客户支持体验](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。
