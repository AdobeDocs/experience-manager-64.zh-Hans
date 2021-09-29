---
title: 资产性能调整指南
description: ' [!DNL Experience Manager] configuration, changes to hardware, software, and network components to remove bottlenecks and optimize the performance of [!DNL Experience Manager] Assets的关键焦点区域。'
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '3151'
ht-degree: 0%

---

# 资产性能调整指南 {#assets-performance-tuning-guide}

Adobe Experience Manager Assets设置包含许多硬件、软件和网络组件。 根据您的部署方案，您可能需要对硬件、软件和网络组件进行特定配置更改，以消除性能瓶颈。

此外，确定并遵守某些硬件和软件优化准则有助于构建一个良好的基础，使您的[!DNL Experience Manager]资产部署能够满足对性能、可扩展性和可靠性的期望。

[!DNL Experience Manager]资产性能不佳可能会影响用户在交互式性能、资产处理、下载速度等方面的体验。

事实上，性能优化是您在为任何项目建立目标量度之前执行的一项基本任务。

以下是一些关键焦点区域，您可以围绕这些区域发现并修复性能问题，然后才能对用户产生影响。

## 平台 {#platform}

虽然在许多平台上都支持[!DNL Experience Manager] ，但Adobe在Linux和Windows上发现对本机工具的最大支持，这有助于实现最佳性能并简化实施过程。 理想情况下，您应该部署64位操作系统，以满足[!DNL Experience Manager]资产部署的高内存要求。 与任何[!DNL Experience Manager]部署一样，您应尽可能实施TarMK。 虽然TarMK无法扩展到单个创作实例之外，但发现它的性能优于MongoMK。 您可以添加TarMK卸载实例，以提高[!DNL Experience Manager]资产部署的工作流处理能力。

### 临时文件夹 {#temp-folder}

要缩短资产上传时间，请对Java temp目录使用高性能存储。 在Linux和Windows上，可使用RAM驱动器或SSD。 在基于云的环境中，可以使用等效的高速存储类型。 例如，在Amazon EC2中，[临时驱动器](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)驱动器可用于temp文件夹。

假设服务器有充足的内存，请配置RAM驱动器。 在Linux上，运行以下命令以创建一个8 GB RAM驱动器：

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

在Windows操作系统中，您必须使用第三方驱动程序来创建RAM驱动器，或者只使用高性能存储（如SSD）。

