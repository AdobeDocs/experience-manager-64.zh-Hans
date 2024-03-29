---
title: 升级前维护任务
seo-title: Pre-Upgrade Maintenance Tasks
description: 了解AEM中的升级前任务。
seo-description: Learn about the pre-upgrade tasks in AEM.
uuid: 6c0d4b31-6464-470b-9e40-1fc2abb9b2a6
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 899ea120-c96d-4dbf-85da-e5d25959d10a
feature: Upgrading
exl-id: f146cb2f-ee77-4c99-8dff-446cdb3a7797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2204'
ht-degree: 1%

---

# 升级前维护任务{#pre-upgrade-maintenance-tasks}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在开始升级之前，务必要遵循以下维护任务，以确保系统已准备就绪，并且在出现问题时可以回滚：

* [确保足够的磁盘空间](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [完全备份AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [备份对/etc的更改](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [生成quickstart.properties文件](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [配置工作流和审核日志清除](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [安装、配置和运行升级前任务](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [禁用自定义登录模块](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [从/install目录中删除更新](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [停止任何冷备用实例](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [禁用自定义计划作业](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [执行脱机修订版清理](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [执行数据存储垃圾收集](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [根据需要升级数据库模式](pre-upgrade-maintenance-tasks.md#upgrade-the-database-schema-if-needed)
* [删除可能阻碍升级的用户](pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)
* [旋转日志文件](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## 确保足够的磁盘空间 {#ensure-sufficient-disk-space}

执行升级时，除了内容和代码升级活动之外，还需要执行存储库迁移。 迁移将以新的Tar区段格式创建存储库的副本。 因此，您需要足够的磁盘空间来保留第二个可能更大的存储库版本。

## 完全备份AEM {#fully-back-up-aem}

AEM应在开始升级之前完全备份。 确保备份您的存储库、应用程序安装、数据存储和Mongo实例（如果适用）。 有关备份和恢复AEM实例的更多信息，请参阅 [备份和恢复](/help/sites-administering/backup-and-restore.md).

## 备份对/etc的更改 {#backup-changes-etc}

升级过程能够很好地维护和合并来自 `/apps` 和 `/libs` 存储库中的路径。 对 `/etc` 路径（包括ContextHub配置）通常需要在升级后重新应用这些更改。 而升级将生成任何无法合并的更改的备份副本 `/var`，我们建议您在开始升级之前手动备份这些更改。

## 生成quickstart.properties文件 {#generate-quickstart-properties}

从jar文件启动AEM时， `quickstart.properties` 文件将在 `crx-quickstart/conf`. 如果AEM过去只是使用启动脚本启动，则此文件将不存在，并且升级将失败。 确保检查此文件是否存在，如果不存在，请从jar文件中重新启动AEM。

## 配置工作流和审核日志清除 {#configure-wf-audit-purging}

的 `WorkflowPurgeTask` 和 `com.day.cq.audit.impl.AuditLogMaintenanceTask` 任务需要单独的OSGi配置，如果没有这些配置，将无法正常工作。 如果在升级前任务执行期间失败，则最可能的原因是缺少配置。 因此，如果您不希望运行这些任务，请确保为这些任务添加OSGi配置，或从升级前优化任务列表中完全删除它们。 有关配置工作流清除任务的文档，请参阅 [管理工作流实例](/help/sites-administering/workflows-administering.md) 和审核日志维护任务配置可在 [AEM 6中的审核日志维护](/help/sites-administering/operations-audit-log.md).

有关在CQ 5.6上清除工作流和审核日志，以及在AEM 6.0上清除审核日志，请参阅 [清除工作流和审核节点](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).

## 安装、配置和运行升级前任务 {#install-configure-run-pre-upgrade-tasks}

由于AEM允许的自定义级别，环境通常不遵循统一的升级方式。 这就使得创建标准化升级过程变得十分困难。

在以前的版本中，也很难对已停止或无法安全恢复的AEM升级进行升级。 这会导致需要重新启动完整升级过程，或执行了有缺陷的升级而未触发任何警告的情况。

为了解决这些问题，Adobe在升级过程中添加了多项增强功能，使其更具弹性且对用户更友好。 必须手动执行之前的升级前维护任务正在优化和自动执行。 此外，还增加了升级后报告，以便对该过程进行充分审查，希望更容易找到任何问题。

升级前维护任务当前分散在手动部分或完全执行的各种界面上。 AEM 6.3中引入的升级前维护优化使能够以统一的方式触发这些任务并能够按需检查其结果。

升级前优化步骤中包含的所有任务都与AEM 6.0以后的所有版本兼容。

### 如何设置 {#how-to-set-it-up}

在AEM 6.3及更高版本中，快速入门Jar中包含升级前维护优化任务。 如果您从旧版AEM 6升级，则可通过单独的包获取这些包，您可以从包管理器中下载这些包。

您可以在以下位置找到包：

* [从AEM 6.0升级](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [从AEM 6.1升级](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [从AEM 6.2升级](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62)

### 如何使用 {#how-to-use-it}

的 `PreUpgradeTasksMBean` OSGi组件预配置了一系列升级前维护任务，这些任务可以一次全部运行。 您可以按照以下过程配置任务：

1. 通过浏览到 `https://serveraddress:serverport/system/console/configMgr`

1. 搜索“**预升级任务**“ ”，然后单击第一个匹配的组件。 组件的全名为 `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. 修改需要运行的维护任务列表，如下所示：

   ![1487758925984](assets/1487758925984.png)

任务列表因用于启动实例的运行模式而异。 以下是每个维护任务所针对的运行模式描述。

<table> 
 <tbody> 
  <tr> 
   <td><strong>任务</strong></td> 
   <td><strong>运行模式</strong></td> 
   <td><strong>注释</strong></td> 
  </tr> 
  <tr> 
   <td><code>TarIndexMergeTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>DataStoreGarbageCollectionTask</code></td> 
   <td>crx2</td> 
   <td>会进行标记和扫描。 对于共享数据存储，请删除此步骤并运行<br /> 在执行之前，请手动或正确准备实例。</td> 
  </tr> 
  <tr> 
   <td><code>ConsistencyCheckTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>WorkflowPurgeTask</code></td> 
   <td>crx2/crx3</td> 
   <td>必须先配置AdobeGranite工作流清除配置OSGi，然后才能运行。</td> 
  </tr> 
  <tr> 
   <td><code>GenerateBundlesListFileTask</code></td> 
   <td>crx2/crx3</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>RevisionCleanupTask</code></td> 
   <td>crx3</td> 
   <td>对于AEM 6.0到6.2上的TarMK实例，请手动运行离线修订清理。</td> 
  </tr> 
  <tr> 
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td> 
   <td>crx3</td> 
   <td>运行前必须配置审核日志清除计划程序OSGi配置。</td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` 正在使用标记和扫描阶段调用数据存储垃圾收集操作（如果使用）。 对于使用共享数据存储的部署，请确保重新配置或正确准备实例，以避免删除其他实例引用的项目。 这可能需要在触发此升级前任务之前，在所有实例上手动运行标记阶段。

### 升级前运行状况检查的默认配置 {#default-configuration-of-the-pre-upgrade-health-checks}

的 `PreUpgradeTasksMBeanImpl` OSGi组件预配置了一个列表，其中包含要在 `runAllPreUpgradeHealthChecks` 方法调用：

* **系统** - granite维护运行状况检查所使用的标记

* **预升级**  — 这是一个自定义标记，可添加到所有运行状况检查中，您可以设置这些检查在升级前运行

该列表是可编辑的。 您可以使用加号 **(+)** 减号 **(-)** 按钮以添加更多自定义标记，或删除默认标记。

**MBean方法**

可以使用 [JMX控制台](/help/sites-administering/jmx-console.md).

您可以通过以下方式访问MBean:

1. 转到JMX控制台(位于 *https://serveraddress:serverport/system/console/jmx*
1. 搜索 **预升级任务** 并单击结果

1. 从 **操作** 选择 **调用** 在以下窗口中。

以下是 `PreUpgradeTasksMBeanImpl` 公开：

<table> 
 <tbody> 
  <tr> 
   <td><strong>方法名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeTasksNames()</code></td> 
   <td>信息</td> 
   <td>显示可用升级前维护任务名称的列表。</td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td> 
   <td>信息</td> 
   <td>显示升级前运行状况检查标记名称的列表。</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeTasks()</code></td> 
   <td>动作</td> 
   <td>运行列表中的所有升级前维护任务。</td> 
  </tr> 
  <tr> 
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td> 
   <td>动作</td> 
   <td>运行升级前维护任务，并将给定的名称作为参数。</td> 
  </tr> 
  <tr> 
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>检查 <code>runAllPreUpgradeTasksmaintenance</code> 任务当前正在运行。</td> 
  </tr> 
  <tr> 
   <td><code>getAnyPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>检查当前是否正在运行任何升级前维护任务，并<br /> 返回包含当前正在运行任务名称的数组。</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td> 
   <td>动作</td> 
   <td>显示升级前维护任务的确切运行时间，其名称为参数。</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td> 
   <td>动作</td> 
   <td>显示升级前维护任务的上次运行状态，其名称为参数。</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td> 
   <td>动作</td> 
   <td><p>运行所有升级前运行状况检查，并将其状态保存在名为 <code>preUpgradeHCStatus.properties</code> 位于sling主路径中的。 如果 <code>shutDownOnSuccess</code> 参数设置为 <code>true</code>，则AEM实例将被关闭，但前提是所有升级前运行状况检查均处于“正常”状态。</p> <p>属性文件将用作将来任何升级的先决条件<br /> 如果进行升级前运行状况检查，则升级过程将停止<br /> 执行失败。 如果要忽略预升级的结果<br /> 运行状况检查并启动升级，您可以删除文件。</p> </td> 
  </tr> 
  <tr> 
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td> 
   <td>动作</td> 
   <td>列出在<br /> 升级到指定的AEM版本。 目标AEM版本必须为<br /> 作为参数给定。</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>MBean方法可通过以下方式调用：
>
>* JMX控制台
>* 连接到JMX的任何外部应用程序
>* cURL
>


## 禁用自定义登录模块 {#disable-custom-login-modules}

>[!NOTE]
>
>仅当您从AEM 5版本升级时，才需要执行此步骤。 可以完全跳过该页面，以便从旧版AEM 6进行升级。

自定义方式 `LoginModules` 在Apache Oak中，针对存储库级别的身份验证进行了根本性更改。

在使用CRX2配置的AEM版本中， `repository.xml` 文件，而从AEM 6开始，可通过Web控制台在Apache Felix JAAS配置工厂服务中完成。

因此，升级后必须禁用并为Apache Oak重新创建任何现有配置。

禁用JAAS配置中定义的自定义模块 `repository.xml`，您需要修改配置以使用默认 `LoginModule`，如下例所示：

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>有关更多信息，请参阅 [使用外部登录模块进行身份验证](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>例如 `LoginModule` 在AEM 6中进行配置，请参阅 [使用AEM 6配置LDAP](/help/sites-administering/ldap-config.md).

## 从/install目录中删除更新 {#remove-updates-install-directory}

>[!NOTE]
>
>在关闭AEM实例后，仅从crx-quickstart/install目录中删除包。 在开始就地升级过程之前，这将是最后的步骤之一。

删除通过 `crx-quickstart/install` 目录。 这将防止在更新完成后，在新AEM版本之上意外安装旧修补程序和Service Pack。

## 停止任何冷备用实例 {#stop-tarmk-coldstandby-instance}

如果使用TarMK冷备用，请停止任何冷备用实例。 这将保证在升级中出现问题时，有效地恢复在线状态。 成功完成升级后，需要从已升级的主实例重建冷备用实例。

## 禁用自定义计划作业 {#disable-custom-scheduled-jobs}

禁用应用程序代码中包含的任何OSGi计划作业。

## 执行脱机修订版清理 {#execute-offline-revision-cleanup}

>[!NOTE]
>
>此步骤仅对于TarMK安装是必需的

如果使用TarMK，则应在升级前执行脱机修订版清理。 这将使存储库迁移步骤和后续升级任务的执行速度大大提高，并有助于确保在升级完成后能够成功执行在线修订版清理。 有关运行脱机修订版清理的信息，请参阅 [执行脱机修订版清理](https://helpx.adobe.com/experience-manager/6-2/sites-deploying/storage-elements-in-aem-6.html#performing-offline-revision-cleanup).

## 执行数据存储垃圾收集 {#execute-datastore-garbage-collection}

>[!NOTE]
>
>仅对于运行crx3的实例，此步骤是必需的

在CRX3实例上运行修订清理后，您应该运行数据存储垃圾收集以删除数据存储中任何未引用的Blob。 有关说明，请参阅 [数据存储垃圾收集](/help/sites-administering/data-store-garbage-collection.md).

## 删除可能阻碍升级的用户 {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>只有在以下情况下，才需要执行此升级前维护任务：
>
>* 您是从AEM 6.3以前的版本升级
>* 在升级过程中，您会遇到以下任何错误。


有些例外情况是，服务用户在旧版AEM中可能被错误地标记为常规用户。

如果发生这种情况，升级将失败，并出现如下消息：

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

要解决此问题，请确保执行以下操作：

要解决此问题，请确保执行以下操作：

* 将实例与生产流量分离
* 创建导致问题的用户的备份。 您可以通过包管理器执行此操作。 有关更多信息，请参阅 [如何使用包](/help/sites-administering/package-manager.md).
* 删除导致问题的用户。 以下是可能属于此类别的用户列表：
   * dynamic-media-replication
   * communities-ugc-writer
   * communities-utility-reader
   * communities-user-admin
   * oauthservice
   * sling-scripting

## 根据需要升级数据库模式 {#upgrade-the-database-schema-if-needed}

通常，用于持久性的基础Apache Oak堆栈AEM将在需要时负责升级数据库架构。

但是，当架构无法自动升级时，可能会出现这些情况。 这些环境通常是高安全性环境，数据库在权限非常有限的用户下运行。 如果发生这种情况，AEM将继续使用旧架构。

为防止出现这种情况，您需要按照以下过程升级架构：

1. 关闭需要升级的AEM实例。
1. 升级数据库模式。 请查阅您的数据库类型的文档，以了解实现此目的所需使用的工具。

   有关Oak如何处理模式升级的更多信息，请参阅 [Apache网站上的此页面](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. 继续升级AEM。

## 旋转日志文件 {#rotate-log-files}

我们建议您在开始升级之前存档当前日志文件。 这样，在升级期间和升级后便可以更轻松地监视和扫描日志文件，以识别和解决可能出现的任何问题。
