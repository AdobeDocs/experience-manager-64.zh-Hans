---
title: 新增功能摘要 | AEM 6.4Forms
seo-title: 新增功能摘要 | AEM 6.4Forms
description: AEM 6.4Forms的新增功能和增强功能摘要。
seo-description: AEM 6.4Forms的新增功能和增强功能摘要。
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: f2b0d37a0666f2a0be9e7034da12dddf0c56fb25
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---


# 新增功能摘要 | AEM 6.4Forms{#new-features-summary-aem-forms}

AEM 6.4Forms的新增功能和增强功能摘要。

AEM Forms包含若干新增功能和增强功能，它们通过自适应表单和交互式通信进一步简化了创建、管理和用户体验。

阅读新增功能和增强功能的快速介绍。 访问文档以了解资源提供的详细信息。 另请参见AEM 6.4Forms[发行说明](/help/release-notes/forms.md)。 有关完整的AEM 6.4Forms文档，请访问[AEM 6.4Forms指南](/help/forms/home.md)。

## 交互式通信 {#interactive-communications}

![通信管理](assets/correspondence-management.png)

交互通信集中化和管理安全、个性化和交互式通信的创建、汇编和投放，如业务通信、信件、文档、声明、利益声明、财富管理招股书、营销邮件、帐单和欢迎工具包。

交互通信使用与自适应表单相同的底层技术、流程和组件创建响应式多渠道通信，与响应式自适应表单非常相似。

交互式通信优惠显着优势：

* 提供与表单数据模型的OOTB集成，以便轻松、简化对后端数据库和其他CRM系统（如MS Dynamics）的访问
* 为印刷和Web渠道提供集成的创作界面
* 为印刷和Web渠道提供与自适应Forms创作类似的基于拖放的创作界面。

交互通信是创建客户通信的默认和推荐方法。 要继续使用AEM 6.3Forms和AEM 6.2Forms中的字母，您需要安装一个兼容包。

### 多渠道交互式通信创作{#multi-channel-interactive-communication-authoring}

使用交互式通信，您可以从单个文档编辑器创作和编辑打印文档和Web数据。 通过使用相同的文档片段构建两个渠道的再现，您可以消除工作重复。
![printweb_2](assets/printweb_2.png)

有关详细信息，请参阅[交互通信概述](/help/forms/using/interactive-communications-overview.md)。

### WYSIWYG文档编辑器{#wysiwyg-document-editor}

WYSIWYG拖放文档编辑器对业务友好。 资产的直观界面、拖放功能、标准组件、数据模型和集成存储库有助于快速轻松地创作交互式通信。

要创建交互式通信或编辑现有通信，商业用户可以使用以下构件：渠道、内容、属性、资产、组件和数据源。

![drag-n-drop-lf](assets/drag-n-drop-lf.png)

有关详细信息，请参阅[创作交互式通信的简介](/help/forms/using/introduction-interactive-communication-authoring.md)。

### 在交互通信中从打印内容自动生成Web版本{#auto-generate-web-version-from-print-content-in-interactive-communication}

作者可以在同一个编辑器中自动生成从印刷文档到创作、预览和编辑印刷文档和Web文档的Web内容。 交互通信作者只需创建一次，即可发布到所有渠道。 交互式通信作者可以在打印和Web渠道中使用相同的文档片段，以防止重复工作。

有关详细信息，请参阅[打印渠道和Web渠道](/help/forms/using/web-channel-print-channel.md)。

### 使用主题来设计交互式通信{#use-themes-to-style-web-channel-of-interactive-communication}的Web渠道样式

交互式通信支持主题。 您可以创建主题并将其应用于您的交互式通信。 主题包含组件和面板的样式详细信息。 您可以在不同的交互式通信中重复使用一个主题，使它们具有共同且一致的外观和品牌。

AEM Forms包含交互式通信的开箱即用主题。 使用主题，您还可以自定义交互式通信在设备上的显示方式。

有关详细信息，请参阅AEM Forms的[主题](/help/forms/using/themes.md)。

### 增强的代理接口{#enhanced-agent-interface}

代理用户界面现在支持交互式通信的打印和Web预览。 在同一Agent用户界面中，您可以选择编辑多渠道交互通信的打印渠道和预览Web渠道。 打印渠道中的字段、变量、FDM元素和文档片段可以配置为由代理用户界面中的代理进行修改。 表单数据模型支持允许您生成包含预填样本数据的预览。

有关详细信息，请参阅[使用代理UI](/help/forms/using/prepare-send-interactive-communication.md)准备和发送交互式通信。

### 在图表{#present-information-in-charts}中显示信息

