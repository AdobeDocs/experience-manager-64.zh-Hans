---
title: 新增功能摘要 | AEM 6.4 Forms
seo-title: New features summary | AEM 6.4 Forms
description: AEM 6.4 Forms中新增功能和增强功能的摘要。
seo-description: Summary of new features and enhancements in AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
exl-id: 21b8ed83-9c0c-41ee-9fbb-56ccebaee132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2038'
ht-degree: 0%

---

# 新增功能摘要 | AEM 6.4 Forms {#new-features-summary-aem-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM 6.4 Forms中新增功能和增强功能的摘要。

AEM Forms包含一些新增功能和增强功能，这些功能和增强功能通过自适应表单和交互式通信进一步简化了创建、管理和用户体验。

请阅读，快速了解新增功能和增强功能。 有关资源提供详细信息的访问文档。 另请参阅AEM 6.4 Forms [发行说明](/help/release-notes/forms.md). 有关完整的AEM 6.4 Forms文档，请访问 [AEM 6.4 Forms指南](/help/forms/home.md).

## 交互式通信 {#interactive-communications}

![通信管理](assets/correspondence-management.png)

交互式通信可集中管理安全、个性化和交互式信函的创建、编排和交付，例如商务信函、信件、文档、报表、福利通知、财富管理招股说明书、营销邮件、账单和欢迎资料包。

交互式通信使用与自适应表单相同的底层技术、流程和组件来创建响应式多渠道通信，与响应式自适应表单非常类似。

交互式通信具有显着优势：

* 提供与表单数据模型的OOTB集成，以便能够轻松、简化地访问后端数据库和其他CRM系统，如MS Dynamics
* 为打印和Web渠道提供集成的创作界面
* 提供基于拖放的创作界面(与自适应Forms创作类似)，用于打印和Web渠道。

交互式通信是创建客户通信的默认和推荐方法。 要继续使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，您需要安装兼容包。

### 多渠道交互式通信创作 {#multi-channel-interactive-communication-authoring}

使用交互式通信，您可以通过单个文档编辑器来创作和编辑打印文档和Web文档。 通过利用相同的文档片段构建两个渠道的演绎版，可以消除重复工作。
![printweb_2](assets/printweb_2.png)

有关更多信息，请参阅 [交互式通信概述](/help/forms/using/interactive-communications-overview.md).

### WYSIWYG文档编辑器 {#wysiwyg-document-editor}

WYSIWYG拖放文档编辑器对业务非常友好。 直观的界面、拖放功能、标准组件、数据模型和资产集成存储库有助于快速轻松地创作交互式通信。

要创建交互式通信或编辑现有通信，企业用户可以使用以下构建基块：渠道、内容、属性、资产、组件和数据源。

![拖放 — n-lf](assets/drag-n-drop-lf.png)

有关更多信息，请参阅 [交互式通信创作简介](/help/forms/using/introduction-interactive-communication-authoring.md).

### 在交互式通信中，从打印内容自动生成Web版本 {#auto-generate-web-version-from-print-content-in-interactive-communication}

作者可以在同一编辑器中自动从打印文档生成Web文档内容，以创作、预览和编辑打印文档和Web文档。 交互式通信作者可以创建一次并发布到所有渠道。 交互式通信作者可以在打印和Web渠道中使用相同的文档片段，以防止工作重复。

有关更多信息，请参阅 [打印渠道和Web渠道](/help/forms/using/web-channel-print-channel.md).

### 利用主题设计交互式通信的Web渠道 {#use-themes-to-style-web-channel-of-interactive-communication}

交互式通信支持主题。 您可以创建主题并将其应用于您的交互式通信。 主题包含组件和面板的样式详细信息。 您可以在不同的交互式通信中重复使用一个主题，以使它们具有共同且一致的外观和品牌。

AEM Forms包含一个用于交互式通信的开箱即用主题。 使用主题，您还可以自定义交互式通信在设备上的外观。

有关更多信息，请参阅 [AEM Forms主题](/help/forms/using/themes.md).

### 增强的Agent界面 {#enhanced-agent-interface}

代理用户界面现在支持交互式通信的打印和Web预览。 在同一Agent用户界面中，您可以选择编辑打印渠道并预览多渠道交互式通信的Web渠道。 打印渠道中的字段、变量、FDM元素和文档片段可以配置为由代理用户界面中的代理进行修改。 表单数据模型支持允许您使用预填充的示例数据生成预览。

