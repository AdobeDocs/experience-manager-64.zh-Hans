---
title: Assets 大小调整指南
description: '确定用于估算部署AEM Assets所需的基础架构和资源的有效量度的最佳实践。 '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: 资产管理
role: Architect,Administrator
exl-id: 6115e5e8-9cf5-417c-91b3-0c0c9c278b5b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1860'
ht-degree: 0%

---

# Assets 大小调整指南 {#assets-sizing-guide}

在调整Adobe Experience Manager(AEM)Assets实施的环境大小时，务必确保在磁盘、CPU、内存、IO和网络吞吐量方面有足够的可用资源。 调整其中许多资源的大小需要了解系统中加载的资产数量。 如果没有更好的量度可用，您可以将现有库的大小除以库的年龄，以查找创建资产的速率。

## 磁盘 {#disk}

### 数据存储 {#datastore}

在调整资产实施所需的磁盘空间大小时，常常会出现一个错误，即根据要摄取到系统中的原始映像的大小进行计算。 默认情况下，AEM会在原始图像之外创建三个演绎版，以用于渲染AEM UI元素。 在以前的实施中，观察到这些演绎版假定采用的资产大小是所摄取资产的两倍。

除了现成的演绎版之外，大多数用户还定义自定义演绎版。 除了演绎版之外，AEM Assets还允许您从常用文件类型(如InDesign和Illustrator)中提取子资产。

最后，AEM版本控制功能会存储版本历史记录中资产的重复项。 您可以配置要经常清除的版本。 但是，许多用户选择在系统中长时间保留版本，这会占用额外的存储空间。

考虑到这些因素，您需要一种方法来计算一个可接受的、准确的存储空间来存储用户资产。

1. 确定要加载到系统中的资产的大小和数量。
1. 获取要上传到AEM中的资产的代表性示例。 例如，如果计划将PSD、JPG、AI和PDF文件加载到系统中，则需要每种文件格式的多个样本图像。 此外，这些示例应代表不同的文件大小和图像的复杂性。
1. 定义要使用的演绎版。
1. 在AEM中使用ImageMagick或Adobe的Creative Cloud应用程序创建演绎版。 除了用户指定的演绎版之外，还创建现成的演绎版。 对于实施Dynamic Media Classic的用户，您可以使用IC二进制文件生成要存储在AEM中的PTIFF呈现版本。
1. 如果您计划使用子资产，请为相应的文件类型生成子资产。 有关如何从InDesign文件生成子资产页面或从Illustrator层生成PNG/PDF文件的在线文档。
1. 将输出图像、演绎版和子资产的大小与原始图像进行比较。 它允许您在加载系统时生成预期的增长因子。 例如，如果您在处理1GB资产后生成合并大小为3GB的演绎版和子资产，则演绎版增长系数为3。
1. 确定在系统中维护资产版本的最长时间。
1. 确定系统中修改现有资产的频率。 如果将AEM用作创意工作流中的协作中心，则更改量会很大。 如果仅将已完成的资产上传到系统，则此数量会低得多。
1. 确定每月有多少资产加载到系统中。 如果不确定，请确定当前可用的资产数量，并将该数量除以最早资产的年龄，以计算一个近似数。

执行步骤1-9可帮助您确定以下内容：

* 要加载的资产的原始大小
* 要加载的资产数量
* 演绎版增长因子
* 每月进行的资产修改次数
* 维护资产版本的月数
* 每月加载的新资产数
* 分配空间的年份

您可以在网络大小调整电子表格中指定这些数字，以确定数据存储所需的总空间。 此外，它还是确定维护AEM中资产版本或修改资产对磁盘增长的影响的有用工具。

工具中填充的示例数据演示了执行上述步骤有多么重要。 如果您仅根据正在加载的原始图像(1TB)来调整数据存储的大小，则您可能将存储库大小低估了15倍。

[获取文件](assets/disk_sizing_tool.xlsx)

### 共享数据存储{#shared-datastores}

对于大型数据存储，您可以通过网络连接驱动器上的共享文件数据存储或通过S3数据存储来实施共享数据存储。 在这种情况下，单个实例无需维护二进制文件的副本。 此外，共享数据存储有助于无二进制复制，并有助于减少将资产复制到发布环境或卸载实例的带宽。

#### 用例{#use-cases}

数据存储可以在主创作实例和备用创作实例之间共享，以使用在主实例中所做的更改来最小化更新备用实例所花费的时间。 Adobe建议在主创作实例和卸载创作实例之间共享数据存储，以减少工作流卸载中的开销。 您还可以在创作实例和发布实例之间共享数据存储，以在复制过程中最大限度地减少流量。

#### 缺点 {#drawbacks}

由于存在某些缺陷，因此在任何情况下都不建议共享数据存储。

#### 单点故障{#single-point-of-failure}

共享数据存储，在基础架构中引入单点故障。 假设您的系统有一个作者实例和两个发布实例，每个实例都有其自己的数据存储。 如果其中任何一个崩溃，则另外两个仍可以继续运行。 但是，如果共享数据存储，则单个磁盘故障可能会破坏整个基础架构。 因此，请确保您维护共享数据存储的备份，您可以在其中快速还原数据存储。

