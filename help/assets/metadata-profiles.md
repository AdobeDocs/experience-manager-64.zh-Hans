---
title: 使用元数据配置文件将默认元数据应用到文件夹中的所有资产
description: 了解资产的元数据配置文件。 了解如何创建元数据配置文件并将其应用到文件夹资产。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: a7b0f1d6-7deb-4565-8c7f-27cad7cd6bf8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 16%

---

# 元数据配置文件 {#metadata-profiles}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过元数据配置文件，您可以将默认元数据应用到文件夹中的资产。 创建元数据配置文件并将其应用到文件夹。 您随后上传到文件夹的任何资产都会继承您在元数据配置文件中配置的默认元数据。

## 添加元数据配置文件 {#adding-a-metadata-profile}

1. 点按或单击 [!DNL Experience Manager] 徽标和导航到 **[!UICONTROL 工具> Assets >元数据配置文件]**，然后点按 **[!UICONTROL 创建]**.
1. 输入元数据配置文件的标题（例如示例元数据），然后单击 **[!UICONTROL 提交]**. 的 **[!UICONTROL 编辑表单]** ，则会显示元数据配置文件。

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. 单击某个组件，然后在 **[!UICONTROL 设置]** 选项卡。 例如，单击 **[!UICONTROL 描述]** 组件并编辑其属性。

   ![chlimage_1-481](assets/chlimage_1-481.png)

   编辑 **[!UICONTROL 描述]** 组件：

   * **[!UICONTROL 字段标签]**:元数据属性的显示名称。 仅供用户引用。
   * **[!UICONTROL 映射到属性]**:此属性的值提供资产节点在存储库中保存的相对路径/名称。 值应始终以开头 `./` 因为它表示路径位于资产的节点下。

   ![chlimage_1-482](assets/chlimage_1-482.png)

   为指定的值 **[!UICONTROL 映射到属性]** 将作为属性存储在资产的元数据节点下。 例如，如果您指定`/jcr:content/metadata/dc:desc` 作为的名称 **[!UICONTROL 映射到属性]**, [!DNL Experience Manager] 资产存储值 `dc:desc` ，位于资产的元数据节点。

   * **[!UICONTROL 默认值]**:使用此属性可为元数据组件添加默认值。 例如，如果您指定“我的描述”，则会将此值分配给属性 `dc:desc` ，位于资产的元数据节点。

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >向新元数据属性添加默认值(该属性在中尚不存在。 `/jcr:content/metadata` 节点)不会在资产上显示属性及其值 **[!UICONTROL 属性]** 页面。 在 [!UICONTROL 属性] ，请修改相应的架构表单。

1. （可选）向 **[!UICONTROL 编辑表单]** 从 **[!UICONTROL 构建表单]** ，并在 **[!UICONTROL 设置]** 选项卡。 “构建表单”选项卡中提供 **[!UICONTROL 以下属性]** :

| 组件 | 属性 |
|---|---|
| [!UICONTROL 章节标题] | 字段标签、 <br> 描述 |
| [!UICONTROL 单行文本] | 字段标签、 <br> 映射到属性， <br> 默认值 |
| [!UICONTROL 多值文本] | 字段标签、 <br> 映射到属性， <br> 默认值 |
| [!UICONTROL 数字] | 字段标签、 <br> 映射到属性， <br> 默认值 |
| [!UICONTROL 日期] | 字段标签、 <br> 映射到属性， <br> 默认值 |
| [!UICONTROL 标准标记] | 字段标签、 <br> 映射到属性， <br> 默认值、 <br> 描述 |

![chlimage_1-484](assets/chlimage_1-484.png)

1. 单击 **[!UICONTROL 完成]**. 元数据配置文件会添加到 **[!UICONTROL 元数据配置文件]** 页面。

   ![chlimage_1-485](assets/chlimage_1-485.png)

## 复制元数据配置文件 {#copying-a-metadata-profile}

1. 从 **[!UICONTROL 元数据配置文件]** 页面，请选择要创建其副本的配置文件。

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. 单击 **[!UICONTROL 复制]** 中。
1. 在 **[!UICONTROL 复制元数据配置文件]** 对话框中，输入用户档案新副本的标题。
1. 单击 **[!UICONTROL 复制]**. 配置文件的副本将显示在 **[!UICONTROL 元数据配置文件]** 页面。

   ![chlimage_1-487](assets/chlimage_1-487.png)

## 删除元数据配置文件 {#deleting-a-metadata-profile}

1. 从 **[!UICONTROL 元数据配置文件]** 页面，选择要删除的配置文件。

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. 单击 **[!UICONTROL 删除元数据配置文件]** 中。
1. 在对话框中，单击 **[!UICONTROL 删除]** 确认删除操作。 元数据配置文件将从列表中删除。

