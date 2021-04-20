---
title: 资产性能调整指南
description: 围绕AEM配置、硬件、软件和网络组件的更改等重点领域，旨在消除瓶颈并优化AEM Assets性能。
contentOwner: AG
feature: Asset Management
role: Architect,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '3210'
ht-degree: 0%

---


# 资产性能调整指南{#assets-performance-tuning-guide}

Adobe Experience Manager(AEM)资产设置包含许多硬件、软件和网络组件。 根据部署方案，您可能需要对硬件、软件和网络组件进行特定配置更改以消除性能瓶颈。

此外，确定并遵守某些硬件和软件优化指南有助于构建一个可靠的基础，使您的AEM Assets部署能够满足性能、可扩展性和可靠性方面的期望。

AEM Assets性能差可能会影响用户在交互性能、资产处理、下载速度等方面的体验。

事实上，性能优化是您在为任何项目建立目标量度之前执行的一项基本任务。

以下是您在发现和修复性能问题后对用户产生影响的关键重点领域。

## 平台 {#platform}

虽然AEM在许多平台上受支持，但Adobe在Linux和Windows上对本机工具的支持最强，这有助于实现最佳性能并简化实施。 理想情况下，您应部署64位操作系统以满足AEM Assets部署的高内存要求。 与任何AEM部署一样，您应尽可能实施TarMK。 虽然TarMK无法扩展到单个作者实例之外，但发现它的性能优于MongoMK。 您可以添加TarMK卸载实例，以提高AEM Assets部署的工作流处理能力。

### 临时文件夹{#temp-folder}

要缩短资源上传时间，请对Java temp目录使用高性能存储。 在Linux和Windows上，可以使用RAM驱动器或SSD。 在基于云的环境中，可以使用等效的高速存储类型。 例如，在Amazon EC2中，[短暂驱动器](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)驱动器可用于临时文件夹。

假定服务器有充足的内存，请配置RAM驱动器。 在Linux上，运行以下命令以创建一个8 GB RAM驱动器：

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

在Windows操作系统中，您必须使用第三方驱动程序来创建RAM驱动器，或仅使用高性能存储（如SSD）。

