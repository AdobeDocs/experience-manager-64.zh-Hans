---
title: 管理资产收藏集
description: 了解管理资产收藏集的任务，如创建、查看、删除、编辑和下载收藏集。
contentOwner: AG
mini-toc-levels: 1
feature: Collections
role: User
exl-id: cadfc569-5725-4012-9f73-864243ba7743
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2362'
ht-degree: 18%

---

# 管理收藏集 {#managing-collections}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

收藏集是Adobe Experience Manager Assets中的一组资产。 使用收藏集可在用户之间共享资源。该集可以是静态收藏集或基于搜索结果的动态收藏集。

收藏集与文件夹的不同之处是可包含来自不同位置的资源。您可以与分配了不同权限级别（包括查看、编辑等）的各种用户共享收藏集。

您可以与一个用户共享多个收藏集。每个收藏集都包含对资源的引用。收藏集中会保持资源的引用完整性。

收藏集的类型如下，具体取决于收藏集整理资产的方式：

* 包含资产、文件夹和其他收藏集的静态引用列表的收藏集。
* 一种智能收藏集，可根据搜索条件动态包含资产。

## 访问收藏集控制台 {#navigating-the-collections-console}

要打开 **[!UICONTROL 收藏集]**，点按或单击Experience Manager徽标。 在导航页面中，转到 **[!UICONTROL 资产]** > **[!UICONTROL 收藏集]**.

## 创建收藏集 {#creating-a-collection}

您可以通过 [静态引用](#creating-a-collection-with-static-references) 或基于 [基于搜索条件的过滤器](#creating-a-smart-collection). 您还可以从灯箱创建收藏集。

### 创建包含静态引用的集合 {#creating-a-collection-with-static-references}

您可以创建包含静态引用的收藏集，例如包含对资产、文件夹、收藏集、旋转集和图像集的引用的收藏集。

1. 导航到 **[!UICONTROL 收藏集]** 控制台。
1. 在工具栏中，点按/单击 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL 创建收藏集]** 页面，输入收藏集的标题和可选描述。
1. 向收藏集添加成员并分配相应的权限。或者，选择&#x200B;**[!UICONTROL 公共收藏集]**，以允许所有用户访问该收藏集。

   >[!NOTE]
   >
   >要使成员能够与其他用户共享收藏集，请提供 `dam-users` 路径上的群组读取权限 `home/users`. 为用户授予以下权限： `/content/dam/collections` 位置，以允许用户在弹出列表中查看收藏集。 或者，将用户设为 `dam-users` 群组。

