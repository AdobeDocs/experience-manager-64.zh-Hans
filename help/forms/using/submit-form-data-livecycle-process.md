---
title: 配置AEM Forms以在JEE流程中将表单数据提交到AEM Forms
seo-title: 配置AEM Forms以在JEE流程中将表单数据提交到AEM Forms
description: AEM Forms允许您在JEE流程中将自适应表单与AEM Forms集成，以处理表单数据。
seo-description: AEM Forms允许您在JEE流程中将自适应表单与AEM Forms集成，以处理表单数据。
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Administrator
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 将AEM Forms配置为在JEE进程{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}上将表单数据提交到AEM Forms

自适应表单支持将数据提交到JEE上的AEM Forms进程，以便进一步处理。 它允许您使用提交的表单中提供的数据，在JEE上触发AEM Forms进程。 请执行以下步骤，使您的AEM Forms实例能够在JEE流程中向AEM Forms提交自适应表单：

## 配置AEM Forms服务器{#configure-your-aem-forms-server}

请执行以下步骤，使您的AEM表单服务器能够向JEE服务器上的AEM Forms提交数据：

1. 转到位于https://[*host*]&#x200B;的AEM Web配置控制台：[*port*]/system/console/configMgr。

1. 找到并单击&#x200B;**AdobeLiveCycle客户端SDK配置**&#x200B;组件。
1. 单击以编辑JEE服务器上AEM Forms的配置服务器URL、用户名和密码。
1. 查看设置并单击&#x200B;**Save**。

![AdobeLiveCycle客户端SDK配置](assets/clientsdkconfiguration.jpg)

## 使用进程字段{#map-data-with-process-fields}映射数据

配置AEM Forms后，将数据XML和附件从提交的表单映射到JEE流程中AEM Forms的字段。 要执行此操作：

1. 在AEM Web配置控制台中，单击以编辑&#x200B;**指南LiveCycle流程定位器和调用程序**&#x200B;配置。
1. 指定以下参数：

   * **数据xml参数的名称** （必需）：指定JEE进程中需要处理提交数据的AEM Forms的XML属性文件。默认值为&#x200B;**dataxml**。
   * **文件附件参数的名称** （可选）：指定JEE上的AEM Forms进程需要处理的文档对象列表。默认值为&#x200B;**fileAttachmentsList**。

1. 查看设置并单击&#x200B;**Save**。

![指南LiveCycle流程定位器和发票人](assets/test3.jpg)

配置完毕后，“提交到Forms Workflow”提交操作会列出JEE服务器上包含指定数据xml参数的AEM Forms进程。
