---
title: 管理内容片段
seo-title: Managing Content Fragments
description: 内容片段以资产形式存储，因此主要通过“资产”控制台进行管理。
seo-description: Content Fragments are stored as Assets, so are primarily managed from the Assets console.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
exl-id: b21ba7a1-6e6f-4b95-9336-b49f7e932af5
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 63%

---

# 管理内容片段 {#managing-content-fragments}

>[!CAUTION]
>
>某些内容片段功能需要应用 [AEM 6.4 Service Pack 2(6.4.2.0)或更高版本](/help/release-notes/sp-release-notes.md).

内容片段存储为 **[!UICONTROL 资产]**，因此主要从 **[!UICONTROL 资产]** 控制台。

>[!NOTE]
>
>然后，内容片段可与创作页面一起使用；请参阅 [使用内容片段进行页面创作](/help/sites-authoring/content-fragments.md).

## 创建内容片段 {#creating-content-fragments}

### 创建内容模型 {#creating-a-content-model}

[内容片段模型](content-fragments-models.md)可在使用结构化内容创建内容片段之前启用和创建。

>[!NOTE]
>
>请参阅 [开发内容片段](/help/sites-developing/customizing-content-fragments.md) 进一步了解模板；用于简单内容片段。

### 创建内容片段 {#creating-a-content-fragment}

对于简单片段和结构化片段，创建内容片段的方法（基本上）相同：

1. 导航到要 **[!UICONTROL 创建片段]** 的Assets文件夹。
1. 选择 **[!UICONTROL 创建]**，然后选择 **[!UICONTROL 内容片段]** ，以打开向导。
1. 向导的第一步要求您指定新片段的基础。

   * 这可以是：

      * [模板](/help/sites-developing/content-fragment-templates.md)  — 例如 **[!UICONTROL 简单片段]**
      * [模型](content-fragments-models.md)  — 用于创建需要结构化内容的片段；例如， **机场** 模型
   * 将显示所有可用的模板和模型。

   选择后，使用 **[!UICONTROL 下一个]** 以继续。

   ![cfm-6420-15](assets/cfm-6420-15.png)

1. 在属性 **[!UICONTROL 步骤中]** ，指定：

   * **[!UICONTROL 基本]**

      * **[!UICONTROL 标题]**

         片段标题。

         强制.

      * **[!UICONTROL 描述]**
      * **[!UICONTROL 标记]**
   * **[!UICONTROL 高级]**

      * **[!UICONTROL 名称]**

         名称；将用于形成URL。

         强制；将自动从标题派生，但可以更新。


1. 选 **[!UICONTROL 择创建]** ，以完成操作，然后打开片段 **[!UICONTROL 进行编辑]** ，或返回控制台并执行完 **[!UICONTROL 成]**。

## 内容片段的操作 {#actions-for-a-content-fragment}

在 **[!UICONTROL 资产]** 控制台为您的内容片段提供了一系列操作，包括：

