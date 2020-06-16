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
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# 配置消息传递 {#configuring-messaging}

## 概述 {#overview}

AEM Communities的消息传递功能允许登录的站点访客（成员）相互发送消息，当登录到站点时，这些消息可供访问。

通过在社区站点创建过程中选中一个框，为社区站 [点启用消息](sites-console.md)。

本页提供了有关默认配置和可能调整的信息。

有关开发人员的其他信息，请参 [阅Messaging Essentials](essentials-messaging.md)。

## Messaging Operations Service {#messaging-operations-service}

AEM Communities [消息传递操作服务](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) (Messaging Operations Service)标识处理与消息相关请求的端点、服务应用于存储消息的文件夹，以及如果消息可能包括文件附件，允许哪些文件类型。

对于使用“社区站点” [控制台创建的社区](sites-console.md)站点，已存在服务实例，收件箱设置为 `/mail/community/inbox`。

### Community Messaging Operations Service {#community-messaging-operations-service}

如下所示，对于使用站点创建向导创建的站点，存 [在服务配置](sites-console.md)。 通过选择配置旁的铅笔图标，可以查看或编辑配置：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置 {#new-configuration}

要添加新配置，请选择服务&#x200B;**名**&#x200B;称旁的加号“+”图标：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息字段允]**&#x200B;许列表指定合成消息组件的属性，用户可以编辑和保留这些属性。 如果添加了新的表单元素，则需要添加元素ID（如果需要）才能存储在SRP中。 默认为两个条目： *主题* 和 *内容*。
**[!UICONTROL 消息框大小限]**&#x200B;制每个用户消息框中的最大字节数。 默认 *为1073741824* (1 GB)。**

* **[!UICONTROL 消息计数]**&#x200B;限制每个用户允许的消息总数。 值为-1表示允许不限数量的消息，但需遵守消息框大小限制。 默认 *值为* 10000(10k)。
**[!UICONTROL 通知投放失败]**&#x200B;如果选中，则在消息投放失败到某些收件人时通知发送方。 默认为选 *中*。*

* **[!UICONTROL 失败投放发送]**&#x200B;者ID投放失败消息中显示的发送者名称。 默认值为 *failureNotifier*。
**[!UICONTROL 失败消息模板]**&#x200B;路径投放失败消息模板根的绝对路径。 默认 *值为/etc/notification/messaging/default*。*

* **[!UICONTROL maxRetries.name]**&#x200B;尝试重新发送失败消息的次数。 Default is *3*.
**[!UICONTROL minWaitBetweenRetries.name在]**&#x200B;尝试重新发送邮件失败后等待的秒数。 默认值为*100 *（秒）。*

* **[!UICONTROL 计数更新池大小]**&#x200B;用于计数更新的并发线程数。 Default is *10*.
**[!UICONTROL inbox.path.name]**(*必需*)用于文件夹的相对于用户节点(/home/users/*username*)的路 **`inbox`** 径。 路径不能以尾随正斜杠“/”结束。 默认为 */mail/inbox* 。*

* **[!UICONTROL sentitems.path.name]**(*必需*)用于文件夹的相对于用户节点(/home/users/*username*)的路 **`senditems`** 径。 路径不能以尾随正斜杠“/”结束。 默认为 */mail/sentitems* 。
**[!UICONTROL supportAttachments.name]**&#x200B;如果选中，用户可以向邮件中添加附件。 默认为选 *中*。*

* **[!UICONTROL batchSize.name]**&#x200B;发送到大量收件人时要一起发送的消息数。 Default is *100*.
**[!UICONTROL maxTotalAttachmentSize.name如果选]**&#x200B;中supportAttachments，此值将指定所有附件所允许的最大总大小（以字节为单位）。 默认 *为104857600* (100 MB)。*

* **[!UICONTROL attachmentTypeAllowlist.name]**&#x200B;文件扩展名的块列表，前缀为&#39;**。**&#x200B;被制度拒绝。 如果未被阻止，则允许扩展。 可以使用“+”和“-**”**&#x200B;图标添加&#x200B;**或删除扩**&#x200B;展。 默认值 *为DEFAULT*。

* **[!UICONTROL allowedAttachmentTypes.name]**

**(*需要操作*)文件扩展名的允许列表** ，与blocklist相反。 要允许除那些被阻止的条目外的所有文件扩展名，请&#x200B;**使用**“-”图标删除单个空条目。

* **[!UICONTROL serviceSelector.name]**(*必需*)从中调用服务的绝对路径（端点）（虚拟资源）。 所选路径的根必须是OSGi配置的“执 *行路径* ”配置设置中的一个 [ 根， `Apache Sling Servlet/Script Resolver and Error Handler`[#$tu39]如、、 `/bin/`和 `/apps/``/services/`等。 要为站点的消息功能选择此配置，此端点将作为站点 **`Service selector`** 的值提供 `Message List and Compose Message components` (请参 [阅消息功能](configure-messaging.md))。 默认值 *为/bin/messaging* 。


* 


* 


* 


* 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeAllowlist.name]**
A blocklist of file extensions, prefixed with &#39;
**.**&#39;, that will be rejected by the system. If not blocklisted, then the extension is allowed. Extensions may be added or removed using the &#39;**+**&#39; and &#39;**-**&#39; icons. Default is *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Action Required*)** An allowlist of file extensions, the opposite of the blocklist. To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to remove the single empty entry.

* **[!UICONTROL serviceSelector.name]**
(*Required*) An absolute path (endpoint) through which the service is invoked (a virtual resource). The root of the path chosen must be one included in the *Execution Paths* configuration setting of OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`-ERR:REF-NOT-FOUND-, such as `/bin/`, `/apps/`, and `/services/`. To select this configuration for a site&#39;s messaging feature, this endpoint is provided as the **`Service selector`** value for the `Message List and Compose Message components` (see [Message Feature](configure-messaging.md)). The default is */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Use 
**Message Fields Allowlist**.

>[!CAUTION]
>
>Each time a `Messaging Operations Service` configuration is opened for edit, if `allowedAttachmentTypes.name` had been removed, an empty entry is re-added to make the property configurable. A single empty entry effectively disables file attachments.
>
>To allow all file extensions, except for those blocklisted, use the &#39;**-**&#39; icon to (again) remove the single empty entry before clicking **[!UICONTROL Save]**.

## Troubleshooting {#troubleshooting}

One way to troubleshoot problems is to enable [debugging messages in the log.](../../help/sites-administering/troubleshooting.md)

See also [Loggers and Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

The package to monitor is `com.adobe.cq.social.messaging`.
