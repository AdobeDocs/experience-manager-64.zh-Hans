---
title: 创建交互式通信
seo-title: Create an Interactive Communication
description: 使用交互式通信编辑器创建交互式通信。 使用拖放功能构建交互式通信，并预览不同设备类型的打印和Web输出。
seo-description: Create an Interactive Communication using the Interactive Communication editor. Use drag-and-drop functionality to build the Interactive Communication, and preview both print and web outputs on different device types.
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
feature: Interactive Communication
exl-id: a65b775d-040c-4069-b43a-6815be959b31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3156'
ht-degree: 2%

---

# 创建交互式通信  {#create-an-interactive-communication}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

使用交互式通信编辑器创建交互式通信。 使用拖放功能构建交互式通信，并预览不同设备类型的打印和Web输出。

## 概述 {#overview}

交互式通信集中管理个性化的交互式信函的创建、汇编和传递。 利用打印作为Web的主控渠道，可最大程度地减少在创建交互式通信的Web输出时的工作重复。

### 前提条件 {#prerequisites}

以下是创建交互式通信的先决条件：

* 设置 [表单数据模型](/help/forms/using/data-integration.md) 包含测试数据或与实际数据源(如Microsoft® Dynamics的实例)。
* 确保您具有 [文档片段](/help/forms/using/document-fragments.md).
* 确保您具有 [打印和Web渠道模板](/help/forms/using/web-channel-print-channel.md).
* 确保您具有 [主题](/help/forms/using/themes.md) ，以访问web渠道。

## 创建交互式通信 {#createic}

1. 登录到AEM创作实例，然后导航到 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms和文档]**.
1. 点按 **[!UICONTROL 创建]** 选择 **[!UICONTROL 交互式通信]**. “创建交互式通信”页面。

   ![创建交互式通信](assets/create-interactive-communication.png)

1. 输入以下信息。 : 

   * **[!UICONTROL 标题]**:输入交互式通信的标题。
   * **[!UICONTROL 名称*]**:交互式通信的名称是从您输入的标题派生的。 根据需要编辑它。
   * **[!UICONTROL 描述]**:输入有关交互式通信的描述。
   * **[!UICONTROL 表单数据模型*]**:浏览并选择表单数据模型。 有关表单数据模型的更多信息，请参阅 [AEM Forms数据集成](/help/forms/using/data-integration.md).
   * **[!UICONTROL 预填充服务]**:选择预填充服务以检索数据并预填充交互式通信。
   * **[!UICONTROL 后处理类型]**:您可以选择在提交交互式通信时触发的AEM或Forms工作流。 选择要触发的工作流的类型。
   * **[!UICONTROL 后处理]**:选择要触发的工作流的名称。 选择AEM工作流时，提供“附件路径”、“布局路径”、“PDF路径”、“打印数据路径”和“Web数据路径”。
   * **[!UICONTROL 标记]**:选择要应用于交互式通信的标记。 您还可以键入新/自定义标记名称，然后按Enter以创建该名称。
   * **[!UICONTROL 作者]**：作者名称将自动从登录用户的用户名中获取。
   * **[!UICONTROL 发布日期：]** 输入发布交互式通信的日期。
   * **[!UICONTROL 取消发布日期]**:输入取消发布交互式通信的日期。

