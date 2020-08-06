---
title: 存储6.4中的元素
seo-title: 存储6.4中的元素
description: 了解AEM 6.4中提供的节点存储实现以及如何维护存储库。
seo-description: 了解AEM 6.4中提供的节点存储实现以及如何维护存储库。
uuid: 3b018830-c42e-48e0-9b6f-cd230b02d914
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0aa2c22f-32bb-4e50-8328-63ed73c0f19e
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
translation-type: tm+mt
source-git-commit: 02aee2202a570320cd7eb40c2e566d886af4e163
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 1%

---


# 存储6.4中的元素{#storage-elements-in-aem}

本文将介绍：

* [AEM 6中的存储概述](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [维护存储库](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## AEM 6中的存储概述 {#overview-of-storage-in-aem}

AEM 6中最重要的变化之一是存储库级别的创新。

目前，AEM6中提供两个节点存储实现： Tar存储和MongoDB存储。

### 焦油存储 {#tar-storage}

#### 使用Tar存储运行新安装的AEM实例 {#running-a-freshly-installed-aem-instance-with-tar-storage}

>[!CAUTION]
>
>“区段”节点存储的PID已从org.apache.jackrabbit.oak更改。**plugins**.segment.SegmentNodeStoreService在AEM 6的先前版本中连接到AEM 6.3中的org.apache.jackrabbit.oak.segment.SegmentNodeStoreService。请确保进行必要的配置调整以反映此更改。

默认情况下，AEM 6使用Tar存储存储节点和二进制文件，使用默认配置选项。 要手动配置其存储设置，请按照以下步骤操作：

1. 下载AEM 6快速入门jar并将其放在新文件夹中。
1. 通过运行来解析AEM:

   `java -jar cq-quickstart-6.jar -unpack`

1. 在安装目录中 `crx-quickstart\install` 创建名为的文件夹。

1. 在新创建的文 `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg` 件夹中创建一个名为的文件。

1. 编辑文件并设置配置选项。 区段节点存储提供以下选项，它是AEM Tar存储实施的基础：

   * `repository.home`: 存储各种存储库相关数据的存储库主目录的路径。 默认情况下，段文件将存储在crx-quickstart/segmentstore目录下。
   * `tarmk.size`: 段的最大大小(MB)。 默认为256MB。

1. 开始AEM。

### 蒙戈存储 {#mongo-storage}

#### 使用Mongo存储运行新安装的AEM实例 {#running-a-freshly-installed-aem-instance-with-mongo-storage}

可以按照以下过程将AEM 6配置为使用MongoDB存储运行：

1. 下载AEM 6快速入门jar并将它放入一个新文件夹。
1. 通过运行以下命令解压AEM:

   `java -jar cq-quickstart-6.jar -unpack`

1. 确保已安装MongoDB并且正在运行 `mongod` 实例。 有关详细信息，请参 [阅安装MongoDB](https://docs.mongodb.org/manual/installation/)。
1. 在安装目录中 `crx-quickstart\install` 创建名为的文件夹。
1. 通过使用要在目录中使用的配置名称创建配置文件来配置节点存储 `crx-quickstart\install` 区。

   文档节点存储(它是AEM MongoDB存储实现的基础)使用名为 `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.cfg`

1. 编辑文件并设置配置选项。 以下选项可供选择：

   * `mongouri`: 连接 [到](https://docs.mongodb.org/manual/reference/connection-string/) Mongo数据库所需的MongoURI。 默认为 `mongodb://localhost:27017`
   * `db`: Mongo数据库的名称。 默认情况下，新的AEM 6安 **装使用aem** -author作为数据库名称。
   * `cache`: 缓存大小(MB)。 它分布于DocumentNodeStore中使用的各种缓存中。 默认为 256。
   * `changesSize`: Mongo中用于缓存差异输出的已封闭集合的大小(MB)。 默认为 256。
   * `customBlobStore`: 指示将使用自定义数据存储的布尔值。 默认值为false。

1. 创建一个配置文件，其中包含您要使用的数据存储的PID，并编辑该文件以设置配置选项。 有关详细信息，请参 [阅配置节点存储和数据存储](/help/sites-deploying/data-store-config.md)。

1. 通过运行以下开始AEM 6 jar和MongoDB存储后端：

   ```shell
   java -jar cq-quickstart-6.jar -r crx3,crx3mongo
   ```

   后端 **`-r`** 运行模式位于何处。 在此示例中，它将开始MongoDB支持。

#### 禁用透明大页面 {#disabling-transparent-huge-pages}

Red Hat Linux使用一种称为“透明大页”(THP)的内存管理算法。 AEM执行细粒度的读写时，THP针对大操作进行了优化。 因此，建议您在Tar和Mongo存储上禁用THP。 要禁用算法，请执行以下步骤：

1. 在您选择的 `/etc/grub.conf` 文本编辑器中打开文件。
1. 将以下代码行添 **加到grub.conf** 文件：

   ```
   transparent_hugepage=never
   ```

1. 最后，通过运行以检查设置是否生效：

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   如果禁用了THP，则上述命令的输出应为：

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>此外，您还可以参考以下资源：
>
>* 有关Red Hat Linux上透明大页的详细信息，请参阅本 [文](https://access.redhat.com/solutions/46111)。
>* 有关Linux调整提示，请参阅 [本文](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)。

>



## 维护存储库 {#maintaining-the-repository}

对存储库的每次更新都会创建新内容修订。 因此，每次更新时，存储库的大小都会增大。 为避免存储库增长失控，需要清理旧的修订以释放磁盘资源。 此维护功能称为修订清理。 修订清除机制将通过从存储库中删除过时的数据来回收磁盘空间。 有关“修订清理”的更多详细信息，请阅 [读“修订清理”页](/help/sites-deploying/revision-cleanup.md)。
