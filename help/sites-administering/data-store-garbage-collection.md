---
title: 数据存储垃圾收集
seo-title: 数据存储垃圾收集
description: 了解如何配置数据存储垃圾收集以释放磁盘空间。
seo-description: 了解如何配置数据存储垃圾收集以释放磁盘空间。
uuid: 1f49e9e9-3a0d-4687-844d-8a32fb30f2b4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5ee9d11a-85c2-440d-b487-a38d04dc040b
translation-type: tm+mt
source-git-commit: 3c4b8bf3fd912406657c4cecb75eb2b77dd41bc7
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 0%

---


# 数据存储垃圾收集 {#data-store-garbage-collection}

当删除常规WCM资产时，对基础数据存储记录的引用可从节点层次中删除，但数据存储记录本身仍然保持。 此未引用的数据存储记录随后变为“垃圾”，无需保留。 在存在大量垃圾资源的情况下，消除垃圾资源可以节省空间并优化备份和文件系统维护性能。

在大多数情况下，WCM应用程序往往收集信息，但删除信息的频率几乎不同。 虽然新图像被添加，甚至取代旧版本，但版本控制系统仍保留旧图像，并支持在必要时还原到旧图像。 因此，我们认为添加到系统的大多数内容都被有效地永久存储。 那么，我们可能想要清理的存储库中“垃圾”的典型来源是什么？

AEM将存储库用作许多内部和家政活动的存储:

* 构建和下载的包
* 为发布复制创建的临时文件
* 工作流负载
* 在DAM渲染过程中临时创建的资产

当这些临时对象中的任何一个都足够大，需要存储在数据存储中，并且当该对象最终失效时，数据存储记录本身将保持为“垃圾”。 在典型的WCM作者／发布应用程序中，此类垃圾的最大来源通常是发布激活的过程。 当数据被复制到发布时，如果首先以名为“Durbo”的有效数据格式收集到集合中并存储在以下存储库中，则数据将被复制 `/var/replication/data`。 数据包通常大于数据存储的临界大小阈值，因此最终存储为数据存储记录。 复制完成后，将删除中的节 `/var/replication/data` 点，但数据存储记录仍保留为“垃圾”。

可恢复垃圾的另一个来源是包。 与其他所有数据一样，包数据存储在存储库中，因此存储在数据存储中的包大于4KB。 在开发项目过程中或在一段时间内维护系统时，可以多次构建和重建包，每个构建都生成新的数据存储记录，同构前一个构建的记录。

## 数据存储垃圾收集是如何工作的？ {#how-does-data-store-garbage-collection-work}