与常规的磁盘架构相比，部署用于共享数据存储的AWS S3服务会显着降低故障概率，因此，这是首选。

#### 复杂性增加{#increased-complexity}

共享数据存储还增加了操作的复杂性，如垃圾收集。 通常，只需单击一次即可启动独立数据存储的垃圾收集。 但是，共享数据存储除了在单个节点上运行实际集合之外，还需要对使用数据存储的每个成员执行标记扫描操作。

对于AWS操作，实施单个中心位置（通过S3），而不是构建EBS卷的RAID阵列，可以显着抵消系统的复杂性和操作风险。

#### 性能问题{#performance-concerns}

共享数据存储要求将二进制文件存储在所有实例之间共享的网络挂载驱动器上。 由于这些二进制文件是通过网络访问的，因此系统性能会受到不利影响。 使用快速网络连接到快速磁盘阵列可以部分减轻影响。 但是，这个建议很昂贵。 对于AWS操作，所有磁盘都是远程的，需要网络连接。 临时卷在实例启动或停止时丢失数据。

#### 延迟 {#latency}

后台写入线程会引入S3实现中的延迟。 备份过程必须考虑此延迟和任何卸载过程。 开始卸载作业时，S3中可能不存在S3资产。 此外，进行备份时， Lucene索引可能仍不完整。 它适用于写入S3数据存储并从其他实例访问的任何时间敏感文件。

### 节点存储/文档存储{#node-store-document-store}

由于以下资源消耗，因此很难获得NodeStore或DocumentStore的精确大小调整图：

* 资产元数据
* 资产版本
* 审核日志
* 存档和活动的工作流

由于二进制文件存储在数据存储中，因此每个二进制文件都占用一些空间。 大多数存储库的大小都低于100GB。 但是，可能存在大到1 TB的较大存储库。 此外，要执行离线压缩，您需要在卷上有足够的可用空间来重写压缩的存储库和预压缩版本。 一条经验法则是，将磁盘的大小调整为存储库预期大小的1.5倍。

对于存储库，使用IOPS级别大于3000的SSD或磁盘。 为了消除IOPS引入性能瓶颈的机率，请监控CPU IO等待级别以及早期问题迹象。

[获取文件](assets/aem_environment_sizingtool.xlsx)

## 网络 {#network}

AEM Assets有许多用例，它们使网络性能比我们的许多AEM项目更重要。 客户可以拥有快速服务器，但如果网络连接不足以支持从系统上传和下载资产的用户加载，则速度仍会很慢。 在[AEM资产注意事项中确定用户与AEM的网络连接中的中断点的方法很好，包括用户体验、实例大小调整、工作流评估和网络拓扑](assets-network-considerations.md)。

## WebDAV {#webdav}

如果将AEM桌面应用程序添加到组合中，则网络问题会因WebDAV协议的低效而变得更加严重。

为了说明这些低效情况，Adobe在OS X上使用WebDAV测试了系统性能。打开、编辑了3.5MB的InDesign文件并保存了更改。 提出了以下意见：

* 总共生成了约100个HTTP请求，以完成操作
* 文件已通过HTTP上传四次
* 通过HTTP下载了一次文件
* 完成整个操作需要42秒
* 总共传输了18MB的数据

在分析WebDAV上文件的平均保存时间时，发现性能会随着带宽的增加而显着提高，直到达到5-10Mbps级别。 因此，Adobe建议同时访问系统的每个用户至少应具有10Mbps的上传速度和5-10Mbps的带宽。

有关更多信息，请参阅[AEM桌面应用程序疑难解答](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)。

## 限制 {#limitations}

在调整实施大小时，务必牢记系统限制。 如果建议的实施超出了这些限制，请采用创意策略，例如在多个资产实施中划分资产。

文件大小并非导致内存不足(OOM)问题的唯一因素。 它还取决于图像的尺寸。 启动AEM时，通过提供更高的堆大小可以避免OOM问题。

此外，您还可以在配置管理器中编辑`com.day.cq.dam.commons.handler.StandardImageHandler`组件的阈值大小属性，以使用大于零的中间临时文件。

## 资产最大数量{#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

由于文件系统限制，数据存储中可以存在的文件数量限制为21亿。 在达到数据存储限制之前，存储库可能会遇到由于节点数量过大而导致的问题。

如果演绎版生成不正确，请使用Camera Raw库。 但是，在这种情况下，图像的最长边不应大于65000像素。 此外，图像不应包含超过512 MP(512 &amp;ast;1024 &amp;ast;1024像素)”。 *资产的规模无关紧要*。

由于像素大小等其他因素影响处理，因此很难准确估计支持为AEM设置特定堆的现成TIFF文件(OOTB)的大小。 AEM可以处理大小为255 MB的文件，但无法处理大小为18 MB的文件，因为与前者相比，后者包含异常高的像素数。

## 资产大小{#size-of-assets}

默认情况下，AEM允许您上传文件大小高达2 GB的资产。 要在AEM中上传超大资产，请参阅[上传超大资产的配置](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)。