## 将元数据配置文件应用到文件夹 {#applying-a-metadata-profile-to-folders}

当您将元数据配置文件分配给文件夹后，该文件夹中的所有子文件夹都会自动继承父文件夹的配置文件。 这意味着您只能向文件夹分配一个元数据配置文件。 因此，请仔细考虑上传、存储、使用和存档资产所在的文件夹结构。

如果您为文件夹分配了不同的元数据配置文件，则新配置文件会覆盖之前的配置文件。 以前存在的文件夹资产将保持不变。 新配置文件会应用于稍后添加到文件夹的资产。

在用户界面中，如果文件夹分配了配置文件，则卡片名称中会显示配置文件的名称。

![chlimage_1-489](assets/chlimage_1-489.png)

您可以将元数据配置文件应用到特定文件夹或全局应用到所有资产。

### 将元数据配置文件应用到特定文件夹 {#applying-metadata-profiles-to-specific-folders}

您可以从&#x200B;**[!UICONTROL 工具]**&#x200B;菜单中将元数据配置文件应用到文件夹，或者如果您在文件夹中，也可以直接从&#x200B;**[!UICONTROL 属性]**&#x200B;中应用。本节将介绍如何通过这两种方式将元数据配置文件应用到文件夹。

如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### 从配置文件用户界面将元数据配置文件应用到文件夹 {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. 点按 [!DNL Experience Manager] 徽标和导航到 **[!UICONTROL 工具> Assets >元数据配置文件]**.
1. 选择要应用于一个或多个文件夹的元数据配置文件。

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. 点按 **[!UICONTROL 将元数据配置文件应用到文件夹]** ，然后选择一个或多个用于接收新上传资产的文件夹，然后点按 **[!UICONTROL 完成]**. 如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### 从“属性”将元数据配置文件应用到文件夹 {#applying-metadata-profiles-to-folders-from-properties}

1. 在左边栏中，点按 **[!UICONTROL 资产]** 然后，导航到要将元数据配置文件应用到的文件夹。
1. 在文件夹中，点按复选标记以将其选中，然后点按  **[!UICONTROL 属性]**.

1. 选择 **[!UICONTROL 元数据配置文件]** 选项卡，从下拉菜单中选择用户档案，然后单击 **[!UICONTROL 保存]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

### 全局应用元数据配置文件 {#applying-a-metadata-profile-globally}

除了将配置文件应用到文件夹之外，您还可以全局应用一个配置文件，以便上传到 [!DNL Experience Manager] 任何文件夹中的资产都会应用选定的配置文件。 要全局应用元数据配置文件，请执行以下步骤：

1. 执行下列操作之一：

   * 导航到 `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` ，然后应用相应的配置文件，然后点按或单击 **[!UICONTROL 保存]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * 导航到CRXDE Lite到以下节点： `/content/dam/jcr:content`. 添加属性 `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` 点按 **[!UICONTROL 全部保存]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## 从文件夹删除元数据配置文件 {#removing-a-metadata-profile-from-folders}

当您将元数据配置文件从文件夹删除后，该文件夹中的所有子文件夹都会自动删除从父文件夹继承的配置文件。 但是，对文件夹中已发生的文件的任何处理均将保持不变。

您可以从&#x200B;**[!UICONTROL 工具]**&#x200B;菜单中的文件夹删除元数据配置文件，或者如果您在文件夹中，也可以直接从&#x200B;**[!UICONTROL 属性]**&#x200B;中删除。本节将介绍如何通过这两种方式将元数据配置文件从文件夹中删除。

### 通过配置文件用户界面将元数据配置文件从文件夹删除 {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

要通过配置文件用户界面将元数据配置文件从文件夹删除，请执行以下步骤：

1. 点按 [!DNL Experience Manager] 徽标和导航到 **[!UICONTROL 工具> Assets >元数据配置文件]**.
1. 选择要从一个或多个文件夹删除的元数据配置文件。
1. 点按 **[!UICONTROL 从文件夹删除元数据配置文件]** 然后，选择一个或多个要从中删除配置文件的文件夹，然后点按 **[!UICONTROL 完成]**.

   您可以确认元数据配置文件不再应用于文件夹，因为该名称不再显示在文件夹名称的下方。

### 通过属性将元数据配置文件从文件夹删除 {#removing-metadata-profiles-from-folders-via-properties}

1. 点按 [!DNL Experience Manager] 徽标和导航 **[!UICONTROL 资产]** 然后，转到要从中删除元数据配置文件的文件夹。
1. 在文件夹中，点按复选标记以将其选中，然后点按 **[!UICONTROL 属性]**.
1. 选择 **[!UICONTROL 元数据配置文件]** 选项卡，然后选择 **[!UICONTROL 无]** 下拉菜单中。 点按 **[!UICONTROL 保存]**.

如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。
