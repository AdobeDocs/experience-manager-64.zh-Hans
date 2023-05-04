---
title: AEM Foundation和存储库
seo-title: AEM Foundation & Repository
description: 特定于Adobe Experience Manager 6.3 AEM平台和存储库的发行说明。
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# AEM Foundation和存储库 {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 更改列表 {#list-of-changes}

### 存储库 {#repository}

* Oak Segment Tar MicroKernel

   * 用于在线修订清理的快速压缩模式（尾部压缩）
   * 提高了写入率
   * 通过JMXBean公开的区段操作统计资料
   * 离线修订清理的持续时间估计

* Oak Mongo微内核

   * MongoMK的连续修订版清理取代了计划清理维护

* 提高了文档节点上修订清理的效率
* 请参阅 [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) 和 [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) 以了解已修复问题的完整概述。

>[!CAUTION]
>
>* 自AEM 6.3以来的新版本Oak Segment Tar需要存储库迁移。 如果您从旧版TarMK升级或希望从其他类型的持久性中切换新的Tar区段，则必须执行此步骤。 有关新区段焦油的优势的更多信息，请参阅 [迁移到Oak区段Tar常见问题解答](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### 搜索和索引 {#search-amp-indexing}

* 通过oak-run(CLI)增强了对索引操作的支持：

   * 索引一致性检查
   * 索引统计信息
   * 索引配置Im/Export
   * 重新索引

* 降低了与Lucene相关的存储库增长，以提高系统整体性能
* 同步Lucene属性索引 [（更多信息）](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* 索引管理器中的“解释查询”现在支持AEM QueryBuilder语法
* 索引管理器现在公开索引量度：大小、上次更新和一致性检查

### 用户界面 {#user-interface}

* 对UI进行了各种增强，使其工作效率更高、使用更方便。
* 新增了内容树边栏，可快速导航层次结构。 与列表视图结合使用，可恢复经典UI交互模型。
* 改进了大型文件夹的卡片视图和列表视图中的滚动。
* 改进了与搜索结果的交互 — 返回按钮可恢复之前的搜索结果。
* 其他键盘快捷键，用于大多数常用操作，例如打开特定边栏、编辑、移动和删除项目，或打开属性。
* 能够禁用键盘快捷键（在“首选项”中启用/禁用）。
* 在7天后，停止在所有UI中显示相对时间戳（在“首选项”中设置默认设置）。

>[!CAUTION]
>
>* Adobe不打算进一步增强经典UI。 AEM 6.4包含经典UI，从早期版本升级的客户可以继续按原样使用它。 请注意，经典UI在弃用时仍完全受支持 [了解更多](/help/sites-deploying/ui-recommendations.md).
>


### 内容分发 {#content-distribution}

* 改进了复制性能以支持发布的大卷资产
* 在分发传输中支持OAuth 2.0身份验证
* 改进了VLT包的性能

### 监测 {#monitoring}

* 新的“系统概述”提供了所有与性能相关的系统状态和活动的快照视图
* 新的运行状况检查：

   * 检测大Lucene索引
   * 异步索引运行状况
   * 大型 Lucene 索引
   * 查询性能
   * 查询遍历限制
   * 同步的时钟
   * 系统维护 — 修订清理
   * 系统维护 — DataStore GC
   * 系统维护 — 连续修订GC

* 用户现在可以定义status.zip下载的范围

### 维护 {#maintenance}

* 使用维护任务主动删除Lucene二进制文件
* MongoDB的RevisionGC维护任务现已禁用，以支持连续修订清理，请参阅上面的Repository部分。
* 版本清除配置允许保留最低版本数
* 版本清除在维护窗口结束时停止。 也可以手动启动和停止，并将在下次启动时以递增方式继续。

### 升级 {#upgrade}

* 向后兼容性：6.4中的向后兼容功能有助于在大多数情况下保持自定义代码的兼容性，并减少升级工作。
* 升级复杂性评估：新的模式检测器工具可评估升级的复杂性。
* 可持续升级：引入API界面和内容分类旨在帮助您轻松遵循最佳实践，在整个开发周期中高效、无缝地升级到下一版本。
* 存储库重组：大幅重组（主要是/etc），以便于更轻松地升级并促进实施最佳实践。 [了解更多。](/help/sites-deploying/repository-restructuring.md)
* 请参阅 [升级文档](/help/sites-deploying/upgrade.md) 以了解有关这些功能的更多详细信息。

### Cloud Service {#cloud-services}

* 许多Cloud Services现在可通过触屏UI进行配置；其余的可在旧版Cloud Services卡下进行配置。
* 站点和资产文件夹可以配置以上下文感知方式加载的Cloud Services。

### 安全性 {#security}

* 增强并简化了用户创建UI，支持多个用户配置文件。
* 提高了用户大型组成员关系的性能。

### 项目和工作流 {#projects-and-workflows}

* 基于触屏UI的工作流编辑器，以更简化的方式管理工作流模型。
* 支持在维护任务中清除项目任务。
