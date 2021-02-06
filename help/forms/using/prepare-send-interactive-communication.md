---
title: 使用代理UI准备和发送交互式通信
seo-title: 使用代理UI准备和发送交互式通信
description: '代理UI允许代理准备交互式通信并将其发送到后处理。 代理根据允许进行所需的修改，并将交互通信提交到后期流程，如电子邮件或打印。 '
seo-description: 使用代理UI准备和发送交互式通信
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
translation-type: tm+mt
source-git-commit: 835618e8e0d01905ad7b476b0172dfecec41cf9d
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 0%

---


# 使用代理UI {#prepare-and-send-interactive-communication-using-the-agent-ui}准备和发送交互式通信

代理UI允许代理准备交互式通信并将其发送到后处理。 代理根据允许进行所需的修改，并将交互通信提交到后期流程，如电子邮件或打印。

## 概述 {#overview}

创建交互式通信后，代理可以在代理UI中打开交互式通信，并通过输入数据和管理内容和附件准备收件人特定的副本。 最后，代理可以将交互通信提交到后处理。

在使用代理UI准备交互式通信时，代理在将交互式通信提交到发布流程之前，在代理UI中管理交互式通信的以下方面：

* **数据**:代理UI的“数据”选项卡显示交互通信中任何可代理编辑的变量和已解锁的表单数据模型属性。这些变量／属性是在编辑或创建包含在交互通信中的文档片段时创建的。 “数据”选项卡还包括在XDP/打印渠道模板中构建的任何字段。 仅当代理可编辑交互通信中的任何变量、表单数据模型属性或字段时，才会显示“数据”选项卡。
* **内容**:在“内容”选项卡中，代理管理交互式通信中的内容，如文档片段和内容变量。在这些文档片段的属性中创建交互通信时，代理可以根据允许的方式在文档片段中进行更改。 如果允许，代理还可以重新排序、添加／删除文档片段和添加分页符。
* **附件**:仅当交互通信具有任何附件或代理具有库访问权限时，“附件”选项卡才会显示在代理UI中。座席可以更改或编辑附件，也可以不允许。

## 使用代理UI {#prepare-interactive-communication-using-the-agent-ui}准备交互式通信

1. 选择&#x200B;**[!UICONTROL Forms]** > **[!UICONTROL Forms和文档]**。
1. 选择相应的交互式通信，然后点按&#x200B;**[!UICONTROL 打开代理UI]**。

   >[!NOTE]
   >
   >代理UI仅在选定的交互通信具有打印渠道时有效。

   ![openentiui](assets/openagentiui.png)

   根据交互通信的内容和属性，代理UI会显示以下三个选项卡：数据、内容和附件。

   ![基因](assets/agentuitabs.png)

   继续输入数据、管理内容和管理附件。

### 输入数据 {#enter-data}

1. 根据需要，在“数据”选项卡中输入变量、表单数据模型属性和打印模板(XDP)字段的数据。 填写标有星号(&amp;ast;)的所有必填字段，以启用&#x200B;**Submit**&#x200B;按钮。

   点按“交互式通信”预览中的数据字段值，以在“数据”选项卡中高亮显示相应的数据字段，反之亦然。

### 管理内容 {#manage-content}

在“内容”选项卡中，管理交互式通信中的内容，如文档片段和内容变量。

1. 选择&#x200B;**[!UICONTROL 内容]**。 此时将显示交互式通信的内容选项卡。

   ![agentuicontentab](assets/agentuicontenttab.png)

