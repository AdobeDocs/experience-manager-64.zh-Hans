---
title: Assets 监控最佳实践
description: 监控环境和性能的最佳实践 [!DNL Experience Manager] 实例。
contentOwner: AG
feature: Asset Management
role: Admin,Architect
exl-id: edbb275a-5ead-4ed2-8708-29e766081d75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 1%

---

# Assets 监控最佳实践 {#assets-monitoring-best-practices}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

从Adobe Experience Manager资产的角度来看，监测应包括观察和报告以下流程和技术：

* 系统CPU
* 系统内存使用
* 系统磁盘IO和IO等待时间
* 系统网络IO
* JMX MBean用于：

   * 堆利用率
   * 异步流程，如工作流

* OSGi控制台运行状况检查

通常， [!DNL Assets] 可以通过两种方式进行监控，即实时监控和长期监控。

## 实时监控 {#live-monitoring}

您应在开发的性能测试阶段或高负载情况下执行实时监控，以了解环境的性能特性。 通常，应使用一套工具执行实时监视。 以下是一些建议：

* [可视化虚拟机](https://visualvm.github.io/):Visual VM允许您查看详细的Java VM信息，包括CPU使用率、Java内存使用率。 此外，它还允许您对在实例上运行的代码进行采样和评估。
* [顶部](https://man7.org/linux/man-pages/man1/top.1.html):顶部是一个Linux命令，用于打开一个功能板，其中显示使用情况统计信息，包括CPU、内存和IO使用情况。 它提供了实例中所发生情况的高级概述。
* [Htop](https://hisham.hm/htop/):Htop是一个交互式进程查看器。 除了Top提供的功能外，它还提供详细的CPU和内存使用情况。 Htop可安装在大多数Linux系统上， `yum install htop` 或 `apt-get install htop`.

* [伊托普](https://guichaz.free.fr/iotop/):Iotop是有关磁盘IO使用情况的详细功能板。 它显示一些条形和米表，这些条形和米表描述了使用磁盘IO的流程及其使用量。 Iotop可安装在大多数Linux系统上， `yum install iotop` 或 `apt-get install iotop`.

* [Iftop](https://www.ex-parrot.com/pdw/iftop/):Iftop显示有关以太网/网络使用的详细信息。 Iftop显示使用以太网的实体的每个通信通道统计信息以及它们使用的带宽量。 Iftop可安装在大多数Linux系统上， `yum install iftop` 或 `apt-get install iftop`.

* Java飞行记录器(JFR):oracle中的商业工具，您可以在非生产环境中自由使用。 有关更多详细信息，请参阅 [如何使用Java飞行记录器诊断CQ运行时问题](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* [!DNL Experience Manager] error.log文件：你可以调查 [!DNL Experience Manager] error.log文件，以了解系统中记录的错误的详细信息。 使用命令 `tail -F quickstart/logs/error.log` 以识别您应该调查的错误。
* [工作流控制台](../sites-administering/workflows.md):利用工作流控制台监控滞后或卡住的工作流。

通常，您会结合使用这些工具来全面了解您的 [!DNL Experience Manager] 实例。

>[!NOTE]
>
>这些工具是标准工具，不直接受Adobe支持。 它们不需要额外的许可证。

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## 长期监测 {#long-term-monitoring}

对 [!DNL Experience Manager] 实例涉及对实时监控的相同部分进行较长时间的监控。 它还包括定义特定于您的环境的警报。

### 日志聚合和报告 {#log-aggregation-and-reporting}

有几种可用于聚合日志的工具，例如Splunk(TM)和Elastic Search/Logstash/Kabana(ELK)。 评估您的 [!DNL Experience Manager] 例如，了解特定于您系统的日志事件并根据这些事件创建警报，这一点非常重要。 了解您的开发和操作实践有助于您更好地了解如何调整日志聚合过程以生成关键警报。

### 环境监控 {#environment-monitoring}

环境监控包括监控以下内容：

* 网络吞吐量
* 磁盘IO
* 内存
* CPU利用率
* JMX MBeans
* 外部网站

您需要外部工具(如NewRelic(TM)和AppDynamics(TM))来监控每个项目。 使用这些工具，您可以定义特定于您系统的警报，例如系统利用率高、工作流备份、运行状况检查失败或未经身份验证的网站访问。 Adobe不推荐任何特定工具而不是其他工具。 找到适合您的工具，并利用它监控所讨论的项目。

#### 内部应用程序监控 {#internal-application-monitoring}

内部应用程序监控包括监控构成 [!DNL Experience Manager] 堆栈，包括JVM、内容存储库，以及通过在平台上构建的自定义应用程序代码进行监控。 通常，它通过JMX Mbeans执行，而JMX Mbeans可以由许多常用的监控解决方案(如SolarWinds(TM)、 HP OpenView(TM)、Hyperic(TM)、Zabbix(TM)等)直接监控。 对于不支持直接连接到JMX的系统，您可以编写shell脚本以提取JMX数据，并以它们本身理解的格式将其公开给这些系统。

默认情况下，不启用对JMX Mbean的远程访问。 有关通过JMX进行监控的更多信息，请参阅 [使用JMX技术进行监控和管理](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

在许多情况下，需要基线才能有效地监控统计数据。 要创建基线，请在预定时间段内在正常工作条件下观察系统，然后识别正常量度。

**JVM监控**

与任何基于Java的应用程序堆栈一样， [!DNL Experience Manager] 取决于通过基础Java虚拟机提供给它的资源。 您可以通过JVM公开的Platform MXBean来监控其中许多资源的状态。 有关MXBean的更多信息，请参阅 [使用Platform MBean服务器和Platform MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

以下是一些可监控JVM的基线参数：

内存

* `MBean: lava.lang:type=Memory`
* URL: */system/console/jmx/java.lang:type=Memory*
* 实例：所有服务器
* 警报阈值：当堆或非堆内存利用率超过相应最大内存的75%时。
* 警报定义：系统内存不足，或代码中出现内存泄漏。 分析线程转储以得到定义。

**注意**:此Bean提供的信息以字节表示。

线程

* MBean: `java.lang:type=Threading`
* URL: */system/console/jmx/java.lang:type=Threading*
* 实例：所有服务器
* 警报阈值：当线程数大于基线的150%时。
* 警报定义：要么存在一个活跃的失控过程，要么低效操作消耗了大量资源。 分析线程转储以得到定义。

**[!DNL Experience Manager]监测**

[!DNL Experience Manager] 还通过JMX公开一组统计和操作。 这些功能有助于评估系统运行状况，并在潜在问题影响用户之前发现它们。 有关更多信息，请参阅 [文档](/help/sites-administering/jmx-console.md) on [!DNL Experience Manager] JMX MBean。

以下是一些可监视的基线参数 [!DNL Experience Manager]:

复制代理

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: */system/console/jmx/com.adobe.granite.replication:type=agent，id=&quot;&lt;agent_name>&quot;*
* 实例：一个创作实例和所有发布实例（用于刷新代理）
* 警报阈值：当 `QueueBlocked` 为true或的值 `QueueNumEntries` 大于基线的150%。

* 警报定义：系统中存在阻止的队列，表示复制目标已关闭或不可访问。 通常，网络或基础架构问题会导致过多条目排入队列，从而对系统性能产生不利影响。

**注意**:对于MBean和URL参数，请替换 `<AGENT_NAME>` 以及要监视的复制代理的名称。

会话计数器

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository统计信息&quot;,type*=&quot;RepositoryStats&quot;
* 实例：所有服务器
* 警报阈值：打开的会话数超过基线50%时。
* 警报定义：会话可通过一段代码打开，且永不关闭。 这可能会随着时间推移缓慢发生，并最终导致系统内存泄漏。 虽然系统上的会话数应有所波动，但不应持续增加。

运行状况检查

运行状况检查 [操作仪表板](/help/sites-administering/operations-dashboard.md#health-reports) 具有相应的JMX MBean进行监控。 但是，您可以编写自定义运行状况检查以显示其他系统统计信息。

以下是一些开箱即用的运行状况检查，这些检查有助于进行监控：

* 系统检查

   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=systemchecks，type=HealthCheck*
   * 实例：一个作者，所有发布服务器
   * 警报阈值：状态不正常时
   * 警报定义：其中一个量度的状态为“警告”或“关键”。 有关问题原因的更多信息，请查看日志属性。

* 复制队列

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue，type=HealthCheck*
   * 实例：一个作者，所有发布服务器
   * 警报阈值：状态不正常时
   * 警报定义：其中一个量度的状态为“警告”或“关键”。 有关导致此问题的队列的详细信息，请查看日志属性。

* 响应性能

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus，type=HealthCheck*
   * 实例：所有服务器
   * 警报持续时间：状态不正常时
   * 警报定义：其中一个量度的状态为“警告”或“关键”。 有关导致此问题的队列的详细信息，请查看日志属性。

* 查询性能

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus，type=HealthCheck*
   * 实例：一个作者，所有发布服务器
   * 警报阈值：状态不正常时
   * 警报定义：一个或多个查询在系统中运行缓慢。 有关导致此问题的查询的详细信息，请查看日志属性。

* 活动包

   * MBean:org.apache.sling.healthcheck:name=inactiveBundles，type=HealthCheck
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles，type=HealthCheck*
   * 实例：所有服务器
   * 警报阈值：状态不正常时
   * 警报定义：系统上存在不活动或未解析的OSGi包。 有关导致此问题的包的详细信息，请查看日志属性。

* 日志错误

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: */system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck，type=HealthCheck*
   * 实例：所有服务器
   * 警报阈值：状态不正常时
   * 警报定义：日志文件中存在错误。 有关问题原因的更多信息，请查看日志属性。

## 常见问题和解决方案  {#common-issues-and-resolutions}

在监控过程中，如果您遇到问题，您可以执行以下一些故障诊断任务来解决 [!DNL Experience Manager] 实例：

* 如果使用TarMK，请经常运行焦油压缩。 有关更多详细信息，请参阅 [维护存储库](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* 检查 `OutOfMemoryError` 日志。 有关更多信息，请参阅 [分析内存问题](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html).
* 检查日志中是否有对未索引查询、树遍历或索引遍历的任何引用。 这表示未编入索引的查询或索引不足的查询。 有关优化查询和索引性能的最佳实践，请参阅 [有关查询和索引的最佳实践](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* 使用工作流控制台验证工作流是否按预期执行。 如有可能，将多个工作流精简为单个工作流。
* 重新访问实时监控，并寻找任何特定资源的其他瓶颈或高消费者。
* 调查来自客户端网络的出口点和指向 [!DNL Experience Manager] 实例网络，包括调度程序。 这些往往是瓶颈领域。 有关更多信息，请参阅 [资产网络注意事项](assets-network-considerations.md).
* 调整您的 [!DNL Experience Manager] 服务器。 您的 [!DNL Experience Manager] 实例。 Adobe客户支持可以帮助您确定您的服务器是否太小。
* 检查 `access.log` 和 `error.log` 出现问题时，条目的文件会出错。 查找可能指示自定义代码异常的模式。 将它们添加到您监视的事件列表。
