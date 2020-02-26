---
title: 新增功能摘要| AEM 6.4表单
seo-title: 新增功能摘要| AEM 6.4表单
description: AEM 6.4 Forms中新增功能和增强功能的摘要。
seo-description: AEM 6.4 Forms中新增功能和增强功能的摘要。
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# 新增功能摘要| AEM 6.4表单 {#new-features-summary-aem-forms}

AEM 6.4 Forms中新增功能和增强功能的摘要。

AEM Forms包括若干新增功能和增强功能，它们通过自适应表单和交互式通信进一步简化了创建、管理和用户体验。

阅读新增功能和增强功能的简介。 请访问文档以获取资源提供详细信息。 另请参阅AEM 6.4 Forms发 [行说明](/help/release-notes/forms.md)。 有关完整的AEM 6.4表单文档，请访 [问AEM 6.4表单用户指南](/help/forms/home.md)。

## 交互式通信 {#interactive-communications}

![通信管理](assets/correspondence-management.png)

Interactive Communications集中管理安全、个性化和交互式通信的创建、汇编和交付，如业务通信、信件、文档、声明、利益声明、财富管理招股说明书、营销邮件、帐单和欢迎工具包。

Interactive Communications使用与自适应表单相同的底层技术、流程和组件来创建响应式多渠道通信，这与响应式自适应表单非常相似。

交互式通信具有显着优势：

* 提供与表单数据模型的OOTB集成，以便轻松、简化对后端数据库和MS Dynamics等其他CRM系统的访问
* 为印刷和Web渠道提供集成的创作界面
* 为打印和Web渠道提供基于拖放的创作界面，与自适应表单创作类似。

交互通信是创建客户通信的默认和推荐方法。 要继续使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，您需要安装兼容包。

### 多渠道交互式通信创作 {#multi-channel-interactive-communication-authoring}

使用交互式通信，您可以从单个文档编辑器中创作和编辑打印文档和Web文档。 通过使用相同的文档片段构建两个渠道的再现，您可以消除工作重复。
![printweb_2](assets/printweb_2.png)

有关详细信息，请参 [阅交互通信概述](/help/forms/using/interactive-communications-overview.md)。

### WYSIWYG文档编辑器 {#wysiwyg-document-editor}

WYSIWYG拖放文档编辑器是商业友好型的。 资产的直观界面、拖放功能、标准组件、数据模型和集成存储库简化了交互式通信的快速而轻松的创作。

要创建交互式通信或编辑现有通信，商业用户可以使用以下构件块：渠道、内容、属性、资产、组件和数据源。

![drag-n-drop-lf](assets/drag-n-drop-lf.png)

有关详细信息，请参 [阅创作交互式通信的介绍](/help/forms/using/introduction-interactive-communication-authoring.md)。

### 在交互式通信中从打印内容自动生成Web版本 {#auto-generate-web-version-from-print-content-in-interactive-communication}

作者可以从打印文档自动生成Web文档内容，在同一编辑器中创作、预览和编辑打印文档和Web文档。 交互式通信作者只需创建一次，即可发布到所有渠道。 交互式通信作者可以在打印和Web渠道中使用相同的文档片段，以防止工作重复。

有关详细信息，请参 [阅打印渠道和Web渠道](/help/forms/using/web-channel-print-channel.md)。

### 使用主题设计交互式通信Web渠道的样式 {#use-themes-to-style-web-channel-of-interactive-communication}

交互式通信支持主题。 您可以创建主题并将其应用于您的交互式通信。 主题包含组件和面板的样式详细信息。 您可以在不同的交互式通信中重复使用一个主题，使它们具有共同且一致的外观和品牌。

AEM Forms包含一个适用于交互式通信的开箱即用主题。 使用主题，您还可以自定义交互式通信在设备上的显示方式。

有关详细信息，请参 [阅AEM Forms中的主题](/help/forms/using/themes.md)。

### 增强的代理界面 {#enhanced-agent-interface}

代理用户界面现在支持交互式通信的打印和Web预览。 从同一Agent用户界面中，您可以选择编辑打印渠道并预览多渠道交互通信的Web渠道。 打印通道中的字段、变量、FDM元素和文档片段可配置为由代理用户界面中的代理进行修改。 表单数据模型支持允许您使用预填充的范例数据生成预览。

有关详细信息，请参 [阅使用代理UI准备和发送交互式通信](/help/forms/using/prepare-send-interactive-communication.md)。

