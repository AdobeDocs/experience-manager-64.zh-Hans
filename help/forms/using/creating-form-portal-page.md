---
title: 创建表单门户页面
seo-title: 创建表单门户页面
description: Forms门户为Web开发人员提供组件，用于在使用Adobe Experience Manager(AEM)创作的网站上创建和自定义表单门户。
seo-description: Forms门户为Web开发人员提供组件，用于在使用Adobe Experience Manager(AEM)创作的网站上创建和自定义表单门户。
uuid: 328f3342-d6ca-4413-9f1d-1a550df74bde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7387dfe8-0029-4ad0-b319-fc519928318b
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 1%

---


# 创建表单门户页面 {#creating-a-forms-portal-page}

Forms门户组件为Web开发人员提供组件，用于在使用Adobe Experience Manager(AEM)创作的网站上创建和自定义表单门户。 有关表单门户的快速概述，请参 [阅在门户上发布表单的简介](/help/forms/using/introduction-publishing-forms.md)。

## 前提条件 {#prerequisites}

Forms门户组件默认不可用。 确保按照启用表单门户组件中的说明启用以 [下表单门户组件类别](/help/forms/using/enabling-forms-portal-components.md)。

**文档服务** 包括搜索和制表人、链接以及草稿和提交组件。

**文档服务谓词** ，包括日期谓词、全文谓词、属性谓词和标记谓词组件。 这些组件用于在搜索和制表人组件中配置搜索。

在AEM站点页面上启用这些组件后，这些组件类别便可在组件浏览器中使用。

![AEM Forms门户组件在组件浏览器中](assets/component-categories.png)**图：** *Forms门户组件类别*

## 搜索和制表人组件 {#search-amp-lister-component}

“文档服务”组件类别下提供的“搜索和制表人”组件用于在页面上列表表单以及在列出的表单上执行搜索。 该组件包括两个窗格：

* 列表窗格中列出表单。
* 添加搜索功能的搜索窗格。

您可以将“搜索和制表人”组件从组件浏览器中的文档服务组件类别拖放到页面上。 添加组件后，其外观与以下内容类似。

![页面中的搜索和制表人组件](assets/fp-grid-viw.png)**图：** *使用网格布局在页面中搜索和制表人组件*

### 列表窗格 {#list-pane}

列表窗格是列出表单的区域。 “搜索和制表人”组件提供各种配置选项，可用于控制表单在列表窗格中的显示。

要配置列表窗格，请点按搜索和制表人组件，然后点 ![按settings_icon](assets/settings_icon.png)。 此时将 **[!UICONTROL 打开编辑]** “组件”对话框。

![列表窗格在编辑模式](assets/edit-list.png)**下图：** *列表窗格在编辑模式下*

“编 **[!UICONTROL 辑]** ”对话框包括若干选项卡，这些选项卡提供下表中所述的配置选项。 完成 **[!UICONTROL 后]** ，点按确定以保存配置。