1. （可选）为收藏集添加缩略图。
1. 点按／单 **[!UICONTROL 击创建]**，然后点按／单 **[!UICONTROL 击确定]** ，关闭对话框。 具有指定标题和属性的集合将在“收藏集”控制台中打开。

   >[!NOTE]
   >
   >Experience Manager Assets允许您为收藏集创建审核任务，其方式与为资产文件夹创建审核任务类似。

   要将资产添加到收藏集，请导航到资产用户界面。 有关详细信息，请参阅 [将资产添加到收藏集](/help/assets/managing-collections-touch-ui.md#adding-assets-to-a-collection).

### 使用拖放区创建收藏集 {#create-collections-using-dropzone}

您可以将资产从资产UI拖到收藏集。 您还可以创建收藏集的副本，并将资产拖动到此处。

1. 从资产UI中，选择要添加到收藏集的资产。
1. 将资产拖到 **[!UICONTROL 放入收藏集]** 区域。

   ![drop_in_collection](assets/drop_in_collection.png)

   当拖放区域处于活动状态，且其标签更改为 **[!UICONTROL 拖放以添加]**.

   ![drop_to_add](assets/drop_to_add.png)

   或者，点按/单击 **[!UICONTROL 收藏]** 图标。

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. 在&#x200B;**[!UICONTROL 添加到收藏集]**&#x200B;页面中，点按/单击工具栏中的&#x200B;**[!UICONTROL 创建收藏集]**&#x200B;图标。

   如果要将资产添加到现有收藏集，请从页面中选择它，然后点按／单击添 **[!UICONTROL 加]**。 默认情况下，将选择最近更新的集合。

1. 在&#x200B;**[!UICONTROL 创建新收藏集]**&#x200B;对话框中，指定收藏集的名称。如果希望所有用户都可以访问该收藏集，请选择&#x200B;**[!UICONTROL 公共收藏集]**。
1. 点按/单击 **[!UICONTROL 继续]** 创建收藏集。

### 创建智能收藏集 {#creating-a-smart-collection}

智能收藏集使用搜索条件动态填充资产。 您可以仅使用文件，而不使用文件夹或文件和文件夹来创建智能收藏集。

要创建智能收藏集，请执行以下步骤：

1. 导航到资产用户界面，然后点按/单击搜索图标。

1. 在Omnisearch框中输入搜索关键词，然后按Enter。 打开“过滤器”面板并应用搜索过滤器。

1. 从 **[!UICONTROL 文件和文件夹]** 列表，选择 **[!UICONTROL 文件]**.

   ![files_option](assets/files_option.png)

1. 点按/单击 **[!UICONTROL 保存智能收藏集]**.
1. 指定集合的名称。 选择 **[!UICONTROL 公共]** 将具有查看者角色的DAM用户组添加到智能收藏集。

   ![save_collection](assets/save_collection.png)

   >[!NOTE]
   >
   >如果您选择 **[!UICONTROL 公共]**，则在创建智能收藏集后，具有所有者角色的每个人都可以使用该智能收藏集。 如果取消选择 **[!UICONTROL 公共]** 选项，则DAM用户组将不再与智能收藏集关联。

1. 点按/单击&#x200B;**[!UICONTROL 保存]**，以创建智能收藏集，然后关闭消息框以完成该进程。

   新的智能收藏集也会添加到 **[!UICONTROL 保存的搜索]** 列表。

   ![collection_listing](assets/collection_listing.png)

   “创建智能选 **[!UICONTROL 择”按钮的标签会变]** 为“编 **[!UICONTROL 辑智能选择”]**。 要编辑智能收藏集的设置，请从“文件和文 **[!UICONTROL 件夹]** ”列 **[!UICONTROL 表中选择“文件]** ”。 然后，点按／单击编辑 **[!UICONTROL 智能选择]** 按钮。

   ![chlimage_1-112](assets/chlimage_1-112.png)

## 将资源添加到收藏集 {#adding-assets-to-a-collection}

您可以将资产添加到包含引用资产或文件夹列表的收藏集。 智能收藏集使用搜索查询来填充资产。 因此，对资产和文件夹的静态引用不适用于这些资产和文件夹。

1. 在Assets用户界面中，选择资产，然后点按/单击 **[!UICONTROL 收藏]** 图标。

   ![chlimage_1-113](assets/chlimage_1-113.png)

   或者，您也可以将资产拖到 **[!UICONTROL 放入收藏集]** 区域。 当区域的标签更改为 **[!UICONTROL 拖放以添加]**.

1. 在 **[!UICONTROL 添加到收藏集]** ，请选择要将资产添加到的收藏集。

1. 点按/单击 **[!UICONTROL 添加]**，然后关闭确认消息。 资产会添加到收藏集。

## 编辑智能收藏集 {#editing-a-smart-collection}

智能收藏集是通过保存搜索来构建的，因此您可以通过修改 [保存的搜索](#editing-saved-searches).

1. 在Assets用户界面中，点按/单击工具栏中的搜索图标。

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. 将光标置于Omnisearch框中，按Return键。

1. 点按/单击GlobalNav图标以显示“过滤器”面板。

1. 从&#x200B;**[!UICONTROL 保存的搜索]**&#x200B;列表中，选择要修改的智能收藏集。“搜索”面板显示为保存的搜索配置的过滤器。

   ![select_smart_collection](assets/select_smart_collection.png)

1. 从 **[!UICONTROL 文件和文件夹]** 列表，选择 **[!UICONTROL 文件]**.

1. 根据需要修改一个或多个过滤器。 点按/单击 **[!UICONTROL 编辑智能收藏集]**.

   您还可以编辑智能收藏集的名称。

   ![edit_smart_collectiondialog](assets/edit_smart_collectiondialog.png)

1. 点按/单击 **[!UICONTROL 保存]**. 的 **[!UICONTROL 编辑智能收藏集]** 对话框。

1. 点按/单击 **[!UICONTROL 覆盖]** 将原始智能收藏集替换为已编辑的收藏集。 或者，选择 **[!UICONTROL 另存为]** 单独保存已编辑的收藏集。

1. 在确认对话框中，点按/单击 **[!UICONTROL 保存]** 以完成该过程。

## 查看和编辑收藏集元数据 {#viewing-and-editing-collection-metadata}

收藏集元数据包含有关收藏集的数据，包括添加的任何标记。

1. 从收藏集控制台中，选择一个收藏集，然后点按/单击 **[!UICONTROL 属性]** 图标。
1. 在&#x200B;**[!UICONTROL 收藏集元数据]**&#x200B;页面中，从&#x200B;**[!UICONTROL 基本]**&#x200B;和&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡中查看收藏集元数据。
1. 根据需要修改元数据，然后点按/单击 **[!UICONTROL 保存并关闭]** 来保存更改。

### 批量编辑多个收藏集的元数据 {#editing-collection-metadata-in-bulk}

您可以同时编辑多个收藏集的元数据。 此功能可帮助您快速在多个集合中复制常用元数据。

1. 在收藏集控制台中，选择要为其编辑元数据的两个或更多收藏集。
1. 在工具栏中，点按/单击 **[!UICONTROL 属性]**.
1. 在&#x200B;**[!UICONTROL 收藏集元数据]**&#x200B;页面中，根据需要编辑&#x200B;**[!UICONTROL 基本]**&#x200B;和&#x200B;**[!UICONTROL 高级]**&#x200B;选项卡下的元数据。
1. 要查看特定收藏集的元数据属性，请取消选择收藏集列表中的其余收藏集。 元数据编辑器字段中填充了特定集合的元数据。

   >[!NOTE]
   >
   >* 在收藏集属性页面中，您可以通过取消选择收藏集来从收藏集列表中删除这些收藏集。 默认情况下，收藏集列表会选择所有收藏集。 您删除的收藏集的元数据不会更新。
   >* 在列表顶部，选中附近的复选框 **[!UICONTROL 标题]** 可在选择收藏集和清除列表之间进行切换。


1. 点按/单击 **[!UICONTROL 保存并关闭]** ，然后关闭确认对话框以完成该过程。
1. 要将新元数据附加到现有元数据，请选择 **[!UICONTROL 追加模式]**. 如果不选中此选项，则新元数据将替换字段中的现有元数据。点按／单击 **[!UICONTROL 提交]**。

   >[!NOTE]
   >
   >您为选定收藏集添加的元数据将覆盖这些收藏集之前的元数据。 使用 [!UICONTROL 追加模式] 向可包含多个值的字段中的现有元数据添加新值。 单值字段始终被覆盖。 您在 [!UICONTROL 标记] 字段，将附加到元数据中的现有标记列表。

自定义元数据 [!UICONTROL 属性] 页面（包括添加、修改、删除元数据属性）使用架构编辑器。

>[!TIP]
>
>批量编辑方法适用于收藏集中的可用资产。 对于跨文件夹提供的资产或符合常用条件的资产，可以在搜索这些资产后批量更新元数据。

## 搜索收藏集 {#searching-collections}

您可以从“收藏集”控制台中搜索收藏集。 在Omnisearch框中使用关键词搜索时， [!DNL Experience Manager] 资产会搜索收藏集名称、元数据以及添加到收藏集的标记。

如果您从顶级搜索收藏集，则搜索结果中只返回单个收藏集。 收藏集中的资产或文件夹将被排除。 在所有其他情况下（例如，在单个收藏集或文件夹层次结构中），都会返回所有相关的资产、文件夹和收藏集。

## 在收藏集中搜索 {#searching-within-collections}

在收藏集控制台中，点按/单击收藏集以将其打开。

在收藏集中，搜索仅限于您正在查看的收藏集中的资产（及其标记和元数据）。 在文件夹中搜索时，将返回当前文件夹中所有匹配的资产和子文件夹。 在收藏集中搜索时，只会返回与收藏集直接成员匹配的资产、文件夹和其他收藏集。

## 编辑收藏集设置 {#editing-collection-settings}

您可以编辑收藏集设置（如标题和描述），或向收藏集添加成员。

1. 选择收藏集，然后点按/单击 **[!UICONTROL 设置]** 图标。 或者，使用 **[!UICONTROL 设置]** 快速操作。
1. 在&#x200B;**[!UICONTROL 收藏集设置]**&#x200B;页面中修改收藏集设置。例如，按照 [添加收藏集](#creating-a-collection).

1. 要保存更改，请点按/单击 **[!UICONTROL 保存]**.

## 删除收藏集 {#deleting-a-collection}

1. 从收藏集控制台中，选择一个或多个收藏集，然后点按/单击工具栏中的删除图标。

1. 在对话框中，点按/单击 **[!UICONTROL 删除]** 以确认删除操作。

   >[!NOTE]
   >
   >您还可以通过 [删除保存的搜索](#deleting-saved-searches).

## 下载收藏集 {#downloading-a-collection}

下载收藏集时，会下载收藏集内整个资产层次结构，包括文件夹和子收藏集。

1. 从收藏集控制台中，选择要下载的一个或多个收藏集。
1. 在工具栏中，点按/单击下载图标。
1. 在 **[!UICONTROL 下载]** 对话框，点按/单击 **[!UICONTROL 下载]**. 如果要下载收藏集中资产的演绎版，请选择 **[!UICONTROL 演绎版]**. 选择 **[!UICONTROL 电子邮件]** 选项向集合所有者发送电子邮件通知。

   选择要下载的收藏集时，将下载该收藏集下的完整文件夹层次结构。 要在单个文件夹中包含您下载的每个收藏集（包括嵌套在父收藏集下的子收藏集中的资产），请选择 **[!UICONTROL 为每个资产创建单独的文件夹]**.

## 创建嵌套收藏集 {#creating-nested-collections}

您可以将一个收藏集添加到另一个收藏集，从而创建一个嵌套的收藏集。

1. 从收藏集控制台中，选择所需的收藏集或收藏集组，然后点按或单击 **[!UICONTROL 收藏]** 图标。

   ![chlimage_1-117](assets/chlimage_1-117.png)

1. 从 **[!UICONTROL 添加到收藏集]** 页面，选择要在其中添加收藏集的收藏集。

   >[!NOTE]
   >
   >默认情况下，最近更新的收藏集会在 **[!UICONTROL 添加到收藏集]** 页面。

1. 点按/单击 **[!UICONTROL 添加]**. 系统会显示一条消息，确认该收藏集已添加到 **[!UICONTROL 选择目标]** 页面。 关闭消息以完成该过程。

>[!NOTE]
>
>无法嵌套智能收藏集。 换言之，智能收藏集不能包含任何其他收藏集。

## 保存的搜索 {#saved-searches}

在“资产”用户界面中，您可以根据某些规则、搜索条件或自定义搜索彩块化来搜索或筛选资产。 如果将这些搜索另存为&#x200B;**[!UICONTROL 保存的搜索]**，则以后可以从“过滤器”面板的&#x200B;**[!UICONTROL 保存的搜索]**&#x200B;列表中访问它们。 创建保存的搜索也会创建智能收藏集。

![saved_searches_list](assets/saved_searches_list.png)

### 创建保存的搜索 {#creating-saved-searches}

创建智能收藏集时将创建保存的搜索。智能收藏集会自动添加到&#x200B;**[!UICONTROL 保存的搜索]**&#x200B;列表。收藏集的“保存的搜索”查询将保存在 `dam:query` crxde中的相对位置的属性 `/content/dam/collections/`. 对于可保存的搜索和列表中显示的已保存搜索，没有任何限制。

>[!NOTE]
>
>您可以像共享静态收藏集一样共享智能收藏集。

### 编辑保存的搜索 {#editing-saved-searches}

编辑保存的搜索与编辑智能收藏集相同。 有关详细信息，请参阅 [编辑智能收藏集](/help/assets/managing-collections-touch-ui.md#editing-a-smart-collection).

### 删除保存的搜索 {#deleting-saved-searches}

1. 在Assets用户界面中，点按/单击工具栏中的搜索图标。

   ![chlimage_1-118](assets/chlimage_1-118.png)

1. 在Omnisearch字段中使用光标，按Enter键。

1. 单击或点按GlobalNav图标以显示“过滤器”面板。

1. 从 **[!UICONTROL 保存的搜索]** 列表中，点按/单击要删除的智能收藏集旁边的删除图标。

   ![select_smart_collection-1](assets/select_smart_collection-1.png)

1. 在对话框中，点按/单击 **[!UICONTROL 删除]** 删除保存的搜索。

## 对集合执行工作流 {#running-a-workflow-on-a-collection}

您可以为收藏集中的资产运行工作流。 如果收藏集包含嵌套收藏集，则工作流还会在嵌套收藏集中的资产上运行。 但是，如果收藏集和嵌套收藏集包含重复的资产，则此类资产的工作流仅运行一次。

1. 从收藏集控制台中，选择要在其中运行工作流的收藏集。
1. 点按/单击GlobalNav图标，然后选择 **[!UICONTROL 时间轴]** 列表。
1. 在时间轴中，单击或点按底部的尖角图标，然后点按／单击开始工 **[!UICONTROL 作流]**。

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. 在&#x200B;**[!UICONTROL 启动工作流]**&#x200B;部分，从列表中选择工作流模型。例如，选择 **[!UICONTROL DAM 更新资产]**&#x200B;模型。
1. 输入工作流的标题，然后点按/单击 **[!UICONTROL 开始]**.
1. 在对话框中，点按/单击 **[!UICONTROL 继续]**. 该工作流会在收藏集中的所有资产上运行。

>[!MORELIKETHIS]
>
>* [配置Experience Manager Assets电子邮件通知](/help/sites-administering/notification.md#assetsconfig)
>* [为收藏集创建审核任务](bulk-approval.md)