高性能临时卷准备就绪后，请设置JVM参数-Djava.io.tmpdir。 例如，您可以将以下JVM参数添加到AEM的bin/开始脚本中的CQ_JVM_OPTS变量中：

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java配置{#java-configuration}

### Java版本{#java-version}

由于Oracle自2015年4月起已停止发布Java 7更新，因此Adobe建议在Java 8上部署AEM Assets。 在某些情况下，它显示性能有所改进。

### JVM参数{#jvm-parameters}

应设置以下JVM参数：

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## 数据存储和内存配置{#data-store-and-memory-configuration}

### 文件数据存储配置{#file-data-store-configuration}

建议所有AEM Assets用户将数据存储区与区段存储区分开。 此外，配置`maxCachedBinarySize`和`cacheSizeInMB`参数有助于最大限度地提高性能。 将`maxCachedBinarySize`设置为可保存在缓存中的最小文件大小。 指定用于`cacheSizeInMB`中数据存储的内存中缓存的大小。 Adobe建议您将此值设置为总堆大小的2-10%之间。 但是，负载/性能测试有助于确定理想的设置。

### 配置缓冲映像缓存的最大大小{#configure-the-maximum-size-of-the-buffered-image-cache}

在将大量资源上传到Adobe Experience Manager时，为了允许意外的内存消耗峰值并防止JVM因OutOfMemoryError而失败，请减小已缓冲的映像缓存的已配置最大大小。 例如，您有一个系统，其最大堆(- `Xmx`param)为5 GB，Oak BlobCache设置为1 GB，文档缓存设置为2 GB。 在这种情况下，缓冲的缓存将占用最大1.25 GB和内存，这将仅留下0.75 GB内存，以防出现意外的峰值。

在OSGi Web控制台中配置缓冲缓存大小。 在`https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`处，设置属性`cq.dam.image.cache.max.memory`（以字节为单位）。 例如，1073741824为1 GB(1024 x 1024 x 1024 = 1 GB)。

从AEM 6.1 SP1，如果您使用`sling:osgiConfig`节点配置此属性，请确保将数据类型设置为“长”。 有关详细信息，请参阅[资产上传](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)期间的CQBufferedImageCache消耗堆。

### 共享数据存储{#shared-data-stores}

实施S3或共享文件数据存储有助于在大规模实施中节省磁盘空间和增加网络吞吐量。 有关使用共享数据存储的利弊的详细信息，请参阅[资产大小调整指南](assets-sizing-guide.md)。

### S3数据存储{#s-data-store}

以下S3数据存储配置(`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`)帮助Adobe从现有文件数据存储中提取12.8 TB的二进制大对象(BLOB)到客户站点的S3数据存储中：

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## 网络优化{#network-optimization}

Adobe建议启用HTTPS，因为许多公司都有防火墙来嗅探HTTP通信，这会对上载和损坏文件产生不利影响。 对于大文件上传，请确保用户已通过有线连接连接到网络，因为WiFi网络会迅速饱和。 有关确定网络瓶颈的指南，请参阅[资产规模调整指南](assets-sizing-guide.md)。 要通过分析网络拓扑来评估网络性能，请参阅[资产网络注意事项](assets-network-considerations.md)。

主要而言，您的网络优化策略取决于可用带宽量和AEM实例的负载。 常用配置选项（包括防火墙或代理）有助于提高网络性能。 以下是需要记住的一些关键点：

* 根据您的实例类型（小、中、大），确保您拥有足够的AEM实例网络带宽。 如果AEM托管在AWS上，则适当的带宽分配尤为重要。
* 如果您的AEM实例托管在AWS上，则您可以通过拥有通用的扩展策略受益。 如果用户期望高负载，请升级实例。 对中/低负载缩减大小。
* HTTPS:大多数用户都有可嗅探HTTP通信的防火墙，这可能会对上传文件或在上传操作期间损坏文件产生不利影响。
* 大文件上载：确保用户有与网络的有线连接（WiFi连接快速饱和）。

## 工作流 {#workflows}

### 瞬态工作流{#transient-workflows}

尽可能将DAM更新资产工作流设置为临时。 该设置显着减少了处理工作流所需的开销，因为在这种情况下，工作流无需通过常规跟踪和归档过程。

>[!NOTE]
>
>默认情况下，在AEM 6.3中，“DAM更新资产”工作流设置为“临时”。在这种情况下，您可以跳过以下步骤。

1. 在要配置的AEM实例上打开`http://localhost:4502/miscadmin`。

1. 在导航树中，展开&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]** > **[!UICONTROL dam]**。
1. 多次 — 单击&#x200B;**[!UICONTROL DAM更新资产]**。
1. 从浮动工具面板切换到&#x200B;**[!UICONTROL Page]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Page Properties]**。
1. 选择&#x200B;**[!UICONTROL 临时工作流]**&#x200B;单击&#x200B;**[!UICONTROL 确定]**。

   >[!NOTE]
   >
   >某些功能不支持临时工作流。 如果您的AEM Assets部署需要这些功能，请不要配置临时工作流。

   如果无法使用临时工作流，请定期运行工作流清除以删除存档的DAM更新资产工作流，以确保系统性能不会降低。

   通常，您应每周运行清除工作流。 但是，在资源密集型场景中（例如在大规模资产摄取期间），您可以更频繁地运行它。

   要配置工作流清除，请通过OSGi控制台添加新的AdobeGranite工作流清除配置。 接下来，在每周维护窗口中配置和计划工作流。

   如果清除时间过长，就会超时。 因此，您应确保清除作业完成，以避免由于工作流数量过多而无法完成清除工作流的情况。

   例如，运行大量非临时工作流（创建工作流实例节点）后，您可以在临时基础上运行[ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html)。 它会立即删除冗余的已完成工作流实例，而不是等待Adobe Granite工作流清除调度程序运行。

### 最大并行作业数{#maximum-parallel-jobs}

