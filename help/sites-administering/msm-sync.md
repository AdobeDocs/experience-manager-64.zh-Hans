---
title: 配置 Live Copy 同步
seo-title: Configuring Live Copy Synchronization
description: 了解如何配置Live Copy同步。
seo-description: Learn about configuring Live Copy Synchronization.
uuid: a14fab89-fd1c-4fec-a9e0-9f6511f764a6
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c491f0f3-375d-4203-bdf3-234987bbf685
feature: Multi Site Manager
exl-id: 42b92993-abde-4ae4-8f0d-44166a3ea22e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2731'
ht-degree: 25%

---

# 配置 Live Copy 同步{#configuring-live-copy-synchronization}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

执行以下任务以控制Live Copy如何以及何时与其源内容同步。

* 确定现有的转出配置是否满足您的要求，或者您是否需要创建一个或多个。
* 指定要用于Live Copy的转出配置。

## 已安装和自定义转出配置 {#installed-and-custom-rollout-configurations}

本节提供有关已安装的转出配置及其使用的同步操作的信息，以及如果需要，如何创建自定义配置。

>[!CAUTION]
>
>正在更新或更改现成的（已安装）转出配置 **not** 推荐。 如果需要自定义实时操作，则应将其添加到自定义转出配置中。

### 转出触发器 {#rollout-triggers}

每个转出配置都使用一个导致转出发生的转出触发器。 转出配置可以使用以下触发器之一：

* **转出时**:的 **转出** 命令，或者 **同步** 命令。

* **修改**：修改源页面。

* **激活**：激活源页面。

* **停用**：停用源页面。