高性能临时卷准备就绪后，设置JVM参数-Djava.io.tmpdir。 例如，您可以将下面的JVM参数添加到AEM的bin/start脚本中的CQ_JVM_OPTS变量中：

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java配置 {#java-configuration}

### Java版本 {#java-version}

由于Oracle自2015年4月起已停止发布Java 7更新，因此Adobe建议在Java 8上部署[!DNL Experience Manager]资产。 在某些情况下，它显示性能有所改善。

### JVM参数 {#jvm-parameters}

您应设置以下JVM参数：

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## 数据存储和内存配置 {#data-store-and-memory-configuration}

### 文件数据存储配置 {#file-data-store-configuration}

建议所有[!DNL Experience Manager]资产用户将数据存储与区段存储分开。 此外，配置`maxCachedBinarySize`和`cacheSizeInMB`参数有助于最大化性能。 将`maxCachedBinarySize`设置为可在缓存中保存的最小文件大小。 指定用于`cacheSizeInMB`内数据存储的内存内缓存大小。 Adobe建议将此值设置为堆总大小的2-10%之间。 但是，负载/性能测试有助于确定理想的设置。

### 配置缓冲的图像缓存的最大大小 {#configure-the-maximum-size-of-the-buffered-image-cache}

在将大量资产上传到Adobe Experience Manager时，为了允许内存消耗出现意外峰值并防止JVM在出现OutOfMemoryErrors时失败，请减小已配置的缓冲图像缓存的最大大小。 例如，您的系统堆（ — `Xmx`参数）最大为5 GB，Oak BlobCache设置为1 GB，文档缓存设置为2 GB。 在这种情况下，缓冲的缓存将最大占用1.25 GB和内存，这将仅保留0.75 GB的内存，以备出现意外峰值。

在OSGi Web控制台中配置缓冲的缓存大小。 在`https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`处，以字节为单位设置属性`cq.dam.image.cache.max.memory`。 例如，1073741824为1 GB(1024 x 1024 x 1024 = 1 GB)。

从[!DNL Experience Manager] 6.1 SP1中，如果使用`sling:osgiConfig`节点来配置此属性，请确保将数据类型设置为Long。 有关更多详细信息，请参阅[CQBufferedImageCache在资产上传](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)期间使用堆。

### 共享数据存储 {#shared-data-stores}

实施S3或共享文件数据存储有助于在大规模实施中节省磁盘空间并提高网络吞吐量。 有关使用共享数据存储的利弊的更多信息，请参阅[资产大小调整指南](assets-sizing-guide.md)。

### S3数据存储 {#s-data-store}

以下S3数据存储配置(`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`)帮助将12.8 TB的二进制大对象(BLOB)从现有文件数据存储中提取到客户站点的S3数据存储中：

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

## 网络优化 {#network-optimization}

Adobe建议启用HTTPS，因为许多公司都有可嗅探HTTP流量的防火墙，这会对上传和损坏文件造成不利影响。 对于大文件上传，请确保用户已通过有线连接连接到网络，因为WiFi网络会迅速饱和。 有关确定网络瓶颈的准则，请参阅[资产大小调整指南](assets-sizing-guide.md)。 要通过分析网络拓扑来评估网络性能，请参阅[资产网络注意事项](assets-network-considerations.md)。

网络优化策略主要取决于可用带宽量和[!DNL Experience Manager]实例的负载。 常用配置选项（包括防火墙或代理）可帮助提高网络性能。 请牢记以下要点：

* 根据您的实例类型（小、中、大），确保您的[!DNL Experience Manager]实例有足够的网络带宽。 如果在AWS上托管[!DNL Experience Manager]，则适当的带宽分配尤为重要。
* 如果您的[!DNL Experience Manager]实例托管在AWS上，则您可以通过使用通用的扩展策略来获益。 如果用户期望获得高负载，请更新实例的大小。 为适中/低负载减小其大小。
* HTTPS:大多数用户具有可嗅探HTTP流量的防火墙，这可能会对上传操作期间文件的上传甚至文件损坏产生不利影响。
* 大文件上传：确保用户有与网络的有线连接（WiFi连接快速饱和）。

## 工作流 {#workflows}

### 瞬态工作流 {#transient-workflows}

尽可能将DAM更新资产工作流设置为“临时”。 该设置可显着减少处理工作流所需的开销，因为在这种情况下，工作流不需要通过常规的跟踪和存档流程。

>[!NOTE]
>
>默认情况下，在[!DNL Experience Manager] 6.3中，DAM更新资产工作流设置为“临时”。在这种情况下，您可以跳过以下过程。

1. 在要配置的[!DNL Experience Manager]实例上打开`http://localhost:4502/miscadmin`。

1. 在导航树中，展开&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]** > **[!UICONTROL dam]**。
1. 双击&#x200B;**[!UICONTROL DAM更新资产]**。
1. 从浮动工具面板中，切换到&#x200B;**[!UICONTROL Page]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Page Properties]**。
1. 选择&#x200B;**[!UICONTROL 临时工作流]**&#x200B;单击&#x200B;**[!UICONTROL 确定]**。

   >[!NOTE]
   >
   >某些功能不支持临时工作流。 如果您的[!DNL Experience Manager]资产部署需要这些功能，请勿配置临时工作流。

   如果不能使用临时工作流，请定期运行工作流清除，以删除已存档的DAM更新资产工作流，以确保系统性能不会下降。

   通常，您应每周运行清除工作流。 但是，在资源密集型场景（例如在大规模资产摄取期间）中，您可以更频繁地运行它。

   要配置工作流清除，请通过OSGi控制台添加新的AdobeGranite工作流清除配置。 接下来，在每周维护窗口中配置并计划工作流。

   如果清除运行过长，则会超时。 因此，您应确保清除作业已完成，以避免由于工作流数量过多而无法完成清除工作流的情况。

   例如，在运行大量非瞬态工作流（创建工作流实例节点）后，您可以在临时基础上运行[ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html)。 它会立即删除冗余的已完成工作流实例，而不是等待AdobeGranite工作流清除计划程序运行。

### 最大并行作业数 {#maximum-parallel-jobs}

