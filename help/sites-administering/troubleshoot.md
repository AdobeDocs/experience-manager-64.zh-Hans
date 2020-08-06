---
title: AEM疑难解答
seo-title: AEM疑难解答
description: 了解AEM的疑难解答问题。
seo-description: 了解AEM的疑难解答问题。
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 10%

---


# AEM疑难解答{#troubleshooting-aem}

下节介绍使用AEM时可能遇到的一些问题，以及有关如何解决这些问题的建议。

>[!NOTE]
>
>如果您对AEM中的创作问题进行疑难解答，请参 [阅作者疑难解答。](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>遇到问题时，还可以查阅实例（发行版本或服务包）的[已知问题](/help/release-notes/known-issues.md)列表。

## 管理员的故障排除方案 {#troubleshooting-scenarios-for-administrators}

下表概述了管理员可能需要解决的问题：

<table> 
 <tbody> 
  <tr> 
   <td><strong>角色</strong></td> 
   <td><strong>问题 </strong></td> 
  </tr> 
  <tr> 
   <td>系统管理员</td> 
   <td><p>多次-单击快速启动jar没有任何效果，或者使用其他项目（例如，归档管理器）打开jar文件</p> </td> 
  </tr> 
  <tr> 
   <td><p>系统管理员</p> </td> 
   <td><p>我在CRX上运行的应用程序会引发内存不足错误</p> </td> 
  </tr> 
  <tr> 
   <td><p>系统管理员</p> </td> 
   <td><p>多次单击AEM CM快速启动后，浏览器中不显示AEM欢迎屏幕</p> </td> 
  </tr> 
  <tr> 
   <td><p>系统管理员</p> <p>管理员用户</p> </td> 
   <td><p>创建线程转储</p> </td> 
  </tr> 
  <tr> 
   <td><p>系统管理员</p> <p>管理员用户</p> </td> 
   <td><p>检查未关闭的JCR会话</p> </td> 
  </tr> 
 </tbody> 
</table>

## 安装问题 {#installation-issues}

有关 [以下疑难解答方](/help/sites-deploying/troubleshooting.md#common-installation-issues) 案的信息，请参阅常见安装问题：

* 双击快速启动程序 jar 不起作用，或者 JAR 文件中包含其他程序（例如归档管理器）。
* 在 CRX 上运行的应用程序出现“内存不足”错误。
* 双击 AEM 快速启动程序后，浏览器中没有显示 AEM 欢迎屏幕。

## 疑难解答分析 {#methods-for-troubleshooting-analysis}

### 创建线程转储 {#making-a-thread-dump}

线程转储是当前处于活动状态的所有Java线程的列表。 如果AEM响应不正确，线程转储可以帮助您识别死锁或其他问题。

### 使用吊线翻身器 {#using-sling-thread-dumper}

1. 打开AEM **Web控制台**; 例如 `http://localhost:4502/system/console/`。

1. 在“状态” **选**&#x200B;项卡下&#x200B;**，选** 择“线程”(Threads)。

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### 使用jstack（命令行） {#using-jstack-command-line}

1. 查找AEM Java实例的PID（进程ID）。

   例如，您可以使 `ps -ef` 用或 `jps`。

1. 运行:

   `jstack <pid>`

1. 这将显示线程转储。

>[!NOTE]
>
>您可以使用输出重定向将线程转储追加到日志 `>>` 文件：
>
>`jstack <pid> >> /path/to/logfile.log`

有关详 [细信息，请参阅JVM中如何获取线程转储](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) 文档。

### 检查未关闭的JCR会话 {#checking-for-unclosed-jcr-sessions}

为AEM WCM开发功能时，可以打开JCR会话（类似于打开数据库连接）。 如果打开的会话从未关闭，则系统可能会出现以下症状：

* 系统变慢了。
* 您可以看到许多CacheManager: resize日志文件中的所有条目； 以下数字(size=&lt;x>)显示高速缓存的数量，每个会话打开多个高速缓存。
* 系统不时内存不足（几小时、几天或几周后——具体取决于严重性）。

要分析未关闭的会话并找出哪些代码未关闭会话，请参阅知识库文章分析未 [关闭的会话](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html)。

### 使用Adobe Experience ManagerWeb控制台 {#using-the-adobe-experience-manager-web-console}

OSGi捆绑包的状态还可以提前指示可能的问题。

1. 打开AEM **Web控制台**; 例如 `http://localhost:4502/system/console/`。

1. 在“ **OSGI** ”选 **项卡下选** 择“捆绑”。

1. 检查:

   * 包的状态。 如果存在“非活动”或“未满足要求”，请尝试停止并重新启动捆绑。 如果问题仍然存在，则可能需要使用其他方法进行进一步调查。
   * 是否有任何包缺少依赖关系。 单击作为链接的单个捆绑包名称即可查看此类详细信息（以下示例没有任何问题）:

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)

