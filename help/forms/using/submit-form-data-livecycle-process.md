---
title: 配置AEM Forms以在JEE流程中将表单数据提交到AEM Forms
seo-title: Configuring AEM Forms to submit form data to an AEM Forms on JEE process
description: AEM Forms允许您在JEE流程中将自适应表单与AEM Forms集成，以处理表单数据。
seo-description: AEM Forms allows you to integrate adaptive forms with AEM Forms on JEE processes for processing form data.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 2%

---

# 配置AEM Forms以在JEE流程中将表单数据提交到AEM Forms {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自适应表单支持将数据提交到JEE上的AEM Forms进程，以便进一步处理。 它允许您使用提交的表单中提供的数据，在JEE上触发AEM Forms进程。 请执行以下步骤，使您的AEM Forms实例能够在JEE流程中向AEM Forms提交自适应表单：

## 配置AEM Forms服务器 {#configure-your-aem-forms-server}

请执行以下步骤，使您的AEM表单服务器能够向JEE服务器上的AEM Forms提交数据：

1. 转到AEM Web配置控制台(https://)[*主机*]:[*端口*]/system/console/configMgr。

1. 找到并单击 **AdobeLiveCycle客户端SDK配置** 组件。
1. 单击以编辑JEE服务器上AEM Forms的配置服务器URL、用户名和密码。
1. 查看设置并单击 **保存**.

![AdobeLiveCycle客户端SDK配置](assets/clientsdkconfiguration.jpg)

## 使用流程字段映射数据 {#map-data-with-process-fields}

配置AEM Forms后，将数据XML和附件从提交的表单映射到JEE流程中AEM Forms的字段。 要执行此操作：

1. 在AEM Web配置控制台中，单击以编辑 **指南LiveCycle流程定位器和发票人** 配置。
1. 指定以下参数：

   * **数据xml参数的名称** （必需）：指定JEE进程中需要处理提交数据的AEM Forms的XML属性文件。 默认值为 **dataxml**.
   * **文件附件参数的名称** （可选）：指定JEE上的AEM Forms进程需要处理的文档对象列表。 默认值为 **fileAttachmentsList**.

1. 查看设置并单击 **保存**.

![指南LiveCycle流程定位器和发票人](assets/test3.jpg)

配置完毕后，“提交到Forms Workflow”提交操作会列出JEE服务器上包含指定数据xml参数的AEM Forms进程。
