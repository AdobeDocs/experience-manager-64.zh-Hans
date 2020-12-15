---
title: 元数据架构
description: '元数据模式定义属性页面的布局以及为资产显示的元数据属性。 了解如何创建自定义元数据模式、编辑元数据模式，以及如何将元数据模式应用于资产。  '
contentOwner: AG
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 23%

---


# 元数据架构 {#metadata-schemas}

在[!DNL Experience Manager Assets]中，元数据模式定义属性页面的布局以及为使用特定模式的资产显示的元数据属性。 元数据属性包括标题、描述、MIME类型、标记等。 您可以使用元数据模式Forms编辑器修改现有模式或添加自定义元数据模式。

要视图和编辑资产的属性页面，请执行以下步骤：

1. 单击或点按卡片视图中资产拼贴的快速操作中的&#x200B;**[!UICONTROL 视图属性]**。

   ![chlimage_1-170](assets/chlimage_1-170.png)

   或者，选择资产，然后单击或点按工具栏中的&#x200B;**[!UICONTROL 属性]**&#x200B;图标。

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. 您可以编辑可用选项卡下的各种可编辑元数据属性。 但是，您无法修改属性页面的[!UICONTROL 基本]选项卡中的资产[!UICONTROL 类型]。

   ![chlimage_1-172](assets/chlimage_1-172.png)

   要修改资产的MIME类型，请使用自定义元数据模式表单或修改现有表单。 有关详细信息，请参阅[编辑元数据模式Forms](metadata-schemas.md#editing-metadata-schema-forms)。 如果您修改某些MIME类型的元数据模式，则将修改当前MIME类型和所有资产子类型的资产的属性页面布局。 例如，修改`default/image`下的`jpeg`模式只会修改MIME类型为`IMAGE/JPEG`的资产的元数据布局（资产属性）。 但是，如果您编辑默认模式，则所做的更改将修改所有类型资产的元数据布局。

## 元数据架构表单 {#default-metadata-schema-forms}

要视图表单／模板的列表，请在[!DNL Experience Manager]界面中导航到&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 资产]** > **[!UICONTROL 元数据模式]**。

[!DNL Experience Manager] 提供以下元数据模式表单模板：

| 模板 |  | 描述 |
|---|---|---|
| [!UICONTROL 默认] |  | 资产的基本元数据模式表单。 |
|  | 以下子表单继承[!UICONTROL default]表单的属性： |  |
|  | <ul><li> [!UICONTROL dm_video]</li></ul> | 模式表单，用于Dynamic Media视频。 |
|  | <ul><li> [!UICONTROL 图像]</li></ul> | 模式表单，用于MIME类型为“image”（例如image/jpeg、image/png等）的资产。 <br> 图像  表单具有以下子表单模板： <ul><li> [!UICONTROL jpeg]:模式子类型为jpeg的资产 [!UICONTROL 表单]。</li> <li>[!UICONTROL tiff]:模式子类型为tiff的资产的 [!UICONTROL 表单]。</li></ul> |
|  | <ul><li> [!UICONTROL 应用]</li></ul> | 模式表单，用于MIME类型为“application”（例如application/pdf、application/zip等）的资产。 <br>[!UICONTROL pdf]:模式子类型为pdf的资产的表单。 |
|  | <ul><li>[!UICONTROL 视频]</li></ul> | 模式表单，用于MIME类型为“”（如video/avi、video/mp4等）的资产。 |
| [!UICONTROL 收藏集] |  | 集合的模式表单。 |
| [!UICONTROL contentfragment] |  | 模式内容片段表单。 |
| [!UICONTROL 表单] |  | 此模式形式与[Adobe Experience Manager Forms](/help/forms/home.md)相关。 |

>[!NOTE]
>
>要视图模式表单的子表单，请单击／点按模式表单名称。

## 添加元数据模式表单{#adding-a-metadata-schema-form}

1. 要向列表添加自定义模板，请单击工具栏中的&#x200B;**[!UICONTROL 创建]**。

   >[!NOTE]
   >
   >未编辑的模板前会显示一个锁图标。 如果自定义任何模板，则模板前面的锁图标会消失。

1. 在对话框中，输入模式表单的标题，然后单击&#x200B;**[!UICONTROL 创建]**&#x200B;以完成表单创建过程。

   ![chlimage_1-174](assets/chlimage_1-174.png)

## 编辑元数据模式表单{#editing-metadata-schema-forms}

可以编辑新添加的或现有的元数据架构表单。元数据模式表包括：

* 选项卡
* 选项卡中的表单项目

您可以将这些表单项映射到／配置到CRX存储库中元数据节点内的字段。