默认情况下，AEM运行的最大并行作业数等于服务器上的处理器数。 此设置的问题在于，在负载较重的时期，所有处理器都被DAM更新资产工作流占用，这会降低UI响应速度，并阻止AEM运行其他可保护服务器性能和稳定性的进程。 最好通过执行以下步骤将此值设置为服务器上可用处理器的一半：

1. 在AEM作者中，转到[http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent)。
1. 在与您的实现相关的每个工作流队列（例如Granite临时工作流队列）上单击“编辑”。
1. 更改“最大并行作业”的值，然后单击“保存”。

将队列设置到可用处理器的一半是开始的可行解决方案。 但是，您可能必须增加或减少此数量，以获得最大吞吐量并按环境调整它。 对于临时和非临时工作流以及其他进程(如外部工作流)，存在单独的队列。 如果设置为50%的处理器同时处于活动状态的多个队列，则系统可以快速过载。 大量使用的队列在不同用户实现中差别很大。 因此，您可能必须仔细配置它们以获得最高效率，而不牺牲服务器稳定性。

### 卸载 {#offloading}

对于大量资源密集型工作流或工作流（如视频转码），您可以将DAM更新资产工作流卸载到第二个作者实例。 通常，卸载的问题是，卸载工作流处理后保存的任何加载都会被实例之间来回复制内容的成本所抵消。

从AEM 6.2开始，借助AEM 6.1的功能包，您可以使用无二进制复制执行卸载。 在此模型中，作者实例共享一个公共数据存储，并仅通过转发复制来回发送元数据。 虽然此方法与共享文件数据存储库配合使用，但S3数据存储库可能存在问题。 由于后台写入线程可能会引发延迟，因此在卸载作业开始之前，可能没有将资产写入数据存储。

### DAM更新资产配置{#dam-update-asset-configuration}

DAM更新资产工作流包含为任务配置的全套步骤，如Dynamic Media Classic PTIFF生成和InDesign Server集成。 但是，大多数用户可能不需要这些步骤中的几个步骤。 Adobe建议您创建DAM更新资产工作流模型的自定义副本，并删除任何不必要的步骤。 在这种情况下，请更新DAM更新资产的启动器以指向新模型。

>[!NOTE]
>
>集中运行DAM更新资产工作流可以大幅增加文件数据存储的大小。 Adobe所做实验的结果表明，如果在8小时内执行约5500个工作流，则数据存储大小可以增加约400 GB。
>
>这是临时增加，在运行数据存储垃圾收集任务后，数据存储将恢复为其原始大小。
>
>通常，数据存储垃圾收集任务每周运行，并运行其他计划维护任务。
>
>如果您的磁盘空间有限，并集中运行DAM更新资产工作流，请考虑更频繁地安排垃圾收集任务。

#### 运行时再现生成{#runtime-rendition-generation}

客户在其网站中使用各种大小和格式的图像，或分发给业务合作伙伴。 由于每个再现都会添加到存储库中资产的占用空间，因此Adobe建议谨慎使用此功能。 要减少处理和存储图像所需的资源量，您可以在运行时生成这些图像，而不是在摄取期间生成再现。

许多Sites客户实施了一个图像Servlet，在请求图像时调整图像大小和裁切图像，这会给发布实例带来额外负载。 但是，只要可以缓存这些图像，挑战就可以缓解。

另一种方法是使用Dynamic Media Classic技术完全放弃图像处理。 此外，您还可以部署Brand Portal，它不仅从AEM基础结构接管再现生成责任，还接管整个发布层。

#### ImageMagick {#imagemagick}

如果您自定义DAM更新资产工作流以使用ImageMagick生成再现，Adobe建议您修改位于&#x200B;*/etc/ImageMagick/*&#x200B;的policy.xml文件。 默认情况下，ImageMagick使用操作系统卷上的整个可用磁盘空间和可用内存。 在policy.xml的`policymap`部分中进行以下配置更改以限制这些资源。

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

此外，将&#x200B;*configure.xml*&#x200B;文件中ImageMagick的临时文件夹的路径(或通过设置环境变量`MAGIC_TEMPORARY_PATH`)设置到具有足够空间和IOPS的磁盘分区。

