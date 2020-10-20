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
translation-type: tm+mt
source-git-commit: d09956e5e7fb42e9c4b145e027778f209876239a
workflow-type: tm+mt
source-wordcount: '3142'
ht-degree: 2%

---


# 技术要求{#technical-requirements}

Adobe在平台上支持Adobe Experience Manager(AEM)，详情请见本文档的以下信息。

有关与平台本身特别相关的任何问题，请直接与平台供应商联系。

>[!NOTE]
>
>根据您安装AEM的平台，可能会有不同的用户管理要求集。

## 前提条件 {#prerequisites}

安装Adobe Experience Manager的最低要求：

* 已安装Java Platform、Standard Edition JDK或其他支持的 [Java虚拟机](#java-virtual-machines)
* Experience Manager快速启动文件（独立JAR或Web应用程序部署WAR）

### 最小规模要求 {#minimum-sizing-requirements}

运营Adobe Experience Manager的最低要求：

* 安装目录中有5 GB可用磁盘空间
* 2 GB内存

>[!NOTE]
>
>* 数字资产使用案例需要更多基本内存。 有关详 [细信息，请参阅](/help/sites-deploying/deploy.md#default-local-install) “部署和维护”。
>* [AEM Forms加载项包](/help/forms/using/installing-configuring-aem-forms-osgi.md) 需要15 GB临时空间。

>



有关详细信 [息，请参阅硬件](/help/managing/hardware-sizing-guidelines.md) 大小调整指南。

### 支持级别 {#support-levels}

此文档列表Adobe Experience Manager支持的客户端和服务器平台。 Adobe为推荐的配置和其他配置提供多种支持级别。

### 支持的配置 {#supported-configurations}

Adobe建议这些配置，并作为标准软件维护协议的一部分提供全面支持。

<table> 
 <tbody> 
  <tr> 
   <td>支持级别</td> 
   <td>描述<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>答：支持</strong></td> 
   <td>Adobe为此配置提供全面支持和维护。 此配置由Adobe的质量保证流程涵盖。</td> 
  </tr> 
  <tr> 
   <td><strong>R:受限支持</strong></td> 
   <td>为了确保我们的客户项目成功，Adobe在受限的支持项目内提供全面支持，这要求满足特定条件。 R级支持需要正式的客户请求和Adobe确认。 有关详细信息，请与Adobe客户服务联系。</td> 
  </tr> 
 </tbody> 
</table>

### 不支持的配置 {#unsupported-configurations}

| 支持级别 | 描述 |
|---|---|
| **Z:不支持** | 不支持此配置。 Adobe不对配置是否工作做出任何声明，也不支持配置。 |

## 支持的平台 {#supported-platforms}

### Java虚拟机 {#java-virtual-machines}

该应用程序需要运行Java虚拟机，该虚拟机由Java开发工具包(JDK)分发提供。

Adobe Experience Manager使用以下版本的Java虚拟机：

>[!CAUTION]
>
>建议跟踪Java供应商的安全公告，以确保生产环境的安全和安全，并安装最新的Java更新。

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>支持级别<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z:不支持 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z:不支持 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64位</strong></td> 
   <td>答：支持[3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM —— 内部版本2.9,JRE 1.8.0 [2]</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM —— 内部版本2.8,JRE 1.8.0 [2]</td> 
   <td>答：支持</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle 已经转向 Oracle Java SE 产品的“长期支持”(LTS) 模型。Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe 将只为 LTS 版本的 Java 提供支持，以便在生产环境中运行 AEM。

1. IBM JRE仅与WebSphere Application Server一起支持。
1. 对于所有使用Oracle Java SE技术的AEM客户，将直接支持支持和分发Oracle Java SE JDK，包括在公共更新结束后对LTS版本的所有维护更新。 有关详 [细信息，请参阅Adobe Experience Manager问题与答案的Oracle](assets/adobe-oracle-java-license-agreement.pdf) Java支持。

### 存储和持久性 {#storage-persistence}

部署Adobe Experience Manager的存储库存在各种选项。 有关支持的技术和列表选项，请参阅以下存储。

<table> 
 <tbody> 
  <tr> 
   <td><strong>平台</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>支持级别</strong></td> 
  </tr> 
  <tr> 
   <td><strong>带有TAR文件的文件系统[1]</strong></td> 
   <td>存储库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td><strong>带有数据存储区[1]的文件系统</strong></td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>在文件系统[1]的TAR文件中存储二进制文件</td> 
   <td>二进制文件</td> 
   <td>Z:不支持生产</td> 
  </tr> 
  <tr> 
   <td>AmazonS3</td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob存储</td> 
   <td>二进制文件</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5]</td> 
   <td>存储库</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3]</td> 
   <td>存储库</td> 
   <td>答：支持</td> 
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
   <td>R:受限支持(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c(12.1.x)</td> 
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
   <td>R:受限支持(4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene（Quickstart内置）</strong></td> 
   <td>搜索服务</td> 
   <td>答：支持</td> 
  </tr> 
  <tr> 
   <td>阿帕奇索尔</td> 
   <td>搜索服务</td> 
   <td>答：支持</td> 
  </tr> 
 </tbody> 
</table>

1. “文件系统”包括符合POSIX的块存储。 这包括网络存储技术。 请注意，文件系统性能可能会有所不同，并影响总体性能。 建议将AEM与网络／远程文件系统一起加载测试。
1. AEM不支持MongoDB共享。
1. 仅支持MongoDB存储引擎WiredTiger。
1. 不支持AEM Forms。
1. 从 AEM 版本 6.4.2.0 开始，支持 MongoDB Enterprise 3.6。

>[!NOTE]
>
>有关 [AEM Communities能](/help/communities/deploy-communities.md) 力的更多信息，请参阅部署社区。

>[!NOTE]
>
>MongoDB是第三方软件，不包含在AEM授权包中。 有关详细信息，请参 [阅MongoDB授权策略](https://www.mongodb.org/about/licensing/) 页。
>
>为了充分利用MongoDB的AEM部署，Adobe建议授权MongoDB企业版，以便从专业支持中受益。 有关详 [细信息](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) ，请参阅推荐的部署。
>
>该许可证包含一个标准副本集，该副本集由一个主实例和两个可用于作者或发布部署的辅助实例组成。
>
>如果您希望在MongoDB上运行作者和发布，则需要购买两个单独的许可证。
>
>Adobe客户关怀将帮助确定与将MongoDB与AEM一起使用相关的问题。
>
>有关详细信息，请参 [阅MongoDB for](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)Adobe Experience Manager页。

>[!NOTE]
>
>上面列出的受支持的关系数据库是第三方软件，不包含在AEM授权包中。
>
>为了在受支持的关系数据库上运行AEM 6.4，需要与数据库供应商签订单独的支持合同。 Adobe客户关怀将帮助确定与AEM 6.4中关系数据库的使用相关的问题。
>
>**请注意，AEM 6.4的Level-R中目前支持大多数关系型项目库，它附带支持标准和支持（如上面的Level-R描述中所述）。**

### Servlet引擎／应用程序服务器 {#servlet-engines-application-servers}

Adobe Experience Manager可以作为独立服务器（快速启动JAR文件）或作为第三方应用程序服务器（WAR文件）中的web应用程序运行。

所需的Servlet API最低版本为Servlet 3.1，但低于Servlet 4.0。

| 平台 | 支持级别 |
|---|---|
| **快速启动内置Servlet引擎(Jetty 9.3)** | 答：支持 |
| Oracle WebLogic Server 12.2(12cR2) | 答：支持 |
| IBM WebSphere Application Server Continuous投放(LibertyProfile)，带Web用户档案7.0和IBM JRE 1.8 | 答：支持 |
| IBM WebSphere Application Server 9.0 | 答：支持 |
| Apache Tomcat 8.5.x | 答：支持 |
| JBoss EAP 7.1.0（带JBoss应用程序服务器） | 答：支持(1) |
| JBoss EAP 7.0.0（带JBoss应用程序服务器） | 答：支持 |

1. 不支持AEM Forms。

### 服务器操作系统 {#server-operating-systems}

Adobe Experience Manager使用以下服务器平台：

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
   <td>Oracle Solaris 11</td> 
   <td>答：受限制(3,5,7)<br /> R:对新合同的限制支持</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>答：受限制(2,5,7)<br /> R:对新合同的限制支持</td> 
  </tr> 
 </tbody> 
</table>

1. Linux内核2.6、3.x和4.x包含Red Hat分发的衍生产品，包括Red Hat Enterprise Linux、CentOS、Oracle Linux和AmazonLinux。 AEM Forms加载项功能仅在CentOS 7和Red Hat Enterprise Linux 7上受支持。
1. AEM Assets:请参见XMP元 [数据回写支持部分](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets:不支持Dynamic Media Imaging。 支持Dynamic Media视频。
1. AEM Forms仅在Ubuntu 16.04 LTS上受支持。
1. AEM Assets:不支持原始 [文件转换](/help/assets/camera-raw.md)
1. AEM Forms:不支持生产环境
1. AEM Assets:不支持增强 [的PDF光栅器](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms:不支持

### 虚拟和云计算环境 {#virtual-cloud-computing-environments}

Adobe Experience Manager支持在云计算环境(如Microsoft Azure和Amazon网络服务(AWS))上的虚拟机中运行，符合本页列出的技术要求，并符合Adobe的标准支持条款。

Adobe建议使用Adobe Managed Services在Azure或AWS上部署AEM。 Adobe Managed Services为专家提供在这些云计算环境中部署和操作AEM的经验和技能。 请查阅我们有关 [Adobe Managed Services的其他文档](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t)。

在部署AEM到Azure或AWS或任何其他云计算环境的所有其他情况下，将根据本页所列技术规范，将来自Adobe的支持包含到虚拟计算环境。 与任何这些云环境中运行的AEM相关的任何报告问题都需要独立于云计算环境特定的任何云服务进行重现，除非云服务是本页所列技术要求的一部分，例如Azure Blob存储或AWS S3。

有关如何在Azure或AWS上部署AEM的建议，我们强烈建议在Adobe托管服务之外直接与云提供商或Adobe合作伙伴合作，支持在您选择的云环境中部署AEM。 选定的云提供商或合作伙伴将负责架构的规模规范、设计和实施。以满足您的特定性能、负载、可扩展性和安全要求。

### 调度程序平台（Web服务器） {#dispatcher-platforms-web-servers}

调度程序是缓存和负载平衡组件。 [下载最新的Dispatcher版本](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html)。 Experience Manager6.4需要Dispatcher版本4.3.1或更高版本。

支持以下Web服务器与Dispatcher 4.3.1版一起使用：

| 平台 | 支持级别 |
|---|---|
| **Apache httpd 2.4.x** （另请参阅下面的1,2） | 答：支持 |
| Microsoft IIS 10(Internet Information Server) | 答：支持 |
| Microsoft IIS 8.5(Internet Information Server) | 答：支持 |

1. 基于Apache httpd源代码构建的Web服务器将具有与其所基于的httpd版本相同的支持级别。 如果有疑问，请向Adobe咨询，以确认与相应服务器产品相关的支持级别。 以下情况：

   1. HTTP服务器是仅使用Apache源正式分发或
   1. HTTP服务器作为运行它的操作系统的一部分进行传送。 示例：IBM HTTP Server、Oracle HTTP Server

1. Dispatcher不适用于Windows操作系统的Apache 2.4.x。

## 支持的客户端平台 {#supported-client-platforms}

### 支持创作用户界面的浏览器 {#supported-browsers-for-authoring-user-interface}

Adobe Experience Manager用户界面可与以下客户端平台一起使用。 所有浏览器都使用默认的插件和加载项集进行测试。

AEM用户界面针对大屏幕（通常是笔记本和台式计算机）和平板电脑外形（如Apple iPad或Microsoft Surface）进行了优化。 不支持手机外形。

>[!NOTE]
>
>**支持发布周期快的浏览器：**
>
>Mozilla Firefox、Google Chrome和Microsoft Edge版本每几个月更新一次。 Adobe承诺为Adobe Experience Manager提供更新，以按照下面所述通过即将推出的这些浏览器版本保持支持级别。

<table> 
 <tbody> 
  <tr> 
   <td><strong>浏览器</strong></td> 
   <td><strong>UI支持<br /> </strong></td> 
   <td><strong>经典UI支持</strong></td> 
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
   <td>Mozilla Firefox最后一个ESR [1]</td> 
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
   <td>答：支持[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td>iOS 11.x上的Apple Safari</td> 
   <td>答：支持[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
  <tr> 
   <td>iOS 10.3上的Apple Safari</td> 
   <td>答：支持[2]</td> 
   <td>Z:不支持</td> 
  </tr> 
 </tbody> 
</table>

1. Firefox长期支持版本了 [解有关此内容的更多信息，请访问mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. 支持Apple iPad

### 支持的网站浏览器 {#supported-browsers-for-websites}

一般来说，AEM Sites提供的网站浏览器支持取决于AEM页面模板、设计和组件输出的实现，因此由实施这些部分的一方控制。

### WebDAV客户端 {#webdav-clients}

**Microsoft Windows 7+**

要成功与Microsoft Windows 7+连接到未通过SSL保护的AEM实例，必须在Windows中启用通过不安全网络进行基本身份验证。 这需要在WebClient的Windows注册表中进行更改：

1. 找到注册表子项：

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 使用值2或更大值将BasicAuthLevel注册表项添加到此子项。

请参 [阅Microsoft支持KB 841215](https://support.microsoft.com/default.aspx/kb/841215)。

要提高Windows下WebDav客户端的响应性——请参 [阅Microsoft支持KB 2445570](https://support.microsoft.com/kb/2445570)

## 其他平台说明 {#additional-platform-notes}

本节提供有关运行Adobe Experience Manager及其加载项的特别说明和更详细的信息。

### IPv4和IPv6 {#ipv-and-ipv}

Adobe Experience Manager的所有元素（实例、调度程序）都可以安装在IPv4和IPv6网络中。

操作是无缝的，因为不需要特殊配置。 如有必要，您只需使用适合您的网络类型的格式指定IP地址。

这意味着，当需要指定IP地址时，您可以从以下位置（根据需要）进行选择：

* IPv6地址

   for example `https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   for example `https://123.1.1.4:4502`

* 服务器名称

   for example, `https://www.yourserver.com:4502`

* 将解释IPv4 `localhost` 和IPv6网络安装的默认情况

   for example, `http://localhost:4502`

### AEM Dynamic Media Add-on的要求 {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media默认处于禁用状态。 See [Enabling Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

启用Dynamic Media后，将适用以下附加系统要求：
>[!NOTE]
>
>以下系统要求 **_仅在_** “Dynamic Media —— 混合”模式下适用；Dynamic Media —— 混合模式具有嵌入式图像服务器，该服务器仅在某些操作系统上得到认证。
>
>对于运行Dynamic Media -Scene7模式(即 **dynamicmedia_scene7运行模式** )的Dynamic Media客户，没有其他系统要求；系统要求与AEM相同。 动态媒体-Scene7模式体系架构使用基于云的图像服务，而不是嵌入在AEM中的服务。

#### 硬件 {#hardware}

以下硬件要求适用于Linux和Windows操作系统：

* 至少具有4个内核的Intel Xeon或AMD Opteron CPU
* 最低16GB内存

#### Linux {#linux}

在Linux上使用Dynamic Media需要以下先决条件：

* RedHat Enterprise 7或CentOS 7及更高版本以及最新的修补程序
* 64位操作系统
* 交换已禁用（建议）
* 禁用SELinux（请参阅以下注意事项）

>[!NOTE]
>
>如果设置区域设置为LC_CTYPE不等于en_US.UTF-8，则会阻止Dynamic Media工作。 在命令提示符下查看其值是什么。 如果未设置为此值，请在运行AEM之前键入“export LC_CTYPE=”，将LC_CTYPE环境变量设置为空字符串。

>[!NOTE]
>
>**禁用SELinux:** 打开SELinux时图像服务不工作。 此选项默认处于启用状态。 要解决此问题，请编 **辑/etc/selinux/config文件** ，并将SELinux值从：
>
>`SELINUX=enforcing` 到  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA架构：** 具有AMD64和Intel EM64T处理器的系统通常配置为非统一内存架构(NUMA)平台，这意味着内核在启动时构建多个内存节点，而不是构建单个内存节点。
>
>该多节点构造可导致在其它节点耗尽之前，一个或多个节点上的内存耗尽。 当内存耗尽时，内核可决定终止进程（例如，映像服务器或平台服务器），即使内存可用。
>
>因此，Adobe建议，如果运行的系统使用numa=off引导选项关 **闭NUMA** ，以避免内核杀死这些进程。

>[!NOTE]
>
>**服务器的主机名必须可解析：** 确保服务器的主机名可解析为IP地址。 如果这不可能，请将完全限定的主机名和IP地址添 **加到/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 交换空间至少等于物理内存(RAM)量的两倍

要在Windows上使用Dynamic Media，必须安装适用于x64和x86的Microsoft Visual Studio 2010、2013和2015可再发行版。

x64

* Microsoft Visual Studio 2010可再分发，网址为 [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* Microsoft Visual Studio 2013可再发行版可在https://www.microsoft.com/en-us/download/details.aspx?id=40784上 [找到](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Microsoft Visual Studio 2015可再发行版可在https://www.microsoft.com/en-us/download/details.aspx?id=48145上 [找到](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Microsoft Visual Studio 2010可再分发，网址为 [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Microsoft Visual Studio 2013可再发行版可在https://www.microsoft.com/en-in/download/details.aspx?id=40769上 [找到](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft Visual Studio 2015可再发行版可在https://www.microsoft.com/en-us/download/details.aspx?id=52685上 [找到](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x及更高版本
* 仅支持试用和演示目的

### AEM FormsPDF生成器要求 {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>产品</strong></p> </th> 
   <th><p><strong>支持的转换为PDF的格式</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat2017年经典赛</a></p> </td> 
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
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、XLSX、DOC、DOCX、PPT、PPTX、图像格式(BMP、GIF、JPG、TIF、TIF、 PNG、 PNG、 PNG、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、XLSX、DOC、DOCX、PPT、PPTX、图像格式(BMP、GIF、JPG、TIF、TIF、 PNG、 PNG、 PNG、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator仅支持支持的操作系统和应用程序的英语、法语、德语和日语版本。
>
>此外：
>
>* PDF Generator需要 [Acrobat2017经典音轨版本17.011.30078或更高版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) ，才能执行转换。
>* AEM Forms仅支持32位版本的受支持软件。
>* OCR PDF（可搜索的PDF）、Optimize PDF和Export PDF功能仅在Microsoft Windows上受支持。
>* AIX上已弃用HTML2PDF服务。
>* 仅在Windows、Linux和Solaris上支持OpenOffice的PDF Generator转换。
>* OCR PDF、Optimize PDF和Export PDF功能仅在Windows上受支持。
>* Acrobat的某个版本与AEM Forms捆绑在一起，以实现PDF Generator功能。 捆绑版本仅应在AEM Forms许可期限内通过AEM Forms以编程方式访问，以便与AEM FormsPDF生成器一起使用。 有关详细信息，请参阅按部署说明的AEM Forms[产品说明(内部部](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) 署 [或Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))”

>



### AEM AssetsXMP元数据回写要求 {#requirements-for-aem-assets-xmp-metadata-write-back}

支持并支持以下平台和文件格式的XMP写回：

**操作系统**

* Linux（32位，需要64位系统上的32位应用程序支持）。 有关安装32位客户端库的步骤，请参 [阅如何在64位RedHat Linux上启用XMP提取和回写](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)。

* Windows Server
* Oracle Solaris
* Mac OS X（64位）

**文件格式**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Requirements for AEM Screens Player {#requirements-for-aem-screens-player}

AEM Screens播放器版本3.3.x支持以下操作系统：

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1（已更新Android系统WebView版本52+）
* Apple iOS 10.3+
* Apple macOS 10.12+