* 工具栏中；选择片段后，所有适当的操作都可用。
* 作为 [快速操作](/help/sites-authoring/basic-handling.md#quick-actions);可用于单个片段卡的操作子集。

![cfm-6420-17](assets/cfm-6420-17.png)

选择片段以显示包含适用操作的工具栏：

* **[!UICONTROL 下载]**

   * 将片段另存为ZIP文件；您可以定义是否包含元素、变量、元数据。

* **[!UICONTROL 创建]**
* **[!UICONTROL 签出]**
* **[!UICONTROL 属性]**

   * 用于查看和/或编辑片段的元数据。

* **[!UICONTROL 编辑]**

   * 允许您 [打开片段以编辑内容](content-fragments-variations.md) 元素、变量、关联内容和元数据。

* **[!UICONTROL 管理标记]**
* **[!UICONTROL 目标收藏集]**

   * 将片段添加到集合。
   * 此操作也可在 [将集合与片段关联](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL 复制/粘贴]**
* **[!UICONTROL 移动]**
* **[!UICONTROL 快速发布]**
* **[!UICONTROL 管理发布]**
* **[!UICONTROL 删除]**

>[!NOTE]
>
>其中很多是 [资产的标准操作](managing-assets-touch-ui.md) 和/或 [桌面应用程序](https://helpx.adobe.com/cn/experience-manager/desktop-app/aem-desktop-app.html).

## 打开片段编辑器 {#opening-the-fragment-editor}

打开片段进行编辑：

>[!CAUTION]
>
>要编辑内容片段，您需要[相应的权限](/help/sites-developing/customizing-content-fragments.md#asset-permissions)。 如果您遇到问题，请联系您的系统管理员。

1. 使用 **[!UICONTROL 资产]** 控制台以导航到内容片段的位置。
1. 通过以下任一方式打开片段进行编辑：

   * 单击/点按片段或片段链接（这取决于控制台视图）。
   * 选择片段，然后 **[!UICONTROL 编辑]** 中。

   将打开片段编辑器：

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. 当内容页面上已引用片段时，将显示一条消息。 
   >
   >2. 可以使用&#x200B;**[!UICONTROL 切换侧面板]**&#x200B;图标来隐藏/显示侧面板。


1. 使用侧面板中的图标在三种模式之间导航：

   * 变体：[编辑内容](#editing-the-content-of-your-fragment)和[管理变量](#creating-and-managing-variations-within-your-fragment)
   * [注释](content-fragments-variations.md#annotating-a-content-fragment)
   * [关联的内容](#associating-content-with-your-fragment)
   * [元数据](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. 进行更改后，请使用 **[!UICONTROL 保存]** 或 **[!UICONTROL 取消]** 。

   >[!NOTE]
   >
   >“保 **[!UICONTROL 存]** ”和“取消 **[!UICONTROL ”将退出编辑器——有关这两个选项如何对内容片段进行操作的完整信息，请参阅]**[](#save-cancel-and-versions) “保存”、“取消”和“版本”。

## 保存、取消和版本 {#save-cancel-and-versions}

>[!NOTE]
>
>版本也可以从时间线[创建、比较和还原](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments)。

编辑器有两个选项：

* **[!UICONTROL 保存]**

   将保存最新更改并退出编辑器。

   >[!CAUTION]
   >
   >要编辑内容片段，您需要[相应的权限](/help/sites-developing/customizing-content-fragments.md#asset-permissions)。 如果您遇到问题，请联系您的系统管理员。

   >[!NOTE]
   >
   >在选择之前，可以保留在编辑器中，进行一系列更改 **[!UICONTROL 保存]**.

   >[!CAUTION]
   >
   >除了仅保存更改外， **[!UICONTROL 保存]** 此外，还会更新任何引用，并确保调度程序根据需要刷新。 这些更改可能需要一些时间才能处理。 因此，对于大型/复杂/重载系统，性能可能会受到影响。
   >
   >
   >在使用 **[!UICONTROL 保存]** 然后快速重新进入片段编辑器以进行并保存进一步的更改。

* **[!UICONTROL 取消]**

   将退出编辑器，而不保存最新更改。

在编辑内容片段时，AEM会自动创建版本，以确保在您 **[!UICONTROL 取消]** 您所做的更改：

1. 打开内容片段以编辑 AEM 时，会检查是否存在基于 Cookie 的令牌，以指示&#x200B;*编辑会话*&#x200B;存在：

   1. 如果找到令牌，则该片段将被视为现有编辑会话的一部分。
   1. 如果令牌为&#x200B;*不*&#x200B;可用，用户便开始编辑内容，并创建一个版本，并将此新编辑会话的令牌发送到客户端，客户端将保存在 Cookie 中。

1. 当有一个&#x200B;*活动*&#x200B;编辑会话时，正在编辑的内容每 600 秒自动保存一次（默认）。

   >[!NOTE]
   >
   >自动保存间隔可使用`/conf`机制进行配置。
   >
   >默认值，请参阅：
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. 如果用户选择 **[!UICONTROL 取消]** 在编辑时，将恢复在编辑会话开始时创建的版本，并删除令牌以结束编辑会话。
1. 如果用户选择&#x200B;**[!UICONTROL 保存]**&#x200B;编辑，将保留更新的元素/变体，并删除令牌以结束编辑会话。

## 编辑片段的内容 {#editing-the-content-of-your-fragment}

打开片段后，您可以使用[变体](content-fragments-variations.md)选项卡来创作内容。

## 创建和管理片段中的变体 {#creating-and-managing-variations-within-your-fragment}

创建主控内容后，即可创建和管理[变体](content-fragments-variations.md)内容的一部分。

## 将内容与片段关联 {#associating-content-with-your-fragment}

您还可以[关联内容](content-fragments-assoc-content.md)与片段。 这提供了一个连接，以便在将资产（即图像）添加到内容页面时，可以（可选）与片段一起使用资产（即图像）。

## 查看和编辑片段的元数据（属性） {#viewing-and-editing-the-metadata-properties-of-your-fragment}

您可以使用[[!UICONTROL 元数据]](content-fragments-metadata.md)选项卡查看和编辑片段的属性。

## 内容片段的时间线 {#timeline-for-content-fragments}

除了标准选项外，[时间线](managing-assets-touch-ui.md#timeline)提供特定于内容片段的信息和操作：

* 查看有关版本、注释和批注的信息
* 版本操作

   * **[[!UICONTROL 还原到此版本]](#reverting-to-a-version)**（选择现有片段，然后选择特定版本）
   * **[[!UICONTROL 与当前比较]](#comparing-fragment-versions)**（选择现有片段，然后选择特定版本）
   * 添加&#x200B;**[!UICONTROL 标签]**&#x200B;和/或&#x200B;**[!UICONTROL 注释]**（选择现有片段，然后选择特定版本）
   * **[!UICONTROL 保存为版本]**（选择现有片段，然后选择时间线底部的向上箭头）

* 注释操作

   * **[!UICONTROL 删除]**

>[!NOTE]
>
>评论包括：
>
>* 所有资产的标准功能
>* 在时间线中制造
>* 与片段资产相关
>
>注释（适用于内容片段）包括：
>
>* 在片段编辑器中输入
>* 特定于片段中选定的文本区段


例如：

![cfm-6420-19](assets/cfm-6420-19.png)

## 比较片段版本 {#comparing-fragment-versions}

选择特定版本后，[[!UICONTROL 时间线]中的&#x200B;**[!UICONTROL 与当前比较]**&#x200B;操作可用。](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments)

此时将打开：

* **[!UICONTROL 当前]**（最新）版本（左）

* 所选版本 **v&lt;*x.y*>**（右）

它们将并排显示，其中：

* 任何差异都会突出显示

   * 已删除的文本 – 红色
   * 插入的文本 – 绿色
   * 替换文本 – 蓝色

* 全屏图标允许您自行打开任一版本；然后切换回并行视图
* 您可以&#x200B;**[!UICONTROL 还原]**&#x200B;到特定版本
* **[!UICONTROL 完成]**&#x200B;将返回控制台

>[!NOTE]
>
>比较片段时无法编辑片段内容。

![cfm-6420-20](assets/cfm-6420-20.png)

## 恢复到某个版本  {#reverting-to-a-version}

您可以还原到片段的特定版本：

* 直接从[[!UICONTROL 时间线]](content-fragments-managing.md#timeline-for-content-fragments)。

   选择所需的版本，然后&#x200B;**[!UICONTROL 还原到此版本]**&#x200B;操作。

* [将版本与当前版本进行比较](content-fragments-managing.md#comparing-fragment-versions)时，您可以&#x200B;**[!UICONTROL 还原]**&#x200B;到所选版本。

## 发布和引用片段 {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>如果您的片段基于模型，则应确保[模型已发布](content-fragments-models.md#publishing-a-content-fragment-model)。
>
>如果发布的内容片段的模型尚未发布，则会显示一个选择列表来指示该情况，并且模型将随该片段一起发布。

必须发布内容片段才能在发布环境中使用。 它们可以发布：

* 创建后；从 **[!UICONTROL 资产]** 控制台。
* 当您 [发布使用片段的页面](/help/sites-authoring/content-fragments.md#publishing);片段将在页面引用中列出。

>[!CAUTION]
>
>片段发布和/或引用后，当作者再次打开片段进行编辑时，AEM 将显示警告。 这是为了警告，对片段所做的更改也会影响引用的页面。

## 删除片段 {#deleting-a-fragment}

删除片段：

1. 在 **[!UICONTROL Assets]** 控制台导航到内容片段的位置。
1. 选择片段。

   >[!NOTE]
   >
   >**[!UICONTROL 删除]**&#x200B;操作不能作为快速操作使用。

1. 从工具栏中选择&#x200B;**[!UICONTROL 删除]**。
1. 确认&#x200B;**[!UICONTROL 删除]**&#x200B;操作。

   >[!CAUTION]
   >
   >如果片段已在页面中被引用，您将看到一条警告消息，需要您确认是否继续执行&#x200B;**[!UICONTROL 强制删除]**。片段及其内容片段组件将从任何内容页面中删除。
