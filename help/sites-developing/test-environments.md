---
title: 需要哪些测试环境？
seo-title: Which Test Environments are needed?
description: 应将多个环境视为测试的一部分
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 2%

---

# 需要哪些测试环境？{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

要定义测试的配置，您应考虑以下事项：

**开发**  — 用于单元和某些集成测试。

**测试**  — 大多数测试。

**实时**  — 用于最终性能和压力测试。 也用于与客户进行验收测试。

您还需要确定在什么位置需要哪些实例（通常在所有测试级别中每个实例至少需要一个）：

**作者**  — 此实例允许作者输入和发布内容。

**发布**  — 此实例以其发布的形式显示网站，供访客访问。

应与Dispatcher一起测试。

最后，必须考虑实际硬件 — 在配置尽可能接近最终实时环境的系统上进行任何性能测试。 因此，还建议将项目启动项拆分为：

**软启动**  — 降低可用性；这样，就可以在生产环境中的实际条件下进行性能测试、调整和优化。

**硬启动**  — 完全可用。