有关更多信息，请参阅 [使用代理UI准备和发送交互式通信](/help/forms/using/prepare-send-interactive-communication.md).

### 在图表中显示信息 {#present-information-in-charts}

交互式通信支持Web中的图表和打印渠道，以实现更丰富的通信。 使用饼状图、圆环图、条形图和柱状图等图表，您可以浓缩并直观地显示大量信息，以便轻松进行解释和分析。

![图表2](assets/chart-2.png) ![图表](assets/chart.png)

有关更多信息，请参阅 [在交互式通信中使用图表](/help/forms/using/chart-component-interactive-communications.md).

### 用于预填文档的现成Data Connectors {#out-of-the-box-data-connectors-to-prefill-documents}

交互式通信提供与业务工具的数据集成，以与包括CRM系统在内的多个业务系统连接，并将数据个性化为文档。

![fdm_ad](assets/fdm_ad.png)

有关更多信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md).

### 增强的文档片段编辑器 {#enhanced-document-fragment-editor}

现在，您可以在交互式通信的文档片段中使用FDM元素和规则。

* 支持表单数据模型元素
* 使用规则显示或隐藏资产/文本片段
* 验证元素/变量的值
* 执行函数以计算数学表达式的值

有关更多信息，请参阅：

* [互动交流中的文本](/help/forms/using/texts-interactive-communications.md)
* [交互式通信中的条件](/help/forms/using/conditions-interactive-communications.md)

### 现有资产的兼容包 {#compatibility-package-for-existing-assets}

默认情况下，此版本不支持来自AEM Forms早期版本的信件资产。 如果您打算继续使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，则需要安装兼容包。

## 数据集成 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms数据集成](/help/forms/using/data-integration.md) 允许您配置不同的数据源；例如数据库、基于RESTful或SOAP的Web服务以及OData服务；创建可用于绑定数据、预填充和调用自适应表单和文档中服务的表单数据模型。

此版本中数据集成新增了一些功能和增强功能。

### 创建不带数据源的表单数据模型 {#create-form-data-model-without-data-source}

业务用户和表单作者现在可以创建表单数据模型（包括其实体和属性），而无需配置数据源，并可用于创作自适应表单和文档。 您可以稍后将表单数据模型绑定到数据源。 它消除了对数据源的依赖，以便使用表单数据模型创作表单和文档。

同样，您可以在现有表单数据模型中创建实体和子属性，并稍后将其绑定到数据源中的相应实体和属性。

有关更多信息，请参阅 [创建表单数据模型](/help/forms/using/create-form-data-models.md).

### 创建计算属性 {#create-computed-properties}

Forms作者和开发人员可以在表单数据模型中创建计算属性。 利用属性，可通过为配置数据源中可用的数据创建规则或逻辑来计算属性值。 规则是一个表达式，当数据加载到表单数据模型中或表达式中属性的值发生更改时，将对其进行评估。 例如，名为“分期付款”的计算属性根据数据源中指定的利率以及用户以格式指定的贷款金额和年限来计算贷款的每月支付金额。

计算属性驻留在表单数据模型中本地，且不存在于数据源中。 您可以在自适应表单和交互式通信中使用计算属性。

有关更多信息，请参阅 [使用表单数据模型](/help/forms/using/work-with-form-data-model.md).

### 使用示例数据预览表单和文档 {#preview-forms-and-documents-with-sample-data}

表单数据模型允许您为表单数据模型中所有实体的属性生成示例数据。 生成的数据对应于为属性配置的数据类型。 预览与表单数据模型关联的自适应表单或文档时，会使用预填充的示例数据呈现该表单或文档。

示例数据是一组随机值，每次您生成该值时都会发生更改。 但是，您可以编辑并保存即使重新生成仍保留的示例数据。 例如，如果编辑并保存“名字”和“姓氏”属性的示例数据，然后在表单数据模型中添加其他属性或实体并重新生成示例数据，则“名字”和“姓氏”属性将在重新生成其他属性的值时显示保存的值。

有关详细信息，请参阅 [使用表单数据模型](/help/forms/using/using-form-data-model.md).

### 刷新数据源定义 {#refresh-data-source-definitions}

数据源实体或属性中的任何更新不会自动反映在关联的表单数据模型中。 表单数据模型编辑器现在的功能 ![refresh_forms_di](assets/refresh_forms_di.png) （刷新数据源定义），使服务器缓存失效并从数据源中获取更新的架构，以立即反映在表单数据模型中。

