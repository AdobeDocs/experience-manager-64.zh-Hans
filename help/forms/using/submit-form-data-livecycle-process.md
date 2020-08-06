---
title: 将AEM Forms配置为在JEE流程中向AEM Forms提交表单数据
seo-title: 将AEM Forms配置为在JEE流程中向AEM Forms提交表单数据
description: AEM Forms允许您将自适应表单与AEM Forms整合到JEE流程中，以处理表单数据。
seo-description: AEM Forms允许您将自适应表单与AEM Forms整合到JEE流程中，以处理表单数据。
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# 将AEM Forms配置为在JEE流程中向AEM Forms提交表单数据 {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

自适应表单支持向AEM Forms提交有关JEE流程的数据，以进一步处理。 它允许您使用提交的表单中提供的数据触发JEE流程上的AEM Forms。 执行以下步骤，使您的AEM Forms实例能够在JEE流程中向AEM Forms提交自适应表单：

## 配置AEM Forms服务器 {#configure-your-aem-forms-server}

请执行以下步骤，使AEM表单服务器能够向JEE服务器上的AEM Forms提交数据：

1. 转到AEM Web配置控制台&#x200B;[*:*][*https://主机*]:port/system/console/configMgr。

1. 找到并单击 **AdobeLiveCycle客户端SDK配置组件** 。
1. 单击可编辑JEE服务器上AEM Forms的配置服务器URL、用户名和密码。
1. 查看设置，然后单击“ **保存**”。

![AdobeLiveCycle客户端SDK配置](assets/clientsdkconfiguration.jpg)

## 将数据与进程字段映射 {#map-data-with-process-fields}

配置您的AEM Forms后，将数据XML和附件从提交的表单映射到AEM FormsJEE流程中的字段。 要执行此操作：

1. 在AEM Web配置控制台中，单击以编辑指南 **LiveCycle流程定位器和调用程序** 配置。
1. 指定以下参数：

   * **数据xml参数的名称** （必填）: 指定AEM FormsJEE进程中需要处理提交数据的XML属性文件。 The default value is **dataxml**.
   * **文件附件参数的名称** （可选）: 指定JEE进程上的AEM Forms需要处理的文档对象的列表。 The default value is **fileAttachmentsList**.

1. 查看设置，然后单击“ **保存**”。

![指南LiveCycle流程货位和发票人](assets/test3.jpg)

配置完毕后，“提交到Forms Workflow”提交操作会列表AEM Forms在JEE服务器上的进程，该进程包含指定的data xml参数。
