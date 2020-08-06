---
title: Oak索引疑难解答
seo-title: Oak索引疑难解答
description: 如何检测和修复慢速重新索引。
seo-description: 如何检测和修复慢速重新索引。
uuid: 6567ddae-128c-4302-b7e8-8befa66b1f43
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: ea70758f-6726-4634-bfb4-a957187baef0
translation-type: tm+mt
source-git-commit: d97828afee7a65e7a4036912c1cc8726404088c9
workflow-type: tm+mt
source-wordcount: '1486'
ht-degree: 1%

---


# Oak索引疑难解答{#troubleshooting-oak-indexes}

## 慢速重新索引  {#slow-re-indexing}

AEM内部重新索引过程会收集存储库数据并将其存储在Oak索引中，以支持对内容的性能查询。 在特殊情况下，该过程可能会变得缓慢甚至停滞。 本页用作疑难解答指南，帮助确定索引编制速度慢、查找原因并解决问题。

区分需要花费不适当长时间的重新编制索引和需要很长时间的重新编制索引非常重要，因为它正在编制大量内容的索引。 例如，索引内容所需的时间会随着内容的数量而扩展，因此大型生产存储库重新索引所需的时间要比小型开发存储库更长。

有关何 [时以及如何重新编制内容索引](/help/sites-deploying/best-practices-for-queries-and-indexing.md) ，请参阅查询和索引方面的最佳实践。

## 初始检测 {#initial-detection}

初始检测慢速索引需要查 `IndexStats` 看JMX MBean。 在受影响的AEM实例上，执行以下操作：

1. 打开Web控制台，单击JMX选项卡或转至https://&lt;host>:&lt;port>/system/console/jmx(例如， [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))。
1. 导航到姆 `IndexStats` 拜人。
1. 打开“ `IndexStats` ”和“ `async`”的MB `fulltext-async`ean。

1. 对于这两个MBean，检 **查Done** timestamp **和LastIndexTime** timestamp是否距当前时间不到45分钟。

1. 对于MBean，如果时间值(**Done****或LastIndexedTime**)从当前时间起大于45分钟，则索引作业将失败或耗时过长。 这会导致异步索引失效。

## 强制关闭后索引暂停 {#indexing-is-paused-after-a-forced-shutdown}