### 使用触屏用户界面配置数据源 {#configure-data-sources-using-touch-user-interface}

在此版本中，数据源的云服务配置在触屏用户界面中可用。 此外，配置云服务的位置已更改为 **[!UICONTROL 工具>Cloud Services>数据源]**. 请参阅 [配置数据源](/help/forms/using/configure-data-sources.md).

## 自适应表单 {#adaptive-forms}

![sumplifience-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 通过增强延迟加载提高自适应表单的性能 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

自适应表单中的延迟加载功能会定义表单片段的初始化，直到需要它们为止。 它通过最大限度地减少渲染表单所需的时间来改善大型表单的性能，从而改善用户体验。

此版本中对延迟加载功能进行了以下增强：

* 在启用了延迟加载的表单片段中，支持文件附件和条款和条件组件。
* 可重复面板中支持启用延迟加载的自适应表单片段。
* AEM Forms应用程序支持具有已启用延迟加载片段的自适应表单。

## 以Forms为中心的AEM工作流 {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

借助以Forms为中心的AEM工作流功能，您可以针对OSGi堆栈上的各种任务快速构建和部署工作流。 您不再需要安装JEE堆栈上提供的流程管理功能，从而简化部署并消除应用程序服务器和基础架构成本。 有关更多信息，请参阅 [OSGi上以Forms为中心的工作流](/help/forms/using/aem-forms-workflow.md).

以下是以Forms为中心的AEM工作流程中的增强功能：·

* 工作流模型编辑器在触屏用户界面中可用。 它有助于您缩短创建以表单为中心的AEM工作流所需的时间。
* 用于发送电子邮件的工作流步骤。 例如，您可以使用电子邮件步骤在工作流完成时发送记录文档。
* 工作流步骤，用于在工作流模型中使用表单数据模型服务。 此步骤允许您调用数据集成服务，而无需编写任何自定义代码。 例如，您可以调用GET服务，从数据库存档中获取员工详细信息，而无需编写任何自定义代码。

## AEM Forms 应用程序 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

AEM Forms应用程序允许现场工作人员将其移动设备与AEM Forms服务器同步，并处理其表单。 当设备处于脱机状态时，应用程序通过将数据保存在设备本地并在设备重新联机时与服务器同步数据来无缝工作。 有关更多信息，请参阅 [AEM Forms应用程序](/help/forms/using/aem-forms-app.md).

以下是AEM Forms应用程序中的改进功能：

* AEM Forms应用程序支持具有已启用延迟加载片段的自适应表单。
* AEM Forms应用程序支持具有表单数据模型的自适应表单。

## 文档安全 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

使用文档安全，您可以安全地分发您以支持格式保存的任何信息。 文档安全确保只有授权用户才能使用您的文档。 以下是文档安全方面的主要更改：

* 文档安全提供 [可移植保护库(PPL)](/help/forms/using/document-security-offerings.md) 在本地保护文档，而不将文档发送到AEM Forms服务器。 只有安全凭据和策略详细信息才能通过网络传输到AEM Forms服务器。 AEM 6.4 Forms以OSGi包格式引入了可移植保护库(PPL)。 现在，您可以直接在AEM Forms服务器上安装PPL库，并将AEM和PPL的功能相互结合使用。
* 文档安全C++ SDK和C++ PPL库可以使用Microsoft Visual Studio 2013进行编译。 以前支持的版本是Microsoft Visual Studio 2010。

## 支持的平台 {#supported-platforms}

AEM Forms可以使用支持的操作系统、应用程序服务器、数据库、数据库驱动程序、 JDK、LDAP服务器和电子邮件服务器的任意组合进行设置。 以下是受支持平台中的主要更改：

<table> 
 <tbody> 
  <tr> 
   <td>组件</td> 
   <td>添加了支持</td> 
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
     <li>EMC Documentum 7.3连接器</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2007的连接器</li> 
     <li>Microsoft Sharepoint 2010的连接器</li> 
     <li>IBM Filenet 5.0的连接器</li> 
     <li>EMC Documentum 6.7连接器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>浏览器</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x on macOS</li> 
     <li>Apple Safari 11.x on iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>适用于Blackberry Z30和Q10设备的Blackberry浏览器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms应用程序<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4或更高版本</li> 
     <li>Apple iOS 10或更高版本</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX和Solaris操作系统仅适用于升级客户。
