---
title: 服务容器
seo-title: Service container
description: 进一步了解服务容器的功能。 此外，本文还介绍了以编程方式调用AEM Forms服务的不同方式。
seo-description: Learn more about the functionalities of service container. In addition, the article also describes the different ways in which you can programmatically invoke AEM Forms services.
uuid: 89f2fd3d-63d7-4b70-b335-47314441f3ec
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: dd9c0ec4-a195-4b78-8992-81d0efcc0a7e
role: Developer
exl-id: 92351e2d-1928-4bc4-aaff-d557ee09d1ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 1%

---

# 服务容器 {#service-container}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

位于服务容器（包括标准服务，如加密服务、长寿命进程和短寿命进程）中的AEM Forms服务可以使用各种提供程序（如EJB提供程序）调用。 EJB提供程序允许通过RMI/IIOP调用AEM Forms服务。 Web服务提供程序使用SOAP/HTTP和SOAP/JMS等标准将服务公开为Web服务（WSDL生成）。

下表介绍了以编程方式调用AEM Forms服务的不同方式。

<table>
 <thead>
  <tr>
   <th><p>调用方法</p></th> 
   <th><p>描述</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr>
   <td><p>远程集成</p></td> 
   <td><p>远程集成为Flex客户端提供了调用服务操作的功能。 (请参阅 <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">使用调用AEM Forms(AEM表单已弃用)AEM Forms Remoting</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>Java API</p></td> 
   <td><p>Java API可以调用AEM Forms服务。 Java API分为客户端库和Java调用API。 (请参阅 <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">使用Java API调用AEM Forms</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>Web服务</p></td> 
   <td><p>AEM Forms支持SOAP/HTTP等Web服务标准。 服务可以作为Web服务公开，WSDL符合W3C定义的Web服务标准。</p><p>可以从任何Web服务堆栈(包括.NET Framework和Sun™ Web Services SDK)中调用服务。 (请参阅 <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">使用Web服务调用AEM Forms</a>.)</p></td> 
  </tr> 
  <tr>
   <td><p>REST请求</p></td> 
   <td><p>AEM Forms支持REST请求。 可以直接从HTML页面调用服务。 (请参阅 <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">使用REST请求调用AEM Forms</a>.)</p></td> 
  </tr> 
 </tbody> 
</table>

下图直观地展示了以编程方式调用AEM Forms服务的不同方式。

>[!NOTE]
>
>除了使用AEM Forms SDK创建可调用AEM Forms服务的客户端应用程序之外，您还可以创建可部署到服务容器的组件。 例如，您可以创建一个银行组件，其中包含可在流程中使用的自定义数据类型。 即，您可以创建数据类型，例如 `com.adobe.idp.BankAccount`. 然后，您可以创建 `com.adobe.idp.BankAccount` 实例。

服务容器提供以下功能：

* 允许使用不同方法调用AEM Forms服务。 您可以通过设置端点来配置服务，以便可以使用所有方法调用该服务：远程处理、Java API、Web服务和REST。 (请参阅 [以编程方式管理端点](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* 将消息转换为称为调用请求的标准化格式。 从客户端应用程序（或其他服务）向位于服务容器中的服务发送调用请求。 调用请求包含要调用的服务的名称和执行该操作所需的数据值等信息。 许多服务都需要文档才能执行操作。 因此，调用请求通常包含文档，文档可以是PDF数据、XDP数据、XML数据等。
* 将调用请求路由到相应的服务（要调用的服务的名称是调用请求的一部分）。
* 执行诸如确定呼叫者是否具有调用指定服务操作的权限之类的任务。 调用请求必须包含有效的AEM表单用户名和密码。

   向服务发送调用请求的方法不同。 此外，还有多种方法可以将所需的输入值发送到该服务。 例如，假定您使用Java API调用需要PDF文档的服务。 相应的Java方法包含接受PDF文档的参数。 在这种情况下，参数的数据类型为 `com.adobe.idp.Document`. (请参阅 [使用Java API将数据传递到AEM Forms服务](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

   如果使用监视文件夹调用服务，则在将文件放置到已配置的监视文件夹中时，将发送调用请求。 如果使用电子邮件调用服务，则当电子邮件到达配置的收件箱中时，将向服务发送调用请求。

   一旦执行操作，服务容器就会发回调用响应。 调用响应包含操作结果等信息。 例如，如果操作修改了PDF文档，则调用响应包含修改后的PDF文档。 如果操作失败，则调用响应包含错误消息。

   可以以发送调用请求的相同方式检索调用响应。 也就是说，如果使用Java API发送调用请求，则可以使用Java API检索调用响应。 例如，假定某个操作修改了PDF文档。 您可以通过获取调用服务的Java方法的返回值来检索修改后的PDF文档。

   当调用长寿命进程时，调用响应包含与调用请求相关联的标识符值。 使用此标识符值，您可以稍后检查进程的状态。 例如，以MortgageLoan长期服务为例。 使用标识符值，您可以检查以确定该过程是否成功完成。 (请参阅 [调用以人为中心的长寿过程](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

   下图显示了一个客户端应用程序（使用Java API）调用服务。

   当客户端应用程序调用服务时，会发生三个事件：

   1. 客户端应用程序向服务发送调用请求。
   1. 服务执行在调用请求中指定的操作。
   1. 服务容器返回对客户端应用程序的调用响应。

**另请参阅**

[了解AEM Forms流程](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[使用调用AEM Forms(AEM表单已弃用)AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[使用Java API调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[使用Web服务调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[调用以人为中心的长寿过程](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[使用REST请求调用AEM Forms](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