默认情况下，[!DNL Experience Manager]运行的最大并行作业数等于服务器上的处理器数。 此设置的问题在于，在负载过重时，所有处理器都被DAM更新资产工作流占用，从而减慢UI响应速度，并阻止[!DNL Experience Manager]运行其他可保护服务器性能和稳定性的进程。 最好通过执行以下步骤将此值设置为服务器上可用处理器的一半：

1. 在[!DNL Experience Manager]作者中，转到[http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent)。
1. 单击与您的实施相关的每个工作流队列上的编辑，例如Granite Transient工作流队列。
1. 更改“最大并行作业数”的值，然后单击“保存”。

将队列设置到一半的可用处理器是一个可行的解决方案。 但是，您可能必须增加或减少此数量，才能实现最大吞吐量，并按环境进行调整。 临时工作流和非临时工作流以及其他进程（如外部工作流）有单独的队列。 如果多个队列设置为50%的处理器同时处于活动状态，则系统可以快速过载。 大量使用的队列在各个用户实施中有很大差异。 因此，您可能必须仔细配置它们以实现最高效率，而不牺牲服务器稳定性。

### 卸载 {#offloading}

对于大量资源密集型工作流或工作流（如视频转码），您可以将DAM更新资产工作流卸载到第二个创作实例。 通常，卸载的问题是，通过卸载工作流处理而保存的任何加载都会被实例之间来回复制内容的成本所抵销。

从[!DNL Experience Manager] 6.2开始，使用[!DNL Experience Manager] 6.1的功能包，可以使用无二进制复制执行卸载。 在此模型中，创作实例共享公共数据存储，并且只通过转发复制来回发送元数据。 虽然此方法与共享文件数据存储非常适用，但S3数据存储可能存在问题。 由于后台写入线程可能会导致延迟，因此在卸载作业开始之前资产可能尚未写入数据存储。

### DAM更新资产配置 {#dam-update-asset-configuration}

DAM更新资产工作流包含为任务配置的完整步骤套件，例如Dynamic Media Classic PTIFF生成和InDesign Server集成。 但是，大多数用户可能不需要执行其中的几个步骤。 Adobe建议您创建DAM更新资产工作流模型的自定义副本，并删除任何不必要的步骤。 在这种情况下，请更新DAM更新资产的启动器，以指向新模型。

>[!NOTE]
>
>集中运行DAM更新资产工作流可能会大幅增加文件数据存储的大小。 通过Adobe进行的实验结果表明，如果在8小时内执行大约5500个工作流，则数据存储大小可以增加大约400 GB。
>
>这是临时增加，在您运行数据存储垃圾收集任务后，数据存储将恢复到其原始大小。
>
>通常，数据存储垃圾收集任务与其他计划维护任务一起每周运行。
>
>如果磁盘空间有限，并且集中运行DAM更新资产工作流，请考虑更频繁地计划垃圾收集任务。

#### 运行时呈现版本生成 {#runtime-rendition-generation}

客户在其网站中使用各种大小和格式的图像，或将其分发给业务合作伙伴。 由于每个演绎版都会增加资产在存储库中的占用空间，因此Adobe建议谨慎使用此功能。 为了减少处理和存储图像所需的资源量，您可以在运行时生成这些图像，而不是在摄取期间作为演绎版生成这些图像。

许多Sites客户实施了一个图像Servlet，在请求时调整图像大小并裁剪图像，这会对发布实例造成额外负载。 但是，只要可以缓存这些图像，挑战就可以缓解。

另一种方法是使用Dynamic Media Classic技术完全放弃图像处理。 此外，您还可以部署Brand Portal，它不仅从[!DNL Experience Manager]基础架构接管再现生成责任，还接管整个发布层。

#### ImageMagick {#imagemagick}

如果您自定义DAM更新资产工作流以使用ImageMagick生成演绎版，则Adobe建议您修改位于&#x200B;*/etc/ImageMagick/*&#x200B;的policy.xml文件。 默认情况下， ImageMagick使用操作系统卷上的整个可用磁盘空间和可用内存。 在policy.xml的`policymap`部分内进行以下配置更改以限制这些资源。

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

此外，在&#x200B;*configure.xml*&#x200B;文件（或通过设置环境变量`MAGIC_TEMPORARY_PATH`）中，将ImageMagick的临时文件夹的路径设置为具有足够空间和IOPS的磁盘分区。

