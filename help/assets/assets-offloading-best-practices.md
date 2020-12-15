---
title: 资产卸载最佳实践
description: 在AEM Assets为卸载资产摄取和复制工作流推荐的使用案例和最佳实践。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# 资产卸载最佳实践{#assets-offloading-best-practices}

>[!WARNING]
>
>从AEM 6.4开始，此功能已弃用，并在AEM 6.5中删除。相应的计划。

在Adobe Experience Manager(AEM)资产中处理大文件和运行工作流会占用大量CPU、内存和I/O资源。 特别是，资产的大小、工作流、用户数和资产摄取频率都会影响系统的整体性能。 资源密集型操作包括AEM资产摄取和复制工作流。 在单个AEM创作实例上大量使用这些工作流会对创作效率产生不利影响。

将这些任务卸载到专用工作器实例可以降低CPU、内存和IO开销。 通常，卸载的想法是将消耗大量CPU/内存/IO资源的任务分发到专用工作器实例。 以下部分包括资产卸载的推荐使用案例。

## AEM Assets卸载{#aem-assets-offloading}

AEM Assets实施了本机特定于资源的工作流扩展，用于卸载。 它构建于卸载框架提供的通用工作流扩展之上，但在实施中包含其他特定于资产的功能。 资产卸载的目标是对上传的资产高效运行DAM更新资产工作流。 资产卸载使您能够更好地控制摄取工作流。

## AEM Assets卸载组件{#aem-assets-offloading-components}

下图描述了资产卸载流程中的主要组件：

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM更新资产卸载工作流{#dam-update-asset-offloading-workflow}

DAM更新资产卸载工作流在用户上传资产的主（作者）服务器上运行。 此工作流由常规工作流启动器触发。 此卸载工作流不会处理已上传的资产，而是使用主题&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;创建新作业。 卸载工作流会添加目标工作流的名称（本例中为DAM更新资产工作流），以及资产路径到作业有效负荷。 在创建卸载作业后，主实例上的卸载工作流会等到卸载作业运行。

### 作业管理器{#job-manager}

作业管理器将新作业分发到工作器实例。 在设计分发机制时，必须考虑主题启用。 作业只能分配给启用作业主题的实例。 禁用主卷上的主题`com/adobe/granite/workflow/offloading`，并在工作器上启用它，以确保将作业分配给该工作器。

### AEM卸载{#aem-offloading}

卸载框架标识分配给工作实例的工作流卸载作业，并使用复制将它们实际传输到工作器，包括它们的有效负荷（例如，要摄取的图像）。

### 工作流卸载作业使用者{#workflow-offloading-job-consumer}

在工作者上写入作业后，作业管理者将调用负责&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;主题的作业使用者。 然后，作业使用者会对资产运行DAM更新资产工作流。

## Sling拓扑{#sling-topology}

Sling拓扑将AEM实例分组，使它们能够相互感知，与底层持久性无关。 Sling拓扑的这一特性允许您为非集群、群集和混合场景创建拓扑。 实例可向整个拓扑公开属性。 框架提供回调，用于侦听拓扑（实例和属性）中的更改。 Sling拓扑为Sling分布式作业提供了基础。

### Sling分布式作业{#sling-distributed-jobs}

Sling分布式作业有助于在作为拓扑成员的一组实例中分配作业。 Sling作业基于能力的理念。 职务由职务主题定义。 要运行作业，实例必须为特定作业主题提供作业使用者。 作业主题是分配机制的主要驱动因素。

作业仅分配给为主题提供作业使用者的实例。 通过在实例上启用／禁用作业使用者，您可以定义实例的功能并影响分发机制。 实例的可用作业使用者被广播到整个拓扑。

在此上下文中，术语分配表示将作业分配给提供作业使用者的特定实例。 对实例的分配存储在存储库中。 换言之，默认情况下，Sling分布式作业可分配给拓扑中的任何实例。 但是，其他作业只能由共享同一存储库的实例运行。 这意味着这些作业只能由属于同一群集的实例运行。 不运行分配给其他群集实例的作业。

### 花岗岩卸载框架{#granite-offloading-framework}

Granite卸载框架补充了Sling作业分配，以运行分配给非集群实例的作业。 它不执行任何分发（实例分配）。 但是，它会标识分发到非集群实例的Sling作业，并将它们传输到目标实例以执行。 目前，卸载使用复制来执行此作业传输。 要运行作业，卸载定义输入和输出，然后将其与作业组合以生成作业有效负荷。

Sling分布式作业提供作业和分发框架。 Granite卸载只负责将作业分配到非群集实例的特殊情况的传输。

除了传输，卸载框架还为工作流引擎提供扩展。 它允许框架创建作为工作流一部分的分布式作业，并等待其完成，然后再进行工作流。 它是使用工作流引擎中的工作流外部步骤API实现的。 其中一个扩展促进工作流的通用分发。 不支持分发单个工作流步骤。

卸载框架还附带用户界面(UI)，可在整个拓扑中可视化和控制启用的作业主题。 通过UI，您可以方便地配置Sling分布式作业的主题启用。 您还可以设置卸载而不使用UI。

## 资产卸载的一般指南和最佳实践{#general-guidance-and-best-practices-for-asset-offloading}

每个实施都是独一无二的，因此不存在一刀切的卸载配置。 以下部分提供有关资产摄取卸载的指导和最佳实践。

资产卸载还会对系统施加间接费用，包括工序间接费用。 如果您在资产摄取加载时遇到问题，Adobe建议您首先改进配置，而不要卸载。 在移至资产卸载之前，请考虑以下选项：

* 扩展硬件
* 优化工作流
* 使用临时工作流
* 限制用于工作流的核数

如果您认为资产卸载是适合您的方法，Adobe将提供以下指导：

* 建议部署基于TarMK
* 基于TarMK的资产卸载并非设计用于广泛的水平缩放
* 确保作者与工作人员之间的网络性能令人满意

### 建议的资源卸载部署{#recommended-assets-offloading-deployment}

在AEM和Oak中，可能有多种部署方案。 对于资产卸载，建议使用共享数据存储进行基于TarMK的部署。 下图概述了建议的部署：

![chlimage_1-56](assets/chlimage_1-56.png)

有关配置数据存储区的详细信息，请参阅[配置AEM](../sites-deploying/data-store-config.md)中的节点存储和数据存储。

### 关闭自动代理管理{#turning-off-automatic-agent-management}

Adobe建议您关闭自动代理管理，因为它不支持无二进制复制，并且在设置新的卸载拓扑时可能会造成混淆。 此外，它不自动支持无二进制复制所需的正向复制流。

1. 从URL `http://localhost:4502/system/console/configMgr`打开Configuration Manager。
1. 打开`OffloadingAgentManager`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)的配置。
1. 禁用自动代理管理。