可以向元数据架构表单中添加新的选项卡或表单项目。从父级派生的选项卡和表单项目处于锁定状态。 无法从子级别更改它们。

1. 在&#x200B;**[!UICONTROL 模式Forms]**&#x200B;页面中，选中表单前面的复选框，然后单击工具栏上的&#x200B;**[!UICONTROL 编辑]**。

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. 在元数 **[!UICONTROL 据架构编辑器页中]** ，通过将“构建表单”选项卡中的组件类型列表中的一个或多个组件拖至“基本”选项卡，自定义资产的属性页 ******** 。

   ![chlimage_1-176](assets/chlimage_1-176.png)

1. 要配置组件，请选择它并在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡中修改其属性。

### “构建表单”选项卡内的组件{#components-within-the-build-form-tab}

**[!UICONTROL 构建表单]**&#x200B;选项卡列表您在模式表单中使用的表单项。 **[!UICONTROL 设置]**&#x200B;选项卡提供您在&#x200B;**[!UICONTROL 构建表单]**&#x200B;选项卡中选择的每个项的属性。 下表列表了&#x200B;**[!UICONTROL 构建表单]**&#x200B;选项卡中可用的表单项：

| 组件名称 | 描述 |
|---|---|
| [!UICONTROL 章节标题] | 添加一系列常用组件的章节标题。 |
| [!UICONTROL 单行文本] | 添加单行文本属性。它将作为字符串存储。 |
| [!UICONTROL 多值文本] | 添加多值文本属性。它将作为字符串数组存储。 |
| [!UICONTROL 数字] | 添加数字组件。 |
| [!UICONTROL 日期] | 添加日期组件。 |
| [!UICONTROL 下拉列表] | 添加下拉列表。 |
| [!UICONTROL 标准标记] | 添加标记。 |
| [!UICONTROL 智能标记] | 通过自动添加元数据标记来增强搜索功能。 |
| [!UICONTROL 隐藏字段] | 添加隐藏字段。在保存资产时，该字段将作为 POST 参数发送。 |
| [!UICONTROL 资产引用对象] | 添加此组件可查看该资产所引用的其他资产的列表。 |
| [!UICONTROL 资产引用] | 添加此组件可显示引用该资产的其他资产的列表。 |
| [!UICONTROL 产品引用] | 添加此组件可显示与该资产关联的产品的列表。 |
| [!UICONTROL 资产评级] | 添加以显示资产评级选项。 |
| [!UICONTROL 上下文元数据] | 添加以控制资产属性页面中其他元数据选项卡的显示。 |

### 编辑元数据组件{#editing-the-metadata-component}

要编辑表单上元数据组件的属性，请单击该组件，并在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡中编辑以下所有属性或属性的子集。

**字段标签**:资产的属性页面上显示的元数据属性的名称。

**映射到属性**:此属性指定资产节点在CRX存储库中保存的相对路径／名称。它以`./`开始，因为它表示路径位于资产的节点下。

以下是此属性的有效值：

* `./jcr:content/metadata/dc:title`：将该值作为属性 `dc:title` 存储在资产的元数据节点中。

* `./jcr:created`:在资产的节点显示JCR属性。如果您在视图属性上配置这些属性，我们建议您将这些属性标记为“禁用编辑”，因为它们是受保护属性。否则，在保存资产属性时，错误[!UICONTROL 资产无法修改]结果。

要确保在元数据模式表单中正确显示组件，属性路径不应包含任何空格。

**占位符**:使用此属性可指定与元数据属性相关的占位符文本。

**必需**:使用此属性可在属性页面上将元数据属性标记为必需。

**禁用编辑**:使用此属性可使元数据属性在属性页面上不可编辑。

**在只读模式下显示空字段**:标记此属性可在属性页面上显示元数据属性，即使其没有值也是如此。默认情况下，当元数据属性没有值时，不会在属性页面中列出该属性。

**显示订购列表**:使用此属性可显示选项的有序列表

**选择**:使用此属性指定列表中的选项

**描述**：使用此属性可添加对元数据组件的简短描述。

**类**:属性关联的对象类。

**删除** 图标单击此图标可从模式表单中删除组件。

>[!NOTE]
>
>隐藏字段组件不包含这些属性。 而是包括属性，如名称、值、字段标签和说明。 无论何时保存资产，都会将“隐藏字段”组件的值作为 POST 参数进行发送。该组件的值不会作为资产的元数据进行保存。

