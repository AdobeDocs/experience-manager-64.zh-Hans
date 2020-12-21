---
title: 不发布创建您的第一个自适应文档
seo-title: 不发布创建您的第一个自适应文档
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 请勿发布创建您的第一个自适应文档{#do-not-publish-create-your-first-adaptive-document}

## 用例 {#use-case}

We Finance是金融服务领域的领先组织，它优惠全面和个性化的财务解决方案以满足不同客户用户档案的需求。

其客户的汽车保险政策即将过期，他们将向她发送提醒，该提醒是交互式的，包含带续订报价的PDF。 通信还包括其他信息，如忠诚度奖励和折扣优惠。

门户在AdobeAEM上运行。 Web和打印欢迎渠道输出是使用自适应文档的多渠道功能创建的。

在教程的末尾，您将有一个与以下内容类似的自适应文档:
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)创建您的第一个自适应文档教程分为几个步骤。 每个步骤本身都是一篇完整的文章。

<table> 
 <tbody>
  <tr>
   <th>您将学习</th> 
   <th>
    <ul> 
     <li>创建自适应文档和表单数据模型。</li> 
     <li>为自适应文档创建模板和主题。</li> 
     <li>使用规则编辑器构建业务规则。<br /> </li> 
     <li>发布自适应文档。<br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>先决条件</td> 
   <td>
    <ul> 
     <li>设置AEM作者实例。 </li> 
     <li>安装 AEM Forms 附加组件. 有关详细信息，请参阅<a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">安装和配置AEM Forms</a>。</li> 
     <li>从数据库提供程序获取JDBC数据库驱动程序（JAR文件）。 本教程中的示例基于MySQL数据库，并使用Oracle的MySQL JDBC数据库驱动程序。 </li> 
     <li>设置包含客户数据的数据库。 数据库是创建自适应文档的必备工具。 本教程使用数据库来显示AEM Forms的表单数据模型和持久性功能。 </li> 
     <li>创建／导入并启用<a href="/help/forms/using/web-channel-print-channel.md">用于打印和Web渠道的模板</a>。</li> 
     <li>确保具有基于FDM</a>的<a href="/help/forms/using/document-fragments.md">文档片段。</a></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 第1步：创建表单数据模型{#step-create-form-data-model}

表单文档模型允许将自适应数据连接到不同的数据源。 例如，AEM用户用户档案、RESTful Web服务、基于SOAP的Web服务、OData服务和关系型数据库。 表单数据模型是业务实体和服务在互联数据源中的统一数据表示模式。 您可以将表单数据模型与自适应文档结合使用，从连接的数据源检索数据。 有关表单数据模型的详细信息，请参阅[AEM Forms数据集成](/help/forms/using/data-integration.md)。

目标：

* 将数据库实例(Microsoft Dynamics)配置为数据源
* 使用Microsoft Dynamics作为数据源创建表单数据模型
* 将数据模型对象添加到表单数据模型
* 为表单数据模型配置读写服务
* 测试表单数据模型和配置的服务以及测试数据

## 第2步：创建自适应文档{#step-create-an-adaptive-document}

客户通信部负责集中管理安全、个性化和交互式通信的创建、汇编和投放，如业务通信、信件、文档、声明、利益声明、财富管理招股书、营销邮件、帐单和欢迎工具包。

使用自适应文档，您可以创建具有吸引力、响应迅速、动态和适应性的客户通信。 AEM Forms提供拖放式WYSIWYG编辑器以创建自适应文档。

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

目标：

* 根据表单文档模型创建自适应打印和Web输出。
* 自适应表单的布局字段，用于向客户显示信息
* 创建规则，从表单数据模型检索和显示信息到自适应文档。

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 第3步：将规则应用于自适应文档字段(仅限Web渠道){#step-apply-rules-to-adaptive-document-fields-web-channel-only}

自适应文档为自适应文档对象提供了编写规则的编辑器。 这些规则根据预设条件和用户对文档的操作定义对文档对象触发的操作。 它有助于确保自适应文档Web版本的准确性并加快用户体验。 有关自适应文档规则和规则编辑器的详细信息，请参阅[规则编辑器](/help/forms/using/rule-editor.md)。

目标：

* 创建规则并将其应用于自适应文档的Web渠道字段
* 在Web文档中使用规则触发渠道数据模型服务

## 第4步：设置自适应文档的样式(仅限Web渠道){#step-style-the-adaptive-document-web-channel-only}

自适应文档提供一个编辑器，用于为自适应文档和内嵌样式创建主题。 主题包含组件和面板的样式详细信息，您可以在不同渠道的Web文档上重用主题。 样式包括背景颜色、状态颜色、透明度、对齐方式和大小等属性。 将主题应用于文档时，指定的样式会反映在文档的相应组件上。 有关详细信息，请参阅[主题](/help/forms/using/themes.md)。

目标：

* 为自适应文档Web渠道创建主题
* 将主题应用于自适应文档Web渠道
* 验证移动设备和桌面上自适应文档Web渠道的显示效果

## 第5步：发布自适应文档{#step-publish-the-adaptive-document}

创建完自适应文档后，您需要将其发布，以便在发布实例中可用，在发布实例中，代理可以使用自适应文档创建基于该自适应数据的通信实例。

要发布自适应文档,文档作者需要具有所需的权限。
