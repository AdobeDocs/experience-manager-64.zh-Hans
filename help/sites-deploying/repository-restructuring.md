---
title: AEM 6.4中的存储库重组
seo-title: Repository Restructuring in AEM 6.4
description: 了解AEM 6.4中存储库重组的基础知识和推理
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 2%

---

# AEM 6.4中的存储库重组{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

在AEM 6.4发布之前，客户代码部署在JCR的不可预测区域，这些区域在升级时可能会发生更改。 因此，正式AEM版本通常会覆盖自定义代码、配置或内容。 此外，客户更改有时会覆盖AEM产品代码或内容，从而破坏产品功能。

通过明确定义AEM产品代码和客户代码的层次结构，可以避免这些冲突。

为此，从AEM 6.4开始，并在将来的版本中继续，内容将从/etc重组到存储库中的其他文件夹，以及有关内容放置位置的准则，同时遵循以下高级规则：

* AEM产品代码将始终置于/libs中，该代码不得被自定义代码覆盖
* 自定义代码应放置在/apps、/content和/conf中

## 对6.4升级的影响 {#impact-on-upgrades}

升级到AEM 6.4时，/etc下的大部分内容将复制到存储库中的其他文件夹中。 这些新位置是引用内容的首选位置。 但是，每次尝试都要使AEM 6.4升级向后兼容/etc文件夹中的先前位置，因此在大多数情况下，AEM代码将继续引用旧位置，直到客户应用程序中主动（在很多情况下是手动）进行更改为止。 从时间轴的角度来看，更改分为两类：

* 使用6.4升级 — 一些/etc重组更改不向后兼容，因此应在AEM 6.4升级中计划并实施这些修改。
* 在6.5升级之前 — 在以后的升级之后，绝大多数的/etc重组更改都可能会被推迟到某段时间。 如前所述，AEM 6.4代码将继续引用旧位置，直到将修改作为客户版本的一部分实施为止。 虽然没有应对其进行更改的强制时间表，但建议在6.5升级之前进行更改，因为将来的功能可能依赖于引用的新位置。 此外，根据惯例，某个特定功能的文档将引用新位置，因此，如果仍在使用旧位置，则可能会令人困惑。

### 重组指南 {#restructuring-guidance}

在计划升级到AEM 6.4时，应参考以下按解决方案划分的页面以评估工作情况：

* [所有AEM解决方案共有的存储库重组](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [AEM Sites存储库重组](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [AEM Assets存储库重组](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
* [AEM Assets Dynamic Media存储库重组](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [AEM Forms存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [AEM Communities存储库重组](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [AEM Commerce存储库重组](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

每个页面都包含两个对应于必要更改的紧急程度的部分。 在AEM 6.4升级项目中，应处理“升级版本6.4”部分下的任何内容。 “6.5升级之前”下的任何内容都可以选择推迟到升级后执行。

页面上的每个条目都包含一个“重组指南”字段，该字段详细介绍了与新的6.4存储库模型保持一致的建议技术策略，以便为以前位于/etc文件夹下的内容引用新位置。 附加的“注释”字段提供了任何其他有用的上下文。