### 在图表中显示信息 {#present-information-in-charts}

交互式通信支持Web中的图表和打印通道，以实现更丰富的通信。 使用饼形、圆环形、条形和柱状图，您可以浓缩并以可视方式呈现大量信息以便于解释和分析。

![图表2图](assets/chart-2.png)![表](assets/chart.png)

有关详细信息，请参 [阅在Interactive Communications中使用图表](/help/forms/using/chart-component-interactive-communications.md)。

### 用于预填文档的现成数据连接器 {#out-of-the-box-data-connectors-to-prefill-documents}

交互式通信提供与业务工具的数据集成，以与包括CRM systems在内的多个业务系统连接并将数据个性化到文档中。

![fdm_ad](assets/fdm_ad.png)

有关详细信息，请参 [阅使用表单数据模型](/help/forms/using/using-form-data-model.md)。

### 增强的文档片段编辑器 {#enhanced-document-fragment-editor}

您现在可以在交互式通信的文档片段中使用FDM元素和规则。

* 支持表单数据模型元素
* 使用规则显示或隐藏资产／文本片段
* 验证元素／变量的值
* 执行函数以计算数学表达式的值

有关详细信息，请参阅：

* [交互通信中的文本](/help/forms/using/texts-interactive-communications.md)
* [交互通信中的条件](/help/forms/using/conditions-interactive-communications.md)

### 现有资产的兼容性包 {#compatibility-package-for-existing-assets}

默认情况下，此版本不支持来自AEM Forms早期版本的字母资产。 如果您打算继续使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，则需要安装兼容性包。

## 数据集成 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms数据集成](/help/forms/using/data-integration.md) ，允许您配置不同的数据源；例如数据库、基于RESTful或SOAP的Web服务以及OData服务；创建表单数据模型，您可以使用它绑定自适应表单和文档中的数据、预填和调用服务。

此版本中的数据集成有若干新增功能和增强功能。

### 创建无数据源的表单数据模型 {#create-form-data-model-without-data-source}

商业用户和表单作者现在无需配置数据源即可创建包含其实体和属性的表单数据模型，并可用于创作自适应表单和文档。 以后可以将表单数据模型绑定到数据源。 它消除了使用表单数据模型创作表单和文档时对数据源的依赖性。

同样，您可以在现有表单数据模型中创建实体和子属性，并稍后将其绑定到数据源中的相应实体和属性。

有关详细信息，请参 [阅创建表单数据模型](/help/forms/using/create-form-data-models.md)。

### 创建计算属性 {#create-computed-properties}

表单作者和开发人员可以在表单数据模型中创建计算属性。 它们允许您通过为配置数据源中可用的数据创建规则或逻辑来计算属性值。 规则是一个表达式，当表单数据模型中的数据加载或表达式中属性的值发生变化时，将计算该表达式。 例如，名为“分期付款”的计算属性根据数据源中指定的利率以及用户在表单中指定的贷款金额和期限计算贷款的每月支付金额。

计算的属性驻留在表单数据模型中，并且不存在于数据源中。 您可以在自适应表单和交互式通信中使用计算属性。

有关详细信息，请参 [阅使用表单数据模型](/help/forms/using/work-with-form-data-model.md)。

### 使用范例数据预览表单和文档 {#preview-forms-and-documents-with-sample-data}

表单数据模型允许您为表单数据模型中所有实体的属性生成示例数据。 生成的数据对应于为属性配置的数据类型。 当您预览与表单数据模型关联的自适应表单或文档时，它会用预填充的样本数据呈现。

样本数据是一组随机值，每次生成它时都会发生变化。 但是，即使重新生成示例数据，您也可以编辑并保存该示例数据。 例如，如果您编辑并保存“名”和“姓”属性的示例数据，稍后在表单数据模型中添加其他属性或实体并重新生成示例数据，则在重新生成其他属性的值时，“名”和“姓”属性将显示保存的值。

有关详细信息，请 [参阅使用表单数据模型](/help/forms/using/using-form-data-model.md)。

### Refresh data source definitions {#refresh-data-source-definitions}

数据源实体或属性中的任何更新不会自动反映在关联的表单数据模型中。 表单数据模型编辑器现在具有 ![refresh_forms_di](assets/refresh_forms_di.png) （刷新数据源定义）功能，该功能使服务器缓存失效，并从数据源获取更新的架构以立即反映在表单数据模型中。

