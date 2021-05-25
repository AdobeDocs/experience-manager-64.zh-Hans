---
title: 不发布创建您的第一个自适应文档
seo-title: 不发布创建您的第一个自适应文档
description: 不发布
seo-description: 不发布
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: 7ec0cd95417c015565fa6e07c753c4ac6df35cdb
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# 不发布创建您的第一个自适应文档{#do-not-publish-create-your-first-adaptive-document}

## 用例 {#use-case}

We Finance是金融服务领域的领先组织，提供全面和个性化的财务解决方案，以满足不同客户档案的要求。

他们客户的一份汽车保险保单即将到期，他们将向她发送一个提醒，该提醒是交互式的，包含PDF，并附有续订报价。 通信还包括其他信息，如忠诚度奖励和折扣优惠。

门户在AdobeAEM上运行。 Web和打印欢迎渠道输出是使用自适应文档的多渠道功能创建的。

在教程结束时，您将拥有一个与以下内容类似的自适应文档：
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)创建第一个自适应文档教程分为几个步骤。 每个步骤本身就是一个完整的文章。

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
     <li>设置AEM创作实例。 </li> 
     <li>安装 AEM Forms 附加组件. 有关详细信息，请参阅<a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">安装和配置AEM Forms</a>。</li> 
     <li>从数据库提供程序获取JDBC数据库驱动程序（JAR文件）。 本教程中的示例以MySQL数据库为基础，使用Oracle的MySQL JDBC数据库驱动程序。 </li> 
     <li>设置包含客户数据的数据库。 数据库对于创建自适应文档至关重要。 本教程使用数据库来显示AEM Forms的表单数据模型和持久性功能。 </li> 
     <li>创建/导入并启用<a href="/help/forms/using/web-channel-print-channel.md">用于打印和Web渠道的模板</a>。</li> 
     <li>确保您具有基于FDM</a>的<a href="/help/forms/using/document-fragments.md">文档片段。</a></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 步骤1:创建表单数据模型{#step-create-form-data-model}

表单数据模型允许将自适应文档连接到不同的数据源。 例如，AEM用户配置文件、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库。 表单数据模型是业务实体和服务在连接数据源中提供的统一数据表示模式。 您可以将表单数据模型与自适应文档结合使用，以从连接的数据源中检索数据。 有关表单数据模型的更多信息，请参阅[AEM Forms数据集成](/help/forms/using/data-integration.md)。

目标：

* 将数据库实例(Microsoft Dynamics)配置为数据源
* 使用Microsoft Dynamics作为数据源创建表单数据模型
* 添加数据模型对象以形成数据模型
* 为表单数据模型配置读写服务
* 测试表单数据模型和配置有测试数据的服务

## 步骤2:创建自适应文档{#step-create-an-adaptive-document}

客户通信部门可以集中管理安全、个性化和交互式信函的创建、编排和交付，例如商务信函、信件、文档、报表、福利通知、财富管理招股说明书、营销邮件、账单和欢迎资料包。

使用自适应文档，您可以创建具有吸引力、响应性、动态和自适应性的客户通信。 AEM Forms提供拖放WYSIWYG编辑器以创建自适应文档。

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

目标：

* 基于表单数据模型创建自适应文档的打印和Web输出。
* 向客户显示信息的自适应表单的布局字段
* 创建规则以从表单数据模型到自适应文档检索和显示信息。

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## 步骤3:将规则应用于自适应文档字段（仅限Web渠道）{#step-apply-rules-to-adaptive-document-fields-web-channel-only}

自适应文档提供了一个编辑器，用于编写自适应文档对象的规则。 这些规则根据文档的预设条件和用户操作定义要在文档对象上触发的操作。 它有助于确保自适应文档Web版本的准确性并加快用户体验。 有关自适应文档规则和规则编辑器的更多信息，请参阅[规则编辑器](/help/forms/using/rule-editor.md)。

目标：

* 创建规则并将其应用于自适应文档的Web渠道字段
* 使用规则在Web渠道中触发文档数据模型服务

## 步骤4:设置自适应文档的样式（仅限Web渠道）{#step-style-the-adaptive-document-web-channel-only}

自适应文档提供了一个编辑器，用于为自适应文档创建主题和内嵌样式。 主题包含组件和面板的样式详细信息，您可以在不同文档的Web渠道中重复使用该主题。 样式包括背景颜色、状态颜色、透明度、对齐方式和大小等属性。 将主题应用于文档时，指定的样式将反映在文档的相应组件上。 有关更多信息，请参阅[主题](/help/forms/using/themes.md)。

目标：

* 为自适应文档Web渠道创建主题
* 将主题应用于自适应文档Web渠道
* 验证在移动设备和桌面上自适应文档Web渠道的外观

## 步骤5:发布自适应文档{#step-publish-the-adaptive-document}

创建完自适应文档后，您需要将其发布，以供在发布实例上使用，代理可在该实例中使用自适应文档来创建基于该文档的通信实例。

要发布自适应文档，文档作者需要拥有所需的权限。
