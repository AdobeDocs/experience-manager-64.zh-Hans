---
title: 自定义欢迎控制台（经典UI）
seo-title: Customizing the Welcome Console (Classic UI)
description: “欢迎”控制台提供了指向AEM中各种控制台和功能的链接列表
seo-description: The Welcome console provides a list of links to the various consoles and functionality within AEM
uuid: 4ef20cef-2d7a-417d-b36b-ed4fa56cd511
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 2e408acb-3802-4837-8619-688cfc3abfa7
exl-id: 11b791f6-b14f-4f50-a64a-27a9501adeb7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 9%

---

# 自定义欢迎控制台（经典UI）{#customizing-the-welcome-console-classic-ui}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>本页介绍经典UI。
>
>请参阅 [自定义控制台](/help/sites-developing/customizing-consoles-touch.md) 有关标准触屏UI的详细信息。

“欢迎”控制台提供了指向AEM中各种控制台和功能的链接列表。

![cq_welcomscreen](assets/cq_welcomescreen.png)

可以配置可见的链接。 这可以为特定用户和/或组定义。 要执行的操作取决于目标类型（与所在控制台的部分相关）：

* [主要控制台](#links-in-main-console-left-pane)  — 主控制台（左窗格）中的链接
* [资源、文档和参考、功能](#links-in-sidebar-right-pane)  — 侧栏（右窗格）中的链接

## 主控制台中的链接（左窗格） {#links-in-main-console-left-pane}

这列出了AEM的主要控制台。

![cq_welcomescreenmainconsole](assets/cq_welcomescreenmainconsole.png)

### 配置主控制台链接是否可见 {#configuring-whether-main-console-links-are-visible}

节点级别权限决定链接是否可见。 相关节点包括：

* **网站：** `/libs/wcm/core/content/siteadmin`

* **数字资产:** `/libs/wcm/core/content/damadmin`

* **社区：** `/libs/collab/core/content/admin`

* **营销活动：** `/libs/mcm/content/admin`

* **收件箱：** `/libs/cq/workflow/content/inbox`

* **用户:** `/libs/cq/security/content/admin`

* **工具：** `/libs/wcm/core/content/misc`

* **标记：** `/libs/cq/tagging/content/tagadmin`

例如：

* 限制对 **工具**，从中删除读取访问权限

   `/libs/wcm/core/content/misc`

请参阅 [安全部分](/help/sites-administering/security.md) 以了解有关如何设置所需权限的更多信息。

### 侧栏中的链接（右窗格） {#links-in-sidebar-right-pane}

![cq_welcomescreensidebar](assets/cq_welcomescreensidebar.png)

这些链接基于 *和* 读取以下路径下的节点访问权限：

`/libs/cq/core/content/welcome`

默认情况下，提供了三个部分（稍微间隔）：

<table> 
 <tbody> 
  <tr> 
   <td><strong>资源</strong></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Cloud Service</td> 
   <td><code>/libs/cq/core/content/welcome/resources/cloudservices</code></td> 
  </tr> 
  <tr> 
   <td> 工作流</td> 
   <td><code>/libs/cq/core/content/welcome/resources/workflows</code></td> 
  </tr> 
  <tr> 
   <td> 任务管理</td> 
   <td><code>/libs/cq/core/content/welcome/resources/taskmanager</code></td> 
  </tr> 
  <tr> 
   <td> 复制</td> 
   <td><code>/libs/cq/core/content/welcome/resources/replication</code></td> 
  </tr> 
  <tr> 
   <td> 报表</td> 
   <td><code>/libs/cq/core/content/welcome/resources/reports</code></td> 
  </tr> 
  <tr> 
   <td> 出版物</td> 
   <td><code>/libs/cq/core/content/welcome/resources/publishingadmin</code></td> 
  </tr> 
  <tr> 
   <td> 手稿</td> 
   <td><code>/libs/cq/core/content/welcome/resources/manuscriptsadmin</code></td> 
  </tr> 
  <tr> 
   <td><strong>文档和参考</strong></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 文档</td> 
   <td><code>/libs/cq/core/content/welcome/docs/docs</code></td> 
  </tr> 
  <tr> 
   <td> 开发人员资源</td> 
   <td><code>/libs/cq/core/content/welcome/docs/dev</code></td> 
  </tr> 
  <tr> 
   <td><strong>功能</strong></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> CRXDE Lite</td> 
   <td><code>/libs/cq/core/content/welcome/features/crxde</code></td> 
  </tr> 
  <tr> 
   <td> 包</td> 
   <td><code>/libs/cq/core/content/welcome/features/packages</code></td> 
  </tr> 
  <tr> 
   <td> 包共享</td> 
   <td><code>/libs/cq/core/content/welcome/features/share</code></td> 
  </tr> 
  <tr> 
   <td> 聚类</td> 
   <td><code>/libs/cq/core/content/welcome/features/cluster</code></td> 
  </tr> 
  <tr> 
   <td> 备份</td> 
   <td><code>/libs/cq/core/content/welcome/features/backup</code></td> 
  </tr> 
  <tr> 
   <td> Web 控制台<br /> </td> 
   <td><code>/libs/cq/core/content/welcome/features/config</code></td> 
  </tr> 
  <tr> 
   <td> Web 控制台状态转储<br /> </td> 
   <td><code>/libs/cq/core/content/welcome/features/statusdump</code></td> 
  </tr> 
 </tbody> 
</table>

#### 配置侧栏链接是否可见 {#configuring-whether-sidebar-links-are-visible}

可以通过删除对表示链接的节点的读取访问权限来隐藏特定用户或组的链接。

* 资源 — 删除对以下项的访问权限：

   `/libs/cq/core/content/welcome/resources/<link-target>`

* 文档 — 删除对以下项的访问权限：

   `/libs/cq/core/content/welcome/docs/<link-target>`

* 功能 — 删除对以下项的访问：

   `/libs/cq/core/content/welcome/features/<link-target>`

例如：

* 删除链接 **报表**，从中删除读取访问权限

   `/libs/cq/core/content/welcome/resources/reports`

* 删除链接 **包**，从中删除读取访问权限

   `/libs/cq/core/content/welcome/features/packages`

请参阅 [安全部分](/help/sites-administering/security.md) 以了解有关如何设置所需权限的更多信息。

### 链接选择机制 {#link-selection-mechanism}

在 `/libs/cq/core/components/welcome/welcome.jsp` 使用 [ConsoleUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ConsoleUtil.html)，用于对具有以下属性的节点执行查询：

* `jcr:mixinTypes` 值为: `cq:Console`

>[!NOTE]
>
>执行以下查询以查看现有列表：
>
>* `select * from cq:Console`
>


当用户或组对具有混合的节点没有读取权限时 `cq:Console`，则该节点不会被 `ConsoleUtil` 搜索，因此它不会列在控制台中。

### 添加自定义项目 {#adding-a-custom-item}

的 [链接选择机制](#link-selection-mechanism) 可用于将您自己的自定义项目添加到链接列表。

通过添加 `cq:Console` 混合到小组件或资源中。 这可通过定义属性来完成：

* `jcr:mixinTypes` 值为: `cq:Console`
