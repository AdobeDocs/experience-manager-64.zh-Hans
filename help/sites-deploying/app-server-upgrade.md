---
title: 应用程序服务器安装的升级步骤
seo-title: Upgrade Steps for Application Server Installations
description: 了解如何升级通过应用程序服务器部署的AEM实例。
seo-description: Learn how to upgrade instances of AEM that are deployed via Application Servers.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Upgrading
exl-id: 1c72093e-82c8-49ad-bd3c-d61904aaab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# 应用程序服务器安装的升级步骤{#upgrade-steps-for-application-server-installations}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本节介绍为更新AEM for Application Server安装而需要遵循的过程。

此过程中的所有示例都使用JBoss作为应用程序服务器，这意味着您已经部署了AEM的工作版本。 此过程用于记录从 **AEM版本5.6至6.3**.

1. 首先，启动JBoss。 在大多数情况下，您可以通过运行 `standalone.sh` 启动脚本，通过从终端运行此命令：

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. 如果已部署AEM 5.6，请通过运行以下命令来检查包是否正常运行：

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. 接下来，取消部署AEM 5.6:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. 停止JBoss。

1. 现在，使用crx2oak迁移工具迁移存储库：

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >在本例中， oak-repository是新转换的存储库所在的临时目录。 在执行此步骤之前，请确保您具有最新的crx2oak.jar版本。

1. 通过执行以下操作，删除sling.properties文件中的必需属性：

   1. 打开位于 `crx-quickstart/launchpad/sling.properties`
   1. 步骤文本删除以下属性并保存文件：

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. 删除不再需要的文件和文件夹。 您需要具体删除的项目包括：

   * 的 **launchpad/startup文件夹**. 您可以通过在终端中运行以下命令来删除它： `rm -rf crx-quickstart/launchpad/startup`
   * 的 **base.jar文件**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * 的 **BootstrapCommandFile_timestamp.txt文件**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. 将新迁移的区段存储复制到其适当位置：

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. 还复制数据存储：

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. 接下来，您需要创建包含将与新升级实例一起使用的OSGi配置的文件夹。 更具体地说，需要在下创建名为install的文件夹 **crx-quickstart**.

1. 现在，创建将与AEM 6.3一起使用的节点存储和数据存储。为此，您可以通过在 **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   这两个文件将配置AEM以使用TarMK节点存储和文件数据存储。

1. 编辑配置文件以使其可供使用。 更具体地说：

   * 将以下行添加到 **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * 然后，将以下行添加到 **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. 通过运行以下命令删除crx2运行模式：

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. 现在，您需要更改AEM 6.3战争文件中的运行模式。 为此，首先创建一个临时文件夹，该文件夹将容纳AEM 6.3战争。 此示例中文件夹的名称将为 **临时**. 复制war文件后，通过从temp文件夹内运行来提取其内容：

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. 提取内容后，转到 **WEB-INF** 文件夹和编辑 `web.xml` 文件来更改运行模式。 要查找在XML中设置它们的位置，请查找 `sling.run.modes` 字符串。 找到该代码后，请更改下一行代码中的运行模式，该代码默认设置为创作：

   ```shell
   <param-value >author</param-value>
   ```

1. 将上述创作值更改为，并将运行模式设置为：author，crx3,crx3tar最终代码块应当如下所示：

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. 使用修改后的内容重新创建jar:

   ```shell
   jar cvf aem62.war
   ```

1. 最后，部署新的战争文件：

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```
