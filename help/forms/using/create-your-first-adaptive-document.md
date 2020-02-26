---
title: 请勿发布创建您的第一个自适应文档
seo-title: 请勿发布创建您的第一个自适应文档
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 请勿发布创建您的第一个自适应文档 {#do-not-publish-create-your-first-adaptive-document}

## 用例 {#use-case}

We Finance是金融服务领域的领先组织，它提供全面和个性化的财务解决方案以满足不同客户档案的需求。

其客户的汽车保险政策即将到期，他们将向她发送一个提醒，该提醒是交互式的，包含带续订报价的PDF。 通信还包括其他信息，如忠诚度奖励和折扣优惠。

门户在Adobe AEM上运行。 Web和打印欢迎频道输出是使用自适应文档的多通道功能创建的。

在教程的结尾，您将有一个与以下内容类似的自适应文档：[ ad-1 ![](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf) ad-2创 [ 建第一个自适应文 ![](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)档教程分为几个步骤。 每个步骤本身都是一篇完整的文章。

<table> 
 <tbody>
  <tr>
   <th>您将学习</th> 
   <th>
    <ul> 
     <li>创建自适应文档和表单数据模型。</li> 
     <li>为自适应文档创建模板和主题。</li> 
     <li>使用规则编辑器构建业务规则。<br /> </li> 
     <li>发布自适应文档。 <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>先决条件</td> 
   <td>
    <ul> 
     <li>设置AEM作者实例。 </li> 
     <li>安装 AEM Forms 附加组件. 有关详细信息，请参 <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">阅安装和配置AEM表单</a>。</li> 
     <li>从数据库提供程序获取JDBC数据库驱动程序（JAR文件）。 本教程中的示例基于MySQL数据库，并使用Oracle的MySQL JDBC数据库驱动程序。 </li> 
     <li>设置包含客户数据的数据库。 数据库是创建自适应文档的必备工具。 本教程使用数据库显示AEM Forms的表单数据模型和持久性功能。 </li> 
     <li>创建／导入并启 <a href="/help/forms/using/web-channel-print-channel.md">用用于打印和Web渠道的模板</a>。</li> 
     <li>确保您有基 <a href="/help/forms/using/document-fragments.md">于FDM的文档片段</a>。</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Step 1: Create Form Data Model {#step-create-form-data-model}

表单数据模型允许将自适应文档连接到不同的数据源。 例如，AEM用户配置文件、RESTful web服务、基于SOAP的Web服务、OData服务和关系数据库。 表单数据模型是业务实体和在互联数据源中可用服务的统一数据表示模式。 您可以将表单数据模型与自适应文档结合使用以从连接的数据源检索数据。 有关表单数据模型的详细信息，请参 [阅AEM表单数据集成](/help/forms/using/data-integration.md)。

目标：

* 将数据库实例(Microsoft Dynamics)配置为数据源
* 使用Microsoft Dynamics作为数据源创建表单数据模型
* 将数据模型对象添加到表单数据模型
* 为表单数据模型配置读写服务
* 测试表单数据模型和配置有测试数据的服务

## 第2步：创建自适应文档 {#step-create-an-adaptive-document}

客户通信集中化和管理安全、个性化和交互式通信的创建、汇编和交付，如业务通信、信函、文档、声明、利益声明、财富管理招股说明书、营销邮件、帐单和欢迎工具包。

使用自适应文档，您可以创建具有吸引力、响应式、动态和适应性的客户沟通。 AEM Forms提供拖放式WYSIWYG编辑器以创建自适应文档。

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

目标：

* 基于表单数据模型创建自适应文档的打印和Web输出。
* 自适应表单的布局字段以向客户显示信息
* 创建规则以检索和显示从表单数据模型到自适应文档的信息。

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 第3步：将规则应用于自适应文档字段（仅限Web渠道） {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

自适应文档提供了一个编辑器，用于编写自适应文档对象的规则。 这些规则根据预设条件和用户对文档的操作定义对文档对象触发的操作。 它有助于确保自适应文档Web版本的准确性并加快用户体验。 有关自适应文档规则和规则编辑器的详细信息，请参阅规 [则编辑器](/help/forms/using/rule-editor.md)。

目标：

* 创建规则并将其应用于自适应文档的Web渠道字段
* 使用规则触发Web渠道中的文档数据模型服务

## 第4步：设置自适应文档的样式（仅限Web通道） {#step-style-the-adaptive-document-web-channel-only}

自适应文档提供了一个编辑器，用于为自适应文档创建主题和联机样式。 主题包含组件和面板的样式详细信息，您可以在不同文档的Web渠道中重用主题。 样式包括背景颜色、状态颜色、透明度、对齐方式和大小等属性。 将主题应用于文档时，指定的样式会反映在文档的相应组件上。 有关详细信息，请参阅 [主题](/help/forms/using/themes.md)。

目标：

* 为自适应文档Web通道创建主题
* 将主题应用于自适应文档Web通道
* 验证自适应文档Web频道在移动设备和桌面上的显示效果

## 第5步：发布自适应文档 {#step-publish-the-adaptive-document}

创建完自适应文档后，您需要发布它，以便它在发布实例中可用，在发布实例中，代理可以使用自适应文档创建基于它的通信实例。

要发布自适应文档，文档作者需要具有所需的权限。
