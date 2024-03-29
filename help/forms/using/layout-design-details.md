---
title: 布局设计
seo-title: Layout Design
description: 布局设计详细信息说明如何创建用于信件或交互式通信的布局。
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---

# 布局设计 {#layout-design}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

XFA表单模板或XDP是用于以下目的的模板：

* [书信](/help/forms/using/create-letter.md)
* [打印渠道](/help/forms/using/web-channel-print-channel.md#printchannel) of [交互式通信](/help/forms/using/interactive-communications-overview.md)

* 布局片段

XDP是在AdobeForms Designer中设计的。 本文详细介绍了如何设计XDP以创建有效的通信/交互式通信，例如在何处使用表单字段或目标区域以及何时使用布局片段。

## 为信件或交互式通信的打印渠道创建布局 {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

布局定义交互式通信的信件/打印渠道的图形布局。 布局可以包含典型的表单字段，如“地址”和“引用编号”。 它还包含表示目标区域的空子形式。 在表单设计器中创建布局，完成后，应用程序专家将其上传到AEM服务器。 从此处，您可以在创建通信模板或交互式通信的打印渠道时选择布局。

![设计器：创建布局](assets/claimsubrogationlayout.png)

按照以下步骤为交互式通信的信件/打印渠道创建布局：

1. 分析布局并确定在所有页面中重复的内容；通常，页眉和页脚适合此类别。 此内容放置在布局的主控页面上。 其余内容将转到布局的正文页面。 在策略夹克中，徽标和公司地址可添加到主控的页眉和页脚中。 例如，取消通知使用相同的布局。
1. 设计正文页面时，请将页面内容分为多个部分。 每个部分都设计为嵌入在布局本身中的子表单或片段布局。 如果节包含表，则将节建模为布局片段。
1. 布局的设计如下所示：

   1. 将每个部分作为包含该部分所有元素的单独子表单。
   1. 将每个部分的子表单设置为同一父子表单的子表单。 父子表单的布局设置为“流”，以便当大数据合并到前几个部分中时，允许各个部分在下面移动。
   1. 节主要居住地也可以跨其他布局重复使用。 将其创建为片段布局。
   1. 章节其他兴趣详细信息仅包含两个元素，它们彼此位于下方，可以包含大数据，并且设计为流。
   1. 其他部分包含位于特定位置的元素，因此它们被设计为定位布局。
   1. 如果部分包含位于特定位置的元素，且这些元素包含大量数据，则将部分划分为子表单。 然后，排列子表单以实现所需的行为。
   1. 对于“主要居住区”部分，添加占位符目标区域。 在信件/交互式通信设计时，此占位符绑定到分片主要住宅。
   1. 将布局(以及使用该布局的片段（如果存在）上传到AEM Forms服务器。

## 使用模式 {#using-schema}

您可以在布局或布局片段中使用架构，但不是必需的。 如果您使用架构，请确保：

1. 信件/交互式通信中使用的布局和所有片段布局使用与信件/交互式通信相同的架构。
1. 使用数据填充所需的所有字段都绑定到架构。

## 创建可靠字段 {#creating-relatable-fields}

默认情况下，所有字段都被视为与各种其他数据源相关。 如果您的布局包含任何与数据源不相关的字段，请使用“_int”（内部）后缀命名该字段；例如，pageCount_int。

可关联的字段必须：

* 是XFA &lt;field> 或 &lt;exclgroup>
* 具有XFA绑定引用
* 如果 &lt;exclgroup>，则必须至少有一个子单选按钮字段；否则，无法确定其值类型

可关联的字段必须：

* 有个名字

可关联的字段不得：

* 在其名称中包含“_int”后缀
* 将绑定设置为“none”
* 是 &lt;exclgroup> 元素

只要可靠字段符合上述标准，它就可以位于布局中的任何位置和任何嵌套深度。 您可以在主控页面中使用可重复字段。

字段的布局配置比目标区域子表单更灵活；但是，它们与单个值类型绑定。 您可以将字段设为大字段，或将其设置为固定的宽度和高度等。 解析的模块或规则结果将推送到字段中。

## 确定何时使用子表单和文本字段 {#deciding-when-to-use-subforms-and-text-nbsp-fields}

如果要以自上而下的垂直流布局（多个段落或图像）捕获多个模块内容，请使用子表单。 您的布局必须处理子表单的高度增长以容纳其内容这一事实。 如果您无法确定与子表单/目标关联的内容长度永远不会超过布局中为子表单保留的空间，请在流子表单容器中将子表单创建为子表单。 此过程可确保子表单下方的布局对象随着子表单的增长而向下流动。

如果要将模块数据或数据字典元素数据捕获到布局的架构中（因为字段与数据绑定），或在主控页面上显示模块内容，请使用字段。 请记住，主控页面中的内容不能与正文页面内容一起流动，因此您必须确保将图像字段用作标题徽标。 此表为决定何时在布局中使用子表单或字段提供了更多标准。

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>在</strong></p> </td> 
   <td><p><strong>在</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>它包含元素的组合，如姓氏和名字</p> </td> 
   <td><p>它包含一个元素，如策略编号。</p> </td> 
  </tr> 
  <tr> 
   <td><p>它包括多个段落</p> </td> 
   <td><p>文本括起来并两端对齐</p> </td> 
  </tr> 
  <tr> 
   <td><p>重复、可选和条件数据组绑定到子表单，以降低在使用脚本获取相同结果时可能发生的设计错误风险</p> </td> 
   <td><p>信件/交互式通信的所有页面上都会显示组织的徽标和地址等元素。 在这种情况下，请为这些元素创建表单字段，并将其置于主控页面。 如果将字段绑定设置为“无数据绑定”，则在信件/交互式通信编辑器中，没有字段显示为可关联的字段。 如果要将某些类型的内容与这些字段相关联，则它们必须具有绑定。</p> <p>如果您的公司地址包含多行数据，请使用带“允许多行”选项的文本字段来表示布局上的地址。</p> <p>如果将文本字段的数据类型设置为纯文本，则会使用模块输出的纯文本版本，而不是富文本版本（将丢弃所有格式）。 要保留格式，请将文本字段的数据类型设置为富文本。</p> </td> 
  </tr> 
  <tr> 
   <td><p>文本被流动</p> </td> 
   <td><p>文本字段和图像字段用于主控页面。 主控页面不能将子表单用作目标区域。</p> </td> 
  </tr> 
  <tr> 
   <td><p>对象进行分组和组织，而不将子表单绑定到数据元素</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>子表单内有一个文本字段。 子表单可以扩展，且不会覆盖布局中子表单下方的其他对象。</p> </td> 
   <td><p>您需要在后处理中轻松访问其数据。</p> </td> 
  </tr> 
 </tbody> 
</table>

## 设置重复性元素 {#setting-up-repetitive-elements}

当信件/交互式通信的所有页面上显示组织的徽标和地址等元素时，请为这些元素创建表单字段，并将它们置于主控页面。 为这些字段使用名称（字段名称）绑定。

## 指定服务器呈现格式 {#specify-the-server-nbsp-render-format}

将布局的服务器渲染格式用于动态XML表单；否则，任何基于此布局的字母/交互式通信都无法正确呈现。 默认情况下，Forms Designer中的服务器渲染格式设置为“动态XML表单”。 要确保使用正确的格式：

* 在Designer中，单击 **[!UICONTROL 文件>表单属性>默认]**，并确保将“PDF渲染/格式”设置设置为“动态XML表单”。