如果存储库已配置外部数据存储，则数 [据存储垃圾收集将作为“每周维护](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection) ”窗口的一部分自动运行。 系统管理员还可以 [根据需要手动运行数据存储垃圾](#running-data-store-garbage-collection) 收集。 通常，建议定期执行数据存储垃圾收集，但在规划数据存储垃圾收集时应考虑以下因素：

* 数据存储垃圾收集需要时间，并可能影响性能，因此应相应地进行规划。
* 删除数据存储垃圾记录不会影响正常性能，因此这不是性能优化。
* 如果不考虑存储利用率和备份时间等相关因素，则可能会安全地延迟数据存储垃圾收集。

数据存储垃圾收集器在进程开始时首先记录当前时间戳。 然后，使用多通标记／扫描模式算法进行该收集。

在第一阶段，数据存储垃圾收集器对所有存储库内容执行全面遍历。 对于每个引用了数据存储记录的内容对象，它将文件放在文件系统中，执行元数据更新——修改“上次修改时间”或MTIME属性。 此时，此阶段访问的文件将比初始基线时间戳更新。

在第二阶段，数据存储垃圾收集器以与“查找”基本相同的方式遍历数据存储的物理目录结构。 它检查了文件的“上次修改时间”或MTIME属性，并作出以下确定：

* 如果MTIME比初始基线时间戳新，则要么在第一阶段找到该文件，要么是在集合过程进行中添加到存储库的全新文件。 其中一种情况，记录被认为有效，不得删除。
* 如果MTIME在初始基线时间戳之前，则该文件不是主动引用的文件，它被视为可移除垃圾。

此方法适用于具有私有数据存储的单个节点。 但是，数据存储可能是共享的，如果这意味着不检查其他存储库中对数据存储记录的潜在活动实时引用，并且可能错误地删除了活动引用的文件。 在规划任何垃圾收集之前，系统管理员必须了解数据存储的共享性质，并且仅当知道数据存储未共享时才使用简单的内置数据存储垃圾收集过程。

>[!NOTE]
>
>当在群集或共享数据存储设置中执行垃圾收集时（使用Mongo或Segment Tar），日志可能显示有关无法删除某些Blob ID的警告。 发生这种情况的原因是以前垃圾收集中删除的blob ID被其他没有ID删除信息的群集或共享节点再次错误引用。 因此，当执行垃圾收集时，当它尝试删除在上次运行中已删除的ID时，它会记录一条警告消息。 此行为不影响性能或功能。

## Running Data Store Garbage Collection {#running-data-store-garbage-collection}

根据AEM所运行的数据存储设置，有三种运行数据存储垃圾收集的方法：

1. 通过 [修订清除](/help/sites-deploying/revision-cleanup.md) -通常用于节点存储清理的垃圾收集机制。

1. 通过 [数据存储垃圾收集](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-operations-dashboard) -一种特定于外部数据存储的垃圾收集机制，可在“操作”仪表板中使用。
1. 通过JMX [控制台](/help/sites-administering/jmx-console.md)。

如果TarMK同时用作节点存储和数据存储，则“修订清理”可用于节点存储和数据存储的垃圾收集。 但是，如果配置了外部数据存储（如文件系统数据存储），则必须显式触发数据存储垃圾收集，而不是修订清除。 数据存储垃圾收集可通过“操作”仪表板或JMX控制台触发。

下表显示了需要用于AEM 6中所有受支持数据存储部署的数据存储垃圾收集类型：

<table> 
 <tbody> 
  <tr> 
   <td><strong>节点存储</strong><br /> </td> 
   <td><strong>数据存储</strong></td> 
   <td><strong>垃圾收集机制</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>TarMK</td> 
   <td>TarMK</td> 
   <td>修订清理（二进制文件与段存储内置）</td> 
  </tr> 
  <tr> 
   <td>TarMK</td> 
   <td>外部文件系统</td> 
   <td><p>通过“操作”任务存储垃圾收集仪表板</p> <p>JMX控制台</p> </td> 
  </tr> 
  <tr> 
   <td>MongoDB</td> 
   <td>MongoDB</td> 
   <td><p>通过“操作”任务存储垃圾收集仪表板</p> <p>JMX控制台</p> </td> 
  </tr> 
  <tr> 
   <td>MongoDB</td> 
   <td>外部文件系统</td> 
   <td><p>通过“操作”任务存储垃圾收集仪表板</p> <p>JMX控制台</p> </td> 
  </tr> 
 </tbody> 
</table>

### 通过“操作”仪表板运行数据存储垃圾收集 {#running-data-store-garbage-collection-via-the-operations-dashboard}

内置的“每周维护”窗口可通过“操 [作”仪表板](/help/sites-administering/operations-dashboard.md)，包含一个内置任务，用于在周日的凌晨1点触发“数据存储垃圾收集”。

如果您需要在此时间之外运行数据存储垃圾收集，则可以通过“操作”仪表板手动触发。

在运行数据存储垃圾收集之前，您应检查当时没有运行备份。

1. 通过导航->工 **具** ->操 **作** ->维护 **仪表板打** 开操 **作**->维护。
1. 单击或点按每周 **维护窗口**。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 选择“ **数据存储垃圾收集** ”任务，然后单击或点 **按运行图** 标。

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. 数据存储垃圾收集运行，其状态显示在仪表板中。

   ![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>只有在配置了外部文件数据存储时，数据存储垃圾收集任务才可见。 有关 [如何设置文件数据存储的信息](/help/sites-deploying/data-store-config.md#file-data-store) ，请参阅在AEM 6中配置节点存储和数据存储。

### 通过JMX控制台运行数据存储垃圾收集 {#running-data-store-garbage-collection-via-the-jmx-console}

本节介绍如何通过JMX控制台手动运行数据存储垃圾收集。 如果安装是在没有外部数据存储的情况下设置的，则这不适用于您的安装。 而是在维护存储库下查看如何运行修订 [清理的说明](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)。

>[!NOTE]
>
>如果您正在与外部数据存储一起运行TarMK，则需要先运行修订清理，以便垃圾收集有效。

要运行垃圾收集，请执行以下操作：

1. 在Apache Felix OSGi管理控制台中，高亮显 **示“** Main（主）”选 **项卡** ，并从以下菜单中选择JMX。
1. 然后，搜索并单击 **Repository Manager** MBean(或转至 `https://<host>:<port>/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Drepository+manager%2Ctype%3DRepositoryManagement`)。
1. 单击 **startDataStoreGC(boolean markOnly)**。
1. 根据需`true`要，输入 `markOnly` “”作为参数：

   | **选项** | **描述** |
   |---|---|
   | 布尔型markOnly | 在标记和扫描操作中，设置为true可仅标记参照而不扫描。 当基础BlobStore在多个不同的存储库之间共享时，将使用此模式。 对于所有其他情况，将其设置为false即可执行完全垃圾收集。 |

1. 单击 **调用**。 CRX运行垃圾收集并指示它何时完成。

>[!NOTE]
>
>数据存储垃圾收集不会收集在过去24小时内已删除的文件。

>[!NOTE]
>
>仅当您配置了外部文件数据存储时，数据存储垃圾收集任务才会开始。 如果尚未配置外部文件数据存储，任务将在调用后返回 `Cannot perform operation: no service of type BlobGCMBean found` 消息。 有关 [如何设置文件数据存储的信息](/help/sites-deploying/data-store-config.md#file-data-store) ，请参阅在AEM 6中配置节点存储和数据存储。

## Automating Data Store Garbage Collection {#automating-data-store-garbage-collection}

如果可能，应在系统上负载很小时（例如在上午）运行数据存储垃圾收集。

内置的“每周维护”窗口可通过“操 [作”仪表板](/help/sites-administering/operations-dashboard.md)，包含一个内置任务，用于在周日的凌晨1点触发“数据存储垃圾收集”。 您还应检查此时是否未运行备份。 可以根据需要通过开始来自定义维护窗口的仪表板。

>[!NOTE]
>
>不同时运行它的原因是，旧（和未使用）数据存储文件也得到备份，因此，如果需要回滚到旧修订，二进制文件仍在备份中。

如果您不想在“操作”仪表板中使用“每周维护窗口”运行数据存储垃圾收集，也可以使用wget或curl HTTP客户端自动进行。 以下是如何使用curl自动备份的示例：

>[!CAUTION]
>
>在以下示例 `curl` 中，可能需要为实例配置各种参数； 例如，主机名( `localhost`)、端口( `4502`)、管理员密码() `xyz`和实际数据存储垃圾收集的各种参数。

下面是一个通过命令行调用数据存储垃圾收集的curl命令示例：

```shell
curl -u admin:admin -X POST --data markOnly=true  http://localhost:4503/system/console/jmx/org.apache.jackrabbit.oak"%"3Aname"%"3Drepository+manager"%"2Ctype"%"3DRepositoryManagement/op/startDataStoreGC/boolean
```

curl命令会立即返回。

## 检查数据存储一致性 {#checking-data-store-consistency}

数据存储一致性检查将报告所有缺少但仍被引用的数据存储二进制文件。 要开始一致性检查，请执行以下步骤：

1. 转到JMX控制台。 有关如何使用JMX控制台的信息，请参 [阅本文](/help/sites-administering/jmx-console.md#using-the-jmx-console)。

1. 搜索Blob **GC** Mbean并单击它。

1. 单击链 `checkConsistency()` 接。

一致性检查完成后，将显示报告为缺失的二进制文件数。 如果数字大于0，请查看，以了解 `error.log` 有关缺失二进制文件的更多详细信息。

在下面，您将在日志中找到如何报告缺少的二进制文件的示例：

```xml
11:32:39.673 INFO [main] MarkSweepGarbageCollector.java:600 Consistency check found [1] missing blobs
```

```xml
11:32:39.673 WARN [main] MarkSweepGarbageCollector.java:602 Consistency check failure in the blob store : DataStore backed BlobStore [org.apache.jackrabbit.oak.plugins.blob.datastore.OakFileDataStore], check missing candidates in file /tmp/gcworkdir-1467352959243/gccand-1467352959243
```

