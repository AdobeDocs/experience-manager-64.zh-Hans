---
title: 自定义独立安装
seo-title: Custom Standalone Install
description: 了解安装独立AEM实例时可用的选项。
seo-description: Learn about the options available when installing a standalone AEM instance.
uuid: e1cb45c4-3b2b-4951-8f67-213072e825b3
contentOwner: Tyler Rushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c9e51008-6009-49a2-9c74-1c610cef2e7f
exl-id: 0933f733-50bf-48ae-a5da-be5dc9335253
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# 自定义独立安装{#custom-standalone-install}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本节介绍在安装独立AEM实例时可用的选项。 您还可以阅读 [存储元素](/help/sites-deploying/storage-elements-in-aem-6.md) 有关在全新安装AEM 6后选择后端存储类型的更多信息。

## 通过重命名文件来更改端口号 {#changing-the-port-number-by-renaming-the-file}

AEM的默认端口为4502。 如果该端口不可用或已在使用中，快速启动会自动将其自身配置为使用第一个可用端口号，如下所示：4502、8080、8081、8082、8083、8084、8085、8888、9362、 `<random>`.

您也可以通过重命名快速入门jar文件来设置端口号，以便文件名包含端口号；例如， `cq5-publish-p4503.jar` 或 `cq5-author-p6754.jar`.

重命名快速入门Jar文件时，需遵循各种规则：

* 重命名文件时，必须以开头 `cq;` as in `cq5-publish-p4503.jar`.

* 建议您 *always* 为端口号添加前缀 — p;与在cq5-publish-p4503.jar或cq5-author-p6754.jar中一样。

>[!NOTE]
>
>这是为了确保您无需担心是否填写用于提取端口号的规则：
>
>* 端口号必须为4位或5位
>* 这些数字必须在短划线后
>* 如果文件名中有任何其他位数，则端口号必须带前缀 `-p`
>* 文件名开头的“cq5”前缀会被忽略
>


>[!NOTE]
>
>您还可以使用 `-port` 选项。

## 运行模式 {#run-modes}

**运行模式** 允许您针对特定目的调整AEM实例；例如，创作或发布、测试、开发、内联网等。 这些模式还允许您控制示例内容的使用。 此示例内容在构建快速入门之前定义，可以包含包、配置等。 当您希望保持安装精简且不含示例内容时，这对于生产就绪型安装特别有用。 有关更多信息，请参阅：

* [运行模式](/help/sites-deploying/configure-runmodes.md)

## 添加文件安装提供程序 {#adding-a-file-install-provider}

默认情况下，文件夹 `crx-quickstart/install` 监视文件。\
此文件夹不存在，但只能在运行时创建。

如果将包、配置或内容包放入此目录中，则会自动选取并安装该包。 如果删除了，则会将其卸载。\
这是将包、内容包或配置放入存储库的另一种方法。

这对于以下几个用例特别有趣：

* 在开发过程中，将某些内容放入文件系统可能会比较容易。
* 如果出现问题，则无法访问Web控制台和存储库。 通过此目录，您可以将其他包放入此目录中，并且应该安装这些包。
* 的 `crx-quickstart/install` 可以在启动快速入门之前创建文件夹，并可将其他包放置到此处。