### 使用正向复制{#using-forward-replication}

默认情况下，卸载传输使用反向复制将卸载的资产从工作器拉回到主服务器。 反向复制代理不支持无二进制复制。 您应将卸载配置为使用正向复制将卸载的资产从worker推回主资产。

1. 如果使用反向复制从默认配置迁移，请禁用或删除主和工作器上名为“ `offloading_outbox`”和“ `offloading_reverse_*`”的所有代理，其中&amp;ast;表示目标实例的Sling ID。
1. 在每个Worker上，创建指向主Adobe的新转发复制代理。 该过程与从主代理到工作者创建转发代理相同。 有关设置卸载复制代理的说明，请参见[创建用于卸载的复制代理](../sites-deploying/offloading.md#creating-replication-agents-for-offloading)。
1. 打开`OffloadingDefaultTransporter`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)的配置。
1. 将属性`default.transport.agent-to-master.prefix`的值从`offloading_reverse`更改为`offloading`。

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### 在作者和工作者之间使用共享数据存储和无二进制复制{#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

建议使用无二进制复制来减少资产卸载的传输开销。 要了解如何为共享数据存储设置无二进制复制，请参阅[在AEM](/help/sites-deploying/data-store-config.md)中配置节点存储和数据存储。 对于资产卸载，此过程并不不同，只是涉及其他复制代理。 由于无二进制复制只适用于正向复制代理，因此您还应对所有卸载代理使用正向复制。

### 关闭传输包{#turning-off-transport-packages}

默认情况下，卸载会创建包含卸载作业和作业有效负荷（原始资产）的内容包，并使用单个复制请求传输此单个卸载包。 使用无二进制复制时，创建这些卸载包会产生反作用，因为在创建包时，二进制文件将再次序列化到包中。 可以关闭这些传输包的使用，这会导致卸载作业和负载在多个复制请求中被传输，每个负载条目一个。 这样，可以利用无二进制复制的好处。

1. 在[http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)打开&#x200B;*OffloadingDefaultTransporter*&#x200B;组件的组件配置
1. 禁用属性&#x200B;*复制包(default.transport.contentpackage)*。

### 禁用工作流模型{#disabling-the-transport-of-workflow-model}的传输

默认情况下，*DAM更新资产卸载*&#x200B;卸载工作流会添加工作流模型，以调用该工作流到作业有效负荷。 由于此工作流默认遵循现成的&#x200B;*DAM更新资产*&#x200B;模型，因此可以删除此附加负载。

如果从作业有效负荷中禁用了工作流模型，请确保使用其他工具（如包管理器）将更改分发到引用的工作流模型。

要禁用工作流模型的传输，请修改DAM更新资产卸载工作流。

1. 从[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)打开工作流控制台。
1. 打开“模型”(Models)选项卡。
1. 打开DAM更新资产卸载工作流模型。
1. 打开DAM工作流卸载步骤的步骤属性。
1. 打开“参数”选项卡，取消选择“将模型添加到输入”和“将模型添加到输出”选项。
1. 保存对模型的更改。

### 优化轮询间隔{#optimizing-the-polling-interval}

工作流卸载是使用主工作流上的外部工作流实现的，该工作流轮询工作器上卸载的工作流是否完成。 外部工作流进程的默认轮询间隔为五秒。 Adobe建议您将资产卸载步骤的轮询间隔增加到至少15秒，以减少主资产卸载的开销。

1. 从[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)打开工作流控制台。

1. 打开“模型”(Models)选项卡。
1. 打开DAM更新资产卸载工作流模型。
1. 打开DAM工作流卸载步骤的步骤属性。
1. 打开“共享资源”选项卡，并调整“期间”属性的值。
1. 保存对模型的更改。

## 更多资源{#more-resources}

此文档重点介绍资产卸载。 以下是有关卸载的其他文档：

* [卸载作业](/help/sites-deploying/offloading.md)
* [资产工作流卸载程序](/help/sites-administering/workflow-offloader.md)

