---
title: 配置消息传送
seo-title: Configuring Messaging
description: 社区消息传送
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# 配置消息传送 {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Communities的消息传送功能允许已登录的网站访客（成员）相互发送消息，这些消息在登录到网站后即可访问。

通过在 [社区站点创建](sites-console.md).

此页面提供了有关默认配置和可能调整的信息。

有关开发人员的其他信息，请参阅 [消息传送要点](essentials-messaging.md).

## 报文传送操作服务 {#messaging-operations-service}

的 [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) 标识处理与消息相关的请求的端点、服务应用于存储消息的文件夹，以及如果消息可能包含文件附件，则允许哪些文件类型。

对于使用 [社区站点控制台](sites-console.md)，服务的实例已存在，但收件箱设置为 `/mail/community/inbox`.

### Community Messaging Operations Service {#community-messaging-operations-service}

如下所示，使用创建的站点的服务配置 [站点创建向导](sites-console.md). 通过选择配置旁边的铅笔图标，可以查看或编辑配置：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置 {#new-configuration}

要添加新配置，请选择加号“**+**&#x200B;服务名称旁的“图标：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息字段允许列表]**
指定用户可以编辑和保留的撰写消息组件的属性。 如果添加了新表单元素，则需要添加元素ID（如果需要）才能将其存储在SRP中。 默认为两个条目： 
*主题* 和 *内容*.

* **[!UICONTROL 消息框大小限制]**
每个用户消息框中的最大字节数。 默认为 
*1073741824* (1 GB)。

* **[!UICONTROL 消息计数限制]**
每个用户允许的消息总数。 值为–1表示允许无限数量的消息，但须符合消息框大小限制。 默认为 
*10000* (10k)。

* **[!UICONTROL 通知投放失败]**
如果选中此选项，则在向某些收件人发送消息失败时通知发件人。 默认为 
*已选中*.

* **[!UICONTROL 投放发件人ID失败]**
发送失败消息中显示的发送者名称。 默认为 
*failureNotifier*.

* **[!UICONTROL 失败消息模板路径]**
投放失败消息模板根的绝对路径。 默认为 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
尝试重新发送消息失败的次数。 默认为 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
尝试在发送失败时重新发送消息之间等待的秒数。 默认值为*100 *（秒）。

* **[!UICONTROL 计数更新池大小]**
用于计数更新的并发线程数。 默认为 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*必需*)相对于用户节点(/home/users/*用户名*)，用于 **`inbox`** 文件夹。 路径不得以尾随正斜杠“/”结尾。 默认为 */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*必需*)相对于用户节点(/home/users/*用户名*)，用于 **`senditems`** 文件夹。 路径不得以尾随正斜杠“/”结尾。 默认为 */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]**
如果选中，则用户能够在其邮件中添加附件。 默认为 
*已选中*.

* **[!UICONTROL batchSize.name]**
发送到大量收件人时要批量发送的消息数。 默认为 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
如果选中了supportAttachments，则此值指定所有附件允许的最大总大小（以字节为单位）。 默认为 
*104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlocklist.name]**
文件扩展名阻止列表的，前缀为“
**。**&#39;，系统将拒绝该请求。 如果未列入阻止列表，则允许使用扩展。 可以使用“**+**&#39;和&#39;**-**“ ”图标。 默认为 *默认*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*所需操作*)** 文允许列表件扩展名的，与阻止列表相反。 要允许使用除文件之外的所列入阻止列表有文件扩展名，请使用&#x200B;**-**“ ”图标，以删除单个空条目。

* **[!UICONTROL serviceSelector.name]**
(*必需*)用于调用服务的绝对路径（端点）（虚拟资源）。 所选路径的根必须包含在 *执行路径* OSGi配置的配置设置 [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)，例如 `/bin/`, `/apps/`和 `/services/`. 要为网站的消息传送功能选择此配置，此端点将作为 **`Service selector`** 值 `Message List and Compose Message components` (请参阅 [消息功能](configure-messaging.md))。 默认值为 */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
使用 
**消息字段允许列表**.

>[!CAUTION]
>
>每次 `Messaging Operations Service` 如果为编辑，则打开配置 `allowedAttachmentTypes.name` 删除后，将重新添加空条目，以配置资产。 单个空条目会有效地禁用文件附件。
>
>要允许使用除文件之外的所列入阻止列表有文件扩展名，请使用&#x200B;**-**“ ”图标（再次）在单击 **[!UICONTROL 保存]**.

## 疑难解答 {#troubleshooting}

解决问题的一种方法是启用 [调试日志中的消息。](../../help/sites-administering/troubleshooting.md)

另请参阅 [个人服务的记者和作家](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

要监视的包是 `com.adobe.cq.social.messaging`.
