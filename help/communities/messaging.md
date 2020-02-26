---
title: 配置消息传递
seo-title: 配置消息传递
description: 社区消息
seo-description: 社区消息
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c

---


# 配置消息传递 {#configuring-messaging}

## 概述 {#overview}

AEM Communities的消息传递功能允许已登录的站点访问者（成员）相互发送消息，当登录到站点时，这些消息可供访问。

通过在社区站点创建过程中选中一个框，为社区站点启 [用消息传递](sites-console.md)。

本页提供了有关默认配置和可能调整的信息。

有关开发人员的其他信息，请参 [阅Messaging Essentials](essentials-messaging.md)。

## Messaging Operations Service {#messaging-operations-service}

[AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) (AEM Communities Messaging Operations Service)标识处理消息相关请求的端点、服务应用于存储消息的文件夹，以及如果消息可能包括文件附件，则允许使用哪些文件类型。

对于使用“社区站点” [控制台创建的社区站点](sites-console.md)，该服务的一个实例已存在，收件箱设置为 `/mail/community/inbox`。

### 社区消息处理运营服务 {#community-messaging-operations-service}

如下所示，对于使用站点创建向导创建的站点，存在服 [务的配置](sites-console.md)。 通过选择配置旁边的铅笔图标，可以查看或编辑配置：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置 {#new-configuration}

要添加新配置，请选择服务名称旁的加号“**+**”图标：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息字段白]**&#x200B;名单指定用户可编辑和保留的合成消息组件的属性。 如果添加了新的表单元素，则需要添加元素ID（如果需要）才能存储在SRP中。 默认为两个条目：主 *题**和内容*。

* **[!UICONTROL 消息框大小限]**&#x200B;制每个用户消息框中的最大字节数。 默认为 *1073741824* (1 GB)。

* **[!UICONTROL 消息计数限]**&#x200B;制每个用户允许的消息总数。 值为-1表示允许不限数量的消息，但须遵守消息框大小限制。 默认为 *10000* (10k)。

* **[!UICONTROL 通知发送失败]**&#x200B;如果选中此项，则在向某些收件人发送消息时通知发送方。 默认为选 *中*。

* **[!UICONTROL 失败发送方ID]**&#x200B;发送方名称，显示在发送失败消息中。 默认值为 *failureNotifier*。

* **[!UICONTROL 失败消息模板路径]**&#x200B;传递失败消息模板根目录的绝对路径。 默认值为 */etc/notification/messaging/default*。

* **[!UICONTROL maxRetries.name]**&#x200B;尝试重新发送失败消息的次数。 Default is *3*.

* **[!UICONTROL minWaitBetweenRetries.name在发送]**&#x200B;失败时尝试重新发送消息之间等待的秒数。 默认值是*100 *（秒）。

* **[!UICONTROL 计数更新池大小]**&#x200B;用于计数更新的并发线程数。 Default is *10*.

* **[!UICONTROL inbox.path.name]**(*必需*)用于文件夹的路径，相对于用户节点(/home/users/*username*) **`inbox`** 。 路径不能以尾随正斜杠&#39;/&#39;结束。 默认为 */mail/inbox* 。

* **[!UICONTROL sentitems.path.name]**(*必需*)用于文件夹的路径，相对于用户节点(/home/users/*username*) **`senditems`** 。 路径不能以尾随正斜杠&#39;/&#39;结束。 默认为 */mail/sentitems* 。

* **[!UICONTROL supportAttachments.name如果选]**&#x200B;中此项，用户可以向其邮件中添加附件。 默认为选 *中*。

* **[!UICONTROL batchSize.name发]**&#x200B;送到大量收件人组时要一起发送的消息数。 Default is *100*.

* **[!UICONTROL maxTotalAttachmentSize.name如果选]**&#x200B;中supportAttachments，此值将指定所有附件所允许的最大总大小（以字节为单位）。 默认 *为104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlacklist.name文件扩]**&#x200B;展名的黑名单，前缀为“**”。**&#x200B;被制度拒绝。 如果未列入黑名单，则允许扩展。 可以使用“**+**”和“**-**”图标添加或删除扩展。 默认为 *DEFAULT*。

* **[!UICONTROL allowedAttachmentTypes.name]**
   **(需&#x200B;*要操作*** )文件扩展名的白名单，与黑名单相反。 要允许除列入黑名单之外的所有文件扩展名，请使用“**-**”图标删除单个空条目。

* **[!UICONTROL serviceSelector.name]**(*必需*)从中调用服务的绝对路径（端点）（虚拟资源）。 所选路径的根必须是OSGi配置的“执行路径 *”配置设置中的一个* , [ 如、 `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)和 `/bin/``/apps/``/services/`。 要为站点的消息功能选择此配置，此端点将作为站点的 **`Service selector`** 值提供 `Message List and Compose Message components` (请参阅 [消息功能](configure-messaging.md))。 默认值为 */bin/messaging* 。

* **[!UICONTROL fieldWhitelist.name使用]**&#x200B;消 **息字段白名单**。

>[!CAUTION]
>
>每次打开配 `Messaging Operations Service` 置进行编辑时，如果已删 `allowedAttachmentTypes.name` 除，则会重新添加一个空条目以使属性可配置。 单个空条目会有效禁用文件附件。
>
>要允许除列入黑名单之外的所有文件扩展名，请在单击“保存”之前，使用“**-**”图标（再次）删除单个空条目 ****。

## 疑难解答 {#troubleshooting}

解决问题的一种方法是启用日 [志中的调试消息。](../../help/sites-administering/troubleshooting.md)

另请参 [阅个人服务的记录者和作者](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)。

要监控的包装是 `com.adobe.cq.social.messaging`。
