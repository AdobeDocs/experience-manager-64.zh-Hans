---
title: 以编程方式与工作流交互
description: 了解如何使用API和脚本管理工作流并与工作流进行编程交互。
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: da06850a-c4d5-44dd-b572-771e3b2a66c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2051'
ht-degree: 1%

---

# 以编程方式与工作流交互{#interacting-with-workflows-programmatically}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

When [自定义和扩展工作流](/help/sites-developing/workflows-customizing-extending.md) 您可以访问工作流对象：

* [使用工作流Java API](#using-the-workflow-java-api)
* [在ECMA脚本中获取工作流对象](#obtaining-workflow-objects-in-ecma-scripts)
* [使用工作流REST API](#using-the-workflow-rest-api)

## 使用工作流Java API {#using-the-workflow-java-api}

工作流Java API由 [`com.adobe.granite.workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/package-summary.html) 包和多个子包。 API最重要的成员是 `com.adobe.granite.workflow.WorkflowSession` 类。 的 `WorkflowSession` 类提供对设计时和运行时工作流对象的访问：

* 工作流模型
* 工作项
* 工作流实例
* 工作流数据
* 收件箱项目

类还提供了几种用于干预工作流生命周期的方法。

下表提供了在以编程方式与工作流交互时要使用的几个关键Java对象的参考文档的链接。 以下示例演示了如何在代码中获取和使用类对象。

| 功能 | 对象 |
|---|---|
| 访问工作流 | [`WorkflowSession`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html) |
| 执行和查询工作流实例 | [`Workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html)</br>[`WorkItem`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkItem.html)</br>[`WorkflowData`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) |
| 管理工作流模型 | [`WorkflowModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowModel.html)</br>[`WorkflowNode`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowNode.html)</br>[`WorkflowTransition`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowTransition.html) |
| 工作流中（或不中）的节点的信息 | [`WorkflowStatus`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) |

## 在ECMA脚本中获取工作流对象 {#obtaining-workflow-objects-in-ecma-scripts}

如 [查找脚本](/help/sites-developing/the-basics.md#locating-the-script), AEM（通过Apache Sling）提供了一个可执行服务器端ECMA脚本的ECMA脚本引擎。 的 [`org.apache.sling.scripting.core.ScriptHelper`](https://sling.apache.org/apidocs/sling5/org/apache/sling/scripting/core/ScriptHelper.html) 类可立即用于您的脚本，作为 `sling` 变量。

的 `ScriptHelper` 类提供对 `SlingHttpServletRequest` 最终获得 `WorkflowSession` 对象；例如：

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

## 使用工作流REST API {#using-the-workflow-rest-api}

工作流控制台充分利用了REST API;因此，本页介绍了工作流的REST API。

>[!NOTE]
>
>curl命令行工具允许您使用工作流REST API访问工作流对象和管理实例生命周期。 本页中的示例演示了如何通过curl命令行工具使用REST API。

REST API支持以下操作：

* 启动或停止工作流服务
* 创建、更新或删除工作流模型
* [启动、暂停、继续或终止工作流实例](/help/sites-administering/workflows.md#workflow-status-and-actions)
* 完成或委派工作项

>[!NOTE]
>
>通过使用Firefox（用于Web开发的Firebug扩展），可以在控制台操作时跟踪HTTP流量。 例如，您可以通过 `POST` 请求。

在本页中，假定AEM在本地主机上的端口运行 `4502` 安装上下文为“ `/`&quot;（根）。 如果安装的URI不是，则需要相应地调整HTTP请求所适用的URI。

支持的渲染 `GET` 请求是JSON渲染。 的URL `GET` 应该有 `.json` 扩展，例如：

`http://localhost:4502/etc/workflow.json`

### 管理工作流实例 {#managing-workflow-instances}

以下HTTP请求方法适用于：

`http://localhost:4502/etc/workflow/instances`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP请求方法</td> 
   <td>操作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出可用的工作流实例。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td><p>创建新的工作流实例。 参数包括：<br /> - <code>model</code>:相应工作流模型的ID(URI)<br /> - <code>payloadType</code>:包含有效负载的类型(例如 <code>JCR_PATH</code> 或URL)。<br /> 负载将作为参数发送 <code>payload</code>. A <code>201</code> (<code>CREATED</code>)响应随包含新工作流实例资源URL的位置标头一起发送回。</p> </td> 
  </tr> 
 </tbody> 
</table>

#### 按状态管理工作流实例 {#managing-a-workflow-instance-by-its-state}

以下HTTP请求方法适用于：

`http://localhost:4502/etc/workflow/instances.{state}`

| HTTP请求方法 | 操作 |
|---|---|
| `GET` | 列出可用的工作流实例及其状态( `RUNNING`, `SUSPENDED`, `ABORTED` 或 `COMPLETED`) |

#### 通过工作流实例的ID管理该实例 {#managing-a-workflow-instance-by-its-id}

以下HTTP请求方法适用于：

`http://localhost:4502/etc/workflow/instances/{id}`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP请求方法</td> 
   <td>操作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>获取实例数据（定义和元数据），包括指向相应工作流模型的链接。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>更改实例的状态。 新状态将作为参数发送 <code>state</code> 和必须具有以下值之一： <code>RUNNING</code>, <code>SUSPENDED</code>或 <code>ABORTED</code>.<br /> 如果新状态无法访问（例如，暂停终止的实例时）a <code>409</code> (<code>CONFLICT</code>)响应会发送回客户端。</td> 
  </tr> 
 </tbody> 
</table>

### 管理工作流模型 {#managing-workflow-models}

以下HTTP请求方法适用于：

`http://localhost:4502/etc/workflow/models`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP请求方法</td> 
   <td>操作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出可用的工作流模型。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>创建新工作流模型. 如果参数 <code>title</code> 将发送，则会使用指定的标题创建新模型。 将JSON模型定义附加为参数 <code>model</code> 根据提供的定义创建新的工作流模型。<br /> A <code>201</code> 响应(<code>CREATED</code>)会随包含新工作流模型资源URL的位置标头一起发送回来。<br /> 当模型定义作为名为 <code>modelfile</code>.<br /> 对于 <code>model</code> 和 <code>modelfile</code> 参数，另一个名为 <code>type</code> 定义序列化格式时需要。 可使用OSGi API集成新的序列化格式。 标准JSON序列化程序随工作流引擎一起提供。 其类型为JSON。 请参阅下文以查看格式示例。</td> 
  </tr> 
 </tbody> 
</table>

示例：在浏览器中， `http://localhost:4502/etc/workflow/models.json` 会生成与以下内容类似的json响应：

```
[
    {"uri":"/var/workflow/models/activationmodel"}
    ,{"uri":"/var/workflow/models/dam/adddamsize"}
    ,{"uri":"/var/workflow/models/cloudconfigs/dtm-reactor/library-download"}
    ,{"uri":"/var/workflow/models/ac-newsletter-workflow-simple"}
    ,{"uri":"/var/workflow/models/dam/dam-create-language-copy"}
    ,{"uri":"/var/workflow/models/dam/dam-create-and-translate-language-copy"}
    ,{"uri":"/var/workflow/models/dam-indesign-proxy"}
    ,{"uri":"/var/workflow/models/dam-xmp-writeback"}
    ,{"uri":"/var/workflow/models/dam-parse-word-documents"}
    ,{"uri":"/var/workflow/models/dam/process_subasset"}
    ,{"uri":"/var/workflow/models/dam/dam_set_last_modified"}
    ,{"uri":"/var/workflow/models/dam/dam-autotag-assets"}
    ,{"uri":"/var/workflow/models/dam/update_asset"}
    ,{"uri":"/var/workflow/models/dam/update_asset_offloading"}
    ,{"uri":"/var/workflow/models/dam/dam-update-language-copy"}
    ,{"uri":"/var/workflow/models/dam/update_from_lightbox"}
    ,{"uri":"/var/workflow/models/cloudservices/DTM_bundle_download"}
    ,{"uri":"/var/workflow/models/dam/dam_download_asset"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-encode-video"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-thumbnail-replacement"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail"}
    ,{"uri":"/var/workflow/models/newsletter_bounce_check"}
    ,{"uri":"/var/workflow/models/projects/photo_shoot_submission"}
    ,{"uri":"/var/workflow/models/projects/product_photo_shoot"}
    ,{"uri":"/var/workflow/models/projects/approval_workflow"}
    ,{"uri":"/var/workflow/models/prototype-01"}
    ,{"uri":"/var/workflow/models/publish_example"}
    ,{"uri":"/var/workflow/models/publish_to_campaign"}
    ,{"uri":"/var/workflow/models/screens/publish_to_author_bin"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_publish_to_youtube"}
    ,{"uri":"/var/workflow/models/projects/request_copy"}
    ,{"uri":"/var/workflow/models/projects/request_email"}
    ,{"uri":"/var/workflow/models/projects/request_landing_page"}
    ,{"uri":"/var/workflow/models/projects/request_launch"}
    ,{"uri":"/var/workflow/models/request_for_activation"}
    ,{"uri":"/var/workflow/models/request_for_deactivation"}
    ,{"uri":"/var/workflow/models/request_for_deletion"}
    ,{"uri":"/var/workflow/models/request_for_deletion_without_deactivation"}
    ,{"uri":"/var/workflow/models/request_to_complete_move_operation"}
    ,{"uri":"/var/workflow/models/reverse_replication"}
    ,{"uri":"/var/workflow/models/salesforce-com-export"}
    ,{"uri":"/var/workflow/models/scene7"}
    ,{"uri":"/var/workflow/models/scheduled_activation"}
    ,{"uri":"/var/workflow/models/scheduled_deactivation"}
    ,{"uri":"/var/workflow/models/screens/screens-update-asset"}
    ,{"uri":"/var/workflow/models/translation"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_remove_from_youtube"}
    ,{"uri":"/var/workflow/models/wcm-translation/create_language_copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/prepare_translation_project"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-i18n-dictionary"}
    ,{"uri":"/var/workflow/models/wcm-translation/sync_translation_job"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-language-copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/update_language_copy"}
]
```

#### 管理特定的工作流模型 {#managing-a-specific-workflow-model}

以下HTTP请求方法适用于：

`http://localhost:4502*{uri}*`

其中 `*{uri}*` 是存储库中模型节点的路径。

<table> 
 <tbody> 
  <tr> 
   <td>HTTP请求方法</td> 
   <td>操作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>获取 <code>HEAD</code> 模型的版本（定义和元数据）。</td> 
  </tr> 
  <tr> 
   <td><code>PUT</code></td> 
   <td>更新 <code>HEAD</code> 模型版本（创建新版本）。<br /> 必须将模型新版本的完整模型定义作为名为的参数添加 <code>model</code>. 此外， <code>type</code> 创建新模型时需要参数，并且需要具有值 <code>JSON</code>.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>与PUT相同的行为。 需要，因为AEM小组件不支持 <code>PUT</code> 操作。</td> 
  </tr> 
  <tr> 
   <td><code>DELETE</code></td> 
   <td>删除模型。 为了解决防火墙/代理问题， <code>POST</code> 包含 <code>X-HTTP-Method-Override</code> 带值的标题条目 <code>DELETE</code> 也将作为 <code>DELETE</code> 请求。</td> 
  </tr> 
 </tbody> 
</table>

示例：在浏览器中， `http://localhost:4502/var/workflow/models/publish_example.json` 返回 `json` 与以下代码类似的响应：

```shell
{
  "id":"/var/workflow/models/publish_example",
  "title":"Publish Example",
  "version":"1.0",
  "description":"This example shows a simple review and publish process.",
  "metaData": 
  {
    "multiResourceSupport":"true",
    "tags":"wcm,publish"
  },
  "nodes":
  [{
    "id":"node0",
    "type":"START",
    "title":"Start",
    "description":"The start node of the workflow.",
    "metaData":
    {
    }
  },
  {
    "id":"node1",
    "type":"PARTICIPANT",
    "title":"Validate Content",
    "description":"Validate the modified content.",
    "metaData":
    {
      "PARTICIPANT":"admin"
    }
  },
  {
    "id":"node2",
    "type":"PROCESS",
    "title":"Publish Content",
    "description":"Publish the modified content.",
    "metaData":
    {
      "PROCESS_AUTO_ADVANCE":"true",
      "PROCESS":"com.day.cq.wcm.workflow.process.ActivatePageProcess"
    }
  },
  {
    "id":"node3",
    "type":"END",
    "title":"End",
    "description":"The end node of the workflow.",
    "metaData":
    {
    }
  }],
  "transitions":
  [{
    "from":"node0",
    "to":"node1",
    "metaData":
    {
    }
  },
  {
    "from":"node1",
    "to":"node2",
    "metaData":
    {
    }
  },
  {
    "from":"node2",
    "to":"node3",
    "metaData":
    {
    }
  }
]}
```

#### 按工作流模型的版本管理工作流模型 {#managing-a-workflow-model-by-its-version}

以下HTTP请求方法适用于：

`http://localhost:4502/etc/workflow/models/{id}.{version}`

| HTTP请求方法 | 操作 |
|---|---|
| `GET` | 获取给定版本中模型的数据（如果存在）。 |

### 管理（用户）收件箱 {#managing-user-inboxes}

以下HTTP请求方法适用于：

`http://localhost:4502/bin/workflow/inbox`

<table> 
 <tbody> 
  <tr> 
   <td>HTTP请求方法</td> 
   <td>操作</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>列出用户收件箱中的工作项，由HTTP身份验证标头标识。</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>完成将其URI作为参数发送的工作项 <code>item</code> 并将相应的工作流实例前进到由参数定义的下一个节点 <code>route</code> 或 <code>backroute</code> 以防退一步。<br /> 如果参数 <code>delegatee</code> 发送，则参数标识的工作项 <code>item</code> 将委派给指定参与者。</td> 
  </tr> 
 </tbody> 
</table>

#### 通过WorkItem ID管理（用户）收件箱 {#managing-a-user-inbox-by-the-workitem-id}

以下HTTP请求方法适用于：

`http://localhost:4502/bin/workflow/inbox/{id}`

| HTTP请求方法 | 操作 |
|---|---|
| `GET` | 获取收件箱的数据（定义和元数据） `WorkItem` 由其ID标识。 |

## 示例 {#examples}

### 如何获取所有正在运行的工作流及其ID的列表 {#how-to-get-a-list-of-all-running-workflows-with-their-ids}

要获取所有正在运行的工作流的列表，请执行以下GET:

`http://localhost:4502/etc/workflow/instances.RUNNING.json`

#### 如何获取所有正在运行的工作流及其ID的列表 — 使用curl进行REST {#how-to-get-a-list-of-all-running-workflows-with-their-ids-rest-using-curl}

使用curl的示例：

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/instances.RUNNING.json
```

的 `uri` 结果中显示的内容可用作实例 `id` 在其他命令中；例如：

```shell
[
    {"uri":"/etc/workflow/instances/server0/2017-03-08/request_for_activation_1"}
]
```

>[!NOTE]
>
>此 `curl` 命令可与任何 [工作流状态](/help/sites-administering/workflows.md#workflow-status-and-actions) 代替 `RUNNING`.

### 如何更改工作流标题 {#how-to-change-the-workflow-title}

要更改 **工作流标题** 显示在 **实例** ，则发送 `POST` 命令：

* 到: `http://localhost:4502/etc/workflow/instances/{id}`

* 使用以下参数：

   * `action`:其价值必须是： `UPDATE`
   * `workflowTitle`:工作流标题

#### 如何使用curl更改工作流标题 — REST {#how-to-change-the-workflow-title-rest-using-curl}

使用curl的示例：

```shell
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/{id}

# for example

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
```

### 如何列出所有工作流模型 {#how-to-list-all-workflow-models}

要获取所有可用工作流模型的列表，请执行以下GET:

`http://localhost:4502/etc/workflow/models.json`

#### 如何列出所有工作流模型 — 使用curl的REST {#how-to-list-all-workflow-models-rest-using-curl}

使用curl的示例：

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/models.json
```

>[!NOTE]
>
>另请参阅 [管理工作流模型](#managing-workflow-models).

### 获取WorkflowSession对象 {#obtaining-a-workflowsession-object}

的 `com.adobe.granite.workflow.WorkflowSession` 类可从 `javax.jcr.Session` 对象或 `org.apache.sling.api.resource.ResourceResolver` 对象。

#### 获取WorkflowSession对象 — Java {#obtaining-a-workflowsession-object-java}

在JSP脚本（或Servlet类的Java代码）中，使用HTTP请求对象获取 `SlingHttpServletRequest` 对象，提供对 `ResourceResolver` 对象。 调整 `ResourceResolver` 对象 `WorkflowSession`.

```java
<%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" 
    import="com.adobe.granite.workflow.WorkflowSession,
  org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
%>
```

#### 获取WorkflowSession对象 — ECMA脚本 {#obtaining-a-workflowsession-object-ecma-script}

使用 `sling` 变量 `SlingHttpServletRequest` 用于获取 `ResourceResolver` 对象。 调整 `ResourceResolver` 对象 `WorkflowSession` 对象。

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

### 创建、读取或删除工作流模型 {#creating-reading-or-deleting-workflow-models}

以下示例显示如何访问工作流模型：

* Java和ECMA脚本的代码使用 `WorkflowSession.createNewModel` 方法。
* curl命令可直接使用其URL访问模型。

使用的示例：

1. 创建模型(具有ID `/var/workflow/models/mymodel/jcr:content/model`)。
1. 删除模型。

>[!NOTE]
>
>删除模型会设置 `deleted` 模型的属性 `metaData` 子节点到 `true`.
>
>删除不会删除模型节点。

创建新模型时：

* 工作流模型编辑器要求模型使用下面的特定节点结构 `/var/workflow/models`. 模型的父节点必须为类型 `cq:Page` 拥有 `jcr:content` 具有以下属性值的节点：

   * `sling:resourceType`: `cq/workflow/components/pages/model`
   * `cq:template`: `/libs/cq/workflow/templates/model`

   创建模型时，必须首先创建此模型 `cq:Page` 节点及其使用 `jcr:content` 节点作为模型节点的父项。

* 的 `id` 某些方法识别模型所需的参数是存储库中模型节点的绝对路径：

   `/var/workflow/models/<*model_name>*/jcr:content/model`

   >[!NOTE]
   >
   >请参阅 [如何列出所有工作流模型](#how-to-list-all-workflow-models).

#### 创建、读取或删除工作流模型 — Java {#creating-reading-or-deleting-workflow-models-java}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" import="com.adobe.granite.workflow.WorkflowSession,
                 com.adobe.granite.workflow.model.WorkflowModel,
             org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
/* Create the parent page */
String modelRepo = new String("/var/workflow/models");
String modelTemplate = new String ("/libs/cq/workflow/templates/model");
String modelName = new String("mymodel");
Page modelParent = pageManager.create(modelRepo, modelName, modelTemplate, "My workflow model");

/* create the model */
String modelId = new String(modelParent.getPath()+"/jcr:content/model")
WorkflowModel model = wfSession.createNewModel("Made using Java",modelId);

/* delete the model */
wfSession.deleteModel(modelId);
%>
```

#### 创建、读取或删除工作流模型 — ECMA脚本 {#creating-reading-or-deleting-workflow-models-ecma-script}

```
var resolver = sling.getRequest().getResource().getResourceResolver();
var wfSession = resolver.adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
var pageManager = resolver.adaptTo(Packages.com.day.cq.wcm.api.PageManager);

//create the parent page node
var workflowPage = pageManager.create("/var/workflow/models", "mymodel", "/libs/cq/workflow/templates/model", "Created via ECMA Script");
var modelId = workflowPage.getPath()+ "/jcr:content/model";
//create the model
var model = wfSession.createNewModel("My Model", modelId);
//delete the model
var model = wfSession.deleteModel(modelId);
```

#### 删除工作流模型 — 使用curl的REST {#deleting-a-workflow-model-rest-using-curl}

```shell
# deleting the model by its id

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
curl -u admin:admin -X DELETE http://localhost:4502/etc/workflow/models/{id}
```

>[!NOTE]
>
>由于需要详细程度，curl在创建和/或读取模型时被认为不实用。

### 检查工作流状态时筛选系统工作流 {#filtering-out-system-workflows-when-checking-workflow-status}

您可以使用 [WorkflowStatus API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) 以检索有关节点的工作流状态的信息。

各种方法均具有参数：

`excludeSystemWorkflows`

此参数可设置为 `true` 以指示应从相关结果中排除系统工作流。

您 [可以更新OSGi配置](/help/sites-deploying/configuring-osgi.md) **AdobeGranite工作流有效负荷MapCache** 指定工作流 `Models` 视为系统工作流。 默认（运行时）工作流模型包括：

* `/var/workflow/models/scheduled_activation/jcr:content/model`
* `/var/workflow/models/scheduled_deactivation/jcr:content/model`

### 超时后自动提前参与者步骤 {#auto-advance-participant-step-after-a-timeout}

如果需要自动推进 **参与者** 尚未在预定义时间内完成的步骤，您可以：

1. 实施OSGi事件侦听器以侦听任务创建和修改。
1. 指定超时（截止时间），然后创建一个计划的sling作业，以在该时触发。
1. 编写一个在超时过期时通知的作业处理程序并触发该作业。

   如果任务尚未完成，此处理程序将对任务执行所需的操作

>[!NOTE]
>
>必须明确界定要采取的行动，以便能够采用这种办法。

### 与工作流实例交互 {#interacting-with-workflow-instances}

以下提供了如何与工作流实例进行交互（编程）的基本示例。

#### 与工作流实例交互 — Java {#interacting-with-workflow-instances-java}

```java
// starting a workflow
WorkflowModel model = wfSession.getModel(workflowId);
WorkflowData wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
Workflow[] workflows workflows = wfSession.getAllWorkflows();
Workflow workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### 与工作流实例交互 — ECMA脚本 {#interacting-with-workflow-instances-ecma-script}

```
// starting a workflow
var model = wfSession.getModel(workflowId);
var wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
var workflows = wfSession.getWorkflows(“RUNNING“);
var workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### 与工作流实例交互 — 使用curl的REST {#interacting-with-workflow-instances-rest-using-curl}

* **启动工作流**

   ```shell
   # starting a workflow
   curl -d "model={id}&payloadType={type}&payload={payload}" http://localhost:4502/etc/workflow/instances
   
   # for example:
   curl -u admin:admin -d "model=/var/workflow/models/request_for_activation&payloadType=JCR_PATH&payload=/content/we-retail/us/en/products" http://localhost:4502/etc/workflow/instances
   ```

* **列出实例**

   ```shell
   # listing the instances
   curl -u admin:admin http://localhost:4502/etc/workflow/instances.json
   ```

   这将列出所有实例；例如：

   ```shell
   [
       {"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_1"}
       ,{"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_2"}
   ]
   ```

   >[!NOTE]
   >
   >请参阅 [如何获取所有正在运行的工作流的列表](#how-to-get-a-list-of-all-running-workflows-with-their-ids) 及其ID，用于列出具有特定状态的实例。

* **暂停工作流**

   ```shell
   # suspending a workflow
   curl -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **恢复工作流**

   ```shell
   # resuming a workflow
   curl -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **终止工作流实例**

   ```shell
   # terminating a workflow
   curl -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

### 与工作项交互 {#interacting-with-work-items}

以下提供了如何与工作项进行交互（按程序方式）的基本示例。

#### 与工作项交互 — Java {#interacting-with-work-items-java}

```java
// querying work items
WorkItem[] workItems = wfSession.getActiveWorkItems();
WorkItem workItem = wfSession.getWorkItem(id);

// getting routes
List<Route> routes = wfSession.getRoutes(workItem);

// delegating
Iterator<Participant> delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### 与工作项交互 — ECMA脚本 {#interacting-with-work-items-ecma-script}

```
// querying work items
var workItems = wfSession.getActiveWorkItems();
var workItem = wfSession.getWorkItem(id);

// getting routes
var routes = wfSession.getRoutes(workItem);

// delegating
var delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### 与工作项交互 — 使用curl的REST {#interacting-with-work-items-rest-using-curl}

* **从收件箱中列出工作项**

   ```shell
   # listing the work items
   curl -u admin:admin http://localhost:4502/bin/workflow/inbox
   ```

   收件箱中将列出当前工作项的详细信息；例如：

   ```shell
   [{
       "uri_xss": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "uri": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "currentAssignee_xss": "workflow-administrators",
       "currentAssignee": "workflow-administrators",
       "startTime": 1519656289274,
       "payloadType_xss": "JCR_PATH",
       "payloadType": "JCR_PATH",
       "payload_xss": "/content/we-retail/es/es",
       "payload": "/content/we-retail/es/es",
       "comment_xss": "Process resource is null",
       "comment": "Process resource is null",
       "type_xss": "WorkItem",
       "type": "WorkItem"
     },{
       "uri_xss": "configuration/configure_analyticstargeting",
       "uri": "configuration/configure_analyticstargeting",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/securitychecklist",
       "uri": "configuration/securitychecklist",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/enable_collectionofanonymoususagedata",
       "uri": "configuration/enable_collectionofanonymoususagedata",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/configuressl",
       "uri": "configuration/configuressl",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     }
   ```

* **委派工作项**

   ```xml
   # delegating
   curl -d "item={item}&delegatee={delegatee}" http://localhost:4502/bin/workflow/inbox
   
   # for example: 
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_act_1&delegatee=administrators" http://localhost:4502/bin/workflow/inbox
   ```

   >[!NOTE]
   >
   >的 `delegatee` 必须是工作流步骤的有效选项。

* **完成或将工作项目推进到下一步**

   ```xml
   # retrieve the list of routes; the results will be similar to {"results":1,"routes":[{"rid":"233123169","label":"End","label_xss":"End"}]}
   http://localhost:4502/etc/workflow/instances/<path-to-the-workitem>.routes.json
   
   # completing or advancing to the next step; use the appropriate route ID (rid value) from the above list
   curl -d "item={item}&route={route}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_activation_1&route=233123169" http://localhost:4502/bin/workflow/inbox
   ```

### 侦听工作流事件 {#listening-for-workflow-events}

使用OSGi事件框架来监听 [ `com.adobe.granite.workflow.event.WorkflowEvent`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/event/WorkflowEvent.html) 类定义。 此类还提供了几种用于获取有关事件主题的信息的有用方法。 例如， `getWorkItem` 方法返回 `WorkItem` 事件中涉及的工作项的对象。

以下示例代码定义了一项服务，该服务侦听工作流事件并根据事件类型执行任务。

```java
package com.adobe.example.workflow.listeners;

import org.apache.sling.event.jobs.JobProcessor;
import org.apache.sling.event.jobs.JobUtil;

import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import com.adobe.granite.workflow.event.WorkflowEvent;
import com.adobe.granite.workflow.exec.WorkItem;

/**
 * The <code>WorkflowEventCatcher</code> class listens to workflow events. 
 */
@Component(metatype=false, immediate=true)
@Service(value=org.osgi.service.event.EventHandler.class)
public class WorkflowEventCatcher implements EventHandler, JobProcessor {

 @Property(value=com.adobe.granite.workflow.event.WorkflowEvent.EVENT_TOPIC)
 static final String EVENT_TOPICS = "event.topics";

 private static final Logger logger = LoggerFactory.getLogger(WorkflowEventCatcher.class);

 public void handleEvent(Event event) {
  JobUtil.processJob(event, this);
 }

 public boolean process(Event event) {
  logger.info("Received event of topic: " + event.getTopic());
  String topic = event.getTopic();

  try {
   if (topic.equals(WorkflowEvent.EVENT_TOPIC)) {
    WorkflowEvent wfevent = (WorkflowEvent)event;
    String eventType = wfevent.getEventType();
    String instanceId = wfevent.getWorkflowInstanceId();

    if (instanceId != null) {
     //workflow instance events
     if (eventType.equals(WorkflowEvent.WORKFLOW_STARTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_RESUMED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_SUSPENDED_EVENT)) {
      // your code comes here...
     } else if (
       eventType.equals(WorkflowEvent.WORKFLOW_ABORTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_COMPLETED_EVENT)) {
      // your code comes here...
     }
     // workflow node event
     if (eventType.equals(WorkflowEvent.NODE_TRANSITION_EVENT)) {
      WorkItem currentItem = (WorkItem) event.getProperty(WorkflowEvent.WORK_ITEM);
      // your code comes here...
     }
    }
   }
  } catch(Exception e){
   logger.debug(e.getMessage());
   e.printStackTrace();
  }
  return true;
 }
}
```
