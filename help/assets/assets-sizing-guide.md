---
title: 资产大小调整指南
description: '确定用于估计部署AEM Assets所需的基础架构和资源的有效指标的最佳实践。 '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
translation-type: tm+mt
source-git-commit: 6aec5927c00f70ce2c044ffd56cabbf68a81071a
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 0%

---


# 资产大小调整指南 {#assets-sizing-guide}

在调整Adobe Experience Manager(AEM)资产实施的环境大小时，务必确保在磁盘、CPU、内存、IO和网络吞吐量方面有足够的可用资源。 调整这些资源中的许多资源的大小需要了解要加载到系统中的资产数量。 如果没有更好的指标，您可以将现有库的大小除以库的年龄，以查找资产的创建速率。

## 磁盘 {#disk}

### 数据存储 {#datastore}

在调整资产实施所需的磁盘空间大小时，常出现一个错误，即根据要引入系统的原始图像的大小进行计算。 默认情况下，AEM在原始图像之外创建三个再现，以用于渲染AEM UI元素。 在以前的实施中，我们观察到这些演绎版采用的资产大小是所摄取资产的两倍。

除了开箱即用的再现，大多数用户还定义自定义再现。 除了演绎版之外，AEM Assets还允许您从常用文件类型(如InDesign和Illustrator)中提取子资产。

最后，AEM的版本控制功能会在版本历史记录中存储重复资产。 您可以经常配置要清除的版本。 但是，许多用户选择在系统中保留版本的时间很长，这会占用额外的存储空间。

考虑到这些因素，您需要一种方法来计算可接受的精确存储空间以存储用户资产。

1. 确定要加载到系统中的资产的大小和数量。
1. 获取要上传到AEM的资产的代表性示例。 例如，如果您计划将PSD、JPG、AI和PDF文件加载到系统中，您需要每种文件格式的多个范例图像。 此外，这些范例应代表不同的文件大小和复杂的图像。
1. 定义要使用的演绎版。
1. 在AEM中使用ImageMagick或Adobe的Creative Cloud应用程序创建再现。 除了用户指定的演绎版之外，还可创建现成的演绎版。 对于实施Scene7的用户，可以使用IC二进制生成要存储在AEM中的PTIFF再现。
1. 如果您计划使用子资产，请为相应的文件类型生成子资产。 请参阅有关如何从InDesign文件生成子资产页面或从Illustrator图层生成PNG/PDF文件的在线文档。
1. 将输出图像、演绎版和子资产的大小与原始图像进行比较。 它允许您在加载系统时生成预期的增长因子。 例如，如果您在处理1GB资产后生成合并大小为3GB的演绎版和子资产，则演绎版增长系数为3。
1. 确定在系统中维护资产版本的最长时间。
1. 确定系统中修改现有资产的频率。 如果AEM在创意工作流中用作协作中心，则更改量很大。 如果只将完成的资产上传到系统，则此数字要低得多。
1. 确定每月系统加载的资产数量。 如果不确定，请确定当前可用的资产数量，并除以最旧资产的年龄，以计算一个近似数字。

执行步骤1-9可帮助您确定以下内容：

* 要加载的资产的原始大小
* 要加载的资产数
* 再现增长因子
* 每月进行的资产修改数
* 维护资产版本的月数
* 每月加载的新资产数
* 分配空间的年份增长

您可以在网络大小调整电子表格中指定这些数字以确定数据存储所需的总空间。 它还是确定维护资产版本或修改AEM中的资产对磁盘增长的影响的有用工具。

工具中填充的示例数据演示了执行上述步骤是多么重要。 如果仅根据要加载的原始图像(1TB)对数据存储区进行大小调整，您可能将存储库大小低估了15倍。

[获取文件](assets/disk_sizing_tool.xlsx)

### 共享数据存储 {#shared-datastores}

对于大型数据存储，您可以通过网络连接驱动器上的共享文件数据存储或通过S3数据存储实现共享数据存储。 在这种情况下，单个实例无需维护二进制文件的副本。 此外，共享数据存储简化了无二进制复制，并有助于减少用于复制资产以发布环境或卸载实例的带宽。

#### Use Cases {#use-cases}

可以在主实例和备用作者实例之间共享数据存储，以最大限度地缩短在主实例中进行更改时更新备用实例所需的时间。 Adobe建议在主作者实例和卸载作者实例之间共享数据存储，以减少工作流卸载中的开销。 您还可以在作者实例和发布实例之间共享数据存储，以最大限度地减少复制过程中的流量。

#### 缺点 {#drawbacks}

由于某些缺陷，在所有情况下都不建议共享数据存储。

#### 单点故障 {#single-point-of-failure}

拥有共享数据存储，在基础架构中引入单点故障。 请考虑一种情况，即您的系统具有一个作者实例和两个发布实例，每个实例都具有自己的数据存储。 如果其中任何一个崩溃，其他两个仍然可以继续运行。 但是，如果共享数据存储，单个磁盘故障可以占用整个基础架构。 因此，请确保在共享数据存储区中保留备份，从而快速恢复数据存储区。

