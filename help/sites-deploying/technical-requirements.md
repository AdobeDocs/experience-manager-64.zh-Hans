---
title: 技术要求
seo-title: 技术要求
description: AEM支持的客户端和服务器平台列表。
seo-description: AEM支持的客户端和服务器平台列表。
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3271'
ht-degree: 2%

---

# 技术要求{#technical-requirements}

Adobe在平台上支持Adobe Experience Manager(AEM)，如本文档中的以下信息所述。

对于任何与平台本身特别相关的问题，请直接与平台供应商联系。

>[!NOTE]
>
>根据您安装AEM的平台，用户管理要求可能会有不同的组。

## 前提条件 {#prerequisites}

安装Adobe Experience Manager的最低要求：

* 已安装的Java平台、标准版JDK或其他受支持的[Java虚拟机](#java-virtual-machines)
* Experience Manager快速入门文件（独立JAR或Web应用程序部署WAR）

### 最小大小调整要求{#minimum-sizing-requirements}

运行Adobe Experience Manager的最低要求：

* 安装目录中有5 GB可用磁盘空间
* 2 GB内存

>[!NOTE]
>
>* 数字资产用例需要更多基本内存。 有关详细信息，请参阅[部署和维护](/help/sites-deploying/deploy.md#default-local-install)。
>* [AEM Forms附加组](/help/forms/using/installing-configuring-aem-forms-osgi.md) 件包需要15 GB的临时空间。

>



有关详细信息，请参阅[硬件大小调整指南](/help/managing/hardware-sizing-guidelines.md)。

### 支持级别{#support-levels}

本文档列出了Adobe Experience Manager支持的客户端和服务器平台。 Adobe为建议的配置和其他配置提供了多个级别的支持。

### 支持的配置{#supported-configurations}

Adobe建议这些配置，并作为标准软件维护协议的一部分提供完全支持。

<table> 
 <tbody> 
  <tr> 
   <td>支持级别</td> 
   <td>描述<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>答：支持</strong></td> 
   <td>Adobe对此配置提供完全支持和维护。 此配置由Adobe的质量保证流程涵盖。</td> 
  </tr> 
  <tr> 
   <td><strong>R:受限支持</strong></td> 
   <td>为确保客户项目成功，Adobe在受限支持计划中提供全面支持，该计划要求满足特定条件。 R级支持需要正式的客户请求和Adobe确认。 有关更多信息，请联系Adobe客户关怀团队。</td> 
  </tr> 
 </tbody> 
</table>

### 不支持的配置{#unsupported-configurations}

| 支持级别 | 描述 |
|---|---|
| **Z:不支持** | 不支持配置。 Adobe不会就配置是否正常进行任何声明，也不支持配置。 |

## 支持的平台 {#supported-platforms}

### Java虚拟机{#java-virtual-machines}

应用程序需要运行Java虚拟机，该虚拟机由Java开发工具包(JDK)分发提供。

Adobe Experience Manager使用以下版本的Java虚拟机：

>[!CAUTION]
>
>建议跟踪Java供应商提供的安全公告，以确保生产环境的安全和安全，并安装最新的Java更新。

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>支持级别<br /> </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 11 JDK [1]</td> 
   <td>Z:不支持 </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 10 JDK [1]</td> 
   <td>Z:不支持 </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 9 JDK [1]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td><strong>OracleJava SE 8 JDK - 64位</strong></td> 
   <td>答：支持的[3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM — 内部版本2.9,JRE 1.8.0 [2]</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM — 内部版本2.8,JRE 1.8.0 [2]</td> 
   <td>答：支持</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle 已经转向 Oracle Java SE 产品的“长期支持”(LTS) 模型。Java 9和10是按Oracle划分的非LTS版本(请参阅[OracleJava SE支持路线图](https://www.oracle.com/technetwork/java/eol-135779.html))。 Adobe 将只为 LTS 版本的 Java 提供支持，以便在生产环境中运行 AEM。

1. IBM JRE仅与WebSphere Application Server一起支持。
1. Adobe将直接为所有使用OracleJava SE技术的AEM客户支持和分发OracleJava SE JDK，包括公共更新结束后对LTS版本进行的所有维护更新。 有关更多信息，请参阅[OracleAdobe Experience Manager Q&amp;A](assets/adobe-oracle-java-license-agreement.pdf)的Java支持。

### 存储和持久性{#storage-persistence}

部署Adobe Experience Manager存储库时存在多种选项。 有关支持的技术和存储选项，请参阅以下列表。

<table> 
 <tbody> 
  <tr> 
   <td><strong>平台</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>支持级别</strong></td> 
  </tr> 
  <tr> 
   <td><strong>具有TAR文件[1]的文件系统</strong></td> 
   <td>存储库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td><strong>具有数据存储[1]的文件系统</strong></td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>将二进制文件存储在文件系统[1]的TAR文件中</td> 
   <td>二进制文件</td> 
   <td>Z:不支持生产</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob Storage</td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>存储库</td> 
   <td>答：受支持，但有限制</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>存储库</td> 
   <td>答：受支持，但有限制</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Forms数据库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Forms数据库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>存储库和Forms数据库</td> 
   <td>R:限制支持(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle数据库12c(12.1.x)</td> 
   <td>存储库和Forms数据库</td> 
   <td>R:受限支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Forms数据库</td> 
   <td>Z:不支持(4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Forms数据库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Forms数据库</td> 
   <td>R:限制支持(4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene（Quickstart内置）</strong></td> 
   <td>搜索服务</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>搜索服务</td> 
   <td>答：支持</td> 
  </tr> 
 </tbody> 
</table>

1. “文件系统”包括符合POSIX的块存储。 这包括网络存储技术。 请注意，文件系统性能可能会有所不同，并会影响整体性能。 建议将测试AEM与网络/远程文件系统结合加载。
1. AEM不支持MongoDB Sharding。
1. 仅支持MongoDB Storage Engine WiredTiger。
1. 不支持AEM Forms。
1. 从 AEM 版本 6.4.2.0 开始，支持 MongoDB Enterprise 3.6。
1. 对MongoDB 3.4的支持已终止(EOL)，而MongoDB 3.6预计将于2021年4月30日达到EOL。 请注意，Adobe将仅对今后的AEM产品相关问题提供支持。

>[!NOTE]
>
>有关AEM Communities功能的其他信息，请参阅[部署Communities](/help/communities/deploy-communities.md) 。

>[!NOTE]
>
>MongoDB是第三方软件，未包含在AEM授权包中。 有关详细信息，请参阅[MongoDB授权策略](https://www.mongodb.org/about/licensing/)页。
>
>为了充分利用MongoDB的AEM部署，Adobe建议授权MongoDB企业版，以便从专业支持中受益。 有关更多信息，请参阅[推荐的部署](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) 。
>
>该许可证包含一个标准副本集，该副本集由一个主实例和两个辅助实例组成，这两个实例可用于创作或发布部署。
>
>如果您希望在MongoDB上同时运行创作和发布，则需要购买两个单独的许可证。
>
>Adobe客户关怀团队将协助确定与将MongoDB与AEM结合使用相关的问题。
>
>有关更多信息，请参阅[MongoDB for Adobe Experience Manager页面](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)。

>[!NOTE]
>
>上面列出的受支持的关系数据库是第三方软件，不包含在AEM授权包中。
>
>为了使用受支持的关系数据库运行AEM 6.4，需要与数据库供应商签订单独的支持合同。 Adobe客户关怀团队将帮助确定与AEM 6.4中的关系数据库的使用相关的问题。
>
>**请注意，AEM 6.4的Level-R中当前支持大多数关系数据库，Level-R中附带支持标准和支持计划，如上面Level-R描述中所述。**

### Servlet引擎/应用程序服务器{#servlet-engines-application-servers}

Adobe Experience Manager可以作为独立服务器（快速入门JAR文件）运行，也可以作为第三方应用程序服务器（WAR文件）中的Web应用程序运行。

所需的Servlet API最低版本为Servlet 3.1，但低于Servlet 4.0。

| 平台 | 支持级别 |
|---|---|
| **快速入门内置Servlet引擎(Jetty 9.3)** | 答：支持 |
| OracleWebLogic Server 12.2(12cR2) | 答：支持 |
| IBM WebSphere Application Server Continuous Delivery(LibertyProfile)，带Web Profile 7.0和IBM JRE 1.8 | 答：支持 |
| IBM WebSphere Application Server 9.0 | 答：支持 |
| Apache Tomcat 8.5.x | 答：支持 |
| JBoss EAP 7.1.0，带JBoss应用程序服务器 | 答：支持(1) |
| JBoss EAP 7.0.0，带JBoss应用程序服务器 | 答：支持 |

1. 不支持AEM Forms。

### 服务器操作系统{#server-operating-systems}

Adobe Experience Manager可与以下服务器平台配合使用：

<table> 
 <tbody> 
  <tr> 
   <td><strong>平台</strong></td> 
   <td><strong>支持级别</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux，基于Red Hat分发</strong></td> 
   <td>答：支持(1)</td> 
  </tr> 
  <tr> 
   <td>Linux，基于Debian分发，包括 乌本图</td> 
   <td>答：支持(4)</td> 
  </tr> 
  <tr> 
   <td>Linux，基于SUSE分发</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>OracleSolaris 11</td> 
   <td>答：受限制(3,5,7)<br /> R:限制对新合同的支持</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>答：受限制(2,5,7)<br /> R:限制对新合同的支持</td> 
  </tr> 
 </tbody> 
</table>

1. Linux内核2.6、3.x和4.x包含Red Hat分发版的衍生产品，包括Red Hat Enterprise Linux、CentOS、OracleLinux和Amazon Linux。 AEM Forms附加功能仅在CentOS 7和Red Hat Enterprise Linux 7中受支持。
1. AEM Assets:请参阅[支持XMP元数据回写](#requirements-for-aem-assets-xmp-metadata-write-back)部分
1. AEM Assets:不支持Dynamic Media成像。 Dynamic Media视频受支持。
1. AEM Forms仅在Ubuntu 16.04 LTS上受支持。
1. AEM Assets:不支持[原始文件转换](/help/assets/camera-raw.md)
1. AEM Forms:不支持生产环境
1. AEM Assets:不支持[增强型PDF光栅器](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms:不支持

### 虚拟和云计算环境{#virtual-cloud-computing-environments}

Adobe Experience Manager支持在云计算环境(如Microsoft Azure和Amazon Web Services(AWS))上的虚拟机中运行，以符合本页所列的技术要求，并且符合Adobe的标准支持条款。

Adobe建议使用Adobe Managed Services在Azure或AWS上部署AEM。 Adobe Managed Services为专家提供了在这些云计算环境中部署和操作AEM的经验和技能。 请查看我们关于Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t)的[其他文档。

在Azure或AWS或任何其他云计算环境上部署AEM的所有其他情况中，将根据本页中列出的技术规范，将来自Adobe的支持包含在虚拟计算环境中。 与在任何这些云环境中运行的AEM相关的任何报告问题都需要独立于特定于云计算环境的任何云服务来重现，除非云服务作为本页面上所列技术要求（例如Azure Blob Storage或AWS S3）的一部分得到专门支持。

有关如何在Azure或AWS上部署AEM的建议，我们强烈建议在Adobe托管服务之外直接与云提供商或Adobe合作伙伴合作，在您选择的云环境中支持部署AEM。 选定的云提供商或合作伙伴将负责架构的大小调整规范、设计和实施，以满足您的特定性能、负载、可扩展性和安全要求。

### 调度程序平台（Web服务器）{#dispatcher-platforms-web-servers}

Dispatcher是缓存和负载平衡组件。 [下载最新的Dispatcher版本](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html)。Experience Manager6.4需要Dispatcher版本4.3.1或更高版本。

支持将以下Web服务器与Dispatcher版本4.3.1一起使用：

| 平台 | 支持级别 |
|---|---|
| **Apache httpd 2.4.x** （另请参阅下面的1、2） | 答：支持 |
| Microsoft IIS 10(Internet Information Server) | 答：支持 |
| Microsoft IIS 8.5(Internet Information Server) | 答：支持 |

1. 基于Apache httpd源代码构建的Web服务器将具有与其所基于httpd版本相同的支持级别。 如有疑问，请向Adobe请求确认与相应服务器产品相关的支持级别。 以下情况：

   1. HTTP服务器是仅使用官方的Apache源分发版本构建的，或者
   1. HTTP服务器作为运行该服务器的操作系统的一部分进行传送。 示例：IBM HTTP Server，OracleHTTP Server

1. Dispatcher不适用于适用于Windows操作系统的Apache 2.4.x。

## 支持的客户端平台{#supported-client-platforms}

### 用于创作用户界面的支持浏览器{#supported-browsers-for-authoring-user-interface}

Adobe Experience Manager用户界面适用于以下客户端平台。 所有浏览器均使用一组默认的插件和加载项进行测试。

AEM用户界面针对大屏幕（通常是笔记本电脑和台式计算机）和平板电脑外形（如Apple iPad或Microsoft Surface）进行了优化。 不支持手机外形规格。

>[!NOTE]
>
>**支持发布周期快的浏览器：**
>
>Mozilla Firefox、Google Chrome和Microsoft Edge版本每几个月更新一次。 Adobe承诺提供Adobe Experience Manager更新，以便通过这些浏览器即将推出的版本保持下面所述的支持级别。

<table> 
 <tbody> 
  <tr> 
   <td><strong>浏览器</strong></td> 
   <td><strong>支持UI<br /> </strong></td> 
   <td><strong>支持经典UI</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome(Evergreen)</strong></td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge(Evergreen)</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox(Evergreen)</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox的最后一个ESR [1]</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>macOS上的Apple Safari 12.x</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>macOS上的Apple Safari 11.x</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>macOS上的Apple Safari 10.x</td> 
   <td>答：支持</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>iOS 12.x上的Apple Safari</td> 
   <td>答：支持的[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td>iOS 11.x上的Apple Safari</td> 
   <td>答：支持的[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td>iOS 10.3上的Apple Safari</td> 
   <td>答：支持的[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
 </tbody> 
</table>

1. Firefox的扩展支持版本[在mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)上了解有关此内容的更多信息
1. 支持Apple iPad

### 支持的网站浏览器{#supported-browsers-for-websites}

通常，浏览器对AEM Sites呈现的网站的支持取决于AEM页面模板、设计和组件输出的实施，因此由实施这些部分的一方控制。

### WebDAV客户端{#webdav-clients}

**Microsoft Windows 7+**

要成功与Microsoft Windows 7+连接到未使用SSL保护的AEM实例，必须在Windows中启用基于不安全网络的基本身份验证。 这要求在WebClient的Windows注册表中进行更改：

1. 找到注册表子项：

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 使用值2或更多将BasicAuthLevel注册表项添加到此子项。

请参阅[Microsoft支持KB 841215](https://support.microsoft.com/default.aspx/kb/841215)。

要提高Windows下WebDav客户端的响应性 — 请参阅[Microsoft支持KB 2445570](https://support.microsoft.com/kb/2445570)

## 其他平台说明{#additional-platform-notes}

本节提供有关运行Adobe Experience Manager及其加载项的特殊说明和更多详细信息。

### IPv4和IPv6 {#ipv-and-ipv}

Adobe Experience Manager的所有元素（实例、调度程序）都可以安装在IPv4和IPv6网络中。

操作是无缝的，因为不需要特殊配置。 如有必要，您只需使用适合您的网络类型的格式指定IP地址即可。

这意味着当需要指定IP地址时，您可以（根据需要）从以下位置进行选择：

* IPv6地址

   例如`https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   例如`https://123.1.1.4:4502`

* 服务器名称

   例如，`https://www.yourserver.com:4502`

* 对于IPv4和IPv6网络安装，将解释`localhost`的默认情况

   例如，`http://localhost:4502`

### AEM Dynamic Media附加组件{#requirements-for-aem-dynamic-media-add-on}的要求

AEM Dynamic Media默认处于禁用状态。 请参阅[启用Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media)。

启用Dynamic Media后，将应用以下其他系统要求：
>[!NOTE]
>
>如果您使用Dynamic Media — 混合模式，则以下系统要求仅适用&#x200B;**__**;Dynamic Media — 混合模式具有嵌入式图像服务器，该服务器仅在某些操作系统上获得认证。
>
>对于运行Dynamic Media - Scene7模式（即&#x200B;**dynamicmedia_scene7**&#x200B;运行模式）的Dynamic Media客户，没有其他系统要求；只有与AEM相同的系统要求。 Dynamic Media - Scene7模式架构使用基于云的图像服务，而不是AEM中嵌入的服务。

#### 硬件 {#hardware}

以下硬件要求适用于Linux和Windows操作系统：

* 至少具有4个内核的英特尔至强或AMD皓龙CPU
* 最少16GB RAM

#### Linux {#linux}

在Linux上使用Dynamic Media需要满足以下先决条件：

* RedHat Enterprise 7或CentOS 7及更高版本，带有最新的修补程序
* 64位操作系统
* 禁用交换（建议）
* 已禁用SELinux（请参阅以下注意事项）

>[!NOTE]
>
>如果设置了LC_CTYPE不等于en_US.UTF-8的区域设置，则会阻止Dynamic Media正常工作。 要在命令提示符下查看其值是什么，请键入“locale”。 如果未将其设置为，请在运行AEM之前，通过键入“export LC_CTYPE=”将LC_CTYPE环境变量设置为空字符串。

>[!NOTE]
>
>**禁用SELinux:** 打开SELinux后，“图像提供”功能不起作用。默认情况下，此选项处于启用状态。 要解决此问题，请编辑&#x200B;**/etc/selinux/config**&#x200B;文件，并将SELinux值从：
>
>`SELINUX=enforcing` 到  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA架构：** 带有AMD64和Intel EM64T处理器的系统通常配置为非均匀内存架构(NUMA)平台，这意味着内核在启动时构建多个内存节点，而不是构建单个内存节点。
>
>该多节点构造可导致在其它节点耗尽之前一个或多个节点上的内存耗尽。 当内存耗尽时，内核可能会决定终止进程（例如，图像服务器或平台服务器），即使内存可用。
>
>因此，Adobe建议，如果您运行这样的系统，以便使用&#x200B;**numa=off**&#x200B;引导选项关闭NUMA，以避免内核杀死这些进程。

>[!NOTE]
>
>**服务器的主机名必须可解析：** 确保服务器的主机名可解析为IP地址。如果无法实现，请将完全限定的主机名和IP地址添加到&#x200B;**/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 交换空间至少等于物理内存(RAM)量的两倍

要在Windows上使用Dynamic Media，必须安装适用于x64和x86的Microsoft Visual Studio 2010、2013和2015可再发行版。

x64

* 可在[https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)上找到Microsoft Visual Studio 2010可再发行版本
* 可在[https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)上找到Microsoft Visual Studio 2013可再发行版本
* 可在[https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)上找到Microsoft Visual Studio 2015可再发行版本

x86

* 可在[https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)上找到Microsoft Visual Studio 2010可再发行版本
* 可在[https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)上找到Microsoft Visual Studio 2013可再发行版本
* 可在[https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)上找到Microsoft Visual Studio 2015可再发行版本

#### MacOS {#macos}

* 10.9.x及更高版本
* 仅支持试用和演示目的

### AEM Forms PDF生成器{#requirements-for-aem-forms-pdf-generator}的要求

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>产品</strong></p> </th> 
   <th><p><strong>支持的转换为PDF的格式</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017款经典曲目</a></p> </td> 
   <td><p>XPS，图像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、DWG、DXF和DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC、DOCX、XLS、XLSX、PPT、PPTX、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC、DOCX、XLS、XLSX、PPT、PPTX、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP， WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、XLS、DOC、DOCX、PPT、PPTX、图像格式(BMP、GIF、JPEG、JPG、TIF、PNG、JPX、JP2、J2K、J2C、JPC、RTPC、HTT)、HTM和HTM</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、XLS、DOC、DOCX、PPT、PPTX、图像格式(BMP、GIF、JPEG、JPG、TIF、PNG、JPX、JP2、J2K、J2C、JPC、RTPC、HTT)、HTM和HTM</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF生成器仅支持受支持操作系统和应用程序的英语、法语、德语和日语版本。
>
>此外：
>
>* PDF生成器要求[Acrobat 2017 Classic跟踪版本17.011.30078或更高版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html)才能执行转换。
>* AEM Forms仅支持32位版本的受支持软件。
>* OCR PDF（可搜索的PDF）、Optimize PDF和Export PDF功能仅在Microsoft Windows上受支持。
>* AIX上已弃用HTML2PDF服务。
>* 仅在Windows、Linux和Solaris上支持用于OpenOffice的PDF生成器转换。
>* OCR PDF、Optimize PDF和Export PDF功能仅在Windows上受支持。
>* Acrobat版本与AEM Forms捆绑在一起，以启用PDF生成器功能。 在AEM Forms许可证有效期内，捆绑版本只应通过AEM Forms以编程方式访问，以便与AEM Forms PDF生成器一起使用。 有关更多信息，请参阅根据您的部署([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)或[Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))的AEM Forms产品说明。

>



### AEM Forms Designer {#requirements-for-aem-forms-designer}的要求

* Microsoft® Windows® 2012 Server R2、Microsoft® Windows® 2016 Server、Microsoft® Windows® 2019 Server、Microsoft® Windows® 10
* 支持PAE、NX和SSE2的1 GHz或更快的处理器。
* 1 GB的RAM（32位）或2 GB的RAM（64位操作系统）
* 对于32位或20 GB的磁盘空间，对于64位操作系统，为16 GB的磁盘空间
* 图形内存 — 128 MB的GPU（建议256 MB）
* 2.35 GB可用硬盘空间
* 1024 X 768像素或更高的显示器分辨率
* 视频硬件加速（可选）
* Acrobat Pro DC、Acrobat Standard DC或Adobe Acrobat Reader DC
* 安装Designer的管理权限

### AEM Assets XMP元数据回写{#requirements-for-aem-assets-xmp-metadata-write-back}的要求

支持并启用以下平台和文件格式的XMP写回：

**操作系统**

* Linux（32位，需要在64位系统上支持32位应用程序）。 有关安装32位客户端库的步骤，请参阅[如何在64位RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)上启用XMP提取和回写。

* Windows Server
* OracleSolaris
* Mac OS X（64位）

**文件格式**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### AEM Screens播放器{#requirements-for-aem-screens-player}的要求

AEM Screens播放器版本3.3.x支持以下操作系统：

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1（已更新Android系统WebView版本52及更高版本）
* Apple iOS 10.3+
* Apple macOS 10.12+
