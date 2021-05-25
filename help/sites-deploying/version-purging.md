---
title: 版本清除
seo-title: 版本清除
description: 本文介绍了用于版本清除的可用选项。
seo-description: 本文介绍了用于版本清除的可用选项。
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: 配置
exl-id: 357d5f23-3e75-44e3-905f-4efe960858bf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 2%

---

# 版本清除{#version-purging}

在标准安装中，当您在更新内容后激活页面时，AEM会创建页面或节点的新版本。

>[!NOTE]
>
>如果未对内容进行任何更改，您将看到一条消息，指出页面已激活，但不会创建任何新版本

您可以使用Sidekick的&#x200B;**版本控制**&#x200B;选项卡在请求时创建其他版本。 这些版本存储在存储库中，并可在需要时还原。

这些版本从未清除过，因此存储库大小会随着时间的推移而增加，因此需要进行管理。

AEM附带了多种机制，可帮助您管理存储库：

* [版本管理器](#version-manager)

   这可以配置为在创建新版本时清除旧版本。

* [清除版本](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)工具

   它用作监控和维护存储库的一部分。

   它允许您根据以下参数干预以删除旧版本的节点或节点层次结构：

   * 要保留在存储库中的最大版本数。

      超过此数量时，将删除最早的版本。

   * 存储库中保留的任何版本的最大年龄。

      当版本的年龄超过此值时，会从存储库中清除该值。

* [版本清除维护任务](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks)。 您可以计划“版本清除”维护任务以自动删除旧版本。 因此，这可以最大限度地减少手动使用版本清除工具的需求。

>[!CAUTION]
>
>为了优化存储库大小，您应经常运行版本清除任务。 当流量有限时，应将任务安排在工作时间之外。

## 版本管理器{#version-manager}

除了通过清除工具明确清除之外，还可以将版本管理器配置为在创建新版本时清除旧版本。

要配置版本管理器，请为以下项创建配置：

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

以下选项可供选择：

* `versionmanager.createVersionOnActivation` (布尔值，默认值：true)

   是否在激活页面时创建版本。

   将创建一个版本，除非将复制代理配置为禁止创建版本，版本管理器会执行此操作

   仅当在versionmanager.ivPaths中包含的路径上进行激活时，才会创建版本（请参阅下文）。

* `versionmanager.ivPaths` (字符串[]，默认值：{&quot;/&quot;})

   如果versionmanager.createVersionOnActivation为true，则激活时会隐式创建版本的路径。

* `versionmanager.purgingEnabled` (布尔值，默认值：false)

   创建新版本时是否启用清除

* `versionmanager.purgePaths` (字符串[]，默认值：{&quot;/content&quot;})

   创建新版本时用于清除版本的路径。

* `versionmanager.maxAgeDays` （整数，默认值）30)

   清除时，将删除低于此值的任何版本。 如果此值小于1，则不会根据版本的年龄执行清除

* `versionmanager.maxNumberVersions` （int，默认5）

   清除时，任何版本早于第n个最新版本的版本都将被删除。 如果此值小于1，则不会根据版本数执行清除

* `versionmanager.minNumberVersions` （int，默认0）

   要保留的最低版本数，与年龄无关。 如果将此值设置为小于1的值，则不会保留最低版本数。

>[!NOTE]
>
>不建议在存储库中保留大量版本。 因此，在配置版本清除操作时，需要注意不要从清除中排除太多版本，否则将无法正确优化存储库大小。 如果您因业务需要而保留了大量版本，请联系Adobe支持以查找优化存储库大小的其他方法。

### 组合保留选项{#combining-retention-options}

定义应如何保留哪些版本的选项(`maxAgeDays`、`maxNumberVersions`、`minNumberVersions`)可根据您的要求进行组合。

例如，在定义要保留的最大版本数时，AND要保留的最旧版本：

* 设置:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* 通过以下方式：

   * 过去60天内制作了10个版本
   * 过去30天内创建的版本中有3个

* 将表示：

   * 最后3个版本将保留

例如，在定义要保留的最大版本数AND最小值数，以及要保留的最旧版本时：

* 设置:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* 通过以下方式：

   * 60天前创建的5个版本

* 将表示：

   * 将保留3个版本

## 清除版本工具{#purge-versions-tool}

[清除版本](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool)工具用于清除存储库中节点或节点层次结构的版本。 其主要目的是通过删除节点的旧版本来帮助您减小存储库的大小。