首选为共享数据存储部署AWS S3服务，因为与普通磁盘体系结构相比，它显着降低了失败的可能性。

#### 复杂性增加 {#increased-complexity}

共享数据存储也增加了操作的复杂性，如垃圾收集。 通常，只需单击一下，即可启动独立数据存储的垃圾收集。 但是，共享数据存储除了在单个节点上运行实际集合外，还需要对使用数据存储的每个成员执行标记扫描操作。

对于AWS操作，实施单一的中心位置（通过S3），而不是构建EBS卷的RAID阵列，可以大大抵消系统的复杂性和操作风险。

#### 性能问题 {#performance-concerns}

共享数据存储要求二进制文件存储在所有实例之间共享的网络装载驱动器上。 由于这些二进制文件通过网络进行访问，因此系统性能会受到不利影响。 使用快速网络连接到快速磁盘阵列，可以部分减轻影响。 然而，这是一个代价高昂的提议。 在AWS操作中，所有磁盘都是远程磁盘，需要网络连接。 实例开始或停止时，短暂的卷会丢失数据。

#### 延迟 {#latency}

S3实现中的延迟由后台写入线程引入。 备份过程必须考虑此延迟和任何卸载过程。 卸载作业开始时，S3资产可能不在S3中。 此外，在进行备份时，Lucene索引可能仍不完整。 它适用于写入到S3数据存储并从另一个实例访问的任何时间敏感文件。

### 节点存储/文档存储 {#node-store-document-store}

由于以下资源占用，很难获得NodeStore或DocumentStore的精确大小调整图：

* 资产元数据
* 资产版本
* 审核日志
* 存档和活动工作流

由于二进制文件存储在数据存储中，因此每个二进制文件都占用一些空间。 大多数存储库的大小都低于100GB。 但是，可能存在大到1 TB的大型存储库。 此外，要执行脱机压缩，您需要在卷上有足够的可用空间以在预压缩版本旁边重写压缩存储库。 一条不错的经验法则是，将磁盘大小调整为存储库预期大小的1.5倍。

对于存储库，使用IOPS级别大于3000的SSD或磁盘。 为了消除IOPS引入性能瓶颈的可能性，请监控CPU IO等待级别，以发现问题的早期迹象。

[获取文件](assets/aem_environment_sizingtool.xlsx)

## 网络 {#network}

AEM Assets有许多使用案例使网络性能比我们的许多AEM项目更重要。 客户可以拥有快速服务器，但如果网络连接不够大，无法支持从系统上传和下载资产的用户的负载，则速度仍会很慢。 有一种很好的方法，可确定用户与AEM的网络连接中的瓶颈， [以考虑用户体验、实例大小、工作流评估和网络拓扑](assets-network-considerations.md)。

## WebDAV {#webdav}

如果将AEM桌面应用程序添加到混合中，则网络问题将更加严重，因为WebDAV协议效率低下。

为了说明这些低效性，Adobe在OS X上使用WebDAV测试了系统性能。打开、编辑了3.5MB的InDesign文件并保存了更改。 有以下意见：

* 总共生成约100个HTTP请求以完成操作
* 通过HTTP上载了四次文件
* 文件通过HTTP下载一次
* 完成整个操作需要42秒
* 总共传输了18MB数据

在分析WebDAV上文件的平均保存时间时，发现随着带宽的增加，性能显着提高，直到5-10Mbps级别。 因此，Adobe建议同时访问系统的每个用户至少应具有10Mbps的上传速度和5-10Mbps的带宽。

有关详细信息，请参阅AEM桌 [面应用程序疑难解答](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)。

## 限制 {#limitations}

调整实施规模时，务必牢记系统限制。 如果建议的实施超出这些限制，则应采用创新战略，如在多个资产实施之间划分资产。

文件大小不是导致内存不足(OOM)问题的唯一因素。 它还取决于图像的尺寸。 在开始AEM时提供更高的堆大小，可以避免OOM问题。

此外，您还可以在Configuration Manager中编辑组件的阈 `com.day.cq.dam.commons.handler.StandardImageHandler` 值大小属性，以使用大于零的中间临时文件。

## 最大资产数 {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

由于文件系统限制，数据存储中可存在的文件数量限制可为21亿。 在达到数据存储限制之前，存储库可能会遇到由于大量节点造成的问题。

如果再现生成不正确，请使用Camera Raw库。 但是，在这种情况下，图像的最长边不应大于65000像素。 此外，图像不应包含超过512 MP(512 &amp;ast; 1024 &amp;ast; 1024像素)。 *资产规模无关紧要*。

由于额外的因素（如像素大小影响处理），很难准确估计AEM的特定堆支持的现成TIFF文件(OOTB)的大小。 AEM可以处理大小为255 MB的文件，但不能处理大小为18 MB的文件，因为后者包含的像素数比前者要高得多。

## 资产大小 {#size-of-assets}

默认情况下，AEM允许您上传文件大小高达2 GB的资源。 要在AEM中上传超大型资产，请参 [阅上传超大型资产的配置](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)。
