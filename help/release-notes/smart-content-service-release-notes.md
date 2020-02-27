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
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# 智能内容服务发行说明 {#smart-content-service-release-notes}

智能内容服务的概述和服务的已知问题。

组织需要根据员工、合作伙伴和客户引用和搜索数字资产时所使用的分类标记其数字资产。 与通用标记相比，基于业务分类标记的资产更容易被基于标记的搜索识别和检索。

智能内容服务使用您的AEM资产业务分类来自动标记数字资产，从而确保最相关的资产显示在搜索中。

您必须针对一组精选的AEM资产和标记培训智能内容服务，以识别您的业务分类。 经过培训后，服务可以将这些标记应用于类似的资产集。

智能内容服务由Adobe Sensei平台提供支持，该平台使您能够根据业务分类培训图像识别算法。 此内容智能随后可用于对类似资产应用相关标记。

## 主要改进 {#key-improvements}

智能内容服务包括以下主要改进：

* 进一步提高模型精度、召回率值的算法优化
* 支持在租户级别重置所有标记的模型培训
* 支持增强的智能标记命名空间以避免冲突
* 避免再培训导致的退化的新模型替换策略
* 服务使用的租户监控
* 针对群集和连接相关问题的修复，它们增强了服务的健壮性

## 修复的问题 {#fixed-issues}

此版本中修复了以下问题：

* 如果无法连接到MySQL服务器，标记和培训工作流的Worker进程将终止。 CQ-4242886

* 未正确计算存在精度偏差的得分。 CQ-4241797

* 模型的PR计算不正确。 CQ-4241381

* 从队列CQ-4240901处理示例资源时，培训工作流会忽略这些资源

* 精确召回方面的改进。 CQ-4239895

* 型号更换策略。 CQ-4239886

* 男式衬衫的图像用女式夹克标签做标记。 CQ-4239650

* 在舞台部署时，会错过培训示例。 CQ-4239483

* 应对为培训提交的一组资产进行培训作业的验证。 CQ-4238834

* 即使标签存在最小的正／负值，模型创建也会因负值筛选而失败。 CQ-4240741

* 培训师日志中负面觅食的误导性条目。 CQ-4240738

* 首次培训的问题：为培训提交的标记是相互随机的负片。 CQ-4240118

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

## Product Access and Support (Restricted Sites) {#product-access-and-support-restricted-sites}

这些网站仅适用于客户。如果您是客户并需要访问，请与您的Adobe客户经理联系。

* [](https://daycare.day.com) 产 [品访问](https://login.marketing.adobe.com)

* [Adobe客户关怀](https://helpx.adobe.com/contact/enterprise-support.ec.html)
