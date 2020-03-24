---
title: 将资产批量迁移到Adobe Experience Manager资产
description: 如何将资产引入AEM、应用元数据、生成演绎版并激活资产以发布实例。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 976d037d701eb7cc61a62e14e554675961d6179c

---


# 资产迁移指南 {#assets-migration-guide}

将资产迁移到AEM时，需要考虑几个步骤。 从其当前主页提取资产和元数据不在本文档的范围内，因为实施之间的差异很大。 本文档介绍如何将这些资产引入AEM、应用其元数据、生成演绎版以及激活或发布资产。

## 前提条件 {#prerequisites}

在执行下述任何步骤之前，请查看并实施资产性能调整提 [示中的指导](performance-tuning-guidelines.md)。 许多步骤（如配置最大并发作业）都增强了服务器在负载下的稳定性和性能。 在系统加载了资产后，执行其他步骤（如文件数据存储配置）很困难。

>[!NOTE]
>
>以下资产迁移工具不是Adobe Experience Manager的一部分。 Adobe客户关怀团队不支持这些工具。
>
>* ACS AEM Tools Tag Maker
>* ACS AEM工具CSV资产导入程序
>* ACS Commons Bulk Workflow Manager
>* ACS Commons Fast Action Manager
>* 合成工作流
>
>
本软件是开放源软件，受 [Apache v2 许可证](https://adobe-consulting-services.github.io/pages/license.html)的保护。要提出问题或报告问题，请访问[针对 ACS AEM 工具的 GitHub 问题](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues)和 [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues)。

## 迁移到AEM {#migrate-to-aem}

将资产迁移到AEM需要多个步骤，并应将其视为一个分阶段的过程。 迁移的阶段如下：

1. 禁用工作流。
1. 加载标记。
1. 摄取资源。
1. 处理再现。
1. 激活资产。
1. 启用工作流。

![chlimage_1-223](assets/chlimage_1-223.png)

### 禁用工作流 {#disable-workflows}

在开始迁移之前，请禁用工作流的启动 `DAM Update Asset` 器。 最好将所有资产引入系统，然后批量运行工作流。 如果迁移发生时您已经处于活动状态，则可以安排这些活动在非工作时间执行。

### 加载标记 {#load-tags}

您可能已经拥有了要应用于图像的标记分类。 CSV资产导入程序和元数据配置文件功能等工具可以帮助您将标记自动应用到资产。 在此之前，请在Experience Manager中添加标记。 通过 [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) （ACS AEM工具标记生成器）功能，您可以使用加载到系统中的Microsoft Excel电子表格填充标记。

### 摄取资源 {#ingest-assets}

将资产引入系统时，性能和稳定性是重要的问题。 在Experience Manager中加载大量数据时，请确保系统运行良好。 这样可最大程度地缩短添加数据所需的时间，并有助于避免系统过载。 这有助于防止系统崩溃，特别是在已在生产的系统中。

将资产加载到系统中有两种方法：使用HTTP的基于推送的方法，或使用JCR API的基于拉式的方法。

#### 通过HTTP推送 {#push-through-http}

Adobe的Managed Services团队使用一种称为Glutton的工具将数据加载到客户环境中。 Glutton是一个小的Java应用程序，它将所有资源从一个目录加载到AEM实例上的另一个目录中。 您还可以使用Perl脚本等工具将资源发布到存储库中，而不是Glutton。

使用通过https的方法有两个主要的缺点：

1. 通过HTTP将资源传输到服务器。 这需要相当多的开销，并且耗时，从而延长执行迁移所需的时间。
1. 如果您有必须应用于资产的标记和自定义元数据，则此方法需要再运行一个自定义流程，以便在导入资产后将此元数据应用于资产。

获取资源的另一种方法是从本地文件系统中提取资源。 但是，如果无法将外部驱动器或网络共享装载到服务器以执行基于拉式的方法，则通过HTTP发布资产是最佳选项。

#### 从本地文件系统中提取 {#pull-from-the-local-file-system}

[](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) ACS AEM工具CSV资产导入程序从文件系统中提取资产，并从CSV文件中提取资产元数据以进行资产导入。 AEM Asset Manager API用于将资产导入系统并应用配置的元数据属性。 理想情况下，资产通过网络文件安装或通过外部驱动器安装在服务器上。

当资产不通过网络传输时，总体性能会大大提高。 此方法通常是将资产加载到存储库中的最有效方法。 此外，由于该工具支持元数据摄取，因此您可以通过一个步骤导入所有资产和元数据。 无需执行任何其他步骤即可应用元数据，例如使用单独的工具。

### 处理再现 {#process-renditions}

在将资产加载到系统中后，您需要通过DAM更新资产工作流处理这些资产，以提取元数据并生成演绎版。 在执行此步骤之前，您需要复制和修改DAM更新资产工作流以满足您的需求。 默认工作流程中的某些步骤可能不是您必需的，例如Scene7 PTIFF生成或InDesign服务器集成。

根据需要配置工作流后，您有两个选项可执行该工作流：

1. 最简单的方法是 [ACS Commons的Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)。 此工具允许您执行查询并通过工作流处理查询结果。 还有用于设置批大小的选项。
1. 您可以将 [ACS Commons Fast Action Manager与Synthetic Workflows一起使](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) 用 [](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)。 虽然此方法涉及的范围更广，但它允许您在优化服务器资源的使用时删除AEM工作流引擎的开销。 此外，Fast Action manager还通过动态监视服务器资源和限制系统上的负载来进一步提升性能。 ACS Commons功能页上提供了示例脚本。

### 激活资产 {#activate-assets}

对于具有发布层的部署，您需要将资产激活到发布场。 虽然Adobe建议运行多个发布实例，但最好将所有资源复制到单个发布实例，然后克隆该实例。 在激活大量资产时，在触发树激活后，您可能需要进行干预。 原因如下：在触发激活时，项目会添加到Sling作业／事件队列。 当此队列的大小开始超过约40,000个项目后，处理速度会显着降低。 当此队列的大小超过100,000项后，系统稳定性开始受到影响。

要解决此问题，您可以使用 [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) （快速操作管理器）管理资产复制。 这可以在不使用Sling队列的情况下工作，从而降低开销，同时限制工作负载以防止服务器过载。 使用FAM管理复制的示例显示在该功能的文档页上。

将资产转至发布场的其他选项包括使用 [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) 或 [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)，这些选项作为 Jackrabbit 中的工具提供。另一个选项的目的是对 AEM 基础结构使用一个名为 [Grabbit](https://github.com/TWCable/grabbit) 的开放源工具，该工具声称比 vlt 的性能更快。

对于任何这些方法，注意作者实例上的资产不显示为已激活。 要使用正确的激活状态标记这些资产，您还需要运行一个脚本以将资产标记为已激活。

>[!NOTE]
>
>Adobe不维护或支持Grabbit。

### 克隆发布 {#clone-publish}

在激活资产后，您可以克隆发布实例以创建部署所需数量的副本。 克隆服务器相当简单，但需要记住一些重要步骤。 要克隆发布，请执行以下操作：

1. 备份源实例和数据存储。
1. 将实例和数据存储的备份恢复到目标位置。 以下步骤均引用此新实例。
1. 在for下执行文件系统 `crx-quickstart/launchpad/felix` 搜索 `sling.id`。 删除此文件。
1. 在数据存储的根路径下，找到并删除任何文 `repository-XXX` 件。
1. 编 `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` 辑并 `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` 指向新环境中数据存储的位置。
1. 启动环境。
1. 更新作者上任何复制代理的配置，以指向新实例上的正确发布实例或调度程序刷新代理，以指向新环境的正确调度程序。

### 启用工作流 {#enable-workflows}

完成迁移后，应重新启用DAM更新资产工作流的启动程序，以支持再现生成和元数据提取，以便持续使用日常系统。

## 跨AEM部署迁移资产 {#migrate-between-aem-instances}

虽然不像以前那样常见，但有时您需要将大量数据从一个AEM实例迁移到另一个实例；例如，当您执行AEM升级、升级硬件或迁移到新数据中心时，例如AMS迁移。

在这种情况下，您的资产已填充元数据，并且已生成演绎版。 您只需将精力集中在将资产从一个实例移动到另一个实例上。 在AEM实例之间迁移时，您需要执行以下步骤：

1. 禁用工作流：由于您正在迁移演绎版以及我们的资产，因此您希望禁用DAM更新资产的工作流启动器。

1. 迁移标记：由于已在源AEM实例中加载了标记，因此您可以在内容包中构建这些标记并将该包安装到目标实例上。

1. 迁移资产：建议使用两种工具将资产从一个AEM实例移至另一个AEM实例：

   * **Vault Remote Copy**，或 `vlt rcp`者，允许您跨网络使用vlt。 您可以指定源目录和目标目录，vlt从一个实例下载所有存储库数据并将其加载到另一个实例中。 Vlt rcp在https://jackrabbit.apache.org/filevault/rcp.html上有相关 [文档](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** 是Time Warner Cable为其AEM实施开发的一个开源内容同步工具。 由于它使用连续的数据流，与vlt rcp相比，它具有更低的延迟，并声称速度比vlt rcp快2到10倍。 Grabbit还支持仅同步Delta内容，这允许它在初始迁移通过完成后同步更改。

1. 激活资产：按照说明激活 [记录到](#activate-assets) AEM的初始迁移资产。

1. 克隆发布：与新迁移一样，加载单个发布实例并克隆它比激活两个节点上的内容更有效。 请参阅 [仿制发布。](#clone-publish)

1. 启用工作流：完成迁移后，请重新启用DAM更新资产工作流的启动程序，以支持再现生成和元数据提取，以便持续使用日常系统。
