---
title: 将资产批量迁移到Adobe Experience Manager Assets
description: 如何将资产导入AEM、应用元数据、生成演绎版，以及激活它们以发布实例。
contentOwner: AG
feature: 迁移，演绎版，资产管理
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1795'
ht-degree: 11%

---

# Assets迁移指南 {#assets-migration-guide}

将资产迁移到AEM时，需要考虑以下几个步骤。 将资产和元数据从其当前主页提取出来，不在本文档的涵盖范围之内，因为不同实施之间的差异很大。 本文档而是介绍如何将这些资产导入AEM、应用其元数据、生成演绎版，以及激活或发布资产。

## 前提条件 {#prerequisites}

在执行下述任何步骤之前，请查看并实施[资产性能调整提示](performance-tuning-guidelines.md)中的指南。 许多步骤（如配置最大并发作业）都可提高服务器在负载下的稳定性和性能。 在系统加载了资产后，很难执行其他步骤，如文件数据存储配置。

>[!NOTE]
>
>以下资产迁移工具未包含在Adobe Experience Manager中。 Adobe客户关怀团队不支持这些工具。
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

将资产迁移到AEM需要多个步骤，应将其视为分阶段过程。 迁移阶段如下：

1. 禁用工作流。
1. 加载标记。
1. 摄取资产。
1. 处理演绎版。
1. 激活资产。
1. 启用工作流。

![chlimage_1-223](assets/chlimage_1-223.png)

### 禁用工作流 {#disable-workflows}

在开始迁移之前，请禁用`DAM Update Asset`工作流的启动器。 最好将所有资产摄取到系统中，然后批量运行工作流。 如果迁移过程中您已经处于实时状态，则可以安排这些活动在非工作时间执行。

### 加载标记 {#load-tags}

您可能已经拥有了要应用于图像的标记分类。 CSV资产导入器和元数据配置文件功能等工具可以帮助自动将标记应用到资产。 在此之前，在Experience Manager中添加标记。 [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html)功能允许您使用加载到系统中的Microsoft Excel电子表格来填充标记。

### 摄取资产 {#ingest-assets}

在将资产摄取到系统中时，性能和稳定性是重要的考虑因素。 在Experience Manager中加载大量数据时，请确保系统运行良好。 这样可最大程度地减少添加数据所需的时间，并有助于避免系统过载。 这有助于防止系统崩溃，特别是在已在生产中的系统中。

将资产加载到系统中的方法有两种：使用HTTP的基于推送的方法，或使用JCR API的基于拉取的方法。

#### 通过HTTP推送 {#push-through-http}

Adobe的Managed Services团队使用名为Glutton的工具将数据加载到客户环境中。 Glutton是一个小型Java应用程序，用于将所有资产从一个目录加载到AEM实例上的另一个目录中。 您还可以使用诸如Perl脚本之类的工具将资产发布到存储库中，而不是Glutton。

使用通过https的方法有两个主要的缺点：

1. 通过HTTP将资产传输到服务器。 这需要相当多的开销并且非常耗时，从而延长了执行迁移所花费的时间。
1. 如果您的标记和自定义元数据必须应用于资产，则此方法需要再运行一个自定义流程，以便在导入资产后将此元数据应用于资产。

摄取资产的另一种方法是从本地文件系统中提取资产。 但是，如果您无法将外部驱动器或网络共享装载到服务器以执行基于拉取的方法，则最好通过HTTP发布资产。

#### 从本地文件系统中提取 {#pull-from-the-local-file-system}

[ACS AEM工具CSV资产导入程序](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html)从文件系统中提取资产，并从CSV文件中提取资产元数据以导入资产。 AEM Asset Manager API用于将资产导入系统并应用配置的元数据属性。 理想情况下，资产通过网络文件装载或通过外部驱动器装载到服务器上。

当资产不通过网络传输时，整体性能会有很大提高。 此方法通常是将资产加载到存储库中的最有效方法。 此外，由于该工具支持元数据摄取，因此您可以在单个步骤中导入所有资产和元数据。 应用元数据无需执行其他步骤，例如使用单独的工具。

### 处理演绎版 {#process-renditions}

将资产加载到系统中后，您需要通过DAM更新资产工作流处理这些资产，以提取元数据并生成演绎版。 在执行此步骤之前，您需要复制并修改DAM更新资产工作流以满足您的需求。 您可能不需要执行默认工作流中的某些步骤，例如Dynamic Media Classic PTIFF生成或InDesign服务器集成。

根据需要配置工作流后，您有两个选项可执行该工作流：