>[!CAUTION]
>
>如果ImageMagick使用所有可用磁盘空间，则配置不当可能会使服务器不稳定。 使用ImageMagick处理大型文件所需的策略更改可能会影响[!DNL Experience Manager]性能。 有关更多信息，请参阅[安装和配置ImageMagick](best-practices-for-imagemagick.md)。

>[!NOTE]
>
>ImageMagick `policy.xml`和`configure.xml`文件可在`/usr/lib64/ImageMagick-*/config/`下找到，而不是`/etc/ImageMagick/`下找到。 有关配置文件位置的详细信息，请参阅[ImageMagick文档](https://www.imagemagick.org/script/resources.php)。

如果您在Adobe Managed Services(AMS)上使用[!DNL Experience Manager]，请联系Adobe客户关怀团队，如果您计划处理大量大型PSD或PSB文件。 Experience Manager可能无法处理超过30000 x 23000像素的高分辨率PSB文件。

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

### XMP写回 {#xmp-writeback}

每当在AEM中修改元数据时，XMP写回会更新原始资产，这会导致以下结果：

* 资产本身已修改
* 此时会创建资产的版本
* 针对资产运行DAM更新资产

所列结果消耗了大量资源。 因此，Adobe建议[禁用XMP写回](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)（如果不需要）。

如果选中了运行工作流标志，则导入大量元数据可能会导致资源密集型XMP写回活动。 在精益服务器使用期间规划此类导入，以便不影响其他用户的性能。

## 复制 {#replication}

在将资产复制到大量发布实例（例如在Sites实施中）时，Adobe建议您使用链复制。 在这种情况下，创作实例会复制到单个发布实例，而该实例又会复制到其他发布实例，从而释放创作实例。

### 配置链复制 {#configure-chain-replication}

1. 选择要将复制链接到的发布实例
1. 在该发布实例上，添加指向其他发布实例的复制代理
1. 在这些复制代理中，在&#x200B;**[!UICONTROL Triggers]**&#x200B;选项卡上启用&#x200B;**[!UICONTROL On Receive]**

>[!NOTE]
>
>Adobe不建议自动激活资产。 但是，如果需要，Adobe建议将此操作作为工作流的最后一步，通常是DAM更新资产。

## 搜索索引 {#search-indexes}

确保实施最新的Service Pack和与性能相关的修补程序，因为它们通常包括对系统索引的更新。 请参阅[性能调整提示 | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) ，用于某些可应用的索引优化，具体取决于您的AEM版本。

为经常运行的查询创建自定义索引。 有关详细信息，请参阅[用于分析慢速查询的方法](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html)和[编制自定义索引](/help/sites-deploying/queries-and-indexing.md)。 有关查询和索引最佳实践的其他分析，请参阅[查询和索引的最佳实践](/help/sites-deploying/best-practices-for-queries-and-indexing.md)。

### Lucene索引配置 {#lucene-index-configurations}

可以对Oak索引配置进行一些优化，以帮助提高[!DNL Experience Manager]资产性能：

更新LuceneIndexProvider配置：

1. 导航到/system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. 在低于[!DNL Experience Manager] 6.2的版本中启用&#x200B;**[!UICONTROL CopyOnRead 、 CopyOnWrite和预取索引文件]**。在[!DNL Experience Manager] 6.2及更高版本中默认启用这些值。

更新索引配置以缩短重新索引时间：

1. 打开CRXDe /crx/de/index.jsp并以管理用户身份登录
1. 浏览到/oak:index/lucene
1. 添加名为&#x200B;**[!UICONTROL excludedPaths]**&#x200B;的String[]属性，其值为“/var”、“/etc/workflow/instances”和“/etc/replication”
1. 浏览到/oak:index/damAssetLucene
1. 添加名为&#x200B;**[!UICONTROL includedPaths]**&#x200B;的String[]属性，其中具有一个值“/content/dam”
1. 保存

(仅限AEM6.1和6.2)更新ntBaseLucene索引以改进资产删除和移动性能：

1. 浏览到&#x200B;*/oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. 在&#x200B;*/oak:index/ntBaseLucene/indexRules/nt:base/properties*&#x200B;下添加两个nt:unstructured节点&#x200B;**[!UICONTROL slingResource]**&#x200B;和&#x200B;**[!UICONTROL damResolvedPath]**
1. 在节点上设置以下属性（其中ordered和propertyIndex属性的类型为&#x200B;*Boolean*）：

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
1. 单击&#x200B;**[!UICONTROL Save All]**
1. 监视error.log以查看何时完成索引：

   已完成索引的重新索引：[/oak:index/ntBaseLucene]

1. 您还可以看到，由于reindex属性将返回false，因此在CRXDe中刷新/oak:index/ntBaseLucene节点后，索引即已完成
1. 完成索引后，返回到CRXDe，并将&#x200B;**[!UICONTROL type]**&#x200B;属性设置为对这两个索引禁用

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. 单击&#x200B;**[!UICONTROL Save All]**

禁用Lucene文本提取：

如果您的用户不需要搜索资产内容（例如搜索PDF文档中包含的文本），则可以禁用此功能以提高索引性能。

1. 转到[!DNL Experience Manager]包管理器/crx/packmgr/index.jsp
1. 上载并安装以下包

[获取文件](assets/disable_indexingbinarytextextraction-10.zip)

### 猜测总计 {#guess-total}

在创建生成大结果集的查询时，请使用`guessTotal`参数以避免在运行这些查询时内存使用率过高。

## 已知问题 {#known-issues}

### 大文件 {#large-files}

在AEM中，存在两个与大文件相关的主要已知问题。 当文件大小超过2 GB时，冷备用同步可能会出现内存不足的情况。 在某些情况下，它会阻止备用同步运行。 在其他情况下，它会导致主实例崩溃。 此方案适用于[!DNL Experience Manager]中任何大于2GB的文件，包括内容包。

同样，当文件在使用共享S3数据存储时达到2GB大小时，文件从缓存完全保留到文件系统可能需要一些时间。 因此，在使用无二进制复制时，可能在复制完成之前没有保留二进制数据。 这种情况可能会导致问题，特别是当数据的可用性很重要时（例如在卸载场景中）。

## 性能测试 {#performance-testing}

对于每个[!DNL Experience Manager]部署，建立一个性能测试机制，以便快速识别和解决瓶颈。 以下是需要重点关注的一些关键方面。

### 网络测试 {#network-testing}

对于客户涉及的所有网络性能问题，请执行以下任务：

* 从客户网络内部测试网络性能
* 从Adobe网络内测试网络性能。 对于AMS客户，请与您的CSE一起从Adobe网络内进行测试。
* 从另一个接入点测试网络性能
* 使用网络基准工具
* 针对调度程序进行测试

### [!DNL Experience Manager] 实例测试 {#aem-instance-testing}

为了通过高效的CPU利用和负载共享将延迟降至最低并实现高吞吐量，请定期监控[!DNL Experience Manager]实例的性能。 特别是：

* 对[!DNL Experience Manager]实例运行负载测试
* 监控上传性能和UI响应性

## [!DNL Experience Manager] 资产性能检查列表 {#aem-assets-performance-checklist}

* 启用HTTPS以绕过任何公司HTTP流量探查器。
* 使用有线连接上传大量资产。
* 设置最佳JVM参数。
* 配置文件系统数据存储或S3数据存储。
* 禁用子资产生成。 如果启用了该功能，AEM工作流会为多页面资产中的每个页面创建一个单独的资产。 其中每个页面都是单个资产，会占用额外的磁盘空间，需要进行版本控制，以及进行额外的工作流处理。 如果不需要单独的页面，请禁用子资产生成和页面提取活动。
* 启用临时工作流。
* 调整Granite工作流队列以限制并发作业。
* 配置ImageMagick以限制资源消耗。
* 从DAM更新资产工作流中删除不必要的步骤。
* 配置工作流和版本清除。
* 优化Lucene索引配置。
* 使用最新的Service Pack和修补程序优化索引。 请咨询Adobe客户关怀团队，了解是否存在任何其他可用的索引优化。
* 使用`guessTotal`优化查询性能。
* 如果配置[!DNL Experience Manager]以从文件内容中检测文件类型（通过在[!UICONTROL [!DNL Experience Manager]Web控制台]中配置[!UICONTROL Day CQ DAM Mime Type Service]），则在非高峰时间会批量上传许多文件，因为该操作占用大量资源。