>[!NOTE]
>
>使用修改触发器可能会影响性能。请参阅 [MSM 最佳实践](/help/sites-administering/msm-best-practices.md#onmodify)以了解更多信息。

### 已安装的转出配置 {#installed-rollout-configurations}

下表列出了随AEM一起安装的转出配置。 该表包含每个转出配置的触发器和同步操作。如果已安装的转出配置操作不符合您的要求，您可以 [创建新转出配置](#creating-a-rollout-configuration).

<table> 
 <tbody> 
  <tr> 
   <th>名称</th> 
   <th>描述</th> 
   <th>触发器</th> 
   <th>同步操作<br /> <br /> 另请参阅 <a href="#installed-synchronization-actions">已安装的同步操作</a></th> 
  </tr> 
  <tr> 
   <td>标准转出配置</td> 
   <td>标准转出配置，允许在触发转出时启动转出流程，并执行以下操作：创建、更新、删除内容和对子节点进行排序。</td> 
   <td>转出</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> productUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>在 Blueprint 激活时激活</td> 
   <td>在发布源时发布Live Copy。</td> 
   <td>激活</td> 
   <td>targetActivate</td> 
  </tr> 
  <tr> 
   <td>在 Blueprint 停用时停用</td> 
   <td>在停用源时停用Live Copy。</td> 
   <td>停用</td> 
   <td>targetDeactivate<br /> </td> 
  </tr> 
  <tr> 
   <td>修改时推送</td> 
   <td><p>在修改源时将内容推送到Live Copy。</p> <p>当此转出配置使用On Modification触发器时，请谨慎使用此转出配置。</p> </td> 
   <td>修改</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> </td> 
  </tr> 
  <tr> 
   <td>修改时推送（简略）</td> 
   <td><p>在修改Blueprint页面时将内容推送到Live Copy，而不更新引用（例如，对于浅层副本）。</p> <p>当此转出配置使用On Modification触发器时，请谨慎使用此转出配置。</p> </td> 
   <td>修改</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>提升发布内容</td> 
   <td>用于提升发布页面的标准转出配置。</td> 
   <td>转出</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> markLiveRelationship</td> 
  </tr> 
  <tr> 
   <td>目录页面内容转出配置</td> 
   <td>从目录 Blueprint 中应用页面模板。</td> 
   <td>转出</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> productCreateUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>目录页面更新转出配置</td> 
   <td>从目录Blueprint中应用目标属性。 必须在目录页面内容转出配置后运行。</td> 
   <td>转出</td> 
   <td>catalogRolloutHooks</td> 
  </tr> 
  <tr> 
   <td>DPS 发布转出配置</td> 
   <td>DPS发布转出配置，该配置允许在转出触发器上启动转出进程，同时在初始转出时排除FolioProducer绑定属性</td> 
   <td>转出</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> dpsMetadataFilter</td> 
  </tr> 
  <tr> 
   <td>旧版(5.6.0)目录转出配置</td> 
   <td>已弃用。请使用 Catalog Generator 代替 MSM 进行目录转出。</td> 
   <td>转出</td> 
   <td>editProperties</td> 
  </tr> 
 </tbody> 
</table>

### 已安装的同步操作 {#installed-synchronization-actions}

下表列出了随AEM一起安装的同步操作。 如果已安装的操作不符合您的要求，您可以 [创建新的同步操作](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).

<table> 
 <tbody> 
  <tr> 
   <th>操作名称</th> 
   <th>描述</th> 
   <th>属性<br /> </th> 
  </tr> 
  <tr> 
   <td>contentCopy</td> 
   <td>如果Live Copy上不存在源节点，则将节点复制到Live Copy。 <a href="#excluding-properties-and-node-types-from-synchronization">配置CQ MSM内容复制操作服务</a> 指定要排除的节点类型、段落项和页面属性。 <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentDelete</td> 
   <td><p>删除源上不存在的Live Copy节点。 <a href="#excluding-properties-and-node-types-from-synchronization">配置 CQ MSM 内容删除操作服务</a>，以指定要排除的节点类型、段落项和页面属性。 </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentUpdate</td> 
   <td>使用源中的更改更新Live Copy内容。 <a href="#excluding-properties-and-node-types-from-synchronization">配置CQ MSM内容更新操作服务</a> 指定要排除的节点类型、段落项和页面属性。 <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>editProperties</td> 
   <td><p>编辑Live Copy的属性。 editMap属性确定要编辑的属性及其值。 editMap属性的值必须使用以下格式：</p> <p><code>[property_name_1]#[current_value]#</code>[new_value],<br /> <code>[property_name_2]#[current_value]#</code>[new_value],<br /> ... ,<br /> <code>[property_name_n]#[current_value]#</code>[new_value]</p> <p>的 <code>current_value</code> 和 <code>new_value</code> 项目是正则表达式。 <br /> </p> <p>例如，请考虑editMap的以下值：</p> <p><code>sling:resourceType#/</code>(contentpage|homepage)#/<br /> mobilecontentpage，<br /> cq:template#/contentpage#/mobilecontentpage</p> <p>此值编辑Live Copy节点的属性，如下所示：</p> 
    <ul> 
     <li>的 <code>sling:resourceType</code> 属性设置为 <code>contentpage</code> 或 <code>homepage</code> 设置为 <code>mobilecontentpage.</code></li> 
     <li>的 <code>cq:template</code> 设置为的属性 <code>contentpage</code> 设置为 <code>mobilecontentpage.</code></li> 
    </ul> </td> 
   <td><p> </p> <p>editMap:（字符串）标识属性、当前值和新值。 有关信息，请参阅描述。<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>notify</td> 
   <td>发送已转出页面的页面事件。 要接收通知，首先需要订阅转出事件。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>orderChildren</td> 
   <td>在Live Copy中，它会根据Blueprint上的顺序对子项（节点）进行排序<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>referencesUpdate</td> 
   <td><p>在Live Copy上，此同步操作会更新引用，如链接。<br /> 它会搜索Live Copy页面中指向Blueprint中资源的路径。 找到后，它会更新路径，以指向Live Copy（而不是Blueprint）中的相关资源。 具有 Blueprint 外部目标的引用不会发生更改。</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">配置 CQ MSM 引用更新操作服务</a>，以指定要排除的节点类型、段落项和页面属性。 </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetVersion</td> 
   <td><p>创建Live Copy的版本。</p> <p>此操作必须是转出配置中包含的唯一同步操作。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetActivate</td> 
   <td><p>激活Live Copy。</p> <p>此操作必须是转出配置中包含的唯一同步操作。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetDeactivate</td> 
   <td><p>停用Live Copy。</p> <p>此操作必须是转出配置中包含的唯一同步操作。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>工作流</td> 
   <td><p>启动由Target属性定义的工作流（仅限页面），并将Live Copy作为有效负载。</p> <p>目标路径是模型节点的路径。</p> </td> 
   <td>目标：（字符串）工作流模型的路径。<br /> </td> 
  </tr> 
  <tr> 
   <td>强制</td> 
   <td><p>将Live Copy页面上多个ACL的权限设置为特定用户组的只读权限。 配置了以下ACL:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_REMOVE</li> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>仅对页面使用此操作。</p> </td> 
   <td>目标：（字符串）您为其设置权限的组的ID。 <br /> </td> 
  </tr> 
  <tr> 
   <td>mandatoryContent</td> 
   <td><p>将Live Copy页面上多个ACL的权限设置为特定用户组的只读权限。 配置了以下ACL:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>仅对页面使用此操作。</p> </td> 
   <td>目标：（字符串）您为其设置权限的组的ID。 </td> 
  </tr> 
  <tr> 
   <td>mandatoryStructure</td> 
   <td>将Live Copy页面上的ActionSet.ACTION_NAME_REMOVE ACL的权限设置为特定用户组的只读权限。 仅对页面使用此操作。</td> 
   <td>目标：（字符串）您为其设置权限的组的ID。 </td> 
  </tr> 
  <tr> 
   <td>VersionCopyAction</td> 
   <td>如果Blueprint/源页面至少已发布一次，则使用已发布的版本创建Live Copy页面。 注意：此操作仅适用于基于已发布的源页面创建Live Copy页面，而不适用于更新现有Live Copy页面。 </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>PageMoveAction</td> 
   <td><p>在Blueprint中移动了页面后，将应用PageMoveAction。</p> <p>操作会复制（相关）LiveCopy页面，而不是从移动之前的位置移动到之后的位置。</p> <p>PageMoveAction不会更改LiveCopy页面在移动前所在位置的位置。 因此，对于连续的RolloutConfigurations，它的状态为不带Blueprint的LiveRelationhip。</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">配置 CQ MSM 页面移动操作服务</a>，以指定要排除的节点类型、段落项和页面属性。 </p> <p>此操作必须是转出配置中包含的唯一同步操作。</p> </td> 
   <td><p>prop_referenceUpdate:（布尔值）设置为true可更新引用。 默认值为true。</p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>productCreateUpdate</td> 
   <td>在目录中创建或更新产品资源。 此操作将用于以下任一情况： 
    <ul> 
     <li>生成或转出目录（或目录部分）</li> 
     <li>用户恢复产品组件的同步继承。</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>markLiveRelationship</td> 
   <td>表示启动项创建的内容存在实时关系。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>catalogRolloutHooks</td> 
   <td>执行特定于目录生成的转出挂接。 调用CatalogGenerator的executePageRolloutHooks和executeProductRolloutHooks方法。<br /> 请参阅AEM Javaoc中的com.adobe.cq.commerce.pim.api.CatalogGenerator 。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>productUpdate</td> 
   <td>更新产品目录Live Copy中的产品页面</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

### 创建转出配置 {#creating-a-rollout-configuration}

您可以 [创建转出配置](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) 当安装的转出配置不符合您的应用程序要求时：

* [创建转出配置](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
* [将同步操作添加到转出配置](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

然后，在Blueprint或Live Copy页面上设置转出配置时，您可以使用新的转出配置。

### 从同步中排除属性和节点类型 {#excluding-properties-and-node-types-from-synchronization}

您可以配置多个支持相应同步操作的 OSGi 服务，以便它们不会影响特定的节点类型和属性。例如，与AEM内部功能相关的许多属性和子节点不应包含在Live Copy中。 只应复制与页面用户相关的内容。

使用AEM时，可通过多种方法来管理此类服务的配置设置；请参阅 [配置OSGi](/help/sites-deploying/configuring-osgi.md) 以了解更多详细信息和建议的实践。

下表列出了可为其指定要排除的节点的同步操作。 该表提供了使用Web控制台配置的服务的名称，以及使用存储库节点配置的PID。

| 同步操作 | Web 控制台中的服务名称 | 服务 PID |
|---|---|---|
| contentCopy | CQ MSM 内容复制操作 | com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory |
| contentDelete | CQ MSM 内容删除操作 | com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory |
| contentUpdate | CQ MSM 内容更新操作 | com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory |
| PageMoveAction | CQ MSM 页面移动操作 | com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory |
| referencesUpdate | CQ MSM 引用更新操作 | com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory |

下表描述了您可以配置的属性：

<table> 
 <tbody> 
  <tr> 
   <th>Web控制台属性/ OSGi属性</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td><p>排除的节点类型</p> <p>cq.wcm.msm.action.excludednodetypes</p> </td> 
   <td>匹配要从同步操作中排除的节点类型的正则表达式.</td> 
  </tr> 
  <tr> 
   <td><p>排除的段落项</p> <p>cq.wcm.msm.action.excludedparagraphitems</p> </td> 
   <td>匹配要从同步操作中排除的段落项的正则表达式.</td> 
  </tr> 
  <tr> 
   <td><p>排除的页面属性</p> <p>cq.wcm.msm.action.excludedprops</p> </td> 
   <td>匹配要从同步操作中排除的页面属性的正则表达式.</td> 
  </tr> 
  <tr> 
   <td><p>忽略的 Mixin 节点类型</p> <p>cq.wcm.msm.action.ignoredMixin</p> </td> 
   <td>仅适用于CQ MSM内容更新操作。 与要从同步操作中排除的mixin节点类型名称匹配的正则表达式。</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>在经典UI中，LiveCopy页面的“页面属性”对话框中显示的锁定图标未反映“排除的页面属性”属性的配置。 即使对于从同步操作中排除的属性，也会显示锁图标。

>[!NOTE]
>
>在触屏UI中，另请参阅 [在页面属性上配置MSM锁定)](/help/sites-developing/extending-msm.md).

#### CQ MSM内容更新操作 — 排除项 {#cq-msm-content-update-action-exclusions}

默认情况下，会排除一些属性和节点类型，这些属性和节点类型在的OSGi配置中定义 **CQ MSM内容更新操作**，在 **排除的页面属性**.

默认情况下，转出时将排除（即未更新）与以下正则表达式匹配的属性：

![chlimage_1-18](assets/chlimage_1-18.png)

您可以根据需要更改定义排除列表的表达式。

例如，如果您希望将页面&#x200B;**标题**&#x200B;包含在考虑转出的更改中，请从排除项中删除 `jcr:title`。例如，使用正则表达式：

`jcr:(?!(title)$).*`

### 配置同步以更新引用 {#configuring-synchronization-for-updating-references}

您可以配置多个 OSGi 服务以支持与更新引用相关的对应同步操作。

使用AEM时，可通过多种方法来管理此类服务的配置设置；请参阅 [配置OSGi](/help/sites-deploying/configuring-osgi.md) 以了解更多详细信息和建议的实践。

下表列出了可为其指定引用更新的同步操作。 该表提供了使用Web控制台配置的服务的名称，以及使用存储库节点配置的PID。

<table> 
 <tbody> 
  <tr> 
   <th>Web控制台属性/ OSGi属性</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td><p>跨嵌套 Live Copy 更新引用</p> <p>cq.wcm.msm.impl.action.referencesupdate.prop_updateNested</p> </td> 
   <td>仅适用于CQ MSM引用更新操作。 选择此选项（Web控制台）或将此布尔属性设置为true（存储库配置），以替换针对位于最顶部LiveCopy分支中的任何资源的引用。</td> 
  </tr> 
  <tr> 
   <td><p>更新引用页面</p> <p>cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate</p> </td> 
   <td>仅适用于CQ MSM页面移动操作。 选择此选项（Web控制台）或将此布尔属性设置为 <code>true</code> （存储库配置），以更新任何引用，以改为使用原始页面引用LiveCopy页面。</td> 
  </tr> 
 </tbody> 
</table>

## 指定要使用的转出配置 {#specifying-the-rollout-configurations-to-use}

MSM允许您指定通常使用的转出配置集，并在需要时可以为特定Live Copy覆盖它们。 MSM 提供了多个位置来指定要使用的转出配置。该位置可确定配置是否适用于特定的Live Copy。

以下位置列表可在其中指定要使用的转出配置，其中说明了MSM如何确定要用于Live Copy的转出配置：

* **[Live Copy页面属性](/help/sites-administering/msm-sync.md#setting-the-rollout-configurations-for-a-live-copy-page):** 将Live Copy页面配置为使用一个或多个转出配置后，MSM会使用这些转出配置。
* **[Blueprint页面属性](/help/sites-administering/msm-sync.md#setting-the-rollout-configuration-for-a-blueprint-page):** 当Live Copy基于Blueprint，并且Live Copy页面未配置转出配置时，将使用与Blueprint源页面关联的转出配置。
* **Live Copy父页面属性：** 如果Live Copy页面和Blueprint源页面均未使用转出配置进行配置，则会使用适用于Live Copy页面父页面的转出配置。
* **[系统默认](/help/sites-administering/msm-sync.md#setting-the-system-default-rollout-configuration):** 当无法确定Live Copy父页面的转出配置时，将使用系统默认转出配置。

例如，Blueprint使用We.Retail引用站点作为源内容。 从Blueprint创建站点。 以下列表中的每个项目都描述了有关使用转出配置的不同方案：

* 未将任何Blueprint页面或Live Copy页面配置为使用转出配置。 MSM对所有Live Copy页面使用系统默认转出配置。
* We.Retail引用站点的根页面配置了多个转出配置。 MSM对所有Live Copy页面都使用这些转出配置。
* We.Retail引用站点的根页面配置了多个转出配置，而Live Copy站点的根页面配置了一组不同的转出配置。 MSM使用在Live Copy站点的根页面上配置的转出配置。

### 为 Live Copy 页面设置转出配置 {#setting-the-rollout-configurations-for-a-live-copy-page}

使用转出配置配置配置Live Copy页面，以便在转出源页面时使用。 子页面默认情况下会继承该配置。当您配置要使用的转出配置时，您正在覆盖Live Copy页面从其父页面继承的配置。

您还可以在 [创建live copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page).

1. 使用 **站点** 控制台来选择live copy页面。

1. 从工具栏中选择&#x200B;**属性**。
1. 打开 **Live Copy** 选项卡。

   **配置**&#x200B;部分将显示页面继承的转出配置。

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. 如果需要，可调整 **Live Copy 继承**&#x200B;标记。如果选中，则Live Copy配置对所有子项都有效。

1. 清除 **从父项继承转出配置** 属性，然后从列表中选择一个或多个转出配置。

   选定的转出配置显示在下拉列表下方。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 单击或点按 **保存**.

### 为Blueprint页面设置转出配置 {#setting-the-rollout-configuration-for-a-blueprint-page}

使用转出配置配置配置Blueprint页面，以在转出Blueprint页面时使用。

请注意，Blueprint页面的子页面将继承配置。 当您配置要使用的转出配置时，您可能正在覆盖页面从其父级继承的配置。

1. 使用&#x200B;**站点**&#x200B;控制台选择 Blueprint 的根页面。
1. 从工具栏中选择&#x200B;**属性**。
1. 打开 **Blueprint** 选项卡。
1. 使用下拉选择器选择一个或多个&#x200B;**转出配置**。
1. 使用&#x200B;**保存**&#x200B;持久存储您的更新。

### 设置系统默认转出配置 {#setting-the-system-default-rollout-configuration}

指定要用作系统默认值的转出配置。 要指定默认设置，请配置OSGi服务：

* **Day CQ WCM Live Relationship Manager**
服务PID为 
`com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

使用 [Web控制台](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) 或 [存储库节点](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* 在 Web 控制台中，要配置的属性名称是默认转出配置。
* 使用存储库节点，要配置的属性的名称是 `liverelationshipmgr.relationsconfig.default`。

将此属性值设置为要用作系统默认值的转出配置的路径。默认值为 `/libs/msm/wcm/rolloutconfigs/default`，这是&#x200B;**标准转出配置**。