### 使用触控用户界面配置数据源 {#configure-data-sources-using-touch-user-interface}

在此版本中，可在触控用户界面中使用数据源的云服务配置。 此外，配置云服务的位置已更改为“工 **[!UICONTROL 具”>“云服务”>“数据源”]**。 请参 [阅配置数据源](/help/forms/using/configure-data-sources.md)。

## 自适应表单 {#adaptive-forms}

![simplification-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 通过增强的延迟加载提高自适应表单的性能 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

自适应表单中的延迟加载功能会将表单片段的初始化定义到需要为止。 它通过最大限度地减少渲染表单所需的时间，从而改善大型表单的性能，从而改善用户体验。

此版本中对延迟加载功能进行了多项增强：

* 在启用了延迟加载的表单片段中支持文件附件和条款和条件组件。
* 可重复面板中支持启用延迟加载的自适应表单片段。
* AEM Forms应用程序支持具有延迟加载片段的自适应表单。

## 以表单为中心的AEM工作流 {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

借助以表单为中心的AEM工作流功能，您可以快速为OSGi堆栈上的各种任务构建和部署工作流。 您不再需要在JEE堆栈上安装可用的流程管理功能，从而简化了部署并消除了应用程序服务器和基础架构成本。 有关详细信息，请参 [阅OSGi上以表单为中心的工作流程](/help/forms/using/aem-forms-workflow.md)。

以下是以表单为中心的AEM工作流程中的增强功能：·

* 工作流模型编辑器在触控用户界面中可用。 它有助于您缩短创建以表单为中心的AEM工作流所需的时间。
* 用于发送电子邮件的工作流步骤。 例如，您可以使用电子邮件步骤在工作流完成时发送记录文档。
* 工作流步骤，用于在工作流模型中使用表单数据模型服务。 通过此步骤，您无需编写任何自定义代码即可调用数据集成服务。 例如，您可以调用GET服务从数据库存档获取员工详细信息，而无需编写任何自定义代码。

## AEM Forms 应用程序 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

AEM Forms应用程序允许现场工作人员将他们的移动设备与AEM Forms服务器同步，并处理他们的表单。 当设备离线时，应用程序通过将数据保存在设备上本地并在设备重新联机时与服务器同步数据来无缝地工作。 有关详细信息，请参阅 [AEM Forms应用程序](/help/forms/using/aem-forms-app.md)。

以下是AEM Forms应用程序中的改进：

* AEM Forms应用程序支持具有延迟加载片段的自适应表单。
* AEM Forms应用程序支持具有表单数据模型的自适应表单。

## 文档安全 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

使用文档安全性，您可以安全地分发以支持的格式保存的任何信息。 文档安全性确保只有授权用户才能使用您的文档。 以下是文档安全性的主要更改：

* 文档安全性提 [供了可移植保护库(PPL)](/help/forms/using/document-security-offerings.md) ，无需将文档发送到AEM Forms服务器即可在本地保护文档。 只有安全凭据和策略详细信息才能通过网络传送到AEM Forms服务器。 AEM 6.4 Forms已采用OSGi捆绑格式引入了可移植保护库(PPL)。 现在，您可以直接在AEM Forms服务器上安装PPL库，并将AEM和PPL的功能相互结合使用。
* 文档安全性C++ SDK和C++ PPL库可以使用Microsoft Visual Studio 2013进行编译。 以前支持的版本是Microsoft Visual Studio 2010。

## 支持的平台 {#supported-platforms}

可以使用支持的操作系统、应用程序服务器、数据库、数据库驱动程序、JDK、LDAP服务器和电子邮件服务器的任意组合来设置AEM Forms。 以下是受支持平台中的主要更改：

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
     <li>Oracle Linux 7 Update 3</li> 
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
     <li>IBM webSphere 8.5.5</li> 
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
     <li>Oracle多租户体系结构</li> 
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
     <li>Oracle Directory Server Enterprise Edition 7.0</li> 
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
     <li>EMC Documentum 7.3连接器</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2007的连接器</li> 
     <li>Microsoft Sharepoint 2010的连接器</li> 
     <li>IBM Filenet 5.0连接器</li> 
     <li>EMC Documentum 6.7连接器</li> 
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
   <td>AEM Forms app<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4或更高版本</li> 
     <li>Apple iOS 10或更高版本</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX和Solaris操作系统仅对升级客户可用。