>[!NOTE]
>
>另请参阅 [如何在服务器启动时自动安装CRX包](https://helpx.adobe.com/experience-manager/kb/HowToInstallPackagesUsingRepositoryInstall.html) 。

## 安装和启动Adobe Experience Manager as a Windows Service {#installing-and-starting-adobe-experience-manager-as-a-windows-service}

>[!NOTE]
>
>在以管理员身份登录时，请务必执行以下步骤，或使用 **以管理员身份运行** 上下文菜单选择。
>
>以具有管理员权限的用户身份登录的情况是 **不足**. 如果您在完成这些步骤时未以管理员身份登录，则会收到 **拒绝访问** 错误。

要安装AEM as a Windows服务并启动，请执行以下操作：

1. 在文本编辑器中打开crx-quickstart\opt\helpers\instsrv.bat文件。
1. 如果要配置64位Windows服务器，请根据您的操作系统，将prunsrv的所有实例替换为以下命令之一：

   * prunsrv_amd64
   * prunsrv_ia64

   此命令将调用相应的脚本，该脚本将在64位Java而不是32位Java中启动Windows服务守护程序。

1. 要阻止进程进入多个进程，请增加最大堆大小和PermGen JVM参数。 找到 `set jvm_options` 命令并设置值，如下所示：

   `set jvm_options=-XX:MaxPermSize=256M;-Xmx1792m`

1. 打开命令提示符，将当前目录更改为AEM安装的crx-quickstart/opt/helpers文件夹，然后输入以下命令以创建服务：

   `instsrv.bat cq5`

   要验证是否已创建服务，请在“管理工具”控制面板中打开“服务”，或键入 `start services.msc` 在命令提示符下。 cq5服务将显示在列表中。

1. 通过执行以下操作之一来启动服务：

   * 在“服务”控制面板中，单击cq5，然后单击“开始”。

   ![chlimage_1-71](assets/chlimage_1-71.png)

   * 在命令行中，键入net start cq5。

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Windows表示服务正在运行。 AEM启动，并且任务管理器中会显示prunsrv可执行文件。 在Web浏览器中，导航到AEM，例如 `http://localhost:4502` 开始使用AEM。

   ![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>创建Windows服务时，将使用instsrv.bat文件中的属性值。 如果在instsrv.bat中编辑属性值，则必须卸载并重新安装服务。

>[!NOTE]
>
>安装AEM as service时，必须在 `com.adobe.xmp.worker.files.ncomm.XMPFilesNComm` 从配置管理器。

要卸载服务，请单击 **停止** 在 **服务** 控制面板或在命令行中，导航到文件夹并键入 `instsrv.bat -uninstall cq5`. 该服务将从 **服务** 控制面板或在键入 `net start`.

## 重新定义临时工作目录的位置 {#redefining-the-location-of-the-temporary-work-directory}

Java计算机临时文件夹的默认位置为 `/tmp`. AEM也使用此文件夹，例如在生成包时。

如果要更改临时文件夹的位置（例如，如果需要具有更多可用空间的目录），请定义 `<new-tmp-path>` 通过添加JVM参数：

`-Djava.io.tmpdir="/<new-tmp-path>"`

至以下任一项：

* 服务器启动命令行
* serverctl或start脚本中的CQ_JVM_OPTS环境参数

## 快速入门文件中提供的其他选项 {#further-options-available-from-the-quickstart-file}

快速入门帮助文件中介绍了更多选项和重命名约定，该文件可通过 — help选项获取。 要访问帮助，请键入：

* `java -jar cq5-<version>.jar -help`

```shell
Loading quickstart properties: default
Loading quickstart properties: instance
Setting properties from filename '/Users/Desktop/AEM/cq-quickstart-5.6.0.jar'
--------------------------------------------------------------------------------
Adobe Experience Manager Quickstart (build 20130129)                            
--------------------------------------------------------------------------------
Usage:                                                                          
 Use these options on the Quickstart command line.                              
--------------------------------------------------------------------------------

-help (--help,-h)
         Show this help message                                                 
-quickstart.server.port (-p,-port) <port>
         Set server port number                                                 
-contextpath (-c,-org.apache.felix.http.context_path) <contextpath>
         Set context path                                                       
-debug <port>
         Enable Java Debugging on port number; forces forking                   
-gui 
         Show GUI if running on a terminal                                      
-nobrowser (-quickstart.nobrowser)
         Do not open browser at startup                                         
-unpack
         Unpack installation files only, do not start the server (implies       
         -verbose)                                                              
-v (-verbose)
         Do not redirect stdout/stderr to files and do not close stdin          
-nofork
         Do not fork the JVM, even if not running on a console                  
-fork
         Force forking the JVM if running on a console, using recommended       
         default memory settings for the forked JVM.                            
-forkargs <args> [<args> ...]
         Additional arguments for the forked JVM, defaults to '-Xmx1024m        
         -XX:MaxPermSize=256m '.  Use -- to specify values starting with -,     
         example: '-forkargs -- -server'                                        
-a (--interface) <interface>
         Optional IP address (interface) to bind to                             
-pt <string>
         Process type (main/fork) - do not use directly, used when forking a    
         process                                                                
-r <string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string>]]]]]]]]]
         Runmode(s) - Use this to define the run mode(s)                        
-b <string>
         Base folder - defines the path under which the quickstart work folder  
         is created                                                             
-low-mem-action <string>
         Low memory action - what to do if memory is insufficient at startup    
-use-control-port
         Start a control port                                                   
-ll <level>
         Define launchpad log level (1 = error...4 = debug)                     
--------------------------------------------------------------------------------
Quickstart filename options                                                     
--------------------------------------------------------------------------------
Usage:                                                                          
 Rename the jar file, including one of the patterns shown below, to set the     
corresponding option. Command-line options have priority on these filename      
patterns.                                                                       
--------------------------------------------------------------------------------

-NNNN
         Include -NNNN.jar or -pNNNN in the renamed jar filename to run on port 
         NNNN, for example: quickstart-8085.jar                                 
-nobrowser
         Include -nobrowser in the renamed jar filename to avoid opening the    
         browser at startup, example: quickstart-nobrowser-8085.jar             
-publish
         Include -publish in the renamed jar filename to run cq5 in "publish"   
         mode, example: cq5-publish-7502.jar                                    
--------------------------------------------------------------------------------
The license.properties file
--------------------------------------------------------------------------------
  The license.properties file stores licensing information, created from the    
  licensing form displayed on first startup and stored in the folder from where 
  Quickstart is run.                                                            
--------------------------------------------------------------------------------
Log files
--------------------------------------------------------------------------------
  Once Quickstart has been unpacked and started, log files can be found under   
  ./crx-quickstart/logs.                                                        
--------------------------------------------------------------------------------
```

## 在Amazon EC2环境中安装AEM {#installing-aem-in-the-amazon-ec-environment}

在Amazon Elastic Compute Cloud(EC2)实例上安装AEM时，如果在EC2实例上同时安装作者和发布，则按照有关如何 [安装AEM实例](/help/sites-deploying/custom-standalone-install.md);但是，发布实例将变为“作者”。

在EC2环境中安装Publish实例之前，请执行以下操作：

1. 首次启动实例之前，解压缩Publish实例的jar文件。 要解压缩文件，请使用以下命令：

   ```xml
   java -jar quickstart.jar -unpack
   ```

   >[!NOTE]
   >
   >如果更改模式 **after** 首次启动实例时，无法更改运行模式。

1. 通过运行以启动实例：

   ```xml
   java -jar quickstart.jar -r publish
   ```

   >[!CAUTION]
   >
   >请确保首先运行上述命令，在解压实例后运行该实例。 否则，将不会生成quickstart.properties填充。 如果没有此文件，任何将来的AEM升级都将失败。

1. 在 **宾** 文件夹，打开 **开始** 脚本并检查以下部分：

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='author'
   fi
   ```

1. 将运行模式更改为 **发布** 并保存文件。

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='publish'
   fi
   ```

1. 停止实例并通过运行 **开始** 脚本。

## 验证安装 {#verifying-the-installation}

以下链接可用于验证安装是否可操作（所有示例均基于实例在localhost的端口8080上运行，CRX安装在/crx和/下的Launchpad下）：

* `http://localhost:8080/crx/de`

   CRXDE Lite控制台。

* `http://localhost:8080/system/console`

   Web控制台。

## 安装后的操作 {#actions-after-installation}

尽管配置AEM WCM有许多可能性，但是应该执行某些操作，或至少在安装后立即进行审核：

* 请查阅 [安全检查列表](/help/sites-administering/security-checklist.md) 执行确保系统安全所需的任务。
* 查看随AEM WCM一起安装的默认用户和组列表。 检查您是否要对任何其他帐户执行操作 — 请参阅 [安全和用户管理](/help/sites-administering/security.md) 以了解更多详细信息。

## 访问CRXDE Lite和Web控制台 {#accessing-crxde-lite-and-the-web-console}

启动AEM WCM后，您还可以访问：

* [CRXDE Lite](#accessing-crxde-lite)  — 用于访问和管理存储库
* [Web控制台](#accessing-the-web-console)  — 用于管理或配置OSGi包（也称为OSGi控制台）

### 访问CRXDE Lite {#accessing-crxde-lite}

要打开CRXDE Lite，您可以选择 **CRXDE Lite** 从欢迎屏幕中，或使用您的浏览器导航到

```
 https://<<i>host</i>>:<<i>port</i>>/crx/de/index.jsp
```

例如：\
`http://localhost:4502/crx/de/index.jsp` ``

![installcq_crxdelite](assets/installcq_crxdelite.png)

### 访问Web控制台 {#accessing-the-web-console}

要访问Adobe CQ Web控制台，您可以选择 **OSGi控制台** 从欢迎屏幕中，或使用您的浏览器导航到

```
 https://<<i>host</i>>:<<i>port</i>>/system/console
```

例如：\
`http://localhost:4502/system/console`\
或“包”页面\
`http://localhost:4502/system/console/bundles`

![chlimage_1-74](assets/chlimage_1-74.png)

请参阅 [使用Web控制台进行OSGi配置](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) 以了解更多详细信息。

## 疑难解答 {#troubleshooting}

有关处理安装过程中可能出现的问题的信息，请参阅：

* [疑难解答](/help/sites-deploying/troubleshooting.md)

## 卸载Adobe Experience Manager {#uninstalling-adobe-experience-manager}

由于AEM安装到单个目录中，因此无需卸载实用程序。 卸载操作与删除整个安装目录一样简单，不过卸载AEM的方式取决于您要实现的内容以及您使用的永久存储。

如果永久存储嵌入在安装目录中，例如，在默认的TarPM安装中，删除文件夹也会删除数据。

>[!NOTE]
>
>Adobe强烈建议您在删除AEM之前备份存储库。 如果删除整个 &lt;cq-installation-directory>，则会删除存储库。 要在删除、移动或复制 &lt;cq-installation-directory>/crx-quickstart/repository文件夹（在删除其他文件夹之前）。

如果您的AEM安装使用外部存储（例如，数据库服务器），则删除文件夹不会自动删除数据，但会删除存储配置，这会使恢复JCR内容变得困难。
