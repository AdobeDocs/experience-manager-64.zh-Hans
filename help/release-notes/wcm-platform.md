---
title: AEM Foundation 和存储库
seo-title: AEM Foundation 和存储库
description: 以下发行说明特定于 Adobe Experience Manager 6.3 AEM 平台和存储库。
seo-description: 以下发行说明特定于 Adobe Experience Manager 6.3 AEM 平台和存储库。
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 17%

---


# AEM Foundation 和存储库  {#aem-foundation-repository}

## 更改列表 {#list-of-changes}

### 存储库 {#repository}

* Oak Segment Tar MicroKernel

   * 用于在线修订清理的快速压缩模式（尾部压缩）
   * 提高了写入速率
   * 通过JMXBean公开的细分操作统计数据
   * 脱机修订清除的持续时间估计

* Oak Mongo Microkernel

   * MongoMK的连续修订清理取代了计划清理维护

* 提高了文档节点修订清理的效率
* 请参见[Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt)、[Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt)和[Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt)，了解已修复问题的完整概述。

>[!CAUTION]
>
>* 自 AEM 6.3 以后提供的新版 Oak Segment Tar 需要存储库迁移。如果要从旧版本的 TarMK 升级或想要从其他类型的持久性切换新的 Tar 区段，那么必须执行此步骤。有关新的Segment Tar的优势的更多信息，请参见[迁移到Oak Segment Tar常见问题解答](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar)。

>



### 搜索和索引 {#search-amp-indexing}

* 通过oak-run(CLI)增强对索引操作的支持：

   * 索引一致性检查
   * 索引统计
   * 索引配置Im/Export
   * 重新索引

* 降低了与Lucene相关的存储库的增长，从而整体提高了系统性能
* 同步Lucene属性索引[（更多信息）](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Index Manager中的说明查询现在支持AEM QueryBuilder语法
* Index Manager现在公开索引指标：大小，上次更新和一致性检查

### 用户界面 {#user-interface}

* 对UI进行了各种增强，使其更高效、更易于使用。
* 新建内容树边栏可快速导航层次结构。 与列表视图相结合，这将恢复经典UI交互模型。
* 改进了卡中的滚动和大型文件夹的列表视图。
* 改进了与搜索结果的交互——返回按钮可恢复先前的搜索结果。
* 其他键盘快捷键，用于大多数常用操作，如打开特定边栏、编辑、移动和删除项目或打开属性。
* 能够禁用键盘快捷键（在首选项中启用／禁用）。
* 在7天后，停止在所有UI中显示时间戳（在“首选项”中设置默认值）。

>[!CAUTION]
>
>* Adobe 不打算进一步增强经典 UI。AEM 6.4 包含经典 UI，从早期发行版升级的客户可以继续按原样使用它。请注意，当[已弃用时，经典UI仍完全受支持。请阅读更多](/help/sites-deploying/ui-recommendations.md)。

>



### 内容分发 {#content-distribution}

* 改进了复制性能以支持大卷资产发布
* 在分发传输中支持OAuth 2.0身份验证
* 改进了VLT包的性能

### 监测 {#monitoring}

* 新的系统概述提供了有关所有与性能相关的系统状态和视图的快照活动
* 新的运行状况检查：

   * 检测大Lucene索引
   * 异步索引运行状况
   * 大型 Lucene 索引
   * 查询性能
   * 查询遍历限制
   * 同步的时钟
   * 系统维护——修订清理
   * 系统维护- DataStore GC
   * 系统维护——连续修订GC

* 用户现在可以定义status.zip下载的范围

### 维护 {#maintenance}

* 使用维护任务主动删除Lucene二进制文件
* MongoDB的RevisionGC维护任务现在禁用，而改为“连续修订清理”，请参阅上面的“存储库”部分。
* 版本清除配置允许保留最低版本数
* 版本清除在维护窗口的末尾停止。 还可以手动启动和停止它，并在下一个开始中以增量方式继续。

### 升级 {#upgrade}

* 向后兼容性：6.4中的向后兼容功能有助于在大多数情况下保持自定义代码的兼容性，并减少升级工作。
* 升级复杂性评估：新的图案检测器工具可评估升级的复杂性。
* 可持续升级：引入API界面和内容分类，帮助您在整个开发周期中轻松遵循最佳实践，实现有效、无缝的下一版本升级。
* 存储库重组：进行重大重组（主要是/etc），以便更轻松地进行升级并促进实施最佳做法。 [阅读更多。](/help/sites-deploying/repository-restructuring.md)
* 有关这些功能的详细信息，请参阅[升级文档](/help/sites-deploying/upgrade.md)。

### 云服务 {#cloud-services}

* 许多Cloud Services现在可通过触屏UI进行配置；其余Cloud Services卡可在旧版卡下配置。
* 站点和资产文件夹可以配置为以上下文感知方式加载的Cloud Services。

### 安全 {#security}

* 增强并简化了用户创建UI，支持多用户用户档案。
* 提高了用户大型组成员关系的性能。

### 项目和工作流 {#projects-and-workflows}

* 基于触屏UI的工作流编辑器，以更简化的方式管理工作流模型。
* 支持在维护任务中清除项目任务。