强制关闭导致AEM在重新启动后将异步索引挂起最多30分钟，并且通常需要另外15分钟来完成第一次重新索引通过，总时间约为45分钟(与45分钟的初始 [检测](/help/sites-deploying/troubleshooting-oak-indexes.md#initial-detection) 时间范围相连)。 在事件中，您怀疑在强制关闭后索引已暂停：

1. 首先，确定AEM实例是以强制方式关闭(AEM进程被强制关闭，还是出现电源故障)，然后重新启动。

   * [AEM日志记录](/help/sites-deploying/configure-logging.md) ，可以为此目的进行审核。

1. 如果发生强制关闭，则在重新启动时，AEM会自动暂停重新索引，时间最长为30分钟。
1. 等待大约45分钟，AEM才能恢复正常的异步索引操作。

## 线程池重载 {#thread-pool-overloaded}

>[!NOTE]
>
>对于AEM 6.1，请确 [保安装AEM 6.1](https://helpx.adobe.com/experience-manager/release-notes-aem-6-1-cumulative-fix-pack.html) CFP 11。

在特殊情况下，用于管理异步索引的线程池可能会过载。 为了隔离索引过程，可以配置一个线程池以防止其他AEM工作干扰Oak及时索引内容的能力。 为此，您应：

1. 为Apache Sling调度程序定义用于异步索引的新的隔离线程池：

   * 在受影响的AEM实例上，导航到AEM OSGi Web Console>OSGi>Configuration>Apache Sling调度程序或转到https://&lt;host>:&lt;port>/system/console/configMgr(例如， [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr))
   * 向“允许的线程池”字段添加一个值为“oak”的条目。
   * 单击右下角的保存以保存更改。

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. 验证新的Apache Sling调度程序线程池是否已注册并显示在Apache Sling调度程序状态Web控制台中。

   * 导航到AEM OSGi Web控制台>状态>Sling调度程序，或转到https://&lt;host>:&lt;port>/system/console/status-slingscheduler(例如， [http://localhost:4502/system/console/status-slingscheduler](http://localhost:4502/system/console/status-slingscheduler))
   * 验证以下池条目是否存在：

      * ApacheSlingoak
      * ApacheSlingdefault

   ![chlimage_1-120](assets/chlimage_1-120.png)

## 观察队列已满 {#observation-queue-is-full}

如果在短时间内对存储库进行了太多更改和提交，则可能由于完全观察队列而延迟索引。 首先，确定观测队列是否满：

1. 转到“Web控制台”并单击“JMX”选项卡或转到https://&lt;host>:&lt;port>/system/console/jmx(例如， [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
1. 打开Oak存储库统计信息MBean，并确 `ObservationQueueMaxLength` 定任何值是否大于10,000。

   * 在正常操作中，此最大值必须最终减小为零(尤 `per second` 其在该部分)，以验证 `ObservationQueueMaxLength`秒量度是否为0。
   * 如果值为10,000或更高，并且稳步增加，则表示至少一个（可能更多）队列无法像发生新更改（提交）那样快速处理。
   * 每个观察队列都有一个限制（默认为10,000），如果队列达到该限制，其处理会降低。
   * 当使用MongoMK时，随着队列长度的增大，内部Oak缓存性能会降低。 统计信息MBean中缓存的 `missRate` 增加 `DocChildren` 可以看到 `Consolidated Cache` 此关联。

1. 为避免超出可接受的观察队列限制，建议：

   * 降低提交的恒定速率。 承诺量中的短峰值是可以接受的，但应该降低恒定速率。
   * 按照性能调整提示> `DiffCache` Mongo存储 [调整>文档缓存大小中的说明增加大小](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html#main-pars_text_3)。

## 识别和修复卡住的重新索引过程 {#identifying-and-remediating-a-stuck-re-indexing-process}

在以下两种情况下，重新编制索引可以视为“完全卡住”:

* 重新编制索引非常慢，直到日志文件中没有报告关于已遍历的节点数的显着进度。

   * 例如，如果在一小时内没有消息，或者进度太慢，需要一周或更长的时间才能完成。

* 如果索引线程的日志文件（例如）中出现重复的异常，则重新索引将卡 `OutOfMemoryException`在一个循环中。 在日志中重复出现相同的异常，表明Oak试图重复对同一事件进行索引，但在同一问题上失败。

要识别并修复卡住的重新索引过程，请执行以下操作：

1. 要确定索引卡住的原因，必须收集以下信息：

   * 收集5分钟的线程转储，每2秒一个线程转储。
   * [设置附加器的DEBUG级别和日志](/help/sites-deploying/configure-logging.md)。

      * *org.apache.jackrabbit.oak.plugins.index.AsyncIndexUpdate*
      * *org.apache.jackrabbit.oak.plugins.index.IndexUpdate*
   * 从异步MBean收集 `IndexStats` 数据：

      * 导航到AEM OSGi Web Console>Main>JMX>IndexStat>async

         或转到 [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats)
   * 使 [用oak-run.jar的控制台模式](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) ，收集**节点下存在内容的 `/:async`详细信息。
   * 使用MBean收集一列表存储库检 `CheckpointManager` 查点：

      * AEM OSGi Web Console>Main>JMX>CheckpointManager>listCheckpoints()

         或转到 [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager)



1. 在收集步骤1中概述的所有信息后，重新启动AEM。

   * 在并发负载较高（观察队列溢出或类似情况）的情况下，重新启动AEM可能会解决该问题。
   * 如果重新启动不能解决问题，请打开Adobe客 [户关怀的问题](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html) ，并提供在步骤1中收集的所有信息。

## 安全中止异步重新索引 {#safely-aborting-asynchronous-re-indexing}

可以通过和f索引通道(Mbean)安全中止(在完成之 `async, async-reindex`前停止 `ulltext-async` 重新索引 `IndexStats` )。 有关详细信息，另请参阅Apache Oak文档中的 [How to Abort Reindexing](https://jackrabbit.apache.org/oak/docs/query/indexing.html#abort-reindex)。 此外，请考虑以下事项：

* Lucene和Lucene属性索引的重新索引可以中止，因为它们是自然异步的。
* 只有在通过启动重新索引后，才能中止Oak属性索引的重新索引 `PropertyIndexAsyncReindexMBean`。

要安全地中止重新索引，请执行以下步骤：

1. 确定控制需要停止的重新索引通道的IndexStats MBean。

   * 通过JMX控制台导航到相应的IndexStats MBean，方法是转到AEM OSGi Web Console>Main>JMX或https://&lt;host>:&lt;port>/system/console/jmx(例如， [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
   * 根据要停止的重新索引通道（、或）打 `async`开 `async-reindex`IndexStats `fulltext-async`MBean

      * 要识别相应的航线，从而识别IndexStats MBean实例，请查看Oak Indexes &quot;async&quot;属性。 “async”属性将包含通道名称： `async`、 `async-reindex`或 `fulltext-async`。
      * 也可通过访问“异步”列中的AEM Index Manager访问该通道。 要访问索引管理器，请导航到“操作”>“诊断”>“索引管理器”。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 调用相 `abortAndPause()` 应MBean上的命 `IndexStats` 令。
1. 正确标记Oak索引定义，以防止在索引通道恢复时恢复重新索引。

   * 重新索引现有索 **引时** ，将reindex属性设置为false

      * `/oak:index/someExistingIndex@reindex=false`
   * 或者，对于新 **索引** ，可以选择：

      * 将类型属性设置为禁用

         * `/oak:index/someNewIndex@type=disabled`
      * 或完全删除索引定义

   完成后，将更改提交到存储库。

1. 最后，在中止的索引通道上恢复异步索引。

   * 在步骤 `IndexStats` 2中发出该命 `abortAndPause()` 令的MBean中，调用该 `resume()`命令。

## 防止慢速重新索引 {#preventing-slow-re-indexing}

最好在安静的时段（例如，不是在大的内容摄取期间）重新索引，最好在已知和控制AEM负载的维护窗口期间重新索引。 另外，确保在其他维护活动中不进行重新索引。
