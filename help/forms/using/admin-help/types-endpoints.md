---
title: 端点类型
seo-title: Types of endpoints
description: 了解不同类型的端点。
seo-description: Learn about the different types of endpoints.
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
exl-id: 7c6b9b6c-d4b5-46a8-8a6a-3b8802ac392d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 1%

---

# 端点类型 {#types-of-endpoints}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

必须配置并启用端点，才能使用服务。 端点指定如何调用服务。

>[!NOTE]
>
>在Workbench中，端点称为起点。

可以向服务添加以下类型的端点。 并非所有服务都支持所有端点：

**电子邮件：** 允许用户通过向指定的电子邮件帐户发送带有一个或多个文件附件的电子邮件来调用服务。 在配置电子邮件端点之前，必须配置所需的电子邮件帐户。 （请参阅配置电子邮件端点。）

**监视文件夹：** 允许用户通过将文件放置在文件夹中来调用服务，该文件夹以定义的间隔进行扫描。 （请参阅配置监视文件夹端点。）

**任务管理器：** 允许工作区用户调用服务。

**远程处理：** 使用Flex构建的应用程序能够使用(AEM表单已弃用)AEM Forms Remoting调用服务。 将自动为每个已激活的服务创建远程处理端点。 创建与端点同名的Flex目标，Flex客户端可以创建指向此目标的远程对象以调用相关服务上的操作。

**SOAP:** 允许使用AEM Forms编程API开发的客户端应用程序使用SOAP模式调用服务。 将为每个激活的服务自动创建SOAP端点。

**注释**: *在Adobe Acrobat或Adobe Reader中查看文档时，如果使用SOAP端点，则可以从文档安全文档中删除安全性。 有关如何在LCRM文档上禁用SOAP引入的详细信息，请参阅 [禁用文档安全文档的SOAP端点](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**EJB:** 使用使用AEM Forms编程API开发的客户端应用程序能够使用企业JavaBeans(EJB)模式调用服务。 将为每个激活的服务自动创建EJB端点。

**WSDL:** 使使用AEM表单编程API开发的客户端应用程序能够使用Web服务定义语言(WSDL)调用服务。 “核心配置”页包含一个选项，用于为AEM表单所包含的所有服务启用WSDL生成。 (请参阅配置常规AEM表单设置。)

**REST:** 可以配置在Workbench中创建的流程，以便您可以通过表示状态传输(REST)请求调用这些流程。 REST请求从HTML页面发送。 即，您可以使用REST请求直接从网页调用AEM表单进程。

电子邮件、TaskManager、监视文件夹和远程处理端点仅显示服务的特定操作。 添加这些端点需要第二个配置步骤来选择调用服务、设置配置参数以及指定输入和输出参数映射的方法。
