---
title: 工具控制台
seo-title: 工具控制台
description: 了解整个 AEM 中的不同工具控制台。
seo-description: 了解整个 AEM 中的不同工具控制台。
uuid: d01382f8-0c8f-4d76-9271-bed9e34b3b4b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 2bf8496d-a485-4b39-a6c9-07222b66d0cd
translation-type: tm+mt
source-git-commit: e9c5fcd8f939d88317c5184b6352b227918088e5
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 36%

---


# 工具控制台{#tools-consoles}

**工具**&#x200B;控制台让您可以访问一些专用工具，这些工具有助于您管理网站、数字资产及内容存储库的其他方面。工具控制台目前有两种 **形式** ，具体取决于您所使用的UI:

* [工具——经典UI](#tools-classic-ui)
* [工具——触屏优化UI](#tools-touch-optimized-ui)

## 工具——经典UI {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>页面或文件夹</th> 
   <th> </th> 
   <th>用途</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM控制中心</a></td> 
   <td> </td> 
   <td>用于管理多个站点的集中点。</td> 
  </tr> 
  <tr> 
   <td>Client Context配置<br /> </td> 
   <td> </td> 
   <td>Client Context <a href="/help/sites-developing/client-context.md">表示动态组合</a> 的用户数据集合。 此处保留默认和营销云配置。<br /> </td> 
  </tr> 
  <tr> 
   <td>Cloud Services配置<br /> </td> 
   <td> </td> 
   <td>保存与集成 <a href="/help/sites-administering/marketing-cloud.md">Adobe Marketing Cloud相关的配置</a>。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">商务</a></td> 
   <td> </td> 
   <td>提供对导入器和各种产品数据的访问。</td> 
  </tr> 
  <tr> 
   <td>DAM -Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>提供对数字权限信息和许可证的访问。</td> 
  </tr> 
  <tr> 
   <td>DAM - Health Checker<br /> </td> 
   <td> </td> 
   <td>比较 <code>/var/dam</code> 和 <code>/content/dam</code> 检查是否有任何不一致<br /> 。 随后可以同步或删除列出的所有文件／文件夹。 文件夹比较的节点类型可在Web控制台中进行配置。</td> 
  </tr> 
  <tr> 
   <td>DAM -AdobeIndesign<br /> </td> 
   <td> </td> 
   <td>用于与AdobeIndesign结合使用的脚本。</td> 
  </tr> 
  <tr> 
   <td>DAM —— 视频用户档案<br /> </td> 
   <td> </td> 
   <td>用于ffmpeg转码的可配置用户档案。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">功能板</a></td> 
   <td> </td> 
   <td>允许您创建报告仪表板; 这为定义显示统一数据的页面提供了一种可自定义的方式。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">设计</a></td> 
   <td> </td> 
   <td>保留定义的设计列表，包括要使用的图形和css文件。</td> 
  </tr> 
  <tr> 
   <td>自定义文档</td> 
   <td> </td> 
   <td>用于扩展文档和联机帮助。</td> 
  </tr> 
  <tr> 
   <td>表单提交</td> 
   <td> </td> 
   <td>保留收到的表单提交的列表。</td> 
  </tr> 
  <tr> 
   <td>导入器- <a href="/help/sites-administering/bulk-editor.md">批量编辑器</a></td> 
   <td> </td> 
   <td>允许您搜索项目并批量编辑它们。 您还可以将内容（批量）导出并导入到存储库中。</td> 
  </tr>
  <tr> 
   <td>导入程序- Feed Importer</td> 
   <td> </td> 
   <td><p>Feed Importer是一个框架，可将外部源中的内容重复导入到您的存储库中。 Feed Importer的想法是以指定的时间间隔轮询远程资源，分析它，并在内容存储库中创建表示远程资源内容的节点。</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">外部链接检查程序</a></td> 
   <td> </td> 
   <td>扫描AEM实例中的所有内容页面并检查任何外部链接。 将显示有效和无效链接列表。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">移动设备</a></td> 
   <td> </td> 
   <td>帮助您创建专为移动设备设计的网站。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>处理多语言和跨国内容，帮助您在集中品牌和本地化内容之间取得平衡。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">通知</a></td> 
   <td> </td> 
   <td>通知模板。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">包</a></td> 
   <td> </td> 
   <td>指向“包管理器”的替代链接，其中显示已为AEM WCM加载的包。 与CRX的包管理器中显示的信息相似。</td> 
  </tr> 
  <tr> 
   <td>复制——复 <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">制代理</a></td> 
   <td> </td> 
   <td>用于在发布页面时将数据从作者复制到发布，或通过反向复制将用户注释从发布环境返回到作者。</td> 
  </tr> 
  <tr> 
   <td>导入器- <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">激活树</a></td> 
   <td> </td> 
   <td>在“网站”选项卡中，可以激活单个页面。如果已经输入或更新大量内容页面（所有内容页面都驻留在同一根页面下），则可以更轻松地通过一个操作来激活整个树。也可以通过“练习”来模拟激活和突出显示要激活的页面。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">报告</a></td> 
   <td> </td> 
   <td>AEM提供一系列自定义报告，允许您创建自定义报告和／或开发您自己的报告。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">默认页面基架</a></td> 
   <td> </td> 
   <td>使用基架，您可以创建一个表单（即基架），其中包含的字段反映您要用于页面的结构，然后使用此表单轻松创建基于此结构的页面。</td> 
  </tr> 
  <tr> 
   <td>安全- <a href="/help/sites-administering/notification.md">自助服务配置 </a> </td> 
   <td> </td> 
   <td>允许您配置用户在创建帐户或重置口令时自动收到的电子邮件以及确认已重置的口令。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">分段</a></td> 
   <td> </td> 
   <td>站点访客在访问站点时的兴趣和目标各不相同。了解这些目标并满足预期是在线营销活动的一个重要成功因素。Segmentation helps to achieve this by analyzing and characterizing a visitor's details.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>默认SRP配置。 请参阅 <a href="/help/communities/srp-config.md">存储配置</a> 控制台。</td> 
  </tr> 
  <tr> 
   <td>任务管理</td> 
   <td> </td> 
   <td>没有与此条目相关的活动功能。</td> 
  </tr> 
  <tr> 
   <td>租户</td> 
   <td> </td> 
   <td>没有与此条目相关的活动功能。</td> 
  </tr> 
  <tr> 
   <td>版本控制- <a href="/help/sites-deploying/version-purging.md">清除版本</a></td> 
   <td> </td> 
   <td>允许您根据需要清除页面版本。</td> 
  </tr> 
  <tr> 
   <td>虚拟存储库</td> 
   <td> </td> 
   <td>您可以使用工作区装载功能设置虚拟存储库，以提供支持JCR的内容应用程序，以简化对基于CRX和JCR连接器的JCR内容基础架构的访问。</td> 
  </tr> 
  <tr> 
   <td>口语</td> 
   <td> </td> 
   <td>已弃用. 请参 <a href="/help/communities/moderate-ugc.md#watchwords">阅协调社区内容</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">工作流</a></td> 
   <td> </td> 
   <td>工作流可以控制页面或数字资产上支持任何编辑流程的一系列操作。</td> 
  </tr> 
 </tbody> 
</table>

## 工具——触屏优化UI {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>区域</th> 
   <th>选项</th> 
   <th>用途</th> 
  </tr> 
  <tr> 
   <td>创作</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">营销活动</a></td> 
   <td>管理您的营销活动。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">启动项</a></td> 
   <td>管理您的营销启动项</td> 
  </tr> 
  <tr> 
   <td>任务</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">收件箱</a></td> 
   <td>管理收件箱项目。</td> 
  </tr> 
  <tr> 
   <td>运营</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">用户和组</a></td> 
   <td>管理用户和组。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">标记管理</a></td> 
   <td>组织您的标记和它们的命名空间。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">云服务</a></td> 
   <td>连接到 Adobe Marketing Cloud.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">工作流</a></td> 
   <td>建模和管理工作流.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">复制</a></td> 
   <td>创建和管理多个网站。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">报告</a></td> 
   <td>创建和监测自定义报告.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">测试</a></td> 
   <td>运行为您的应用程序定义的测试.</td> 
  </tr> 
  <tr> 
   <td>Granite 操作</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>使用基于 Web 的 IDE 开发应用程序.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">包</a></td> 
   <td>打包和共享应用程序.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">包共享</a></td> 
   <td>从 Adobe 及社区下载应用程序.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">拓扑浏览器</a></td> 
   <td>查看实例拓扑.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">正在卸载浏览器</a></td> 
   <td>管理卸载。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">备份</a></td> 
   <td>执行备份任务.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Web 控制台<br /> </td> 
   <td>配置和管理应用程序平台.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Web 控制台配置转储<br /> </td> 
   <td>从Web控制台下载配置状态。<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>用户</td> 
   <td>管理您的用户.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>组</td> 
   <td>管理您的组.</td> 
  </tr> 
  <tr> 
   <td>外部资源<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>文档</td> 
   <td>查看 Web Experience Management 文档.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>开发人员资源</td> 
   <td>开发人员资源和下载.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>以上某些选项实际链接到经典UI。

