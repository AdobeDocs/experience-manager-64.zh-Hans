---
title: Assets 卸载最佳实践
description: 在AEM Assets中卸载资产摄取和复制工作流的推荐使用案例和最佳做法。
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1823'
ht-degree: 0%

---


# Assets 卸载最佳实践 {#assets-offloading-best-practices}

>[!WARNING]
>
>此功能从AEM 6.4开始已弃用，在AEM 6.5中已删除。请相应地进行计划。

在Adobe Experience Manager(AEM)资产中处理大文件和运行工作流会占用大量CPU、内存和I/O资源。 特别是，资产的大小、工作流、用户数和资产摄取频率会影响系统的整体性能。 资源密集型操作包括AEM资产摄取和复制工作流。 在单个AEM创作实例上大量使用这些工作流可能会对创作效率产生负面影响。

将这些任务卸载到专用工作实例可以降低CPU、内存和IO开销。 通常，卸载的想法是将消耗大量CPU/内存/IO资源的任务分发到专用工作实例。 以下部分包括资产卸载的推荐使用案例。

## AEM Assets卸载{#aem-assets-offloading}

AEM Assets实现了用于卸载的特定于本机资源的工作流扩展。 它构建于卸载框架提供的通用工作流扩展之上，但在实施中包含其他特定于资产的功能。 资产卸载的目标是对上传的资产高效运行DAM更新资产工作流。 资产卸载使您能够更好地控制摄取工作流。

## AEM Assets卸载组件{#aem-assets-offloading-components}

下图描述了资产卸载流程中的主要组件：

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM更新资产卸载工作流{#dam-update-asset-offloading-workflow}

DAM更新资产卸载工作流在用户上传资产时运行在主（作者）服务器上。 此工作流由常规工作流启动器触发。 此卸载工作流不会处理已上传的资产，而是使用主题&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;创建新作业。 卸载工作流会添加目标工作流的名称 — 在这种情况下为DAM更新资产工作流，以及资产到作业有效负荷的路径。 创建卸载作业后，主实例上的卸载工作流将等待卸载作业运行。

### 作业管理器{#job-manager}

作业管理器将新作业分发到工作器实例。 在设计分发机制时，必须考虑主题支持。 作业只能分配给启用了作业主题的实例。 禁用主卷上的主题`com/adobe/granite/workflow/offloading`，并在worker上启用它以确保将作业分配给该worker。

### AEM卸载{#aem-offloading}

卸载框架标识分配给worker实例的工作流卸载作业，并使用复制将它们实际传输到worker，包括它们的有效负荷（例如，要摄取的图像）。

### 工作流卸载作业使用者{#workflow-offloading-job-consumer}

在worker上写入作业后，作业管理器将调用负责&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;主题的作业使用者。 然后，作业使用者会对资产运行DAM更新资产工作流。

## Sling拓扑{#sling-topology}

Sling拓扑将AEM实例分组，使它们能够相互感知，而不受基础持久性的影响。 Sling拓扑的这一特性使您能够为非群集、群集和混合场景创建拓扑。 实例可向整个拓扑公开属性。 框架提供用于侦听拓扑（实例和属性）中的更改的回调。 Sling拓扑为Sling分布式作业提供了基础。

### Sling分布式作业{#sling-distributed-jobs}

Sling分布式作业有助于在作为拓扑成员的一组实例中分配作业。 Sling作业基于能力的理念。 作业由其作业主题定义。 要运行作业，实例必须为特定作业主题提供作业使用者。 作业主题是分配机制的主要驱动因素。

作业仅分配给为主题提供作业使用者的实例。 通过在实例上启用/禁用作业使用者，您可以定义实例的功能并影响分发机制。 实例的可用作业使用者将广播到整个拓扑。

在此上下文中，术语分配表示将作业分配给提供作业使用者的特定实例。 对实例的赋值存储在存储库中。 换句话说，默认情况下，Sling分布式作业可分配给拓扑中的任何实例。 但是，其他作业只能由共享同一存储库的实例运行。 这意味着这些作业只能由属于同一群集的实例运行。 不运行分配给其他群集实例的作业。

### 花岗岩卸载框架{#granite-offloading-framework}

Granite卸载框架补充了Sling作业分发，以运行分配给非群集实例的作业。 它不执行任何分发（实例分配）。 但是，它会标识分发到非群集实例的Sling作业，并将它们传输到目标实例以执行。 当前，卸载使用复制来执行此作业传输。 要运行作业，卸载定义输入和输出，然后将其与作业组合以生成作业负载。

Sling分布式作业提供作业和分发框架。 Granite卸载只负责将作业分配给非群集实例的特殊情况的传输。

除传输外，卸载框架还为工作流引擎提供扩展。 它允许框架创建作为工作流一部分的分布式作业，并等待其完成，然后工作流继续前进。 它是使用工作流引擎中的工作流外部步骤API实现的。 其中一个扩展促进工作流的通用分发。 不支持分发单个工作流步骤。

卸载框架还附带用户界面(UI)，可直观地显示和控制整个拓扑中启用的作业主题。 通过UI，您可以方便地配置Sling分布式作业的主题启用。 您还可以设置不使用UI的卸载。

## 资产卸载的一般指南和最佳实践{#general-guidance-and-best-practices-for-asset-offloading}

每个实施都是独一无二的，因此不存在一刀切的卸载配置。 以下部分提供了有关资产摄取卸载的指导和最佳实践。

资产卸货还会对系统施加间接费用，包括工序间接费用。 如果您在资产摄取加载时遇到问题，Adobe建议您首先改进配置，而不要卸载。 在移至资产卸载之前，请考虑以下选项：

* 扩展硬件
* 优化工作流
* 使用临时工作流
* 限制用于工作流的核数

如果您认为资产卸载是适合您的方法，Adobe将提供以下指导：

* 建议部署基于TarMK
* 基于TarMK的资产卸载不适合广泛的水平缩放
* 确保作者与工作人员之间的网络性能令人满意

### 建议的资源卸载部署{#recommended-assets-offloading-deployment}

通过AEM和Oak，可能存在多种部署方案。 对于资产卸载，建议使用共享数据存储进行基于TarMK的部署。 下图概述了建议的部署：

![chlimage_1-56](assets/chlimage_1-56.png)

有关配置数据存储的详细信息，请参阅[在AEM](../sites-deploying/data-store-config.md)中配置节点存储和数据存储。

### 关闭自动代理管理{#turning-off-automatic-agent-management}

Adobe建议您关闭自动代理管理，因为它不支持无二进制复制，并且在设置新的卸载拓扑时可能会造成混淆。 此外，它并不自动支持无二进制复制所需的正向复制流。

1. 从URL `http://localhost:4502/system/console/configMgr`打开Configuration Manager。
1. 打开`OffloadingAgentManager`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)的配置。
1. 禁用自动代理管理。