<table> 
 <tbody> 
  <tr> 
   <th>选项卡·</th> 
   <th>配置</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>资产文件夹</strong></span></td> 
   <td>添加项目</td> 
   <td>配置使用AEM FormsUI上传资产的文件夹。 默认情况下，它会列表所有上传的资产。 有关AEM FormsUI的详细信息，请参 <a href="/help/forms/using/introduction-managing-forms.md" target="_blank">阅表单管理简介</a>。</td> 
  </tr> 
  <tr> 
   <td><p><span class="uicontrol"><strong>显示器</strong></span></p> </td> 
   <td>标题文本</td> 
   <td>搜索和制表人组件的标题。 默认标题为 <strong>Forms门户。</strong></td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>布局模板</td> 
   <td>资产的布局。 </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>禁用高级搜索</td> 
   <td>启用后，将隐藏高级搜索图标。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>禁用文本搜索</td> 
   <td>启用后，隐藏全文搜索栏。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>结果</strong></span></td> 
   <td>每页结果数</td> 
   <td>配置要在页面上显示的最大表单数。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>结果文本</td> 
   <td><p>配置结果文本(例如，601个结果中的1- <strong>12</strong>)。 The default value is <strong>Results</strong>.</p> <p>例如，如果在此字 <strong>段 </strong>中指定了Forms，并且共有601个表单，则结果文本将更改为1-12个，共601个 <strong>Forms。</strong></p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>页面文本</td> 
   <td><p>配置页面文本(例如，第1 <strong>页， </strong>共51页)。 The default value is <strong>Page</strong>.</p> <p>例如，如果在此字段 <strong>中指 </strong>定应用程序表单，并且有51页，则页面文本将更改为应用程 <strong>序表 </strong>单1（共51页）。</p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Of 文本</td> 
   <td><p>将单词 <strong>替换</strong> 为指定的文本(第1页， <strong>共51 </strong>页)。 The default value is <strong>of</strong>.</p> <p>例如，如果在此字 <strong>段中 </strong>指定“退出”，则文本将变为第1页， <strong>共51 </strong>页。</p> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>表单链接</strong></span></td> 
   <td>呈现类型</td> 
   <td>根据指定的渲染类型控制表单列表。 可用选项为PDF和HTML。 例如，如果仅选择HTML作为渲染类型，则会过滤掉PDF forms。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>HTML用户档案</td> 
   <td>配置用于渲染的HTML用户档案。 所有可用用户档案都列在下拉列表中。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>提交URL</td> 
   <td><p>配置提交表单数据的Servlet。</p> <p><strong>注意：</strong> <em>表单的提交URL可以在多个位置指定，其优先顺序如下：</em></p> 
    <ol> 
     <li><em>嵌入在表单中（在“提交”按钮中）的提交URL具有最高优先级。</em></li> 
     <li><em>在AEM FormsUI中提及的提交URL具有第二高优先级。</em></li> 
     <li><em>表单门户中提及的提交URL的优先级最低。</em></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>HTML渲染操作工具提示</td> 
   <td>配置工具提示的文本，将指针悬停在上方时 <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> 显示该文本（HTML5图标）。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>PDF渲染操作工具提示</td> 
   <td>配置工具提示的文本，将指针悬停在上方时 <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> 显示该文本（PDF图标）。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>样式</strong></span></td> 
   <td>样式类型</td> 
   <td>允许您指定“ <strong>无样式”、“默认样式</strong>”或“ <strong>自定义样 </strong>式”来列出表单。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>自定义样式路径</td> 
   <td>如果选择“自定义”作为样式类型，则浏览以指定自定义CSS的路径，否则选择“默认”。</td> 
  </tr> 
 </tbody> 
</table>

### 搜索窗格 {#search-pane}

在“搜索”窗格中，您可以从AEM Sidekick中的“文档服务”谓词类别添加日期谓词、全文谓词、属性谓词和标记谓词组件。 这些组件实现了搜索功能，供用户在列出的表单上执行搜索。

**提示：** *您可以根据预设条件控制在表单门户上显示的表单的列表，并隐藏最终用户的搜索功能。 要控制表单的列表，请使用谓词组件应用搜索过滤器。 您还可以指定默认筛选器值，并从编辑组件对话框的显示选项卡中禁用搜索。*

![“搜索”面板中包含日期、全文、属性和标记谓词](assets/search-with-predicates.png)**图：** *带有日期、全文、属性和标记谓词的搜索面板*

#### 日期谓词 {#date-predicate}

添加日期谓词组件后，可以搜索在指定持续时间内修改的列出表单。

要配置日期谓词组件，请执行以下操作：

1. 点按组件，然后点 ![按settings_icon](assets/settings_icon.png)。 此时将打开编辑对话框。
1. 指定以下内容：

   * **[!UICONTROL 类型：]** 唯一可用的选项是“上次 **[!UICONTROL 修改日期”]**。
   * **[!UICONTROL 文本：]** 日期谓词组件的标签或题注。 默认值为“上次修 **[!UICONTROL 改日期”]**。
   * **[!UICONTROL 开始日期标签：]** 开始日期字段的标签或标题。
   * **[!UICONTROL 结束日期标签：]** 结束日期字段的标签或题注。
   * **[!UICONTROL 隐藏：]** 要强制使用默认日期筛选器来列表表单。

1. 点按 **[!UICONTROL 确定]**。

#### 全文谓词 {#full-text-predicate}

全文谓词组件可对表单数据（如名称和说明）实现全文搜索。 用户可以搜索任何文本字符串以返回在其名称或描述中包含文本的表单。

