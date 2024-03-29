---
title: 微调运行状况监视器性能
seo-title: Fine-tuning Health Monitor performance
description: 了解如何优化运行状况监视器性能
seo-description: Learn how to fine-tune Health Monitor performance
uuid: 770b10cb-065f-41b5-9594-a291e4311151
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b8f8bddc-0d38-4d5e-b33f-978f04bc16c6
exl-id: b2814b0d-e843-4aba-8c74-a3be0a96f726
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 2%

---

# 微调运行状况监视器性能{#fine-tuning-health-monitor-performance}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

收集填充运行状况监视器的系统统计信息会对AEM表单环境的性能产生一些影响。 可以通过在应用程序服务器中设置下面列出的Java选项来控制此影响。

<table> 
 <thead> 
  <tr> 
   <th><p>属性</p></th> 
   <th><p>用途</p></th> 
   <th><p>默认值</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>adobe.healthmonitor.enabled</p></td> 
   <td><p>打开或关闭健康监视器线程</p></td> 
   <td><p>true</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.cache.statistics-enabled</p></td> 
   <td><p>打开或关闭Gemfire缓存</p></td> 
   <td><p>true</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.healthmonitor.refresh-interval</p></td> 
   <td><p>运行状况监视器线程收集统计信息之后的间隔（以毫秒为单位）</p></td> 
   <td><p>10分钟（600,000毫秒）</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.cache.multicast-port</p></td> 
   <td><p>用于与分布式系统的其他成员通信的多播端口。 如果设置为零，则对于成员发现和分发都禁用多播。 </p><p>注意：为不同的分布式系统选择不同的多播地址和端口。 请勿仅使用不同的地址。</p></td> 
   <td><p>没有默认值。 有效值介于0到65535之间。</p></td> 
  </tr> 
  <tr> 
   <td><p>统计样本率</p></td> 
   <td><p>统计信息采样的速率（以毫秒为单位）。 仅在采用示例时才会更新操作系统统计信息。</p></td> 
   <td><p>600000</p></td> 
  </tr> 
  <tr> 
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td> 
   <td><p>此属性可启用或禁用工作管理器统计收集，如作业或工作项计数。</p></td> 
   <td><p>true</p></td> 
  </tr> 
 </tbody> 
</table>

## 将Java选项添加到JBoss {#add-java-options-to-jboss}

1. 停止JBoss应用程序服务器。
1. 打开 *[appserver根]*/bin/run.bat(Windows)或在编辑器中运行.sh（Linux或UNIX），并根据需要添加任何Java选项。
1. 重新启动服务器。

## 将Java选项添加到WebLogic {#add-java-options-to-weblogic}

1. 通过键入https://以启动WebLogic管理控制台[主机名]:[端口]/console。
1. 键入您为WebLogic Server域创建的用户名和密码，然后单击“更改中心”下的“日志”，然后单击“锁定并编辑”。
1. 在“域结构”下，单击“环境”>“服务器”，然后在右窗格中，单击受控服务器名称。
1. 在下一个屏幕上，单击“配置”选项卡>“服务器开始”选项卡。
1. 在参数框中，将所需的参数附加到当前内容的末尾。 例如，添加 —  `Dadobe.healthmonitor.enabled=false` 禁用运行状况监视器。
1. 单击保存，然后单击激活更改。
1. 重新启动WebLogic托管服务器。

## 将Java选项添加到WebSphere {#add-java-options-to-websphere}

1. 在WebSphere管理控制台导航树中，为应用程序服务器执行以下操作：

   (WebSphere 6.x)单击“服务器”>“应用程序服务器”

   (WebSphere 7.x)单击“服务器”>“服务器类型”>“WebSphere应用程序服务器”

1. 在右窗格中，单击服务器名称。
1. 在“服务器基础架构”下，单击Java和表单工作流>进程定义。
1. 在“其他属性”下，单击“Java虚拟机”。
1. 在“通用JVM参数”框中，键入所需的参数。
1. 单击确定或应用，然后单击直接保存到主控配置。
