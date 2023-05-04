---
title: 跟踪弹回的电子邮件
seo-title: Tracking Bounced Emails
description: 当您向许多用户发送新闻稿时，列表中通常会存在一些无效的电子邮件地址。 向这些地址发送新闻稿时会弹回。 AEM能够管理这些退回，并可在超出配置的退回计数后停止向这些地址发送新闻稿。
seo-description: When you send a newsletter to many users, there are usually some invalid emails addresses in the list. Sending newsletters to those addresses bounce back. AEM is capable of managing those bounces and can stop sending newsletters to those addresses after the configured bounce counter is exceeded.
uuid: 749959f2-e6f8-465f-9675-132464c65f11
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: fde9027b-9057-48c3-ae34-3f3258c5b371
exl-id: 3be35bb8-3485-42a6-8195-c3e95d097856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 跟踪弹回的电子邮件{#tracking-bounced-emails}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe不打算进一步增强对AEM SMTP服务发送的打开/弹回电子邮件的跟踪。
>
>建议是 [利用Adobe Campaign及其AEM集成](/help/sites-administering/campaign.md).

向许多用户发送新闻稿时，列表中通常会存在一些无效的电子邮件地址。 向这些地址发送新闻稿时会弹回。 AEM能够管理这些退回，并且在超出配置的退回计数后停止向这些地址发送新闻稿。 默认情况下，跳出率设置为3，但可进行配置。

要设置AEM以跟踪退回的电子邮件，您需要设置AEM以轮询接收退回电子邮件的现有邮箱（通常是您指定的“发件人”电子邮件地址，您将在此地址发送新闻稿）。 AEM会轮询此收件箱并导入轮询配置中指定路径下的所有电子邮件。 然后，会触发一个工作流，以搜索用户内的退回电子邮件地址，并相应地更新用户的bounceCounter属性值。 超出配置的最大跳出次数后，用户将从新闻稿列表中删除。

## 配置馈送导入器 {#configuring-the-feed-importer}

通过馈送导入器，您可以将外部源中的内容重复导入您的存储库。 使用Feed Importer的此配置， AEM会检查发件人邮箱中的退回电子邮件。

要配置Feed Importer以跟踪弹回的电子邮件，请执行以下操作：

1. 在 **工具**，选择馈送导入器。

1. 单击 **添加** 创建新配置。

   ![chlimage_1](assets/chlimage_1.png)

1. 通过选择类型并向轮询URL添加信息以配置主机和端口来添加新配置。 此外，您还需要向URL查询添加一些特定于邮件和协议的参数。 将配置设置为每天至少轮询一次。

   轮询URL中的所有配置都需要以下信息：

   `username`:用于连接的用户名

   `password`:用于连接的密码

   此外，您还可以根据协议配置某些设置。

   **POP3配置属性：**

   `pop3.leave.on.server`:定义是否将消息保留在服务器上。 设置为true可将消息保留在服务器上，否则设置为false。 默认值为true。

   **POP3示例：**

   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret | 使用pop3 over SSL通过用户/密钥在端口995上连接到GMail，默认情况下将消息保留在服务器上 |
   |---|---|
   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false |

   **IMAP配置属性：**

   用于设置要搜索的标记。

   `imap.flag.SEEN`：对于新消息/未看消息，设置为false；对于已读消息，设置为true

   请参阅 [https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html](https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html) 全部的旗子。

   **IMAP示例：**

   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret | 使用IMAP over SSL通过用户/密钥在端口993上连接到GMail。 默认情况下仅获取新消息。 |
   |---|---|
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true | 使用IMAP over SSL通过用户/密钥连接到GMail 993，只获取已看到的消息。 |
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true&amp;imap.flag.SEEN=false | 使用IMAP over SSL通过用户/密钥连接到GMail 993，获取已读或新邮件。 |

1. 保存配置。

## 配置新闻稿服务组件 {#configuring-the-newsletter-service-component}

配置馈送导入器后，您需要配置“发件人”地址和退件计数器。

要配置新闻稿服务，请执行以下操作：

1. 在OSGi控制台中， `<host>:<port>/system/console/configMgr` 并导航到 **MCM新闻稿**.

1. 配置服务并在完成后保存更改。

   ![chlimage_1-1](assets/chlimage_1-1.png)

   可以设置以下配置来调整行为：

   | 跳出计数器最大值(max.bounce.count) | 定义在用户发送新闻稿时被忽略之前的退回次数。 将此值设置为0将完全禁用退回检查。 |
   |---|---|
   | 活动无缓存(sent.activity.nocache) | 定义用于新闻稿发送活动的缓存设置 |

   保存后，Newsletter MCM服务会执行以下操作：

   * 成功发送新闻稿后，将活动写入用户隐藏的流。
   * 在检测到跳出且用户跳出计数器发生更改时写入活动。
