---
title: 智能内容服务发行说明
seo-title: 智能内容服务发行说明
description: 智能内容服务概述以及与服务相关的已知问题。
seo-description: 智能内容服务概述以及与服务相关的已知问题。
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: a842c45f0a0597f4c7f143974a550874258e5382
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 8%

---

# 智能内容服务发行说明{#smart-content-service-release-notes}

智能内容服务概述以及与服务相关的已知问题。

组织要求根据员工、合作伙伴和客户用来引用和搜索数字资产的分类来标记其数字资产。 与通用标记相比，基于业务分类标记的资产通过基于标记的搜索更容易识别和检索。

智能内容服务使用您的AEM Assets业务分类自动标记数字资产，以确保最相关的资产显示在搜索中。

您必须针对一组经过策划的AEM资产和标记来培训智能内容服务，以识别您的业务分类。 经过培训后，该服务可以将这些标记应用于一组类似的资产。

智能内容服务由Adobe Sensei平台提供支持，该平台允许您根据业务分类培训图像识别算法。 然后，可使用此内容智能对类似资产应用相关标记。

## 关键改进{#key-improvements}

智能内容服务包括以下主要改进：

* 算法优化以进一步提高模型精度、查全值
* 支持在租户级别重置所有标记的模型培训
* 支持增强型智能标记命名空间以避免冲突
* 新的模型替换政策，以避免因再培训而造成任何降级
* 按租户监控服务使用情况
* 修复了与群集和连接有关的问题，这些问题可增强服务的稳健性

## 修复的问题 {#fixed-issues}

此版本中修复了以下问题：

* 如果无法连接到MySQL服务器，则标记和培训工作流的工作进程将终止。 CQ-4242886

* 未正确计算有偏精度的分数。 CQ-4241797

* 模型的PR计算不正确。 CQ-4241381

* 培训工作流在从队列CQ-4240901中处理示例资产时缺少示例资产

* 提高了查准率。 CQ-4239895

* 模型替换策略。 CQ-4239886

* 男衬衫的图像上贴有女装夹克标签。 CQ-4239650

* 舞台部署中缺少培训示例。 CQ-4239483

* 应对提交培训的一组资产验证培训作业。 CQ-4238834

* 即使标记存在最小的正/负值，模型创建仍无法进行负筛选。 CQ-4240741

* 培训员日志中负面觅食的误导性条目。 CQ-4240738

* 如果为培训提交的标记是彼此随机的负值，则首次培训出现问题。 CQ-4240118

* 即时修改日志，以监控每个租户的服务使用情况。 CQ-4239781

## 语言 {#languages}

智能内容服务可用于以下区域设置：

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
* [增强型智能标记文档](/help/assets/enhanced-smart-tags.md)

## 产品访问和支持（受限站点）{#product-access-and-support-restricted-sites}

这些网站仅适用于客户。如果您是客户并需要访问，请联系您的Adobe客户经理。

* [产品访问](https://login.experiencecloud.adobe.com/exc-content/login.html)
* [产品下载：licensing.adobe.com](https://licensing.adobe.com/).
* 产品更新、修补程序和软件包，以获取[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上的其他功能。
* [通过Admin Console提供客户支持](https://adminconsole.adobe.com/)。有关更多信息，请参阅[新Adobe客户支持体验](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。
