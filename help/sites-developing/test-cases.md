---
title: 定义测试案例
seo-title: Defining your Test Cases
description: 您的测试用例应基于用例和详细要求规范
seo-description: Your test cases should be based upon the use cases and the detailed requirements specification
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
exl-id: ad529be3-9d31-492f-943f-ef3e99e13586
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 1%

---

# 定义测试案例{#defining-your-test-cases}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您的测试案例应基于：

**用例**

* 这些功能在行为者（启动某些操作的角色）与系统之间的交互方面定义了所需的功能。
* 用例应由客户定义。

**详细要求规范**

* 所有功能和性能要求都应进行测试。

测试应明确定义：

* 先决条件；这些功能可能涵盖特定系统、配置或测试人员的经验。
* 应采取的步骤；在适当的细节级别。
* 预期结果。
* 通过或失败的明确标准。

自动化测试用例的前景显然具有吸引力，因为它可以消除重复性任务。

## 手动测试与自动测试 {#manual-versus-automated-tests}

但是，自动化测试案例是一项重大投资，因此应考虑以下某些方面：

* 设置和配置需要时间、精力和经验。
* 如果基于浏览器，则安装浏览器更新时出现问题的风险会增加；需要更多时间进行纠正。
* 只对大项目是可行的。
* 当为测试或在长期发行计划中生成多个版本时，这是好事。

## 测试特定方面 {#testing-specific-aspects}

在测试AEM时，需要特别注意的一些特定详细信息：

创作和发布环境

不过， [环境](/help/sites-developing/the-basics.md#environments) 在测试方面，需要强调AEM的决定因素。

您必须将AEM视为两个应用程序：

* the **作者** 环境此实例允许作者输入和发布内容。
这有一小组（呃）可预测的用户，对于这些用户而言，特定功能和性能至关重要。
* the **发布** 环境此实例以其发布的形式显示网站，供访客访问。
这通常有更大的一组用户，其中流量并非总是100%可预测。 在响应请求时，性能仍然至关重要。 还必须考虑缓存和负载平衡。

尽管软件与此相同，但它们：

* 用于不同用途
* 对功能和性能有不同的要求
* 配置方式不同
* 单独调整
* 每人都有自己的一套验收测试

换言之，必须分别使用不同的测试用例对它们进行测试。

**个性化**

在测试个性化时，应使用多个用户帐户重复每个单独的用例，以证明其行为。

还必须检查缓存是否正确行为。

**调度程序**

大多数项目都将安装用于缓存和负载平衡的Dispatcher。

测试很困难（缓存发生在不同级别和不同位置），且必须使用黑匣子进行。 要测试的关键方面包括：

* **准确度**;确保网站访客能够看到内容更新。
* **连续性**;确保当一台服务器关闭时网站仍然可用。
* **聚类** 群集用于提供：
   * **故障转移**
如果一台服务器出现故障，则群集中的其他服务器将接管处理。
   * **性能**
具有完全故障转移的负载平衡可提高群集的性能。

当用于客户项目时，必须测试群集以确认配置的正确操作。

## 测试第三方软件 {#testing-third-party-software}

任何与AEM接口的第三方软件都将在详细要求规范中引用。

必须分析所需的任何测试（取决于定义的范围），并获得干净的测试。
