---
title: 使用API调用AEM Forms
seo-title: Invoking AEM Forms using APIs
description: Adobe Experience Manager Forms是基于J2EE的企业软件，它包含在共享基础架构中运行的服务。 了解如何使用客户端应用程序通过Java API、Web服务、远程处理和REST API以编程方式调用AEM Forms。
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# 使用API调用AEM Forms {#invoking-aem-forms-using-apis}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Forms是基于J2EE的企业软件，它包含在共享基础架构中运行的服务。 服务操作通常会消耗或生成文档。 通过使用AEM Forms，您可以将表单工作流与电子表单、文档安全和文档生成结合到一组集成且有凝聚力的服务中。 这些服务可以从防火墙内部和外部访问。

客户端应用程序可以使用Java API、Web服务、远程处理和REST以编程方式调用AEM Forms服务。 使用Administration Console，您可以配置服务以公开允许通过编程调用的AEM Forms服务的端点。 默认情况下，大多数服务都经过预配置，以公开远程处理、Java和Web服务端点。

您的业务需求决定了要使用的调用方法。 例如，使用Java API，您可以将AEM Forms功能集成到Java企业应用程序中，如Java实体和消息Bean。 同样，您可以使用Web服务将AEM Forms功能集成到.NET项目（或与支持Web服务标准的开发环境一起开发的其他项目）中。

服务需要运行服务容器，与Enterprise JavaBeans™(EJB)需要J2EE容器的方式类似。 AEM Forms只包含一个服务容器实施。 服务容器负责管理服务的生命周期，包括部署服务并确保所有请求都发送到正确的服务。 它还管理服务使用或生成的文档。

>[!NOTE]
>
>使用AEM表单进行编程时，不包含有关如何使用“已监视文件夹”或电子邮件调用AEM Forms的信息。
