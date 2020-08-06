---
title: 延迟内容迁移
seo-title: 延迟内容迁移
description: 了解AEM 6.4中的延迟内容迁移。
seo-description: 了解AEM 6.4中的延迟内容迁移。
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
translation-type: tm+mt
source-git-commit: ba16a6870bc621a585b2b2d7c7536baef05adc72
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 6%

---


# 延迟内容迁移{#lazy-content-migration}

为了向后兼容，从AEM 6.3开 **始的** /etc **和/content中的内容和配置不** 会随升级一起被触及或立即转换。 这样做是为了确保客户应用程序对这些结构的依赖性保持不变。 与这些内容结构相关的功能仍然相同，即使开箱即用的AEM 6.4内容将托管在其他位置。

虽然并非所有这些位置都可以自动转换，但也有一些延迟 `CodeUpgradeTasks` 称为延迟内容迁移。 这允许客户通过使用此系统属性重新启动实例来触发这些自动转换：

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

这将导致迁 `CodeUpgradeTasks` 移期间执行迁移。

虽然目标是有效执行，但此升级过程是同步的，因此会因需要处理的内容数量而导致停机。 建议在生产系统之前评估阶段环境的执行时间，以根据维护窗口进行计划。

由于这通常也需要调整应用程序，因此应该与相应的应用程序部署一起执行此活动。

以下是6.4中 `CodeUpgradeTasks` 引入的完整列表:

| **名称** | **与AEM之前的版本相关** | **迁移类型** | **详细信息** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | 即时 |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | 即时 | 检测已 `LiveRelationShips` 删除 `VersionStorage` 的所有属性，并向父级添加排除属性 |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | 即时 | 在默认设置下重新构建云服务以确保安全 |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | 即时 | 删除从/content到/conf **的基于属性的链** 接 **(由OSGi机制替换** )，并生成相应的OSGi配置 |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | 即时 | 由于merge_preserve处理安全性（默认情况下）会拒绝规则覆盖给定的权限，因此需要在升级时重新排序 |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | 即时 | 检测使用Html5SmartFile构件的组件，在内容中搜索组件的使用实例并重新构建持久性，有效地将二进制文件向下移动一个级别，而不将其存储在组件级别。 |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | 即时 | 将旧样式项 **目从/etc** / **projects移至/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | 即时 | 将容器层引入层次结构（区域）并调整参照。 |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | 即时 | 将固定位置名称设置为目标组件。 |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | 即时 | 对早于6.2结构、实例和通知的工作流模型进行复杂转换，然后从备份位置从/var/ **backup合并回来** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | 即时 | 将资源、自定义元数据模式和处理用户档案 **从** /app移 **动到/conf** ，并将元数据模式和元数据用户档案表从coral2转换到coral3。 |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | 即时 | 将资产和自定义搜索彩块 **化从** /app移 **动到/conf** ，并将元数据模式和元数据用户档案表单从coral2转换到coral3。 |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | 即时 | 更新收件箱用于对收件箱项目进行排序的项目（调整元数据以进行有效排序） |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | 即时 | 通过替换到/conf的相对路径代替/apps，调整 **文件夹** 上的 **metadataSchema属性** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | 即时 | 调整导航结构 |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | 即时 | 从/libs和/app移动监视仪表板 **的自定****义配置** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | 即时 | 转换资产中的processingProfile属性（直至6.1），以匹配6.3及更高版本的结构。 还调整用户档案到/conf的相 **对路径** ，代替/ **apps**。 |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | 即时 | 升级任务，在升级时删除废弃的CRXDE Lite和Web控制台菜单项。 |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | 延迟 | 移动SRP云配置、社区观察词配置、清理 **/etc** /social **和/etc/enablement** （在延迟迁移运行时，需要调整任何引用和数据——应用程序部分不再依赖此结构）。 |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | 延迟 | 清除 **/etc/cloudsettings** （包含ContextHub配置）。 配置在首次访问时自动迁移。 如果延迟内容迁移是在升级时启动的，则必须在升级前通过包保留此内容 **** ，并重新安装该内容，以便隐式转换开始，并在完成后卸载包。 |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | 延迟 | 在用户用户档案节点中根据标题调整旧版标题结构。 |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | 延迟 | 将商务内容 **从/etc** /commerce迁 **移到/var/commerce**。 在迁移期间，移动内容并更新对移动内容的引用以反映新位置。 |
