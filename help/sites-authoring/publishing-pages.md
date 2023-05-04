---
title: 发布页面
seo-title: Publishing Pages
description: 发布页面
seo-description: null
uuid: 1222859d-ef8d-462e-a125-b76e6cfec26d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8f2714bc-9d6c-4e6f-97a1-3b4f977348c5
exl-id: 3de608f3-569f-438d-8ce7-24e82e5c1ec6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 52%

---

# 发布页面{#publishing-pages}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在创作环境中创建并审核内容后，您的目标便是 [在您的公共网站上提供](/help/sites-authoring/author.md#concept-of-authoring-and-publishing) （您的发布环境）。

这称为发布页面。 当您要从发布环境中删除页面时，称为取消发布。 发布和取消发布页面时，该页面会在创作环境中保留以供进一步更改，直到将其删除为止。

您还可以立即发布/取消发布页面，或者在某个预定义的将来日期/时间发布/取消发布页面。

>[!NOTE]
>
>某些与发布相关的术语可能会混淆：
>
>* **发布/取消发布**
   >  这些是在发布环境中公开提供（或不公开提供）您的内容的主要操作术语。
>
>* **激活／取消激活**
   >  这两个术语与发布/取消发布同义。
>
>* **复制**
   >  这些是技术术语，用于描述数据（例如页面内容、文件、代码、用户评论）从一个环境移动到另一个环境（例如在发布或反向复制用户评论时）的移动。
>


>[!NOTE]
>
>如果您没有发布特定页面所需的权限，请执行以下操作：
>
>* 将触发一个工作流，向相应的人员通知您的发布请求。
>* 此 [工作流可能已自定义](/help/sites-developing/workflows-models.md) 由您的开发团队负责。
>* 将显示一条简短的消息，通知您工作流已经触发。
>


## 发布页面 {#publishing-pages-2}

根据您的位置，您可以发布：

