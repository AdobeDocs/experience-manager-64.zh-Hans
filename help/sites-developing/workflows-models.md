---
title: 创建工作流模型
seo-title: Creating Workflow Models
description: 您可以创建工作流模型以定义用户启动工作流时执行的一系列步骤。
seo-description: You create a workflow model to define the series of steps executed when a user starts the workflow.
uuid: 53d94176-4d5f-4ab3-9628-6b7d44f81139
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 9d2dba11-0d2d-4aed-b941-c8ade9bb7bfa
exl-id: d9c9db5f-9788-460f-ac09-88dd3c911edd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 2%

---

# 创建工作流模型{#creating-workflow-models}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>要使用经典UI，请参阅 [AEM 6.3文档](https://helpx.adobe.com/experience-manager/6-3/sites-developing/workflows-models.html) 以供参考。

您可以创建 [工作流模型](/help/sites-developing/workflows.md#model) 定义用户启动工作流时执行的一系列步骤。 您还可以定义模型属性，例如工作流是临时的还是使用多个资源。

用户启动工作流时，会启动实例；这是相应的运行时模型，在 [同步](#sync-your-workflow-generate-a-runtime-model) 您的更改。

## 创建新工作流 {#creating-a-new-workflow}

首次创建新的工作流模型时，该模型包含：

* 步骤， **[!UICONTROL 流量开始]** 和 **[!UICONTROL 流量结束]**.

   它们表示工作流的开始和结束。 这些步骤是必需的，无法编辑或删除。

* 示例 **参与者** 已命名步骤 **步骤1**.

   此步骤配置为将工作项分配给工作流启动器。 编辑或删除此步骤，并根据需要添加步骤。

要使用编辑器创建新工作流，请执行以下操作：

1. 打开 **[!UICONTROL 工作流模型]** 控制台；通过 **[!UICONTROL 工具]**, **[!UICONTROL 工作流]**, **[!UICONTROL 模型]** 例如：

   [http://localhost:4502/aem/workflow](http://localhost:4502/aem/workflow)

1. 选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建模型]**.
1. 的 **[!UICONTROL 添加工作流模型]** 对话框。 输入 **[!UICONTROL 标题]** 和 **[!UICONTROL 名称]** （可选）在选择 **[!UICONTROL 完成]**.
1. 新模型列在 **[!UICONTROL 工作流模型]** 控制台。
1. 选择新的工作流，然后使用 [**[!UICONTROL 编辑&#x200B;]**打开进行配置](#editing-a-workflow):

   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>如果以编程方式创建模型（使用crx包），则还可以在中创建子文件夹：
>
>`/var/workflow/models`
>
>例如，`/var/workflow/models/prototypes`
>
>然后，可以将此文件夹用于 [管理对该文件夹中模型的访问权限](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that).

## 编辑工作流 {#editing-a-workflow}

您可以编辑任何现有的工作流模型，以：

* [定义步骤](#adding-a-step-to-a-model) 和 [参数](#configuring-a-workflow-step)

* 配置工作流属性，包括 [阶段](#configuring-workflow-stages-that-show-workflow-progress), [工作流是否是瞬态的](#creating-a-transient-workflow) 和/或 [使用多个资源](#configuring-a-workflow-for-multi-resource-support)

编辑 [**默认或旧版** （现成）工作流](#editing-a-default-or-legacy-workflow-for-the-first-time) 还有一个额外步骤，以确保 [安全拷贝](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) 会在您进行更改之前执行。

工作流更新完成后，您必须使用 **[!UICONTROL 同步]** to **[!UICONTROL 生成运行时模型]**. 请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

### 同步工作流 — 生成运行时模型 {#sync-your-workflow-generate-a-runtime-model}

**同步** （在编辑器工具栏的右侧）会生成 [运行时模型](/help/sites-developing/workflows.md#runtime-model). 运行时模型是用户启动工作流时实际使用的模型。 如果您没有 **[!UICONTROL 同步]** 则更改在运行时将不可用。

当您（或任何其他用户）对必须使用的工作流进行任何更改时 **[!UICONTROL 同步]** 生成运行时模型 — 即使单个对话框（例如，步骤）具有其自己的保存选项时也是如此。

当更改与运行时（保存）模型同步时， **[!UICONTROL 同步]** 中，将显示。

某些步骤包含必填字段和/或内置验证。 如果不满足这些条件，则在尝试 **[!UICONTROL 同步]** 模型。 例如，当没有为 **[!UICONTROL 参与者]** 步骤：

![wf-21](assets/wf-21.png)

### 首次编辑默认或旧版工作流 {#editing-a-default-or-legacy-workflow-for-the-first-time}

当您打开 [默认和/或旧模型](/help/sites-developing/workflows.md#workflow-types) 进行编辑：

* 的 **[!UICONTROL 步骤]** 浏览器不可用（左侧）。
* 有 **[!UICONTROL 编辑]** 操作（右侧）中可用。
* 最初，模型及其属性以只读模式显示为：

   * 默认工作流位于 `/libs`
   * 旧版工作流位于 `/etc`

选择 **[!UICONTROL 编辑]** 将：

* 将工作流的副本导入 `/conf`
* make **[!UICONTROL 步骤]** 浏览器可用
* 允许您进行更改

>[!NOTE]
>
>请参阅 [工作流模型的位置](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) 以了解更多信息。

![wf-22](assets/wf-22.png)

### 向模型添加步骤 {#adding-a-step-to-a-model}

您需要向模型中添加步骤以表示要执行的活动 — 每个步骤都会执行特定活动。 标准AEM实例中提供了一系列步骤组件。

在编辑模型时，可用的步骤会显示在 **[!UICONTROL 步骤]** 浏览器。 例如：

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>有关随AEM一起安装的主要步骤组件的信息，请参阅 [工作流步骤参考](/help/sites-developing/workflows-step-ref.md).

**向模型添加步骤**:

1. 打开现有的工作流模型进行编辑。 从 **[!UICONTROL 工作流模型]** 控制台中，选择所需的模型，然后 **[!UICONTROL 编辑]**.
1. 打开 **[!UICONTROL 步骤]** 浏览器；使用 **[!UICONTROL 切换侧面板]**，位于顶部工具栏的最左侧。 在此编辑器中，您可以：

   * **[!UICONTROL 过滤器]** 中。
   * 使用下拉选择器将选择限制为一组特定步骤。
   * 选择显示描述图标 ![wf-stepinfo-icon](assets/wf-stepinfo-icon.png) 以显示有关相应步骤的更多详细信息。

   ![wf-02](assets/wf-02.png)

1. 将相应的步骤拖动到模型中的所需位置。

   例如， **[!UICONTROL 参与者步骤]**.

   将其添加到流程后，您可以 [配置步骤](#configuring-a-workflow-step).

   ![wf-03](assets/wf-03.png)

1. 根据需要添加任意数量的步骤或其他更新。

   在运行时，会按步骤在模型中的显示顺序执行步骤。 添加步骤元件后，可将其拖动到模型中的其他位置。

   您还可以复制、剪切、粘贴、分组或删除现有步骤；与 [页面编辑器。](/help/sites-authoring/editing-content.md)

   也可以使用工具栏选项折叠/展开拆分步骤： ![wf-collapseexpand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png)

1. 确认更改 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

### 配置工作流步骤 {#configuring-a-workflow-step}

您可以 **配置** 和使用 **[!UICONTROL 步骤属性]** 对话框。

1. 要打开 **[!UICONTROL 步骤属性]** 对话框：

   * 点按工作流模型中的步骤，然后选择 **[!UICONTROL 配置]** 中。
   * 双击该步骤。

   >[!NOTE]
   >
   >有关随AEM一起安装的主要步骤组件的信息，请参阅 [工作流步骤参考](/help/sites-developing/workflows-step-ref.md).

1. 配置 **[!UICONTROL 步骤属性]** （视需要）；可用的属性取决于步骤类型，还可能有多个可用选项卡。 例如，默认 **[!UICONTROL 参与者步骤]**，在新工作流中以 `Step 1`:

   ![wf-11](assets/wf-11.png)

1. 使用勾号确认您的更新。
1. 确认更改 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

### 创建临时工作流 {#creating-a-transient-workflow}

您可以创建 [瞬态](/help/sites-developing/workflows.md#transient-workflows) 创建新模型时，或通过编辑现有模型时的工作流模型：

1. 打开的工作流模型 [编辑](#editing-a-workflow).
1. 选择 **[!UICONTROL 工作流模型属性]** 中。
1. 在对话框中，激活 **[!UICONTROL 瞬态工作流]** （或根据需要取消激活）：

   ![wf-07](assets/wf-07.png)

1. 确认更改 **[!UICONTROL 保存并关闭]**;后跟 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

>[!NOTE]
>
>在中运行工作流时 [瞬态](/help/sites-developing/workflows.md#transient-workflows) 模式AEM不存储任何工作流历史记录。 因此， [时间轴](/help/sites-authoring/basic-handling.md#timeline) 不显示与该工作流相关的任何信息。 [](/help/sites-authoring/basic-handling.md#timeline)

### 在触屏UI中使工作流模型可用 {#make-workflow-models-available-in-touchui}

如果工作流模型在经典UI中存在，但在 **[!UICONTROL 时间轴]** 边栏，然后按照配置使其可用。 以下步骤说明了如何使用称为 **[!UICONTROL 激活请求]**.

1. 确认模型在触屏优化UI中不可用。 使用 `/assets.html/content/dam` 路径。 选择资产。 打开 **[!UICONTROL 时间轴]** 在左边栏中。 单击 **[!UICONTROL 启动工作流]** 确认 **[!UICONTROL 激活请求]** 模型不在弹出式列表中。

1. 浏览 **[!UICONTROL 工具>常规>标记]**. 选择 **[!UICONTROL 工作流]**.

1. 选择 **[!UICONTROL 创建>创建标记]**. 已设置 **[!UICONTROL 标题]** as `DAM` 和 **[!UICONTROL 名称]** as `dam`. 选择 **[!UICONTROL 提交]**.
   ![在工作流模型中创建标记](assets/workflow_create_tag.png)

1. 导航到 **[!UICONTROL 工具>工作流>模型]**. 选择 **[!UICONTROL 激活请求]**，然后选择 **[!UICONTROL 编辑]**.

1. 选择 **[!UICONTROL 编辑]** ，然后打开 **[!UICONTROL 工作流模型属性]**. 转到 **[!UICONTROL 基本]** 选项卡。

1. 添加 `Workflow : DAM` to **[!UICONTROL 标记]** 字段。 使用勾号（勾号）确认选择。

1. 确认添加标记 **[!UICONTROL 保存并关闭]**.
   ![编辑模型的页面属性](assets/workflow_model_edit_activation1.png)

1. 使用完成该过程 **[!UICONTROL 同步]**. 现在，触屏UI中提供了工作流。

### 为多资源支持配置工作流 {#configuring-a-workflow-for-multi-resource-support}

您可以为配置工作流模型 [多资源支持](/help/sites-developing/workflows.md#multi-resource-support) 创建新模型或通过编辑现有模型时：

1. 打开的工作流模型 [编辑](#editing-a-workflow).
1. 选择 **[!UICONTROL 工作流模型属性]** 中。

1. 在对话框中，激活 **[!UICONTROL 多资源支持]** （或根据需要取消激活）：

   ![wf-08](assets/wf-08.png)

1. 确认更改 **[!UICONTROL 保存并关闭]**;后跟 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

### 配置工作流阶段（显示工作流进度） {#configuring-workflow-stages-that-show-workflow-progress}

[工作流阶段](/help/sites-developing/workflows.md#workflow-stages) 在处理任务时帮助可视化工作流的进度。

>[!CAUTION]
>
>是否在 **[!UICONTROL 页面属性]**，但不会用于任何工作流步骤，则进度栏不会显示任何进度（无论当前的工作流步骤如何）。

可用阶段在工作流模型中进行定义；可以更新现有的工作流模型以包含阶段定义。 您可以为工作流模型定义任意数量的阶段。

定义 **[!UICONTROL 阶段]** 对于您的工作流：

1. 打开工作流模型进行编辑。
1. 选择 **[!UICONTROL 工作流模型属性]** 中。 然后，打开 **[!UICONTROL 阶段]** 选项卡。
1. 添加（和定位）您需要的 **[!UICONTROL 阶段]**. 您可以为工作流模型定义任意数量的阶段。

   例如：

   ![wf-08-1](assets/wf-08-1.png)

1. 单击 **[!UICONTROL 保存并关闭]** 以保存属性。
1. 为工作流模型中的每个步骤分配一个阶段。 例如：

   ![wf-09](assets/wf-09.png)

   可以将阶段分配到多个步骤。 例如：

   | **步骤** | **暂存** |
   |---|---|
   | 步骤 1 | 创建 |
   | 步骤 2 | 创建 |
   | 步骤 3 | 审核 |
   | 步骤 4 | 批准 |
   | 步骤 5 | 批准 |
   | 步骤 6 | 完成 |

1. 确认更改 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

## 在包中导出工作流模型 {#exporting-a-workflow-model-in-a-package}

1. 使用 [包管理器](/help/sites-administering/package-manager.md#package-manager):

   1. 通过导航到包管理器 **[!UICONTROL 工具]**, **[!UICONTROL 部署]**, **[!UICONTROL 包]**.
   1. 单击 **[!UICONTROL 创建资源包]**.
   1. 指定 **[!UICONTROL 包名称]**，以及任何其他所需的详细信息。
   1. 单击&#x200B;**[!UICONTROL 确定]**。

1. 单击 **[!UICONTROL 编辑]** 中。

1. 打开 **[!UICONTROL 过滤器]** 选项卡。

1. 选择 **[!UICONTROL 添加过滤器]** 并指定工作流模型的路径 *设计*:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   单击 **[!UICONTROL 完成]**.

1. 选择 **[!UICONTROL 添加过滤器]** 并指定 *运行时* 工作流模型：

   `/var/workflow/models/<*your-model-name*>`

   单击 **[!UICONTROL 完成]**.

1. 为模型使用的任何自定义脚本添加其他过滤器。
1. 单击 **[!UICONTROL 保存]** 以确认过滤器定义。
1. 选择 **[!UICONTROL 生成]** 来访问Advertising Cloud帮助。
1. 选择 **[!UICONTROL 下载]** 中。

## 使用工作流处理表单提交 {#using-workflows-to-process-form-submissions}

您可以配置表单以供选定工作流处理。 用户提交表单时，将创建一个新的工作流实例，并将表单提交的数据作为其有效负载。

要配置要与表单一起使用的工作流，请执行以下操作：

1. 创建新页面并将其打开进行编辑。
1. 添加 **[!UICONTROL 表单]** 组件。
1. 配置 **[!UICONTROL 表单开始]** 显示在页面中的组件。
1. 使用 **[!UICONTROL 启动工作流]** 要从以下可用工作流中选择所需的工作流，请执行以下操作：

   ![wf-12](assets/wf-12.png)

1. 使用勾号确认新表单配置。

## 测试工作流 {#testing-workflows}

在测试工作流以使用各种负载类型时，这是一种良好的做法；包括与其开发对象不同的类型。 例如，如果您打算将工作流与资产进行处理，请通过将页面设置为有效负载来测试该工作流，并确保该工作流不会引发错误。

例如，按如下方式测试新工作流：

1. [启动工作流模型](/help/sites-administering/workflows-starting.md) 中。
1. 定义 **[!UICONTROL 负载]** 确认。

1. 根据需要采取相应操作，以便继续工作流。
1. 在工作流运行时监控日志文件。

您还可以配置AEM以显示 **[!UICONTROL 调试]** 日志文件中的消息。 请参阅 [记录](/help/sites-deploying/configure-logging.md) 有关更多信息，以及开发完成后，请将 **[!UICONTROL 日志级别]** 返回 **[!UICONTROL 信息]**.

## 示例 {#examples}

### 示例：创建用于接受或拒绝发布请求的（简单）工作流 {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

为了说明创建工作流的一些可能性，以下示例创建了 `Publish Example` 工作流。

1. [创建新的工作流模型](#creating-a-new-workflow).

   新工作流将包含：

   * **[!UICONTROL 流程开始]**
   * `Step 1`
   * **[!UICONTROL 流程结束]**

1. 删除 `Step 1` （因为此示例的步骤类型错误）：

   * 单击该步骤并选择 **[!UICONTROL 删除]** 中。 确认操作。

1. 从 **[!UICONTROL 工作流]** 选择步骤浏览器，拖动 **[!UICONTROL 参与者步骤]** 放在工作流上，并在 **[!UICONTROL 流量开始]** 和**[!UICONTROL 流量结束*]*.
1. 要打开属性对话框，请执行以下操作之一：

   * 单击参与者步骤并选择 **[!UICONTROL 配置]** 中。
   * 双击参与者步骤。

1. 在 **[!UICONTROL 常用]** 选项卡输入 `Validate Content` 对于 **[!UICONTROL 标题]** 和 **[!UICONTROL 描述]**.
1. 打开 **[!UICONTROL 用户/组]** 选项卡：

   * 激活 **[!UICONTROL 通过电子邮件通知用户]**.
   * 选择 `Administrator` ( `admin`) **[!UICONTROL 用户/组]** 字段。

   >[!NOTE]
   >
   >对于要发送的电子邮件， [需要配置邮件服务和用户帐户详细信息](/help/sites-administering/notification.md).

1. 使用勾号确认更新。

   您将返回到工作流模型的概述，此处的参与者步骤将重命名为 `Validate Content`.

1. 拖动 **[!UICONTROL 或拆分]** 放在工作流上，并在 `Validate Content` 和 **[!UICONTROL 流量结束]**.
1. 打开 **[!UICONTROL 或拆分]** ，以进行配置。
1. 配置：

   * **[!UICONTROL 常用]**:选择 **[!UICONTROL 2个分支]**
   * **[!UICONTROL 分行1]**:选择 **[!UICONTROL 默认路由]**.
   * **[!UICONTROL 分支2]**:确保 **[!UICONTROL 默认路由]** 未选择。

1. 确认对 **[!UICONTROL 或拆分]**.
1. 拖动 **[!UICONTROL 参与者步骤]** 在左侧分支中，打开属性，指定以下值，然后确认更改：

   * **[!UICONTROL 标题]**: `Reject Publish Request`
   * **[!UICONTROL 用户/组]**:例如， `projects-administrators`
   * **[!UICONTROL 通过电子邮件通知用户]**:激活以通过电子邮件通知用户。

1. 拖动 **[!UICONTROL 流程步骤]** 在右侧分支中，打开属性，指定以下值，然后确认更改：

   * **[!UICONTROL 标题]**: `Publish Page as Requested`
   * **[!UICONTROL 进程]**:选择 `Activate Page`. 此过程会将选定的页面发布到发布者实例。

1. 单击 **[!UICONTROL 同步]** （编辑器工具栏）以生成运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

   您的新工作流模型将如下所示：

   ![wf-13](assets/wf-13.png)

1. 将此工作流应用于您的页面，以便用户在 **[!UICONTROL 完成]** the **[!UICONTROL 验证内容]** 步骤，用户可以选择是否要 **[!UICONTROL 根据请求发布页面]**&#x200B;或 **[!UICONTROL 拒绝发布请求]**.

   ![chlimage_1-182](assets/chlimage_1-182.png)

### 示例：为OR拆分定义规则 {#example-defining-a-rule-for-an-or-split}

**[!UICONTROL 或拆分]** 利用步骤，可向工作流引入条件处理路径。

要定义OR规则，请执行以下操作：

1. 创建两个脚本并将其保存在存储库中，例如：

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >脚本必须具有 [函数 `check()`](#function-check) 返回布尔值。

1. 编辑工作流并添加 **[!UICONTROL 或拆分]** 到模型。
1. 编辑的属性 **[!UICONTROL 分行1]** 的 **[!UICONTROL 或拆分]**:

   * 将其定义为 **[!UICONTROL 默认路由]** 设置 **[!UICONTROL 值]** to `true`.
   * 作为 **[!UICONTROL 规则]**，则设置脚本的路径。 例如：

      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   >
   >您可以根据需要切换分支顺序。

1. 编辑 **[!UICONTROL 分支2]** 的 **[!UICONTROL 或拆分]**.

   * 作为 **[!UICONTROL 规则]**，则设置其他脚本的路径。 例如：

      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. 设置每个分支中各个步骤的属性。 确保 **[!UICONTROL 用户/组]** 设置。
1. 单击 **同步** （编辑器工具栏）来将更改保留到运行时模型。

   请参阅 [同步工作流](#sync-your-workflow-generate-a-runtime-model) 以了解详细信息。

#### 函数检查() {#function-check}

>[!NOTE]
>
>请参阅 [使用ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).

以下示例脚本返回 `true` 如果节点是 `JCR_PATH` 位于 `/content/we-retail/us/en`:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      } 
     } else {
      return false;
     }
}
```

### 示例：自定义的激活请求 {#example-customized-request-for-activation}

您可以自定义任何现成的工作流。 要实现自定义行为，请叠加相应工作流的详细信息。

例如， **[!UICONTROL 激活请求]**. 此工作流用于在 **[!UICONTROL 站点]** 和会在内容作者没有相应的复制权限时自动触发。 请参阅 [自定义页面创作 — 自定义激活请求工作流](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow) 以了解更多详细信息。
