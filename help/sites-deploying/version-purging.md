---
title: 版本清除
seo-title: 版本清除
description: 本文介绍了用于清除版本的可用选项。
seo-description: 本文介绍了用于清除版本的可用选项。
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
translation-type: tm+mt
source-git-commit: 510b6765e11a5b3238407322d847745f09183d63

---


# 版本清除{#version-purging}

在标准安装中，在更新内容后激活页面时，AEM会创建页面或节点的新版本。

>[!NOTE]
>
>如果未进行任何内容更改，您将看到一条消息，指明页面已激活，但不会创建新版本

您可以使用Sidekick的“版本控制”选项卡 **在请求时** ，创建其他版本。 这些版本存储在存储库中，并可在需要时恢复。

这些版本从不被清除，因此存储库大小会随着时间而增大，因此需要进行管理。

AEM随附各种机制，可帮助您管理存储库：

* 版本 [管理器](#version-manager)

   可以将其配置为在创建新版本时清除旧版本。

* 清除 [版本工具](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   这用作监视和维护存储库的一部分。

   它允许您根据以下参数干预删除旧版本的节点或节点层次结构：

   * 存储库中要保存的最大版本数。

      超出此数量时，将删除最旧版本。

   * 存储库中保存的任何版本的最大年龄。

      当版本的年龄超过此值时，将从存储库中清除该版本。

* “版 [本清除”维护任务](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks)。 您可以计划“版本清除”维护任务，以自动删除旧版本。 因此，这会最大限度地减少手动使用版本清除工具的需求。

>[!CAUTION]
>
>要优化存储库大小，您应经常运行版本清除任务。 当流量有限时，应在工作时间以外安排任务。

## 版本管理器 {#version-manager}

除了通过清除工具明确清除外，还可以将版本管理器配置为在创建新版本时清除旧版本。

要配置版本管理器，请为以下对象创建配置：

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

以下选项可供选择：

* `versionmanager.createVersionOnActivation` (Boolean，默认值：true)

   是否在激活页面时创建版本。

   除非将复制代理配置为禁止创建版本，否则将创建一个版本，Version Manager将支持此功能

   只有在versionmanager.ivPaths中包含的路径上进行激活时，才会创建版本（请参阅下文）。

* `versionmanager.ivPaths` (字符串[]，默认值：{&quot;/&quot;})

   在versionmanager.createVersionOnActivation为true时，在激活时隐式创建版本的路径。

* `versionmanager.purgingEnabled` (Boolean，默认值：false)

   是否在创建新版本时启用清除

* `versionmanager.purgePaths` (字符串[]，默认值：{&quot;/content&quot;})

   创建新版本时要清除版本的路径。

* `versionmanager.maxAgeDays` (int, default:30)

   清除时，将删除任何早于此值的版本。 如果此值小于1，则不根据版本的年龄执行清除

* `versionmanager.maxNumberVersions` （int，默认为5）

   清除后，将删除早于第n个最新版本的任何版本。 如果此值小于1，则不根据版本数执行清除

* `versionmanager.minNumberVersions` (int, default 0)

   不论使用期限如何，要保留的最低版本数。 如果将此值设置为小于1的值，则不保留最低版本数。

>[!NOTE]
>
>建议不要在存储库中保留大量版本。 因此，在配置版本清除操作时，请注意不要从清除中排除太多版本，否则存储库大小将无法正确优化。 如果您因业务需要而保留大量版本，请联系Adobe支持部门以找到优化存储库大小的其他方法。

### 组合保留选项 {#combining-retention-options}

定义应如何保留的版本( `maxAgeDays`、 `maxNumberVersions`、 `minNumberVersions`)的选项可根据您的要求组合。

例如，在定义要保留的最大版本数时，以及要保留的最旧版本时：

* 设置:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* 通过以下方式：

   * 过去60天内制作了10个版本
   * 过去30天内创建的版本中的3个

* 威尔的意思是：

   * 最后3个版本将保留

例如，在定义要保留的最大AND最小版本数和要保留的最旧版本数时：

* 设置:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* 通过以下方式：

   * 60天前制作的5个版本

* 威尔的意思是：

   * 将保留3个版本

## 清除版本工具 {#purge-versions-tool}

清 [除版本工具](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) ，用于清除存储库中节点或节点层次结构的版本。 其主要用途是通过删除旧版本的节点来帮助您减小存储库的大小。