如果选择&#x200B;**[!UICONTROL 必需]**&#x200B;选项，则可以搜索缺少必需元数据的资产。从&#x200B;**[!UICONTROL 过滤器]**&#x200B;面板中，展开&#x200B;**[!UICONTROL 元数据验证]**&#x200B;谓词，然后选择&#x200B;**[!UICONTROL 无效]**&#x200B;选项。搜索结果中显示的资产缺少您通过架构表单配置的必需元数据。

![chlimage_1-178](assets/chlimage_1-178.png)

如果您将上下文元数据组件添加到任何模式表单的任何选项卡，该组件将作为列表显示在应用特定模式的资产的属性页面中。 该列表包括除您应用了上下文元数据组件的选项卡外的所有其他选项卡。 目前，此功能提供基本功能，用于根据上下文控制元数据的显示。

![chlimage_1-179](assets/chlimage_1-179.png)

要在属性页面中除应用上下文元数据组件的选项卡外，还包括任何选项卡，请从列表中选择该选项卡。 该选项卡会添加到属性页面。

![chlimage_1-180](assets/chlimage_1-180.png)

### 在JSON文件{#specifying-properties-in-json-file}中指定属性

您还可以通过指定相应的键值对在 JSON 文件中定义选项，而不是为&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡中的选项指定属性。在 **[!UICONTROL JSON 路径]**&#x200B;字段中指定 JSON 文件的路径。

### 在模式表单{#adding-deleting-a-tab-in-the-schema-form}中添加或删除选项卡

通过架构编辑器，可以添加或删除选项卡。默认架构表单包括&#x200B;**[!UICONTROL 基本]**、**[!UICONTROL 高级]**、**[!UICONTROL IPTC]** 和 **[!UICONTROL IPTC 扩展]**&#x200B;选项卡（默认情况下）。

![chlimage_1-181](assets/chlimage_1-181.png)

单击`+`在模式表单上添加新选项卡。默认情况下，新选项卡的名称为`Unnamed-1`。可以从&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡中修改该名称。 单击`X`以删除选项卡。

![chlimage_1-182](assets/chlimage_1-182.png)

## 删除元数据模式表单{#deleting-metadata-schema-forms}

AEM 仅允许您删除自定义架构表单。您无法删除默认的架构表单/模板。但是，您可以删除对这些表单所做的任何自定义更改。

要删除某个表单，请选择该表单，然后单击&#x200B;**[!UICONTROL 删除]**&#x200B;图标。

>[!NOTE]
>
>删除对默认表单的自定义更改后，元数据模式界面上会重新显示锁图标，以指示表单已恢复为默认状态。

>[!NOTE]
>
>您无法删除AEM Assets的现成元数据模式表单。

## 模式MIME类型{#schema-forms-for-mime-types}的表单

AEM Assets为各种开箱即用的MIME类型提供默认表单。 但是，您可以为各种MIME类型的资产添加自定义表单。

### 为MIME类型{#adding-new-forms-for-mime-types}添加新表单

在相应的表单类型下创建新表单。例如，要为`image/png`子类型添加新模板，请在`image`表单下创建表单。 架构表单的标题是子类型名称。在这种情况下，标题为`png`。

### 对各种MIME类型{#using-an-existing-schema-template-for-various-mime-types}使用现有模式模板

您可以为不同的 MIME 类型使用现有模板。例如，对MIME类型为`image/png`的资产使用`image/jpeg`表单。

在这种情况下，请在CRX存储库中的`/etc/dam/metadataeditor/mimetypemappings`处创建新节点。 指定节点的名称并定义以下属性：

| 名称 | 描述 | 类型 | 值 |
|---|---|---|---|
| `exposedmimetype` | 要映射的现有表单的名称 | `String` | `image/jpeg` |
| `mimetypes` | 使用`exposedmimetype`属性中定义的表单的MIME类型列表 | `String` | `image/png` |

AEM Assets 映射以下 MIME 类型和架构表单：

| 架构表单 | MIME类型 |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi、video/msvideo、video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## 授予对元数据模式的访问权限{#granting-access-to-metadata-schemas}

元数据模式功能仅对管理员可用。 但是，管理员可以通过在`/conf`文件夹中提供&#x200B;**[!UICONTROL 创建]**、**[!UICONTROL 修改]**&#x200B;和&#x200B;**[!UICONTROL 删除]**&#x200B;权限，为非管理员用户提供访问权限。

## 应用特定于文件夹的元数据{#applying-folder-specific-metadata}

AEM Assets允许您定义元数据模式的变体，并将其应用到特定文件夹。

例如，您可以定义默认元数据模式的变体并将其应用到文件夹。 应用修改后的模式时，该模式将覆盖应用于文件夹内资产的原始默认元数据区域。

只有上传到应用此模式的文件夹的资产才会与变体元数据模式中定义的修改后的元数据相符。