交互式通信支持Web中的图表和打印渠道，实现更丰富的通信。 使用饼形图、圆环图、条形图和柱状图，您可以浓缩并以可视方式呈现大量信息，以便于解释和分析。

![图表-2](assets/chart-2.png) ![图表](assets/chart.png)

有关详细信息，请参阅[在Interactive Communications中使用图表](/help/forms/using/chart-component-interactive-communications.md)。

### 开箱即用的文档连接器，用于预填充{#out-of-the-box-data-connectors-to-prefill-documents}

交互式通信提供与业务工具的数据集成，以连接多个业务系统（包括CRM Systems），并将数据个性化为文档。

![fdm_ad](assets/fdm_ad.png)

有关详细信息，请参阅[使用表单数据模型](/help/forms/using/using-form-data-model.md)。

### 增强的文档片段编辑器{#enhanced-document-fragment-editor}

您现在可以在交互通信的文档片段中使用FDM元素和规则。

* 支持表单数据模型元素
* 使用规则显示或隐藏资产／文本片段
* 验证元素／变量的值
* 执行函数以计算数学表达式的值

有关详细信息，请参阅：

* [交互通信中的文本](/help/forms/using/texts-interactive-communications.md)
* [交互通信中的条件](/help/forms/using/conditions-interactive-communications.md)

### 现有资产{#compatibility-package-for-existing-assets}的兼容性包

默认情况下，此版本不支持先前版本的AEM Forms的字母资产。 如果您打算继续使用AEM 6.3Forms和AEM 6.2Forms的字母，则需要安装兼容性软件包。

## 数据集成{#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms数](/help/forms/using/data-integration.md) 据集成允许您配置不同的数据源；例如数据库、基于RESTful或SOAP的Web服务以及OData服务；创建表单数据模型，您可以使用该模型在自适应表单和文档中绑定数据、预填和调用服务。

此版本中的数据集成新增了若干功能和增强功能。

### 创建没有数据源{#create-form-data-model-without-data-source}的表单数据模型

现在，商业用户和表单作者无需配置数据源即可创建包括其实体和属性在内的表单数据模型，并可用于创作自适应表单和文档。 以后可以将表单数据模型绑定到数据源。 它消除了对数据源的依赖性，使用表单数据模型创作表单和文档。

同样，您可以在现有表单数据模型中创建实体和子属性，然后将它们绑定到数据源中的相应实体和属性。

有关详细信息，请参阅[创建表单数据模型](/help/forms/using/create-form-data-models.md)。

### 创建计算属性{#create-computed-properties}

Forms的作者和开发者可以创建表单数据模型的计算属性。 它们允许您通过为配置数据源中可用的数据创建规则或逻辑来计算属性值。 规则是当表达式加载到表单数据模型中或表达式中属性的值发生更改时进行评估的。 例如，名为“分期付款”的计算属性根据数据源中指定的利率以及用户在表单中指定的贷款金额和年限计算贷款的每月支付额。

计算属性驻留在表单数据模型中，并且数据源中不存在。 您可以在自适应表单和交互式通信中使用计算属性。

有关详细信息，请参阅[使用表单数据模型](/help/forms/using/work-with-form-data-model.md)。

### 预览表单和文档（示例数据{#preview-forms-and-documents-with-sample-data}）

表单数据模型允许您为表单数据模型中所有图元的属性生成示例数据。 生成的数据与为属性配置的数据类型相对应。 当您预览与表单数据模型关联的自适应表单或文档时，它使用预填样本数据来呈现。

样本数据是一组随机值，每次生成它时都会发生变化。 但是，您可以编辑并保存示例数据，即使重新生成该数据，该示例数据也仍然存在。 例如，如果您编辑并保存“名”和“姓”属性的示例数据，然后在表单数据模型中添加其他属性或实体并重新生成示例数据，则在重新生成其他属性的值时，“名”和“姓”属性将显示保存的值。

有关详细信息，请参阅[使用表单数据模型](/help/forms/using/using-form-data-model.md)。

### 刷新数据源定义{#refresh-data-source-definitions}

数据源实体或属性中的任何更新不会自动反映在关联的表单数据模型中。 表单数据模型编辑器现在具有![refresh_forms_di](assets/refresh_forms_di.png)（刷新数据源定义）功能，使服务器缓存失效，从数据源获取更新的模式以立即反映在表单数据模型中。

### 使用触控用户界面{#configure-data-sources-using-touch-user-interface}配置数据源

在此版本中，数据源的云服务配置可在触屏用户界面中使用。 此外，配置云服务的位置已更改为&#x200B;**[!UICONTROL 工具>Cloud Services>数据源]**。 请参阅[配置数据源](/help/forms/using/configure-data-sources.md)。

