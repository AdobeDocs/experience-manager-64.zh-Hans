---
title: 配置消息传送
seo-title: 配置消息传送
description: 社区消息传送
seo-description: 社区消息传送
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Administrator
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 配置消息{#configuring-messaging}

## 概述 {#overview}

AEM Communities的消息传送功能允许已登录的网站访客（成员）相互发送消息，这些消息在登录到网站后即可访问。

在[社区站点创建](sites-console.md)期间选中框，可为社区站点启用消息传送。

此页面提供了有关默认配置和可能调整的信息。

有关开发人员的其他信息，请参阅[Messaging Essentials](essentials-messaging.md)。

## 消息传送操作服务{#messaging-operations-service}

[AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl)标识了处理与消息相关请求的端点、服务应用于存储消息的文件夹，以及如果消息可能包含文件附件，则允许使用哪些文件类型。

对于使用[Communities Sites控制台](sites-console.md)创建的社区站点，服务的实例已存在，收件箱设置为`/mail/community/inbox`。

### 社区消息传送操作服务{#community-messaging-operations-service}

如下所示，对于使用[站点创建向导](sites-console.md)创建的站点，该服务的配置存在。 通过选择配置旁边的铅笔图标，可以查看或编辑配置：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置{#new-configuration}

要添加新配置，请选择服务名称旁边的加号“**+**”图标：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息字段]**
允许列表指定撰写消息组件用户可以编辑和保留的属性。如果添加了新表单元素，则需要添加元素ID（如果需要）才能将其存储在SRP中。 默认为两个条目： 
** 主题和 *内容*。

* **[!UICONTROL 消息框大]**
小限制每个用户消息框中的最大字节数。默认为 
*1073741824* (1 GB)。

* **[!UICONTROL 消息计]**
数限制每个用户允许的消息总数。值为–1表示允许无限数量的消息，但须符合消息框大小限制。 默认为 
*1000* (10k)。

* **[!UICONTROL 通知投放]**
失败如果选中此选项，则在向某些收件人发送消息失败时通知发送者。默认为 
*已选中*.

* **[!UICONTROL 失败投放发件]**
人id发送失败邮件中显示的发件人的名称。默认为 
*failureNotifier*。

* **[!UICONTROL 失败消息模]**
板路径投放失败消息模板根的绝对路径。默认为 
*/etc/notification/messaging/default*。

* **[!UICONTROL maxRetries.]**
name尝试重新发送消息失败的次数。默认为 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
尝试在发送失败时重新发送消息之间等待的秒数。默认值为*100 *（秒）。

* **[!UICONTROL 计数更新池]**
大小用于计数更新的并发线程数。默认为 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*必需*)相对于用户节点(/home/users/*username*)用于文件夹的路径( **`inbox`** /)。路径不得以尾随正斜杠“/”结尾。 默认值为&#x200B;*/mail/inbox* 。

* **[!UICONTROL sentitems.path.name]**
(
*必需*)相对于用户节点(/home/users/*username*)用于文件夹的路径( **`senditems`** /)。路径不得以尾随正斜杠“/”结尾。 默认值为&#x200B;*/mail/sentitems* 。

* **[!UICONTROL supportAttachments.]**
name如果选中此选项，则用户可以在其邮件中添加附件。默认为 
*已选中*.

* **[!UICONTROL batchSize.]**
name发送到大量收件人时要一起发送的消息数。默认为 
*100*。

* **[!UICONTROL maxTotalAttachmentSize.name如果]**
选中supportAttachments，此值将指定所有附件所允许的最大总大小（以字节为单位）。默认为 
*104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlocklist.]**
name文件阻止列表扩展名的，前缀为“
**。**&#39;，系统将拒绝该请求。如果未列入阻止列表，则允许使用扩展。 可以使用“**+**”和“**-**”图标添加或删除扩展。 默认值为&#x200B;*DEFAULT*。

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*需要操作*)** 文件允许列表扩展名的，与阻止列表相反。要允许除已的条目之外的所列入阻止列表有文件扩展名，请使用“**-**”图标删除单个空条目。

* **[!UICONTROL serviceSelector.name]**
(*必需*)用于调用服务的绝对路径（端点）（虚拟资源）。所选路径的根必须包含在OSGi配置[ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)的&#x200B;*执行路径*&#x200B;配置设置中，例如`/bin/`、`/apps/`和`/services/`。 要为站点的消息传送功能选择此配置，此端点将作为`Message List and Compose Message components`的&#x200B;**`Service selector`**&#x200B;值提供（请参阅[消息功能](configure-messaging.md)）。 默认值为&#x200B;*/bin/messaging* 。

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**消息字段允许列表**。

>[!CAUTION]
>
>每次打开`Messaging Operations Service`配置进行编辑时，如果删除了`allowedAttachmentTypes.name`，则会重新添加一个空条目，以便对属性进行配置。 单个空条目会有效地禁用文件附件。
>
>要允许所有文件扩展名(列入阻止列表的扩展名除外)，请使用“**-**”图标（再次）在单击&#x200B;**[!UICONTROL Save]**&#x200B;之前删除单个空条目。

## 疑难解答 {#troubleshooting}

解决问题的一种方法是在日志中启用[调试消息。](../../help/sites-administering/troubleshooting.md)

另请参阅[个人服务的记录器和写入器](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)。

要监视的包为`com.adobe.cq.social.messaging`。