应用原始模式的其他文件夹中的资产会继续与原始模式中定义的元数据保持一致。

资产的元数据继承基于应用于层次结构中第一级文件夹的模式。 换言之，如果文件夹不包含子文件夹，则文件夹内的资产会继承应用于该文件夹的模式的元数据。

如果文件夹有子文件夹，则子文件夹内的资产会继承子文件夹级别所应用模式的元数据(如果子文件夹级别应用了其他模式)。 但是，如果子文件夹级别未应用模式或同一模式，则子文件夹资产将继承父文件夹级别所应用模式的元数据。

1. 单击 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 元数据架构]**。此时会显示&#x200B;**[!UICONTROL 元数据架构表单]**&#x200B;页面。
1. 选中表单前面的复选框，例如默认元数据表单，然后单击或点按&#x200B;**[!UICONTROL 复制]**&#x200B;图标，并将其另存为自定义表单。 指定表单的自定义名称，例如`my_default`。 或者，您也可以创建自定义表单。

   ![chlimage_1-184](assets/chlimage_1-184.png)

1. 在&#x200B;**[!UICONTROL 元数据模式Forms]**&#x200B;页面中，选择`my_default`表单，然后单击&#x200B;**[!UICONTROL 编辑]**。

1. 在&#x200B;**[!UICONTROL 元数据模式编辑器]**&#x200B;页面中，向模式表单添加一个文本字段。 例如，添加标签为&#x200B;**[!UICONTROL 类别]**&#x200B;的字段。

   ![chlimage_1-186](assets/chlimage_1-186.png)

1. 单击&#x200B;**[!UICONTROL 保存]**。修改后的表单列在&#x200B;**[!UICONTROL 元数据模式Forms]**&#x200B;页面中。
1. 单击／点按工具栏中的&#x200B;**[!UICONTROL 应用到文件夹]**，将自定义元数据应用到文件夹。

   ![chlimage_1-187](assets/chlimage_1-187.png)

1. 选择要应用已修改模式的文件夹，然后单击／点按&#x200B;**[!UICONTROL 应用]**。

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. 如果该文件夹应用了其他元数据模式，则会显示一条消息，警告您将覆盖现有元数据模式。 单击&#x200B;**[!UICONTROL 覆盖]**。
1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;以关闭成功消息。
1. 导览至应用已修改元数据模式的文件夹。

## 定义必需元数据{#defining-mandatory-metadata}

您可以在文件夹级别定义必填字段，这将强制执行于上传到该文件夹的资产。 如果您上传的资产上传之前定义的必填字段缺少元数据，则卡视图的资产上会显示缺少元数据的可视指示。

>[!NOTE]
>
>可以根据其他字段的值将元数据字段定义为强制字段。 在“卡”视图中，AEM不显示有关此类强制元数据字段缺失元数据的警告消息。

1. 单击 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 元数据架构]**。此时会显示&#x200B;**[!UICONTROL 元数据架构表单]**&#x200B;页面。
1. 将默认元数据表单另存为自定义表单。 例如，将其另存为`my_default`。

   ![chlimage_1-109](assets/chlimage_1-189.png)

1. 编辑自定义表单。 添加必填字段。 例如，添加&#x200B;**类别**&#x200B;字段，并将该字段设为必填。

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. 单击&#x200B;**[!UICONTROL 保存]**。修改后的表单列在&#x200B;**[!UICONTROL 元数据模式Forms]**&#x200B;页面中。 要将自定义元数据应用到文件夹，请选择表单，然后单击／点按工具栏中的&#x200B;**[!UICONTROL 应用到文件夹]**。

1. 导航到文件夹，然后上传某些资产，其中缺少您添加到自定义表单的必填字段的元数据。 资产的卡片视图会显示必填字段中缺少的元数据的消息。

   ![chlimage_1-112](assets/chlimage_1-192.png)

1. （可选）访问`http://[server]:[port]/system/console/components/`。 配置并启用默认禁用的`com.day.cq.dam.core.impl.MissingMetadataNotificationJob`组件。 设置AEM在资产上检查元数据有效性的频率。
此配置将属性`hasValidMetadata`添加到资产的jcr:content。 使用此属性，AEM可以在搜索中筛选结果。

>[!NOTE]
>
>如果资产是在计划检查后添加的，则直到下一个计划检查后，资产才会被标记为`hasValidMetadata`。 资产不会显示在中间搜索结果中。

>[!CAUTION]
>
>元数据验证检查会占用大量资源，并且可能会影响系统性能。 计划相应的检查。 如果AEM部署存在性能问题，请尝试禁用此作业。
