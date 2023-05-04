---
title: 开发和页面差异
seo-title: Developing and Page Diff
description: 开发和页面差异
seo-description: null
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
exl-id: 365e944d-d8a3-4f4e-8925-88629845232f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 1%

---

# 开发和页面差异{#developing-and-page-diff}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 功能概述 {#feature-overview}

内容创建是一个迭代过程。 高效创作需要能够查看从一个迭代到另一个迭代所发生的更改。 查看一个页面版本，然后查看另一个页面版本效率低下且容易出错。 作者希望能够并排比较当前页面与之前版本之间的差异。

页面差异允许用户将当前页面与启动项、先前版本等进行比较。 有关此用户功能的详细信息，请参阅 [页面差异](/help/sites-authoring/page-diff.md).

## 操作详细信息 {#operation-details}

比较页面版本时，用户希望比较的先前版本由AEM在后台重新创建，以便进行比较。 需要此参数才能渲染内容 [并排比较](/help/sites-authoring/page-diff.md#presentation-of-differences).

此娱乐操作由AEM内部完成，对用户是透明的，无需干预。 但是，如果管理员在CRX DE Lite中查看存储库（例如，查看存储库），则会在内容结构中看到这些重新创建的版本。

根据AEM修补程序级别的不同，行为不同，可能需要特定权限才能正常工作。

### AEM 6.4.3之前 {#prior-to-aem}

比较内容时，会在以下位置重新创建要比较页面之前的整个树：

`/content/versionhistory/<userId>/<site structure>`

由于使用页面差异机制时，AEM会重新创建页面的先前版本，因此要使用该功能，用户必须具有特定的JCR权限。

>[!CAUTION]
>
>要使用页面差异功能，用户需要 **修改/创建/删除** 对节点的权限 `/content/versionhistory`.

### 自AEM 6.4.3起 {#as-of-aem}

比较内容时，会在以下位置重新创建要比较页面之前的整个树：

`/tmp/versionhistory/`

此内容由具有限制当前用户可见性的权限的服务用户创建。 因此，无需特殊权限。

自动运行清理任务以清理此临时内容。

## 开发人员限制 {#developer-limitations}

以前，在经典UI中，必须特别考虑开发问题以便于进行AEM比较(例如，使用 `cq:text` 标记库，或自定义集成 `DiffService` OSGi服务到组件)。 新的差异功能不再需要此功能，因为差异会通过DOM比较在客户端发生。

但是，开发人员需要考虑许多限制。

* 此功能使用与AEM产品无间隔名称的CSS类。 如果页面上包含其他具有相同名称的自定义CSS类或第三方CSS类，则差异的显示可能会受到影响。

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 由于差异是客户端，并在页面加载时执行，因此在客户端差异服务运行后对DOM所做的任何调整将不会计算在内。 这可能会影响

   * 使用AJAX包含内容的组件
   * 单页面应用程序
   * 可在用户交互时处理DOM的基于Javascript的组件。