1. 最简单的方法是[ACS Commons&#39; Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)。 利用此工具，可执行查询并通过工作流处理查询结果。 还有一些选项可用于设置批处理大小。
1. 您可以将 [ACS Commons Fast Action Manager与Synthetic Workflows一起使](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) 用 [](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)。 虽然此方法涉及的范围更广，但它允许您在优化服务器资源的使用时删除AEM工作流引擎的开销。 此外，Fast Action manager还通过动态监视服务器资源和限制系统上的负载来进一步提升性能。 ACS Commons功能页上提供了示例脚本。

### 激活资产 {#activate-assets}

对于具有发布层的部署，您需要将资产激活到发布场。 虽然Adobe建议运行多个发布实例，但最有效的方法是将所有资产复制到单个发布实例，然后克隆该实例。 激活大量资产时，在触发树激活后，您可能需要干预。 原因如下：触发激活时，项目会添加到Sling作业/事件队列。 此队列的大小开始超过大约40,000个项目后，处理速度会急剧减慢。 当此队列的大小超过100,000个项目后，系统稳定性开始受到影响。

要解决此问题，您可以使用[快速操作管理器](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)管理资产复制。 这在不使用Sling队列的情况下可正常工作，从而降低开销，同时限制工作负载以防止服务器过载。 有关使用FAM管理复制的示例，请参见该功能的文档页面。

将资产转至发布场的其他选项包括使用 [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) 或 [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)，这些选项作为 Jackrabbit 中的工具提供。另一个选项的目的是对 AEM 基础结构使用一个名为 [Grabbit](https://github.com/TWCable/grabbit) 的开放源工具，该工具声称比 vlt 的性能更快。

对于这些方法中的任何一种方法，我们应当注意，创作实例上的资产未显示为已激活。 要使用正确的激活状态标记这些资产，您还需要运行一个脚本来将资产标记为已激活。

>[!NOTE]
>
>Adobe不维护或支持Grabbit。

### 克隆发布 {#clone-publish}

激活资产后，您可以克隆发布实例，以创建部署所需的任意数量的副本。 克隆服务器相当简单，但需要记住一些重要步骤。 要克隆发布，请执行以下操作：

1. 备份源实例和数据存储。
1. 将实例和数据存储的备份还原到目标位置。 以下步骤均引用此新实例。
1. 在`crx-quickstart/launchpad/felix`下对`sling.id`执行文件系统搜索。 删除此文件。
1. 在数据存储的根路径下，找到并删除任何`repository-XXX`文件。
1. 编辑`crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`和`crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`以指向新环境中数据存储的位置。
1. 启动环境。
1. 更新作者上任何复制代理的配置，以指向新实例上正确的发布实例或调度程序刷新代理，以指向新环境的正确调度程序。

### 启用工作流 {#enable-workflows}

完成迁移后，应重新启用DAM更新资产工作流的启动器，以支持生成演绎版和元数据提取，以便持续使用日常系统。

## 跨AEM部署迁移资产 {#migrate-between-aem-instances}

虽然这种情况并不常见，但有时您需要将大量数据从一个AEM实例迁移到另一个实例；例如，当您执行AEM升级、升级硬件或迁移到新数据中心时，例如通过AMS迁移。

在这种情况下，您的资产已经填充了元数据，并且已经生成了演绎版。 您只需将精力集中在将资产从一个实例移动到另一个实例即可。 在AEM实例之间迁移时，您需要执行以下步骤：

1. 禁用工作流：由于您正在迁移演绎版和我们的资产，因此您需要禁用DAM更新资产的工作流启动器。

1. 迁移标记：由于源AEM实例中已加载标记，因此您可以在内容包中构建标记，并在目标实例上安装该包。

1. 迁移资产：推荐使用两种工具将资产从一个AEM实例移动到另一个实例：

   * **保险库远程副本**&#x200B;或 `vlt rcp`，允许您跨网络使用vlt。您可以指定源目录和目标目录，然后vlt从一个实例下载所有存储库数据并将其加载到另一个实例。 Vlt rcp记录在[https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **** Grabbitis是由Time Warner Cable为实施其AEM而开发的一款开源内容同步工具。由于它使用连续数据流，与vlt rcp相比，它具有更低的延迟，并声称速度比vlt rcp快2到10倍。 Grabbit还仅支持增量内容的同步，这允许它在完成初始迁移过程后同步更改。

1. 激活资产：按照初始迁移到AEM时记录的[激活资产](#activate-assets)的说明操作。

1. 克隆发布：与新迁移一样，加载单个发布实例并克隆该实例比在两个节点上激活内容更有效。 请参阅[克隆发布。](#clone-publish)

1. 启用工作流：完成迁移后，请重新启用DAM更新资产工作流的启动器，以支持生成演绎版和元数据提取，以便持续使用日常系统。