1. 根据需要，在“内容”选项卡中编辑文档片段。 要将焦点置于内容层次结构中的相关片段，您可以点按交互通信预览中的相关行或段落，或直接点按内容层次结构中的片段。

   例如，在下图的文档中选择了行为“立即在线付款……”的预览片段，在“内容”选项卡中选择了同一文档片段。

   ![contentmodulefocus](assets/contentmodulefocus.png)

   在“内容”或“数据”选项卡中，通过点按预览左上角的“高亮显示内容中的选定模块”(![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png))，可以禁用或启用在预览中点按／选择相关文本、段落或数据字段时转到文档片段的功能。

   创建交互通信时代理允许编辑的片段具有编辑选定内容(![iconeditedselectedcontent](assets/iconeditselectedcontent.png))图标。 点按编辑选定内容图标以在编辑模式下启动片段并在其中进行更改。 使用以下选项设置文本格式和管理文本：

   * [格式选项](#formattingtext)

      * [从其他应用程序复制粘贴格式文本](#pasteformattedtext)
      * [高亮文本的部分](#highlightemphasize)
   * [特殊字符](#specialcharacters)
   * [键盘快捷键](/help/forms/using/keyboard-shortcuts.md)

   有关代理用户界面中各种文档片段可用的操作的详细信息，请参阅代理用户界面中的[操作和可用信息](#actionsagentui)。

1. 要将分页符添加到交互通信的打印输出，请将光标放在要插入分页符的位置，然后选择“分页前”或“分页后”（![分页前后](assets/pagebreakbeforeafter.png)）。

   在交互通信中插入显式分页符占位符。 要视图显式分页符如何影响交互式通信，请参阅打印预览。

   ![excitapagebreak](assets/explicitpagebreak.png)

   继续管理交互式通信的附件。

### 管理附件{#manage-attachments}

1. 选择&#x200B;**[!UICONTROL 附件]**。 代理UI在创建交互式通信时按设置显示可用的附件。

   通过点按视图图标，您可以选择不随交互通信一起提交附件，也可以点按附件中的叉号，从交互通信中删除该附件（如果允许代理删除或隐藏附件）。 对于在创建交互式通信时指定为必需的附件，将禁用“视图”和“删除”图标。

   ![附件AGENTUI](assets/attachmentsagentui.png)

1. 点按库访问（![库访问](assets/libraryaccess.png)）图标以访问内容库以将DAM资产作为附件插入。

   >[!NOTE]
   >
   >仅当在创建交互式通信时启用了库访问(在打印渠道的文档容器属性中),“库访问”图标才可用。

1. 如果在创建交互式通信时未锁定附件的顺序，您可以通过选择附件并点按向下和向上箭头对附件重新排序。
1. 使用Web预览和打印预览来查看这两个输出是否符合您的要求。

   如果您认为预览令人满意，请点按&#x200B;**[!UICONTROL Submit]**&#x200B;以提交／发送交互通信至后期进程。 或者，要进行更改，请退出预览以返回进行更改。

## 格式化文本{#formattingtext}

在代理UI中编辑文本片段时，工具栏会根据您选择进行的编辑类型而发生更改：字体、段落或列表:

![Typeofformatting](assets/typeofformattingtoolbar.png) ![工具栏字体工具栏](do-not-localize/fonttoolbar.png)

字体工具栏

![段落工具栏](do-not-localize/paragraphtoolbar.png)

段落工具栏

![列表工具栏](do-not-localize/listtoolbar.png)

列表工具栏

### 突出显示／突出显示部分文本{#highlightemphasize}

要高亮显示可编辑片段中的部分文本，请选择文本并点按高亮显示颜色。

![highlighttextagentui](assets/highlighttextagentui.png)

### 粘贴格式化文本{#pasteformattedtext}

![已过文本](assets/pastedtext.png)

### 在文本{#specialcharacters}中插入特殊字符

代理UI内置了对210个特殊字符的支持。 管理员可以通过自定义](/help/forms/using/custom-special-characters.md)添加对更多／自定义特殊字符的支持。[

#### 附件投放{#attachmentdelivery}

* 当使用服务器端API将交互式通信渲染为交互式或非交互式PDF时，渲染的PDF将包含附件作为PDF附件。
* 当与交互式通信关联的后期进程作为“使用代理UI提交”的一部分加载时，附件将作为列表&lt;com.adobe.idp.文档> inAttachmentDocs参数传递。
* 投放机制工作流（如电子邮件和打印）还提供附件以及PDF版的交互式通信。

## 代理用户界面{#actionsagentui}中可用的操作和信息

### 文档片段{#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **向上／向下箭头**:在交互式通信中向上或向下移动文档片段的箭头。
* **删除**:如果允许，请从交互通信中删除文档片段。
* **分页前** (适用于目标区域的子片段):在文档片段之前插入分页符。
* **缩进**:增加或减少文档片段缩进。
* **分页后** (适用于目标区域的子片段):在文档片段后插入分页符。

![docfragoptions](assets/docfragoptions.png)

* 编辑（仅限文本片段）:打开富文本编辑器以编辑文本文档片段。 有关详细信息，请参阅[格式化文本](#formattingtext)。

* 选择（眼睛图标）:包括\排除交互通信中的文档片段。
* 未填充值（信息）:指示文档片段中未填充的变量数。

### 列表文档片段{#list-document-fragments}

![列表选项](assets/listoptions.png)

* 插入空行：插入新的空行。
* 选择（眼睛图标）:包括\排除交互通信中的文档片段。
* 跳过项目符号／编号：启用此选项，可跳过列表文档片段中的项目符号／编号。
* 未填充值（信息）:指示文档片段中未填充的变量数。

