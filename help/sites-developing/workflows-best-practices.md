---
title: 工作流最佳实践
seo-title: 工作流最佳实践
description: 'null'
seo-description: 'null'
uuid: 79be4055-c2ef-428e-9054-103c6cfde1d2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 0be8b88c-6f57-4dcc-ae11-77b378a2decd
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '1922'
ht-degree: 0%

---


# 工作流最佳实践{#workflow-best-practices}

工作流使您能够自动完成Adobe Experience Manager(AEM)活动。

它们通常表示AEM环境中发生的大量处理，因此，当自定义工作流步骤未根据最佳实践编写，或者现成工作流未配置为尽可能高效地运行时，系统会因此受到影响。

因此，强烈建议仔细规划工作流实施。

## 配置 {#configuration}

在配置工作流程（自定义和／或现成流程）时，应牢记以下几点：

### 临时工作流 {#transient-workflows}

要优化高摄取负载，您可以将工作流定 [义为临时工作流](/help/sites-developing/workflows.md#transient-workflows)。

当工作流为临时工作流时，与中间工作步骤相关的运行时数据在运行时不会保留在JCR中（当然会保留输出再现）。

优势包括：

* 缩短工作流处理时间； 10%。
* 显着减少存储库增长。
* 不再需要CRUD工作流进行清除。
* 此外，它还将TAR文件的数量减少到压缩。

>[!CAUTION]
>
>如果您的企业要求您出于审计目的而保留／存档工作流运行时数据，请不要启用此功能。

### 调整DAM工作流 {#tuning-dam-workflows}

有关DAM工作流的性能调整指南，请参 [阅《AEM Assets性能调整指南](/help/assets/performance-tuning-guidelines.md)》。

### 配置并发工作流的最大数量 {#configure-the-maximum-number-of-concurrent-workflows}

AEM可以允许多个工作流线程同时运行。 默认情况下，线程数配置为系统上处理器核心数的一半。

如果正在执行的工作流需要系统资源，这可能意味着AEM将几乎不能用于其他任务，如渲染创作UI。 因此，在批量图像上传等活动期间，系统可能不灵活。

要解决此问题，Adobe建议将 **最大并行作业** (Maximum Parallel Jobs)的数量配置为系统上处理器核心数的一半到四分之三。 这应允许系统在处理这些工作流时保持响应能力。

要配置最 **大并行作业**，您可以执行以下任一操作：

* 从AEM **[Web控制台](/help/sites-deploying/configuring-osgi.md)**，配置OSGi配置； 对于&#x200B;**队列： Granite Workflow Queue**(一&#x200B;**种Apache Sling作业队列配置**)。

* 通过AEM Web控制台的 **Sling Jobs** 选项配置队列； 对于作 **业队列配置： Granite Workflow Queue**，位 `http://localhost:4502/system/console/slingevent`置。

此外，Granite工作流外部进程作 **业队列也有单独的配置**。 它用于启动外部二进制文件(如 **InDesign Server** 或 **图像标记**)的工作流

### 配置单个作业队列 {#configure-individual-job-queues}

在某些情况下，配置单个作业队列以基于单个作业控制并发线程或其他队列选项非常有用。 您可以通过Apache Sling作业队列配置工厂从Web控制台 **添加和配置单个队列** 。 要查找要列表的适当主题，请执行工作流模型并在Sling作业控制台 **中查找** ; 例如，在 `http://localhost:4502/system/console/slingevent`。

也可以为临时工作流添加单个作业队列。

### 配置工作流清除 {#configure-workflow-purging}

在标准安装中，AEM提供维护控制台，可安排和配置每日和每周的维护活动; 例如，在：

`http://localhost:4502/libs/granite/operations/content/maintenance.html`

默认情况下，“ **每周维护** ”窗 **口具有“工作流清除** ”任务，但需要先配置此，才能运行它。 要配置工作流清除，必须在 **Web控制台中添加新的Adobe** “Granite工作流清除配置”。

有关AEM中维护任务的更多详细信息，请参 [阅操作仪表板](/help/sites-administering/operations-dashboard.md)。

## 自定义 {#customization}

编写自定义工作流程时，应牢记一些事情。

### 位置 {#locations}

工作流模型、启动器、脚本和通知的定义会根据类型保存在存储库中； 即开箱即用、自定义等。

>[!NOTE]
>
>另请参 [阅AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md)。

#### 位置——工作流模型 {#locations-workflow-models}

工作流模型根据类型存储在存储库中：

* 开箱即用的工作流程设计采用以下路径：

   `/libs/settings/workflow/models/`

   >[!CAUTION]
   >
   >不要：
   >
   >* 将任何自定义工作流模型放置在此文件夹中
   >* 编辑任何内容 `/libs`

   >
   >由于任何更改可能会在升级时或在安装修补程序、累积修复包或服务包时被覆盖。

* 自定义工作流设计位于以下位置：

   ```
   /conf/global/settings/workflow/models/...
   ```

* 运行时工作流程设计（现成和自定义）都保留在以下路径下：

   `/var/workflow/models/`

* 旧版工作流程设计（设计时和运行时）按以下路径进行：

   `/etc/workflow/models/`

   >[!NOTE]
   >
   >如果这些设计是使 *用AEM UI编辑*，则详细信息将复制到新位置。

#### 位置——工作流启动器 {#locations-workflow-launchers}

工作流启动器定义也根据类型存储在存储库中：

* 开箱即用的工作流启动器位于以下路径下：

   `/libs/settings/workflow/launcher/`

   >[!CAUTION]
   >
   >不要：
   >
   >* 将任何自定义工作流启动程序放入此文件夹中
   >* 编辑任何内容 `/libs`

   >
   >由于任何更改可能会在升级时或在安装修补程序、累积修复包或服务包时被覆盖。

* 自定义工作流启动器位于：

   ```
   /conf/global/settings/workflow/launcher/... 
   ```

* 旧版工作流启动程序位于以下路径下：

   `/etc/workflow/launcher/`

   >[!NOTE]
   >
   >如果这些定义是 *使用AEM UI编辑*，则详细信息将复制到新位置。

#### 位置——工作流脚本 {#locations-workflow-scripts}

工作流脚本还根据类型存储在存储库中：

* 开箱即用的工作流脚本位于以下路径下：

   `/libs/workflow/scripts/`

   >[!CAUTION]
   >
   >不要：
   >
   >* 将任何自定义工作流脚本放置在此文件夹中
   >* 编辑任何内容 `/libs`

   >
   >由于任何更改可能会在升级时或在安装修补程序、累积修复包或服务包时被覆盖。

* 自定义工作流脚本位于以下位置：

   ```
   /apps/workflow/scripts/... 
   ```

* 旧版工作流脚本保存在以下路径中：

   `/etc/workflow/scripts/`

#### 位置——工作流通知 {#locations-workflow-notifications}

工作流通知也根据类型存储在存储库中：

* 现成的工作流通知定义位于以下路径下：

   `/libs/settings/workflow/notification/`

   >[!CAUTION]
   >
   >不要：
   >
   >* 将任何自定义工作流通知定义放置在此文件夹中
   >* 编辑任何内容 `/libs`

   >
   >由于任何更改可能会在升级时或在安装修补程序、累积修复包或服务包时被覆盖。

* 自定义工作流通知定义位于以下位置：

   ```
   /conf/global/settings/workflow/notification/... 
   ```

   >[!NOTE]
   >
   >如果要覆盖工作流通知文本，请在以下位置创建一个覆盖路径：
   >
   >
   >`/conf/global/settings/workflow/notification/<path-under-libs>`

* 传统工作流通知定义位于以下路径下：

   `/etc/workflow/notification/`

### 进程会话 {#process-sessions}

与任何自定义开发一样，始终建议尽可能使用用户的会话：

* 以最好地遵守安全准则
* 允许系统管理会话的打开和关闭

实施工作流进程时：

* 将提供工作流会话，并且应使用该会话，除非有令人信服的理由不这样做。
* 不应根据工作流步骤创建新会话，因为这会导致状态不一致以及工作流引擎中可能出现的并发问题。
* 您不应从工作流中的流程步骤中获取新的JCR会话； 您应将流程步骤API提供的工作流会话调整为jcr会话。 例如：

```
public void execute(WorkItem item, WorkflowSession workflowSession, MetaDataMap args) throws WorkflowException {
        // to obtain a jcr session:
        javax.jcr.Session jcrSession = workflowSession.adaptTo(javax.jcr.Session.class);

        // to obtain a sling resource resolver:
        org.apache.sling.api.resource.ResourceResolver slingResourceResolver = workflowSession.adaptTo(org.apache.sling.api.resource.ResourceResolver.class);
```

保存会话：

* 在工作流进程中，如 `WorkflowSession` 果正在用于修改存储库，则不显式保存会话——工作流将在会话完成时保存会话。
* `Session.Save` 不应从工作流步骤中调用：

   * 建议采用工作流jcr会话； 然后， `save` 则无需这样做，因为工作流引擎在工作流完成执行后自动保存会话。
   * 不建议对进程步骤创建自己的jcr会话。

* 通过消除不必要的节省，您可以减少开销，从而提高工作流的效率。

>[!CAUTION]
>
>如果您确实创建了自己的jcr会话，则需要保存它。

### 最小化启动器的数量／范围 {#minimize-the-number-scope-of-launchers}

有一个监听器负责注册的所有工 [作流启动](/help/sites-administering/workflows-starting.md#workflows-launchers) 器：

* 它将侦听其他启动器的全局属性中指定的所有路径更改。
* 分派事件时，工作流引擎将评估每个启动器以确定它是否应运行。

创建过多启动器将导致评估过程运行更慢。

在单个启动器上在存储库的根中创建全局事件路径将导致工作流引擎侦听并评估对存储库中每个节点的创建／修改。 因此，建议仅创建所需的启动器，并尽可能使覆盖路径具体化。

由于这些启动器对工作流行为的影响，禁用任何未使用的现成启动器也非常有用。

### Launcher的配置增强功能 {#configuration-enhancements-for-launchers}

自定义启 [动器配置](/help/sites-administering/workflows-starting.md#workflows-launchers) 已得到增强，可支持以下各项：

* 将多个条件“AND”结合在一起。
* 在单个条件下具有OR条件。
* 根据功能标志是启用还是禁用，禁用／启用启动器。
* 在启动器条件中支持正则表达式。

### 不要开始其他工作流的工作流 {#do-not-start-workflows-from-other-workflows}

工作流可以带来大量开销，无论是在内存中创建的对象，还是在存储库中跟踪的节点。 因此，最好让工作流在其内部进行处理，而不是开始其他工作流。

一个例子是对一组内容实施业务流程然后激活该内容的工作流。 最好创建一个激活每个这些节点的自定义工作流进程，而不是为每个需要发布的 **内容节点启动** “激活内容”模型。 此方法需要额外的开发工作，但执行时比为每个激活启动单独的工作流实例更加有效。

另一个示例是处理多个节点、创建工作流包、然后激活所述包的工作流。 您可以在创建包的步骤中更改工作流的有效负荷，然后调用该步骤以在同一工作流模型中激活该包，而不是先创建包，然后以包作为有效负荷启动单独的工作流。

### 处理程序前进 {#handler-advance}

设计工作流模型时，您可以选择在工作流步骤上启用处理程序。 或者，您也可以向工作流步骤中添加代码，以确定下一步应运行哪个步骤，然后执行它。

建议使用处理程序高级功能，因为它可提供更好的性能。

### 工作流阶段 {#workflow-stages}

您可以定义 [工作流阶段](/help/sites-developing/workflows.md#workflow-stages)，然后将任务/步骤分配到特定工作流阶段。

此信息用于在您单击收件箱中某个工作项的“工作流信 [**息”选项卡&#x200B;**时显示工作流的**&#x200B;进度&#x200B;**](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions)。 可以编辑现有工作流模型以添加阶段。

### 激活页面处理步骤 {#activate-page-process-step}

激活 **页面流程** (Activate Page Process)步骤将为您激活页面，但不会自动查找任何引用的DAM资产并激活这些资产。

如果您计划将此步骤用作工作流模型的一部分，请牢记这一点。

### 升级注意事项 {#upgrade-considerations}

升级实例时：

* 确保在升级实例之前备份任何自定义工作流模型。
* 确认您的自定义工作流不存储在位 [置下](#locations):

   * `/libs/settings/workflow/models/projects`

>[!NOTE]
>
>另请参 [阅AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md)。

## 系统工具 {#system-tools}

有许多系统工具可用于帮助监视、维护和排除工作流故障。 以下所有示例URL `localhost:4502`均使用，但应可用于任何作者实例( `<hostname>:<port>`)。

### Sling作业处理控制台 {#sling-job-handling-console}

`http://localhost:4502/system/console/slingevent`

Sling作业处理控制台将显示：

* 上次重新启动后系统中作业状态的统计信息。
* 它还将显示所有作业队列的配置，并提供在配置管理器中编辑这些队列的快捷方式。

### 工作流报告工具 {#workflow-report-tool}

工作流报告工具将在6.3中删除，以防止性能降级。

### 工作流维护操作MBean {#workflow-maintenance-operations-mbean}

`http://localhost:4502/system/console/jmx/com.adobe.granite.workflow:type=Maintenance`

工作流维护MBean公开了一些有用的维护例程，如清除已完成的工作流和检索工作流统计信息。

## 更多信息 {#further-information}

有关更多信息，请参阅：

* [使用工作流](/help/sites-authoring/workflows.md)
* [管理工作流](/help/sites-administering/workflows.md)
* [开发和扩展工作流](/help/sites-developing/workflows.md)
* [性能优化](/help/sites-deploying/configuring-performance.md)