要配置全文谓词组件，请执行以下操作：

1. 点按组件，然后点 ![按settings_icon](assets/settings_icon.png)。 此时将打开编辑对话框。
1. 在“主标题”字 **[!UICONTROL 段中指定]** 标题。
1. 点按 **[!UICONTROL 确定]**。

#### 属性谓词 {#properties-predicate}

属性谓词组件实现根据表单属性（如标题、作者和说明）搜索表单。

要配置属性谓词组件，请执行以下操作：

1. 点按组件，然后点 ![按settings_icon](assets/settings_icon.png)。 The **[!UICONTROL Edit dialog]** opens.
1. 在“常 **[!UICONTROL 规]** ”选项卡中，指定搜索标签。 The default value is **[!UICONTROL Properties]**.

1. 在“选 **[!UICONTROL 项]** ”选项卡中，点 **[!UICONTROL 按添加项]**。
1. 从下拉列表中选择一个属性，并在下拉列表下的字段中为它指定搜索标签。
1. 重复第4步以添加更多属性。 您还可以根据指定的条件指定默认筛选器值来列表表单，并隐藏属性以供最终用户搜索。 为属性选中“隐藏”复选框，然后指定默认筛选器值。

   例如，如果要显示标题中包含“Travel”的表单，请选择“标题”属性旁的“隐藏”。 此外，指定“默认筛选值中的行程”文本框。

1. 点按 **[!UICONTROL 确定]**。

#### 标记谓词 {#tags-predicate}

标记谓词组件根据在Forms管理器中定义的标记实现表单搜索。

要配置标记谓词组件，请执行以下操作：

1. 点按组件，然后点 ![按settings_icon](assets/settings_icon.png)。 The **[!UICONTROL Edit dialog]** opens.
1. 点按“标记”字段旁边的向下箭头按钮。
1. 选择适当的标记。
1. 点按 **[!UICONTROL 确定]**。

所选标记会与选中的复选框一起显示在“搜索”窗格中。 用户现在可以根据标记缩小搜索范围。

## 列表页面上的表单 {#list-forms-on-a-page-br}

要列表页面上的表单，请将“搜 **[!UICONTROL 索和制表人]** ”组件添加到页面并配 **[!UICONTROL 置列表窗格]**。 要使最终用户能够使用日期、文本和标记搜索表单，请添加“搜 **[!UICONTROL 索窗格]** ”组件。

要从页面上的任意位置链接表单，请使用链接组件。 有关链接组件的详细信息，请参 [阅在页面中嵌入链接组件](/help/forms/using/embedding-link-component-page.md)。

要列表处于草稿状态的表单和已提交的表单，请使用草 **[!UICONTROL 稿和提交组件]** 。 有关详细信息，请参阅自 [定义草稿和提交组件](/help/forms/using/draft-submission-component.md)。

## 移动设备友好性 {#mobile-device-friendliness}

Forms门户搜索和制表器组件适合移动设备，并相应地进行调整。 所有三个默认视图: 网格、卡、面板根据打开网站的设备重新设置，同时网页也进行调整。 简单的事实是，Search &amp; Lister仅是一个组件，不控制页面级别样式。

下图描述在移动设备上打开时的搜索和制表人组件：

![“搜索”和“制表人”组件的屏幕截](assets/search_lister.png)**图：** *搜索和制表人组件*

## 自定义表单门户页面 {#customizing-a-forms-portal-page-br}

可以自定义表单门户页面，为页面提供不同的外观。 您还可以添加元数据以改进搜索体验、更改页面布局和添加自定义CSS样式。 有关详细信息，请参 [阅自定义Forms门户组件模板](/help/forms/using/customizing-templates-forms-portal-components.md)。

AEM FormsUI允许您向表单添加自定义元数据。 自定义元数据有助于向最终用户提供列表和搜索表单体验。 有关自定义元数据的详细信息，请参 [阅自定义Forms门户组件模板](/help/forms/using/customizing-templates-forms-portal-components.md)。

开箱即用的表单门户提供渲染操作。 您可以自定义表单门户以添加更多操作。 有关详细信息，请参 [阅添加对表单制表人项目的自定义操作。](/help/forms/using/add-custom-action-form-lister.md)