1. 点按 **[!UICONTROL 下一个]**. 将显示用于指定打印和Web渠道详细信息的屏幕。
1. 输入以下内容：

   * **[!UICONTROL 打印]**:选择此选项可生成交互式通信的打印渠道。
   * **[!UICONTROL 打印模板*:]** 浏览并选择XDP作为打印模板。
   * **[!UICONTROL 将“打印为主控”用于Web渠道：]** 选择此选项可创建与打印渠道同步的Web渠道。 将打印渠道用作Web渠道的主控，可确保Web渠道的内容和数据绑定是从打印渠道派生的，并且在点按“同步”时，在打印渠道中所做的更改会反映在Web渠道中。 但是，作者可以根据需要中断Web渠道中特定组件的继承。 有关更多信息，请参阅 [将Web渠道与打印渠道同步](/help/forms/using/create-interactive-communication.md#synchronize).
   * **[!UICONTROL Web:]** 选择此选项可生成交互式通信的Web渠道或响应式输出。
   * **[!UICONTROL 交互式通信Web模板*:]** 浏览并选择Web模板。
   * **[!UICONTROL 主题]** 和 **[!UICONTROL 选择主题*]**:浏览并选择主题以设置交互式通信的Web渠道的样式。 有关更多信息，请参阅 [AEM Forms主题](/help/forms/using/themes.md).
   有关打印渠道和Web渠道的更多信息，请参阅 [打印渠道和Web渠道](/help/forms/using/web-channel-print-channel.md).

1. 点按 **[!UICONTROL 创建]**. 将创建交互式通信，并出现一个警报框。 点按 **[!UICONTROL 编辑]** 开始构建交互式通信的内容，如 [使用交互式通信创作用户界面添加内容](#step2). 或者，您也可以点按 **[!UICONTROL 完成]** 并选择稍后编辑交互式通信。

## 向交互式通信添加内容 {#step2}

创建交互式通信后，可以使用交互式通信创作界面来构建其内容。

有关交互式通信创作界面的更多信息，请参阅 [交互式通信创作简介](/help/forms/using/introduction-interactive-communication-authoring.md).

1. 按照 [创建交互式通信](#createic). 或者，您也可以导航到AEM上的现有交互式通信资产，选择该资产，然后点按 **[!UICONTROL 编辑]** 启动交互式通信创作界面。

   默认情况下，将显示交互式通信的打印渠道，除非交互式通信是仅限Web渠道。 交互式通信的打印渠道显示目标区域，如所选XDP/打印渠道模板中所示。 在这些目标区域和字段中，您可以添加组件或资产。

1. 选择打印渠道后，选择 **[!UICONTROL 组件]** 选项卡。 打印渠道中提供以下组件：

   | **Component** | **功能** |
   |---|---|
   | 图表 | 添加一个图表，可在交互式通信中使用该图表，以可视方式表示从表单数据模型集合中检索的二维数据。 有关更多信息，请参阅 [在交互式通信中使用图表](/help/forms/using/chart-component-interactive-communications.md). |
   | 文档片段 | 允许您向交互式通信添加可重用的组件，如文本、列表或条件。 添加的组件可以是基于表单数据模型的组件，也可以是没有表单数据模型的组件。 |
   | 图像 | 可让您插入图像。 |

   将组件拖放到交互式通信中，并根据需要对其进行配置。

1. 选择打印渠道后，转到 **[!UICONTROL 资产]** 选项卡，然后应用过滤器以仅显示您要查看的资产。

   使用资产浏览器，您还可以直接将资产拖放到交互式通信目标区域。

   ![assets-docfragments](assets/assets-docfragments.png)

1. 将文档片段拖放到交互式通信中。 以下是可在交互式通信的打印渠道中使用的文档片段类型。

<table> 
 <tbody> 
  <tr> 
   <td><strong>文档片段类型</strong></td> 
   <td><strong>示例用途</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">文本</a></td> 
   <td>用于添加地址、收件人电子邮件和信件正文文本的文本 </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">条件</a></td> 
   <td>根据策略类型向通信添加相应标头图像的条件：Standard或Premium。 <br /> </td> 
  </tr> 
  <tr> 
   <td>列表</td> 
   <td>文档片段的组，包括文本、条件、其他列表和图像。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

有关文档片段的更多信息，请参阅 [文档片段](/help/forms/using/document-fragments.md).

1. 要设置变量绑定，请点按变量并选择 ![configure_icon](assets/configure_icon.png) （配置），然后在侧栏的“属性”面板中设置绑定属性。

   * **[!UICONTROL 无]**:代理将填写变量的值。
   * **[!UICONTROL 文本片段]**:如果选中此选项，则可以浏览并选择其内容在字段中呈现的文本文档片段。 只能将这些文本文档片段绑定到中没有变量的变量。
   * **[!UICONTROL 数据模型对象]**:选择在字段中填充其值的表单数据模型属性。
   您还可以选择配置相关文本文档片段。 “属性”面板显示文本文档片段中的变量列表。 您可以点按 ![编辑](assets/edit.png) （编辑）在变量名称旁边，以显示该变量的设置进行编辑。

1. 要在选择打印渠道的情况下，在 **[!UICONTROL 资产]** 选项卡，以仅显示布局片段。 将所需的布局片段拖放到交互式通信中。 布局片段基于XDP，可用于在交互式通信中创建图形布局或使用动态数据填充的静态和动态表。

   示例：一个布局表，用于显示旧政策和新政策的毛额溢价、忠诚度折扣%以及紧急路边援助可用性。

   有关布局片段的更多信息，请参阅 [文档片段](/help/forms/using/document-fragments.md).

1. 选择打印渠道后，在 **[!UICONTROL 资产]** 选项卡。 将所需的图像拖放到交互式通信中，如公司徽标。

   此外，在交互式通信中管理以下内容：

   * [添加和配置图表](/help/forms/using/chart-component-interactive-communications.md)
   * [将Web渠道与打印渠道同步](/help/forms/using/create-interactive-communication.md#synchronize)

      * 自动同步
      * 取消继承
      * 重新启用继承
      * 同步
   * [附件和库访问](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [XDP/布局字段属性](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [将规则添加到组件](/help/forms/using/create-interactive-communication.md#rules)


1. 切换到 **[!UICONTROL Web渠道]**. Web渠道显示在交互式通信编辑器中。 首次从“打印”渠道切换到Web渠道时，会进行自动同步。 有关更多信息，请参阅 [从打印渠道同步Web渠道](/help/forms/using/create-interactive-communication.md#synchronize).

   由于在本例中，我们将“打印”用作Web的主控，因此“打印”渠道占位符、内容和数据绑定会同步到Web渠道。 但是，您可以根据需要更改和自定义Web渠道中的特定内容。

   ![webchannelassets](assets/webchannelassets.png)

1. 要在选择Web渠道的Web渠道中添加其他组件，请点按 **[!UICONTROL 组件]**. 根据需要将组件拖放到交互式通信的Web渠道中，然后继续配置这些组件。

   | 组件 | 功能 |
   |---|---|
   | 图表 | 添加一个图表，可在交互式通信中使用该图表，以可视方式表示从表单数据模型集合中检索的二维数据。 有关更多信息，请参阅 [使用图表组件](/help/forms/using/chart-component-interactive-communications.md). |
   | 文档片段 | 允许向交互式通信添加可重用的组件、文本、列表或条件。 您添加到交互式通信的可重用组件可以是基于表单数据模型的组件，也可以是没有表单数据模型的组件。 |
   | 图像 | 可让您插入图像。 |
   | 面板 | 面板组件是用于将其他组件分组在一起的占位符，可控制在交互式通信中如何布局一组组件（如折叠面板和选项卡）。 面板组件还允许您使一组组件可重复用于最终用户，例如在填写教育凭据所需的多个条目中。 |
   | 表 | 添加表格以便按行和列整理数据。 |
   | 目标区域 | 在Web渠道中插入目标区域以组织特定于Web渠道的组件。 目标区域是一个纯容器，用于对特定于Web渠道的组件进行分组。 |
   | 文本 | 向交互式通信的Web渠道中添加富文本。 文本还可以利用表单数据模型对象来使内容动态。 |

1. 根据需要，在您的Web渠道中插入资产。

   您可以 [预览交互式通信](#previewic) 查看交互式通信的打印和web输出，并根据需要继续进行更改。

## 预览交互式通信 {#previewic}

您可以使用 **[!UICONTROL 预览]** 用于评估交互式通信外观的选项。 交互式通信的Web渠道还提供了用于模拟各种设备的交互式通信体验的选项。 例如，iPhone、iPad和桌面。 您可以同时使用 **[!UICONTROL 预览]** 和 **[!UICONTROL 模拟器]** ![标尺](assets/ruler.png) 选项，以预览不同屏幕大小的设备的web输出。 预览中的示例数据是从指定的表单数据模型填充的。

1. 选择（打印或Web）渠道以预览和点按预览。 出现“Interactive Communication（交互式通信）”。

   >[!NOTE]
   >
   >预览将使用指定表单数据模型的示例数据填充。 有关预览与其他某些数据交互式通信或使用预填充服务的更多信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md) 和 [使用表单数据模型](/help/forms/using/work-with-form-data-model.md).

1. 对于Web渠道，请使用 ![标尺](assets/ruler.png) 查看交互式通信在各种设备上的外观。

   ![webchannelpreview](assets/webchannelpreview.png)

此外，您可以 [使用代理UI准备和发送交互式通信](/help/forms/using/prepare-send-interactive-communication.md).

## 在交互式通信中配置属性  {#configuring-properties-in-interactive-communication}

### 附件和库访问 {#attachmentslibrary}

在“打印”渠道中，您可以配置附件和库访问权限，以允许代理在代理UI中管理用于交互式通信的附件：

1. 在“打印”渠道中，突出显示文档容器，然后点按 **[!UICONTROL 属性]**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   “属性”面板将显示在侧栏中。

   ![属性附件](assets/propertiesattachments.png)

1. 展开 **[!UICONTROL 附件]** 并指定以下属性：

   * **[!UICONTROL 允许库访问]**:选择以在代理UI中启用代理的库访问。 如果启用，则代理可在准备交互式通信时从库添加文件。
   * **[!UICONTROL 允许重新排序附件]**:选择以使代理使用交互式通信重新排序附件。
   * **[!UICONTROL 允许的最大附件数]**:指定交互式通信允许的最大附件数。
   * **[!UICONTROL 要附加的文件]**:点按 **[!UICONTROL 添加]** 并浏览以选择要附加的文件，并指定以下内容：

      * **[!UICONTROL 默认情况下，将此文件附加到文档]**:如果仅附件不是“必填”，则可以更改此选项。
      * **[!UICONTROL 必需：]** 代理将无法在代理UI中删除附件。
   ![附件](assets/attachfiles.png)

1. 点按 **[!UICONTROL 完成]**.

### XDP/布局字段属性 {#xdplayoutfieldproperties}

1. 在编辑交互式通信的打印渠道时，将鼠标悬停在打印渠道模板中构建的字段上，然后选择 ![configure_icon](assets/configure_icon.png) （配置）。

   “属性”(Properties)对话框显示在侧栏中。

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. 指定以下内容：

   * **[!UICONTROL 名称]**:JCR节点名称。
   * **[!UICONTROL 标题]**:在代理UI和文档容器树中输入代理可见的标题。
   * **[!UICONTROL 绑定类型]**:为字段选择以下绑定类型之一。

      * 无：代理将填写属性的值。
      * 文本片段：如果选中此选项，则可以浏览并选择在字段中呈现内容的文本文档片段。
      * 数据模型对象：选择在字段中填充其值的表单数据模型属性。
   * **[!UICONTROL 默认值]**:默认值可确保当指定的数据模型对象或文本片段没有提供任何值时，该字段不为空。 如果数据绑定类型为“无”，则会在字段中预填充默认值。
   * **[!UICONTROL 由代理编辑]**:选择以允许代理编辑代理UI中字段中的值。 如果“绑定类型”为“文本片段”，则此设置不适用。
   * **[!UICONTROL 标签]**:在代理UI中为代理指定随字段一起显示的文本字符串。 如果“绑定类型”为“文本片段”，则此设置不适用。
   * **[!UICONTROL 工具提示]**:在Agent UI中，输入一个文本字符串，该字符串将在鼠标悬停在Agent上时可见。 如果“绑定类型”为“文本片段”，则此设置不适用。
   * **[!UICONTROL 必需]**:选择以使该字段对座席为必填字段。 如果“绑定类型”为“文本片段”，则此设置不适用。
   * **[!UICONTROL 允许多行]**:选择此字段可允许在字段中输入多行文本。 如果“绑定类型”为“文本片段”，则此设置不适用。


1. 点按 ![done_icon](assets/done_icon.png).

## 将规则应用于交互式通信组件 {#rules}

要在交互式通信中对组件或内容进行条件化，请点按组件/内容块，然后选择 ![createrleicon](assets/createruleicon.png) （创建规则）以启动规则编辑器。

有关更多信息，请参阅：

* [规则编辑器](/help/forms/using/rule-editor.md)
* [交互式通信创作简介](/help/forms/using/introduction-interactive-communication-authoring.md)

## 使用表 {#tables}

### 交互式通信中的动态表 {#dynamic-tables-in-interactive-communication}

您可以在交互式通信中使用布局片段添加动态表。 以下步骤使用信用卡报表的示例来说明如何使用布局片段在交互式通信中创建动态表。

1. 确保创建表所需的布局片段在AEM中可用。
1. 在交互式通信的打印渠道中，从资产浏览器将布局片段（包含多列表）拖放到目标区域中。

   ![lf_dragdrop](assets/lf_dragdrop.png)

   “交互式通信”布局区域中会显示一个表。

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. 为表的每个单元格指定数据绑定。 要创建可重复行，请在属于公共集合属性的行中插入表单数据模型属性。

   1. 点按表中的单元格，然后选择 ![configure_icon](assets/configure_icon.png) （配置）。

      “属性”(Properties)对话框显示在侧栏中。

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. 配置属性：

      * **[!UICONTROL 名称]**:JCR节点名称。
      * **[!UICONTROL 标题]**:输入将在交互式通信编辑器中显示的标题。
      * **[!UICONTROL 绑定类型]**&amp;ast;为字段选择以下绑定类型之一。

         * **[!UICONTROL 无]**
         * **[!UICONTROL 数据模型对象]**:字段中会填充表单数据模型属性的值。
      * **[!UICONTROL 数据模型对象]**:其值在字段中填充的表单数据模型属性。
      * **[!UICONTROL 默认值]**:默认值可确保当指定的数据模型对象没有提供值时，该字段不为空。 默认值已预填充在字段中。
      * **[!UICONTROL 由代理编辑]**:选择以允许代理编辑代理UI中字段中的值。
   1. 点按 ![done_icon](assets/done_icon.png).



1. 预览交互式通信以查看使用数据呈现的表。

   ![lf_preview](assets/lf_preview.png)

### 仅Web渠道表 {#web-channel-only-tables}

您可以使用类型集合的数据模型属性在交互式通信中创建仅Web渠道动态表。 此类表是集合属性的子属性的表示形式。 您只能编辑表中各单元格的格式属性。

1. 切换到Web渠道，然后选择显示数据源浏览器。
1. 将收藏集属性拖放到子表单中。

   将在子表单中创建表。

1. 在交互式通信的Web预览中预览表。

## 与打印渠道同步Web渠道 {#synchronize}

在创建交互式通信时，如果选择“打印为Web渠道的主控”，则会创建与“打印”渠道同步的Web渠道，并且Web渠道的内容和数据绑定从打印渠道派生，并且当您点按“同步”时，在打印渠道中所做的更改会反映在Web渠道中。

但是，作者可以根据需要中断Web渠道中组件的继承。
![printweb_2-3](assets/printweb_2-3.png)
[单击放大](assets/printweb_2-3.png)

![交互式通信编辑器中的打印和Web渠道](assets/printweb_2-1.png)

### 自动同步 {#auto-sync}

如果使用“打印”渠道作为Web渠道的主控，并从“打印”渠道切换到Web渠道，则会进行自动同步。 自动同步将占位符、内容和数据绑定从打印渠道引入Web渠道。 根据交互式通信的复杂性和内容，自动同步可能需要一些时间。

>[!NOTE]
>
>同步渠道仅同步从打印渠道到Web渠道的文档片段、图像、条件、列表和布局片段。 包含此类元素的子表单或父节点不会同步。

### 取消继承 {#cancel-inheritance}

在Web渠道中，组件嵌入到目标区域中。

将鼠标悬停在Web渠道中的相关目标区域上，然后选择 ![取消继承](assets/cancelinheritance.png) （取消继承），然后在取消继承对话框中，点按 **[!UICONTROL 是]**.

目标区域中组件的继承将被取消，现在您可以根据需要对其进行编辑。

### 重新启用继承 {#re-enable-inheritance}

在Web渠道中，如果已取消组件的继承，则可以重新启用该组件。 要重新启用继承，请将鼠标悬停在相关目标区域（包括该组件）的边界上，然后点按 ![重新启用继承](assets/reenableinheritance.png).

此时会出现“还原继承”对话框。

![反继承](assets/revertinheritance.png)

如果需要，请选择 **[!UICONTROL 在还原继承后同步页面]**. 选择此选项可同步整个交互式通信。 如果不选择此选项，则只有在恢复继承时同步相关目标区域。

点按 **[!UICONTROL 是]**.

### 同步 {#synchronize-1}

如果您将“打印为Web渠道的主控”并对打印渠道进行更改，则可以点按“同步”，将新做的更改引入Web渠道。

1. 要将Web渠道与打印渠道同步，请点按 **[!UICONTROL 同步]**.

   将显示“从主控渠道同步内容”对话框。

   ![synchronizecontentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. 点按以下任一项：

   * **[!UICONTROL 放弃更改]**:放弃对Web渠道所做的所有更改，而不考虑在Web渠道中所做的更改。
   * **[!UICONTROL 保留更改]**:仅同步未取消继承的目标区域的内容。