* [从页面编辑器中](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor)
* [从站点控制台中](/help/sites-authoring/publishing-pages.md#publishing-from-the-console)

### 从编辑器中发布 {#publishing-from-the-editor}

如果您在编辑页面，则可以直接从编辑器中发布该页面。

1. 选择&#x200B;**页面信息**&#x200B;图标以打开相应的菜单，然后选择&#x200B;**发布页面**&#x200B;选项。

   ![screen_shot_2018-03-21at152734](assets/screen_shot_2018-03-21at152734.png)

1. 根据页面是否包含需要发布的引用：

   * 如果不包含要发布的引用，则将直接发布页面。
   * 如果页面包含需要发布的引用，则将在&#x200B;**发布**&#x200B;向导中列出该内容，从该向导中可以：

      * 指定要与页面一起发布的资产/标记/等，然后使用&#x200B;**发布**&#x200B;完成该过程。
      * 使用&#x200B;**取消**&#x200B;中止操作。

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. 选择&#x200B;**发布**&#x200B;会将页面复制到发布环境。在页面编辑器中，将显示一个确认发布操作的信息横幅。

   ![screen_shot_2018-03-21at152840](assets/screen_shot_2018-03-21at152840.png)

   当在控制台中查看同一页面时，将显示更新的发布状态。

   ![screen_shot_2018-03-21at152951](assets/screen_shot_2018-03-21at152951.png)

>[!NOTE]
>
>从编辑器中发布是一种简单的发布方式，即只发布选定的页面/页面，而不发布任何子页面。

>[!NOTE]
>
>无法发布编辑器中按[别名](/help/sites-authoring/editing-page-properties.md#advanced)处理的页面。编辑器中的发布选项仅适用于通过其实际路径访问的页面。

### 从控制台中发布 {#publishing-from-the-console}

在站点控制台中，有两个用于发布的选项：

* [快速发布](/help/sites-authoring/publishing-pages.md#quick-publish)
* [管理发布](/help/sites-authoring/publishing-pages.md#manage-publication)

#### 快速发布 {#quick-publish}

**快速发布**&#x200B;适用于一些简单的情况，可立即发布选定的页面，而无需进行任何进一步的交互。因此，任何未发布的引用也将自动发布。

要通过快速发布发布发布页面，请执行以下操作：

1. 在站点控制台中选择一个或多个页面，然后单击&#x200B;**快速发布**&#x200B;按钮。

   ![screen_shot_2018-03-21at153115](assets/screen_shot_2018-03-21at153115.png)

1. 在快速发布对话框中，单击 **发布** 或单击以取消 **取消**. 请记住，任何未发布的引用也将被自动发布。

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. 发布页面时，会显示确认发布的警报。

>[!NOTE]
>
>“快速发布”是一种简单的发布方式，即只发布选定的页面/页面，而不发布任何子页面。

#### 管理发布 {#manage-publication}

与“快速发布”相比，**管理发布**&#x200B;提供了更多选项，允许包含子页面、自定义引用和启动任何适用的工作流，并且还提供了在以后的日期发布的选项。

要使用“管理发布”发布或取消发布页面，请执行以下操作：

1. 在站点控制台中选择一个或多个页面，然后单击&#x200B;**管理发布**&#x200B;按钮。

   ![screen_shot_2018-03-21at153309](assets/screen_shot_2018-03-21at153309.png)

1. 此时会启动&#x200B;**管理发布**&#x200B;向导。第一个步骤&#x200B;**选项**&#x200B;允许您：

   * 选择发布或取消发布选定的页面。
   * 选择立即或稍后执行该操作。

   稍后发布会启动一个工作流，用于在指定时间发布选定的一个或多个页面。 相反，稍后取消发布则会启动一个工作流，用于在特定时间取消发布选定的一个或多个页面。

   如果您要稍后撤消发布/取消发布页面，请转到[“工作流”控制台](/help/sites-administering/workflows.md)以终止相应的工作流。

   ![chlimage_1-52](assets/chlimage_1-52.png)

   单击&#x200B;**下一步**&#x200B;以继续。

1. 在“管理发布”向导的下一步中， **范围**，您可以定义发布/取消发布的范围，如包括子页面和/或包括引用。

   ![screen_shot_2018-03-21at153354](assets/screen_shot_2018-03-21at153354.png)

   如果您因一时疏忽而忘记在启动“管理发布”向导之前选择某个页面，则可以使用&#x200B;**添加内容**&#x200B;按钮将其他页面添加到要发布的页面列表中。

   单击“添加内容”按钮会启动[路径浏览器](/help/sites-authoring/author-environment-tools.md#path-browser)以供选择内容。

   选择所需的页面，然后单击&#x200B;**选择**&#x200B;以将该内容添加到向导，或单击 **取消** 以取消所做的选择并返回到向导。

   返回向导后，您可以选择列表中的某个项目以配置其其他选项，例如：

   * 包括其子项。
   * 将其从选定范围中删除。
   * 管理其已发布的引用。

   ![screen_shot_2018-03-21at153450](assets/screen_shot_2018-03-21at153450.png)

   单击&#x200B;**包括子项**&#x200B;会打开一个对话框，它允许您：

   * 仅包括下级子项.
   * 仅包括已修改的页面.
   * 仅包括已发布的页面.

   单击&#x200B;**添加**&#x200B;可根据选择的选项将子页面添加到要发布或取消发布的页面列表中。单击&#x200B;**取消**&#x200B;可取消所做的选择并返回到向导。

   ![chlimage_1-53](assets/chlimage_1-53.png)

   返回到向导后，您将看到根据您在“包括子项”对话框中选择的选项添加的页面。

   您可以通过选择页面，然后单击&#x200B;**已发布引用**&#x200B;按钮，来查看和修改该页面要发布或取消发布的引用。

   ![screen_shot_2018-03-21at153801](assets/screen_shot_2018-03-21at153801.png)

   的 **发布的引用** 对话框显示所选内容的引用。 默认情况下，这些参数都处于选中状态并将被发布/取消发布，但您可以取消选中以将其选中，以便这些参数不会包含在操作中。

   单击 **完成** 保存更改或 **取消** 以取消选择并返回到向导。

   ![screen_shot_2018-03-21at153824](assets/screen_shot_2018-03-21at153824.png)

   返回到向导后，**引用**&#x200B;列将进行相应的更新，以反映您选择的要发布或取消发布的引用。

   ![screen_shot_2018-03-21at153925](assets/screen_shot_2018-03-21at153925.png)

1. 单击&#x200B;**发布**&#x200B;以完成。

   返回到站点控制台后，将显示一条确认发布的通知消息。

   ![screen_shot_2018-03-21at153951](assets/screen_shot_2018-03-21at153951.png)

1. 如果发布的页面与工作流相关联，则这些工作流可能会显示在发布向导的最后一个步骤&#x200B;**工作流**&#x200B;中。

   >[!NOTE]
   >
   >将根据用户可能拥有也可能没有的权限显示&#x200B;**工作流**&#x200B;步骤。请参阅 [本页的前面注释](/help/sites-authoring/publishing-pages.md) 关于发布权限 [管理工作流的访问权限](/help/sites-administering/workflows-managing.md) 和 [将工作流应用于页面](/help/sites-authoring/workflows-applying.md) 以了解详细信息。

   资源按触发的工作流进行分组，每个给定选项可用于：

   * 定义工作流的标题。
   * 保留工作流包，前提是工作流已 [多资源支持](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).
   * 在选择保留工作流包的选项时，定义工作流包的标题。

   单击 **发布** 或**稍后发布**以完成发布。

   ![chlimage_1-54](assets/chlimage_1-54.png)

## 取消发布页面 {#unpublishing-pages}

取消发布页面将从发布环境中删除该页面，以便不再将其提供给您的读者。

通过[与发布类似的方式](/help/sites-authoring/publishing-pages.md#publishing-pages)，可以取消发布一个或多个页面：

* [从页面编辑器中](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-editor)
* [从站点控制台中](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-console)

### 从编辑器中取消发布 {#unpublishing-from-the-editor}

在编辑页面时，如果要取消发布该页面，请选择 **取消发布页面** 在 **页面信息** 菜单，就象你想的 [发布页面](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor).

>[!NOTE]
>
>无法取消发布编辑器中按[别名](/help/sites-authoring/editing-page-properties.md#advanced)处理的页面。编辑器中的发布选项仅适用于通过其实际路径访问的页面。

### 从控制台中取消发布 {#unpublishing-from-the-console}

正如[使用“管理发布”选项发布页面](/help/sites-authoring/publishing-pages.md#manage-publication)一样，也可以使用它来取消发布页面。

1. 在站点控制台中选择一个或多个页面，然后单击&#x200B;**管理发布**&#x200B;按钮。
1. 此时会启动&#x200B;**管理发布**&#x200B;向导。在第一个步骤&#x200B;**选项**&#x200B;中，选择&#x200B;**取消发布**，而不是默认选项&#x200B;**发布**。

   ![chlimage_1-55](assets/chlimage_1-55.png)

   正如稍后发布会启动一个工作流，以在指定时间发布此版本页面一样，稍后取消激活也会启动一个工作流，以在指定时间取消发布选定的一个或多个页面。

   如果您要稍后撤消发布/取消发布页面，请转到[“工作流”控制台](/help/sites-administering/workflows.md)以终止相应的工作流。

1. 要完成取消发布，请按照所需的步骤继续完成向导 [发布页面](/help/sites-authoring/publishing-pages.md#manage-publication).

## 发布和取消发布树 {#publishing-and-unpublishing-a-tree}

当您输入或更新了大量内容页面（所有内容页面都位于同一根页面下）后，可以更轻松地通过一个操作发布整个树。

您可以使用 [管理发布](/help/sites-authoring/publishing-pages.md#manage-publication) 选项来执行此操作。

1. 在站点控制台中，选择要发布或取消发布的树的根页面，然后选择 **管理发布**.
1. 此时会启动&#x200B;**管理发布**&#x200B;向导。选择发布或取消发布以及应在何时发布，然后选择 **下一个** 继续。
1. 在 **范围** 步骤中，选择根页面并选择 **包含子项**.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. 在 **包含子项** 对话框中，取消选中选项：

   * 仅包括下级子项
   * 仅包括已发布的页面

   这些选项默认处于选中状态，因此您必须记住取消选择它们。 单击 **添加** 确认并将内容添加到发布/取消发布。

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 的 **管理发布** 向导会列出树的内容以供审阅。 您可以通过添加其他页面或删除那些选定的页面进一步自定义所做的选择。

   ![screen_shot_2018-03-21at154237](assets/screen_shot_2018-03-21at154237.png)

   请记住，您还可以通过&#x200B;**已发布引用**&#x200B;选项查看要发布的引用。

1. [照常继续“管理发布”向导](#manage-publication) 以完成树的发布或取消发布。

## 确定发布状态 {#determining-publication-status}

您可以确定页面的发布状态：

* 在[站点控制台上的资源概述信息](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)中

   ![screen_shot_2018-03-21at154336](assets/screen_shot_2018-03-21at154336.png)

   站点控制台的[信息卡](/help/sites-authoring/basic-handling.md#card-view)、[列](/help/sites-authoring/basic-handling.md#column-view)和[列表](/help/sites-authoring/basic-handling.md#list-view)视图中将显示发布状态。

* 在[时间线](/help/sites-authoring/basic-handling.md#timeline)中

   ![screen_shot_2018-03-21at154420](assets/screen_shot_2018-03-21at154420.png)

* 在[“页面信息”菜单](/help/sites-authoring/author-environment-tools.md#page-information)中（编辑页面时）

   ![screen_shot_2018-03-21at154456](assets/screen_shot_2018-03-21at154456.png)