## 自适应表单 {#adaptive-forms}

![simplification-of-authoring-forms-and-文档_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 借助增强的延迟加载{#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}提高自适应表单的性能

自适应表单中的延迟加载功能将延迟表单片段的初始化，直到需要它们。 它通过最大限度地减少渲染表单所需的时间来改进大型表单的性能，从而获得更好的用户体验。

此版本中对延迟加载功能进行了多项增强：

* 在启用了延迟加载的表单片段中支持文件附件和条款和条件组件。
* 可重复面板支持启用延迟加载的自适应表单片段。
* AEM Forms应用程序支持具有延迟加载启用片段的自适应表单。

## 以Forms为中心的AEM工作流{#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

借助以Forms为中心的AEM工作流功能，您可以快速为OSGi堆栈上的各种任务构建和部署工作流。 您不再需要在JEE堆栈上安装可用的流程管理功能，从而简化了部署并消除了应用程序服务器和基础架构成本。 有关详细信息，请参阅OSGi[上以Forms为中心的工作流。](/help/forms/using/aem-forms-workflow.md)

以下是以Forms为中心的AEM工作流的增强功能：·

* 工作流模型编辑器在触控用户界面中可用。 它有助于您缩短创建以表单为中心的AEM工作流所需的时间。
* 用于发送电子邮件的工作流步骤。 例如，您可以使用电子邮件步骤在完成工作流时发送记录文档。
* 在工作流模型中使用表单数据模型服务的工作流步骤。 通过此步骤，您无需编写任何自定义代码即可调用数据集成服务。 例如，您可以调用GET服务从数据库存档获取员工详细信息，而无需编写任何自定义代码。

## AEM Forms 应用程序 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

AEM Forms应用程序允许现场工作人员将他们的移动设备与AEM Forms服务器同步并处理表单。 当设备离线时，应用程序可无缝地工作，方法是将数据保存在设备上本地，当设备重新联机时，将数据与服务器同步。 有关详细信息，请参阅[AEM Forms应用程序](/help/forms/using/aem-forms-app.md)。

以下是AEM Forms应用程序的改进：

* AEM Forms应用程序支持具有延迟加载启用片段的自适应表单。
* 在AEM Forms应用程序中支持具有表单数据模型的自适应表单。

## 文档安全 {#document-security}

![aem-forms-文档-安全-](assets/aem-forms-document-security-.png)

使用文档安全性，您可以安全地分发以支持的格式保存的任何信息。 文档安全性确保只有授权用户才能使用您的文档。 以下是文档安全性的主要变化：

* 文档安全提供[可移植保护库(PPL)](/help/forms/using/document-security-offerings.md)以在本地保护文档，而不将文档发送到AEM Forms服务器。 只有安全凭据和策略详细信息通过网络传送到AEM Forms服务器。 AEM 6.4Forms已采用OSGi捆绑格式引入便携保护库(PPL)。 现在，您可以直接在AEM Forms服务器上安装PPL库，并将AEM和PPL的功能相互结合使用。
* 文档安全性C++ SDK和C++ PPL库可以使用Microsoft Visual Studio 2013进行编译。 以前支持的版本是Microsoft Visual Studio 2010。

## 支持的平台 {#supported-platforms}

AEM Forms可以使用支持的操作系统、应用程序服务器、数据库、数据库驱动程序、JDK、LDAP服务器和电子邮件服务器的任意组合进行设置。 以下是受支持平台中的主要更改：

<table> 
 <tbody> 
  <tr> 
   <td>组件</td> 
   <td>已添加支持</td> 
   <td>已删除支持</td> 
  </tr> 
  <tr> 
   <td>操作系统</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>OracleLinux 7更新3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>应用程序服务器<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>数据库</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19及更高版本</li> 
     <li>IBM DB2 11.1</li> 
     <li>Oracle多租户架构</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>LDAP服务器</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle目录服务器企业版7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>电子邮件服务器</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>连接器</td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2016的连接器</li> 
     <li>EMC Documentum 7.3的连接器</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2007的连接器</li> 
     <li>Microsoft Sharepoint 2010的连接器</li> 
     <li>IBM Filenet 5.0的连接器</li> 
     <li>EMC Documentum 6.7的连接器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>浏览器</td> 
   <td> 
    <ul> 
     <li>macOS上的Apple Safari 11.x</li> 
     <li>iOS上的Apple Safari 11.x</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>用于Blackberry Z30和Q10设备的Blackberry浏览器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms应用<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4或更高版本</li> 
     <li>Apple iOS 10或更高</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX和Solaris操作系统只适用于升级客户。