### 使用前向复制{#using-forward-replication}

默认情况下，卸载传输使用反向复制将卸载的资产从worker拉回到主。 反向复制代理不支持无二进制复制。 您应将卸载配置为使用转发复制将卸载的资产从worker推回到主。

1. 如果您使用反向复制从默认配置迁移，请禁用或删除主和worker上名为“ `offloading_outbox`”和“ `offloading_reverse_*`”的所有代理，其中&amp;ast;表示目标实例的Sling ID。
1. 在每个worker上，创建指向主的新转发复制代理。 该过程与从主代理到工作代理创建转发代理相同。 有关设置卸载复制代理的说明，请参见[创建用于卸载的复制代理](../sites-deploying/offloading.md#creating-replication-agents-for-offloading)。
1. 打开`OffloadingDefaultTransporter`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)的配置。
1. 将属性`default.transport.agent-to-master.prefix`的值从`offloading_reverse`更改为`offloading`。

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### 在作者和Worker之间使用共享数据存储和无二进制复制{#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

建议使用无二进制复制来减少资源卸载的传输开销。 要了解如何为共享数据存储设置无二进制复制，请参阅AEM](/help/sites-deploying/data-store-config.md)中的[配置节点存储和数据存储。 对于资产卸载，此过程并不不同，只是涉及其他复制代理。 由于无二进制复制只能与转发复制代理一起使用，因此您还应对所有卸载代理使用转发复制。

### 关闭传输包{#turning-off-transport-packages}

默认情况下，卸载会创建一个包含卸载作业和作业负载（原始资产）的内容包，并使用单个复制请求传输此单个卸载包。 使用无二进制复制时，创建这些卸载包会产生反作用，因为在创建包时，二进制文件将再次序列化到包中。 可以关闭这些传输包的使用，这导致卸载作业和负载在多个复制请求中被传输，每个负载输入一个。 这样，可以利用无二进制复制的好处。

1. 在[http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)打开&#x200B;*OffloadingDefaultTransporter*&#x200B;组件的组件配置
1. 禁用属性&#x200B;*复制包(default.transport.contentpackage)*。

### 禁用工作流模型{#disabling-the-transport-of-workflow-model}的传输

默认情况下，*DAM更新资产卸载*&#x200B;卸载工作流会将要对worker调用的工作流模型添加到作业负载。 由于此工作流默认遵循现成&#x200B;*DAM更新资产*&#x200B;模型，因此可以删除此附加负载。

如果从作业有效负荷中禁用了工作流模型，请确保使用其他工具（如包管理器）将更改分发到引用的工作流模型。

要禁用工作流模型的传输，请修改DAM更新资产卸载工作流。

1. 从[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)打开工作流控制台。
1. 打开“模型”(Models)选项卡。
1. 打开DAM更新资产卸载工作流模型。
1. 打开DAM工作流卸载步骤的步骤属性。
1. 打开“参数”选项卡，取消选择“将模型添加到输入”和“将模型添加到输出”选项。
1. 保存对模型的更改。

### 优化轮询间隔{#optimizing-the-polling-interval}

工作流卸载是使用主工作流上的外部工作流实现的，该工作流轮询工作流上已卸载的工作流是否完成。 外部工作流进程的默认轮询间隔为五秒。 Adobe建议您将资产卸载步骤的轮询间隔至少增加到15秒，以减少主资产卸载的开销。

1. 从[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)打开工作流控制台。

1. 打开“模型”(Models)选项卡。
1. 打开DAM更新资产卸载工作流模型。
1. 打开DAM工作流卸载步骤的步骤属性。
1. 打开“共享资源”选项卡，并调整Period属性的值。
1. 保存对模型的更改。

## 更多资源{#more-resources}

此文档重点介绍资产卸载。 以下是有关卸载的其他文档：

* [卸载作业](/help/sites-deploying/offloading.md)
* [资产工作流卸载程序](/help/sites-administering/workflow-offloader.md)

