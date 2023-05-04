---
title: 配置电子邮件通知
seo-title: Configuring Email Notification
description: 了解如何在AEM中配置电子邮件通知。
seo-description: Learn how to configure Email Notification in AEM.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
exl-id: ea12035c-09b6-4197-ab23-c27fe71e7432
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 2%

---

# 配置电子邮件通知{#configuring-email-notification}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM会向以下用户发送电子邮件通知：

* 已订阅页面事件，例如修改或复制。 的 [通知收件箱](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) 部分介绍如何订阅此类事件。

* 已订阅论坛活动。
* 必须在工作流中执行步骤。 的 [参与者步骤](/help/sites-developing/workflows-step-ref.md#participant-step) 部分介绍如何在工作流中触发电子邮件通知。

先决条件：

* 用户需要在其配置文件中定义有效的电子邮件地址。
* 的 **Day CQ Mail Service** 需要正确配置。

当用户收到通知时，他会收到一封电子邮件，其语言为其个人资料中定义的语言。 每种语言都有其自己的可自定义的模板。 可以为新语言添加新的电子邮件模板。

>[!NOTE]
>
>使用AEM时，可通过多种方法来管理此类服务的配置设置；请参阅 [配置OSGi](/help/sites-deploying/configuring-osgi.md) 以了解更多详细信息和建议的实践。

## 配置邮件服务 {#configuring-the-mail-service}

要使AEM能够发送电子邮件，请 **Day CQ Mail Service** 需要正确配置。 您可以在Web控制台中查看配置。 使用AEM时，可通过多种方法来管理此类服务的配置设置；请参阅 [配置OSGi](/help/sites-deploying/configuring-osgi.md) 以了解更多详细信息和建议的实践。

以下约束适用：

* 的 **SMTP服务器端口** 必须为25或更高。

* 的 **SMTP服务器主机名** 不得为空。
* 的 **“发件人”地址** 不得为空。

为帮助您调试 **Day CQ Mail Service**，您可以查看服务的日志：

`com.day.cq.mailer.DefaultMailService`

配置在Web控制台中如下所示：

![chlimage_1-276](assets/chlimage_1-276.png)

## 配置电子邮件通知渠道 {#configuring-the-email-notification-channel}

订阅页面或论坛事件通知时，发件人的电子邮件地址会设置为 `no-reply@acme.com` 默认情况下。 您可以通过配置 **通知电子邮件渠道** 服务。

要配置发件人的电子邮件地址，请添加 `sling:OsgiConfig` 节点添加到存储库。 使用以下过程直接使用CRXDE Lite添加节点：

1. 在CRXDE Lite中，添加名为 `config` 下方。
1. 在配置文件夹中，添加一个名为的节点：

   `com.day.cq.wcm.notification.email.impl.EmailChannel` 类型 `sling:OsgiConfig`

1. 添加 `String` 属性添加到名为的节点 `email.from`. 对于值，指定要使用的电子邮件地址。

1. 单击 **全部保存**.

使用以下过程定义内容包源文件夹中的节点：

1. 在 `jcr_root/apps/*app_name*/config folder`，创建名为的文件 `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`

1. 添加以下XML来表示节点：

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. 替换 `email.from` 属性( `name@server.com`)。

1. 保存文件。

## 配置工作流电子邮件通知服务 {#configuring-the-workflow-email-notification-service}

当您收到工作流电子邮件通知时，发件人电子邮件地址和主机URL前缀均设置为默认值。 您可以通过配置 **Day CQ工作流电子邮件通知服务** 中。 如果这样做，建议在存储库中保留所做的更改。

默认配置在Web控制台中如下所示：

![chlimage_1-277](assets/chlimage_1-277.png)

### 页面通知的电子邮件模板 {#email-templates-for-page-notification}

页面通知的电子邮件模板位于以下位置：

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

默认的英语模板( `en.txt`)的定义如下：

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 为页面通知自定义电子邮件模板 {#customizing-email-templates-for-page-notification}

要自定义页面通知的英语电子邮件模板，请执行以下操作：

1. 在CRXDE中，打开文件：

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. 根据需要修改文件。
1. 保存更改。

模板需要具有以下格式：

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

其中 &lt;text_x> 可以是静态文本和动态字符串变量的混合变量。 可以在电子邮件模板中使用以下变量来发送页面通知：

* `${time}`，事件日期和时间。

* `${userFullName}`，触发事件的用户的全名。

* `${userId}`，触发事件的用户ID。
* `${modifications}`，采用以下格式描述页面事件类型和页面路径：

   &lt;page event=&quot;&quot; type=&quot;&quot;> => &lt;page path=&quot;&quot;>

   例如：

   PageModified => /content/geometrixx/en/products

### 论坛通知的电子邮件模板 {#email-templates-for-forum-notification}

论坛通知的电子邮件模板位于：

`/etc/notification/email/default/com.day.cq.collab.forum`

默认的英语模板( `en.txt`)的定义如下：

```xml
subject=[CQ Forum Notification]

header=-------------------------------------------------------------------------------------\n \
Time: Time: ${time}\n \
Forum Page Path: ${forum.path}\n \
-------------------------------------------------------------------------------------\n\n

message=Page: ${host.prefix}${forum.path}.html\n

footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 为论坛通知自定义电子邮件模板 {#customizing-email-templates-for-forum-notification}

要自定义论坛通知的英语电子邮件模板，请执行以下操作：

1. 在CRXDE中，打开文件：

   `/etc/notification/email/default/com.day.cq.collab.forum/en.txt`

1. 根据需要修改文件。
1. 保存更改。

模板需要具有以下格式：

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

其中 `<text_x>` 可以是静态文本和动态字符串变量的混合变量。

在论坛通知的电子邮件模板中可以使用以下变量：

* `${time}`，事件日期和时间。

* `${forum.path}`，查看论坛页面的路径。

### 工作流通知的电子邮件模板 {#email-templates-for-workflow-notification}

工作流通知的电子邮件模板（英文）位于：

`/libs/settings/workflow/notification/email/default/en.txt`

定义如下：

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### 为工作流通知自定义电子邮件模板 {#customizing-email-templates-for-workflow-notification}

要自定义工作流事件通知的英语电子邮件模板，请执行以下操作：

1. 在CRXDE中，打开文件：

   `/libs/settings/workflow/notification/email/default/en.txt`

1. 根据需要修改文件。
1. 保存更改。

模板需要具有以下格式：

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>其中 `<text_x>` 可以是静态文本和动态字符串变量的混合变量。 每行 `<text_x>` 项目需要以反斜杠( `\`)，但最后一个实例除外，当没有反斜线表示 `<text_x>` 字符串变量。
>
>有关模板格式的更多信息，请参阅 [属性.load()的javaoc](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-) 方法。

方法 `${payload.path.open}` 显示工作项有效负载的路径。 例如，对于Sites中的页面，然后 `payload.path.open` 将类似于 `/bin/wcmcommand?cmd=open&path=…`.;这没有服务器名称，因此模板会在 `${host.prefix}`.

以下变量可在电子邮件模板中使用：

* `${event.EventType}`，事件类型
* `${event.TimeStamp}`、事件的日期和时间
* `${event.User}`，触发事件的用户
* `${initiator.home}`，启动器节点路径

* `${initiator.name}`，启动器名称

* `${initiator.email}`，启动器的电子邮件地址
* `${item.id}`，工作项的id
* `${item.node.id}`，与此工作项关联的工作流模型中节点的id
* `${item.node.title}`，工作项的标题
* `${participant.email}`，参与者的电子邮件地址
* `${participant.name}`、参与者姓名
* `${participant.familyName}`，参与者的姓氏
* `${participant.id}`，参与者的id
* `${participant.language}`，参与者语言
* `${instance.id}`，工作流id
* `${instance.state}`，工作流状态
* `${model.title}`，工作流模型的标题
* `${model.id}`，工作流模型的id

* `${model.version}`，工作流模型的版本
* `${payload.data}`，负载

* `${payload.type}`，有效负载类型
* `${payload.path}`、有效负载路径
* `${host.prefix}`，主机前缀，例如：http://localhost:4502

### 为新语言添加电子邮件模板 {#adding-an-email-template-for-a-new-language}

为新语言添加模板：

1. 在CRXDE中，添加文件 `<language-code>.txt` 下面：

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page` :用于页面通知
   * `/etc/notification/email/default/com.day.cq.collab.forum` :用于论坛通知
   * `/libs/settings/workflow/notification/email/default` :用于工作流通知

1. 使文件适应语言。
1. 保存更改。

>[!NOTE]
>
>的 `<language-code>` 用作电子邮件模板的文件名需要是由AEM识别的小写字母语言代码。 对于语言代码，AEM依赖于ISO-639-1。

## 配置AEM Assets电子邮件通知 {#assetsconfig}

在AEM Assets中的收藏集进行共享或取消共享时，用户可以从AEM收到电子邮件通知。 要配置电子邮件通知，请执行以下步骤。

1. 按照上文中的说明配置电子邮件服务 [配置邮件服务](/help/sites-administering/notification.md#configuring-the-mail-service).
1. 以管理员身份登录 AEM。单击 **工具** >  **操作** >  **Web控制台** 打开Web控制台配置。
1. 编辑 **Day CQ DAM资源收集Servlet**. 选择 **发送电子邮件**. 单击“**保存**”。
