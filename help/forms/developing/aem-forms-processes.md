---
title: 了解AEM Forms流程
seo-title: Understanding AEM Forms Processes
description: 了解如何使用AEM Forms业务流程实现操作自动化。 激活流程以创建服务，以便您可以像其他服务一样调用它。 流程可以是短期的，也可以是长期的。
seo-description: Learn how to use AEM Forms business processes to automate operations. Activate the processes to create a service so that you can invoke it like other services. Processes can be short-lived or long-lived.
uuid: 7cbebe7d-f222-42fa-8eb6-d2443458a791
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: ac9fe461-63e7-442b-bd1c-eb9576ef55aa
role: Developer
exl-id: 0ae0ddbf-ded6-4494-bf94-bf6cf7f1fd46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---

# 了解AEM Forms流程 {#understanding-aem-forms-processes}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

一个常见用例是，一组AEM Forms服务要在单个文档上运行。 您可以通过使用Workbench创建流程，将请求发送到服务容器。 流程表示您正在实现自动化的业务流程。 有关创建流程的信息，请参阅 [使用Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

一旦某个进程被激活，它就会成为一项服务，可以像其他服务一样被调用。 标准服务（如加密服务）与源自进程的服务之间的一个区别是，后者有一个操作可执行许多操作。 相比之下，标准服务有许多操作。 每个操作通常执行一个操作，例如将策略应用于文档或对文档进行加密。

流程可以是短期的，也可以是长期的。 短期进程是同步执行的操作，在从中调用该进程的同一执行线程上执行。 短期操作与大多数编程语言中的标准行为类似，在这些语言中，客户端应用程序调用方法并等待返回值。

但是，在某些情况下，由于以下因素，无法同步完成进程：

* 流程可以跨越大量时间。
* 流程可以跨组织边界。
* 进程需要外部输入才能完成。 例如，假设某个表单被发送到不在办公室的经理。 在这种情况下，在管理器返回并填写表单之前，该过程不会完成。

   这些类型的进程称为长寿命进程。 可以异步执行长时间的过程，允许系统在资源允许的情况下进行交互，并允许跟踪和监视操作。 在调用长寿命进程时，AEM Forms会创建调用标识符值，作为跟踪长寿命进程状态的记录的一部分。 记录存储在AEM Forms数据库中。 您可以在不再需要长期处理记录时清除这些记录。

>[!NOTE]
>
>AEM Forms在调用短期流程时不会创建记录。

使用调用标识符值，可以跟踪长生命周期进程的状态。 例如，您可以使用进程调用标识符值执行进程管理器操作，如终止正在运行的进程实例。

**短暂的流程示例**

下图是一个名为 *MyApplication/EncryptDocument*.

>[!NOTE]
>
>此过程不基于现有的AEM Forms进程。 要遵循讨论如何调用此过程的代码示例，请创建一个名为 `MyApplication/EncryptDocument` 使用Workbench。 (请参阅 [使用Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

在调用此短暂的进程时，它会执行以下操作：

1. 获取作为输入值传递给流程的不安全PDF文档。
1. 使用密码加密PDF文档。 此流程的输入参数名称为 `inDoc` 数据类型为文档。
1. 将密码加密的PDF文档作为PDF文件保存到本地文件系统。 此过程会将加密的PDF文档作为输出值返回。 此进程的输出参数的名称为 `outDoc` 数据类型为文档。

   此过程在从中调用该进程的同一执行线程上同步完成。 这个短暂的过程的名称是 `MyApplication/EncryptDocument`它的操作是 `invoke`.

   >[!NOTE]
   >
   >通常，短期流程包含三个以上的操作。 您可以使用Workbench创建流程。 (请参阅 [使用Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *使用AEM表单进行编程*&#x200B;介绍以下可通过编程方式调用此短暂流程的方式：

   * [使用AEM Forms Remoting通过传递不安全的文档来调用短暂的进程](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) (使用Flex应用程序)
   * [使用调用API调用短暂的进程](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) （Java调用API）
   * [使用Base64编码调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) （web服务示例）
   * [使用MTOM调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) （web服务示例）
   * [使用SwaRef调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref) （web服务示例）
   * [通过HTTP使用BLOB数据调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http) （web服务示例）
   * [使用DIME调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime) （web服务示例）
   * [使用REST调用MyApplication/EncryptDocument进程](/help/forms/developing/invoking-aem-forms-using-rest.md)

**长期处理示例**

下图是一个长期使用的过程的示例。

申请人提交贷款表时，将调用此流程。 在贷款官员批准或拒绝贷款请求之前，该过程无法完成。 这个长期使用的流程的名称是* FirstAppSolution/PreLoanProcess *，其操作是 `invoke_Async`. 必须异步调用此进程。 有关以编程方式调用此长生命周期流程的信息，请参阅 [调用以人为中心的长寿过程](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>此过程可通过按照 [创建您的第一个AEM Forms应用程序](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).
