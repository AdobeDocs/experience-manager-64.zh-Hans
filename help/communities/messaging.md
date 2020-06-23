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
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
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

* **[!UICONTROL 消息字段允]**&#x200B;许列表指定合成消息组件的属性，用户可以编辑和保留这些属性。 如果添加了新的表单元素，则需要添加元素ID（如果需要）才能存储在SRP中。 默认为两个条目： ****

* *主题* 和 *内容*。**

* **[!UICONTROL 消息框大小限]**&#x200B;制每个用户消息框中的最大字节数。 默认为 **

* *1073741824* (1 GB)。]****

* **[!UICONTROL 消息计数]**&#x200B;限制每个用户允许的消息总数。 值为-1表示允许不限数量的消息，但需遵守消息框大小限制。 默认为 **

* *10000* (10k)。]****

* **[!UICONTROL 通知投放失败]**&#x200B;如果选中，则在消息投放失败到某些收件人时通知发送方。 默认为 **

* *已选中*.]**

* **[!UICONTROL 失败投放发送]**&#x200B;者ID投放失败消息中显示的发送者名称。 默认为 **

* *failure通告程序*。]********`inbox`****

* **[!UICONTROL 失败消息模板]**&#x200B;路径投放失败消息模板根的绝对路径。 默认为 ******`senditems`****

* */etc/notification/messaging/default*。]****

* **[!UICONTROL maxRetries.name]**&#x200B;尝试重新发送失败消息的次数。 默认为 **

* *3*.]****

* **[!UICONTROL minWaitBetweenRetries.name在]**&#x200B;尝试重新发送邮件失败后等待的秒数。 默认值为*100 *（秒）。**************

* **[!UICONTROL 计数更新池大小]**&#x200B;用于计数更新的并发线程数。 默认为    *10*.*******

* **[!UICONTROL inbox.path.name]**(****[`Apache Sling Servlet/Script Resolver and Error Handler`-ERR:REF-NOT-FOUND-`/bin/``/apps/``/services/`**`Service selector`**`Message List and Compose Message components`[](configure-messaging.md)**

* 

>
>
>
>
>

## 