>[!CAUTION]
>
>如果ImageMagick使用所有可用磁盘空间，则错误配置可能会使您的服务器不稳定。 使用ImageMagick处理大型文件所需的策略更改可能会影响AEM性能。 有关详细信息，请参阅[安装和配置ImageMagick](best-practices-for-imagemagick.md)。

>[!NOTE]
>
>ImageMagick `policy.xml`和`configure.xml`文件可在`/usr/lib64/ImageMagick-*/config/`下找到，而不是`/etc/ImageMagick/`下。 有关配置文件位置的详细信息，请参阅[ImageMagick文档](https://www.imagemagick.org/script/resources.php)。

如果您在Adobe Managed Services(AMS)上使用AEM，则如果您计划处理大量大型PSD或PSB文件，请联系Adobe客户服务中心。 Experience Manager可能无法处理超30000 x 23000像素的高分辨率PSB文件。

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP写回{#xmp-writeback}

只要在AEM中修改元数据，XMP writeback就会更新原始资产，这会导致：

* 资产本身已修改
* 此时会创建资产的某个版本
* DAM更新资产会针对资产运行

所列成果消耗了大量资源。 因此，Adobe建议[禁用XMP写回](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)（如果不需要）。

如果选中了运行工作流标志，导入大量元数据可能会导致资源密集型XMP写回活动。 在精益服务器使用期间计划此类导入，以便不影响其他用户的性能。

## 复制 {#replication}

在将资产复制到大量发布实例（例如，在Sites实施中）时，Adobe建议您使用链复制。 在这种情况下，作者实例将复制到单个发布实例，而该实例又复制到其他发布实例，从而释放了作者实例。

### 配置链复制{#configure-chain-replication}

1. 选择要将复制链接到的发布实例
1. 在该发布实例上，添加指向其他发布实例的复制代理
1. 在每个复制代理上，在&#x200B;**[!UICONTROL 触发器]**&#x200B;选项卡上启用&#x200B;**[!UICONTROL 接收]**

>[!NOTE]
>
>Adobe不建议自动激活资产。 但是，如果需要，Adobe建议将此操作作为工作流（通常是DAM更新资产）的最后一步。

## 搜索索引{#search-indexes}

请确保实施最新的Service Pack和与性能相关的修补程序，因为它们通常包括对系统索引的更新。 请参阅[性能调整提示 | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)，用于某些可应用的索引优化，具体取决于您的AEM版本。

为经常运行的查询创建自定义索引。 有关详细信息，请参阅用于分析慢查询](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html)和[制作自定义索引](/help/sites-deploying/queries-and-indexing.md)的方法。 [有关查询和索引最佳实践的更多洞察，请参阅[查询和索引的最佳实践](/help/sites-deploying/best-practices-for-queries-and-indexing.md)。

### Lucene索引配置{#lucene-index-configurations}

可以对Oak索引配置进行一些优化，以帮助提高AEM Assets性能：

更新LuceneIndexProvider配置：

1. 导航到/system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. 在AEM 6.2之前的版本中启用&#x200B;**[!UICONTROL CopyOnRead、CopyOnWrite和预回迁索引文件]**。这些值在AEM 6.2及更高版本中默认处于启用状态。

更新索引配置以缩短重新索引时间：

1. 打开CRXDe /crx/de/index.jsp并以管理用户身份登录
1. 浏览到/oak:index/lucene
1. 添加名为&#x200B;**[!UICONTROL excludedPaths]**&#x200B;的String[]属性，其值为&quot;/var&quot;、&quot;/etc/workflow/instances&quot;和&quot;/etc/replication&quot;
1. 浏览到/oak:index/damAssetLucene
1. 添加名为&#x200B;**[!UICONTROL includedPaths]**&#x200B;的String[]属性，其值为“/content/dam”
1. 保存

(仅限AEM6.1和6.2)更新ntBaseLucene索引以改进资产删除和移动性能：

1. 浏览至&#x200B;*/oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. 在&#x200B;*/oak:index/ntBaseLucene/indexRules/nt:base/properties*&#x200B;下添加两个nt:unstructured节点&#x200B;**[!UICONTROL slingResource]**&#x200B;和&#x200B;**[!UICONTROL damResolvedPath]**
1. 在节点上设置以下属性(其中ordered和propertyIndex属性的类型为&#x200B;*Boolean*:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvedPath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. 在/oak:index/ntBaseLucene节点上，设置属性`reindex=true`
1. 单击&#x200B;**[!UICONTROL 保存全部]**
1. 监视error.log以查看何时完成索引：

   已完成索引的重新索引：[/oak:index/ntBaseLucene]

1. 您还可以看到，通过刷新CRXDe中的/oak:index/ntBaseLucene节点，索引完成，因为重新索引属性将返回false
1. 完成索引后，返回CRXDe并将这两个索引上的&#x200B;**[!UICONTROL type]**&#x200B;属性设置为禁用

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. 单击&#x200B;**[!UICONTROL 保存全部]**

禁用Lucene文本提取:

如果您的用户无需搜索资产内容(例如，搜索PDF文档中包含的文本)，则可以通过禁用此功能来提高索引性能。

1. 转到AEM包管理器/crx/packmgr/index.jsp
1. 上载并安装下面的包

[获取文件](assets/disable_indexingbinarytextextraction-10.zip)

### 猜测总数{#guess-total}

创建生成大结果集的查询时，请使用`guessTotal`参数以避免在运行这些结果集时占用大量内存。

## 已知问题 {#known-issues}

### 大文件{#large-files}

与AEM中的大文件有关的两个主要已知问题。 当文件大小超过2 GB时，冷备用同步可能会出现内存不足的情况。 在某些情况下，它会阻止备用同步运行。 在其他情况下，它会导致主实例崩溃。 此方案适用于AEM中大于2GB的任何文件，包括内容包。

同样，当使用共享S3数据存储时文件大小达到2GB时，文件从缓存完全保留到文件系统可能需要一些时间。 因此，在使用无二进制复制时，可能在复制完成之前没有保留二进制数据。 这种情况可能会导致问题，尤其是当数据可用性很重要时（例如在卸载场景中）。

## 性能测试{#performance-testing}

对于每个AEM部署，都要建立一个性能测试机制，以快速发现和解决瓶颈。 以下是需要关注的一些关键领域。

### 网络测试{#network-testing}

对于客户关心的所有网络性能问题，请执行以下任务:

* 从客户网络内测试网络性能
* 从Adobe网络中测试网络性能。 对于AMS客户，请与CSE协作，在Adobe网络中进行测试。
* 从另一个接入点测试网络性能
* 使用网络基准工具
* 针对调度程序进行测试

### AEM实例测试{#aem-instance-testing}

要通过高效的CPU利用率和负载共享将延迟降至最低并实现高吞吐量，请定期监控AEM实例的性能。 特别是：

* 针对AEM实例运行加载测试
* 监视上载性能和UI响应

## AEM Assets性能清单{#aem-assets-performance-checklist}

* 使HTTPS能够绕过任何企业HTTP流量侦听器。
* 使用有线连接进行重资产上传。
* 设置最佳JVM参数。
* 配置文件系统数据存储或S3数据存储。
* 禁用子资产生成。 如果启用，AEM工作流会为多页资产中的每个页面创建单独的资产。 这些页中的每个页都是消耗额外磁盘空间、需要版本控制和其他工作流处理的单个资产。 如果您不需要单独的页面，请禁用子资产生成和页面提取活动。
* 启用临时工作流。
* 调整Granite工作流队列以限制并发作业。
* 配置ImageMagick以限制资源消耗。
* 从DAM更新资产工作流中删除不必要的步骤。
* 配置工作流和版本清除。
* 优化Lucene索引配置。
* 使用最新的Service Pack和修补程序优化索引。 请咨询Adobe客户服务部门，了解可能提供的任何其他索引优化。
* 使用`guessTotal`优化查询性能。
* 如果将AEM配置为从文件内容中检测文件类型(通过在[!UICONTROL AEM Web Console]中配置[!UICONTROL Day CQ DAM Mime类型服务])，则在非高峰时间批量上传许多文件，因为该操作占用大量资源。
