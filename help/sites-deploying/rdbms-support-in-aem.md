---
title: AEM 6.4中的RDBMS支持
seo-title: AEM 6.4中的RDBMS支持
description: 了解AEM 6.4中的关系数据库持久性支持以及可用的配置选项。
seo-description: 了解AEM 6.4中的关系数据库持久性支持以及可用的配置选项。
uuid: 599d3e61-99eb-4a1c-868b-52b20a615500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 56a984a5-4b7f-4a95-8a17-95d2d355bfed
feature: Configuring
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---


# AEM 6.4{#rdbms-support-in-aem}中的RDBMS支持

## 概述 {#overview}

使用文档 Microkernel实现了AEM中对关系数据库持久性的支持。 文档 Microkernel是实现MongoDB持久性的基础。

它包含一个基于Mongo Java API的Java API。 还提供了BlobStore API的实现。 默认情况下，blob存储在数据库中。

有关实施详细信息，请参阅[RDBDocumentStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBDocumentStore.html)和[RDBBlobStore](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/oak/plugins/document/rdb/RDBBlobStore.html)文档。

>[!NOTE]
>
>还提供对&#x200B;**PostgreSQL 9.4**&#x200B;的支持，但仅用于演示目的。 它不适用于生产环境。

## 支持的数据库{#supported-databases}

有关AEM中关系型数据库支持级别的详细信息，请参阅[技术要求页](/help/sites-deploying/technical-requirements.md)。

## 配置步骤{#configuration-steps}

通过配置`DocumentNodeStoreService` OSGi服务创建存储库。 除了MongoDB外，它还扩展为支持关系数据库持久性。

要使其正常工作，需要使用AEM配置数据源。 可通过`org.apache.sling.datasource.DataSourceFactory.config`文件执行此操作。 各个数据库的JDBC驱动程序需要作为OSGi绑定在本地配置中单独提供。

有关为JDBC驱动程序创建OSGi包的步骤，请参阅Apache Sling网站上的此[文档](https://wiki.eclipse.org/Create_and_Export_MySQL_JDBC_driver_bundle)。

>[!NOTE]
>
>某些SQL驱动程序已打包为OSGi包。
>
>如果是这种情况，只需将jar文件复制到install-path/crx-quickstart/install/9。

部署好这些包后，请按照以下步骤配置AEM以保持RDB持久性：

1. 确保数据库守护程序已启动，并且您有一个活动数据库供AEM使用。
1. 将AEM 6.3 jar复制到安装目录中。
1. 在安装目录中创建一个名为`crx-quickstart\install`的文件夹。
1. 通过在`crx-quickstart\install`目录中创建具有以下名称的配置文件，配置文档节点存储：

   * `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. 通过在`crx-quickstart\install`文件夹中创建另一个具有以下名称的配置文件，配置数据源和JDBC参数：

   * `org.apache.sling.datasource.DataSourceFactory-oak.config`
   >[!NOTE]
   >
   >有关每个支持的数据库的数据源配置的详细信息，请参阅[数据源配置选项](/help/sites-deploying/rdbms-support-in-aem.md#data-source-configuration-options)。

1. 接下来，准备要与AEM一起使用的JDBC OSGi包：

   1. 从https://dev.mysql.com/downloads/connector/j/下载ZIP存档
      * 版本必须>= 5.1.38
   1. 从存档解压`mysql-connector-java-version-bin.jar`(bundle)
   1. 使用Web控制台安装并开始捆绑包：
      * 转到&#x200B;*http://serveraddress:serverport/system/console/bundles*
      * 选择&#x200B;**安装/更新**
      * 浏览到从下载的ZIP存档中提取的包
      * 检查&#x200B;**Oracle Corporation的MySQLcom.mysql.jdbc**&#x200B;的JDBC驱动程序是否处于活动状态，并开始它。

1. 最后，将AEM与`crx3`和`crx3rdb`运行模式开始:

   ```java
   java -jar quickstart.jar -r crx3,crx3rdb
   ```

## 数据源配置选项{#data-source-configuration-options}

`org.apache.sling.datasource.DataSourceFactory-oak.config` OSGi配置用于配置AEM与数据库持久层之间通信所需的参数。

以下配置选项可用：

* `datasource.name:` 数据源名称。默认为 `oak`.

* `url:` 需要与JDBC一起使用的数据库的URL字符串。每个数据库类型都有其自己的URL字符串格式。 有关详细信息，请参阅下面的[URL字符串格式](/help/sites-deploying/rdbms-support-in-aem.md#url-string-formats)。

* `driverClassName:` JDBC驱动程序类名。这会因您要使用的数据库而有所不同，随后还会因连接到数据库所需的驱动程序而有所不同。 以下是AEM支持的所有数据库的类名：

   * `org.postgresql.Driver` for PostgreSQL;
   * `com.ibm.db2.jcc.DB2Driver` DB2;
   * `oracle.jdbc.OracleDriver` oracle;
   * `com.mysql.jdbc.Driver` （针对MySQL和MariaDB）；
   * c `om.microsoft.sqlserver.jdbc.SQLServerDriver` for Microsoft SQL Server（实验）。

* `username:` 数据库运行时使用的用户名。

* `password:` 数据库密码。

### URL字符串格式{#url-string-formats}

在数据源配置中，会根据需要使用的数据库类型使用不同的URL字符串格式。 以下是AEM当前支持的数据库的格式列表:

* `jdbc:postgresql:databasename` for PostgreSQL;

* `jdbc:db2://localhost:port/databasename` DB2;
* `jdbc:oracle:thin:localhost:port:SID` oracle;
* `jdbc:mysql://localhost:3306/databasename` （针对MySQL和MariaDB）；

* `jdbc:sqlserver://localhost:1453;databaseName=name` （实验）。

## 已知限制{#known-limitations}

虽然RDBMS持久性支持将多个AEM实例与单个数据库同时使用，但并发安装不支持。

要解决此问题，请确保先使用单个成员运行安装，并在完成安装后添加其他成员。

