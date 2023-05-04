---
title: 消息传送要点
seo-title: Messaging Essentials
description: 消息传送组件概述
seo-description: Messaging component overview
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 3%

---

# 消息传送要点 {#messaging-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页记录了有关使用消息传送组件在网站上包含消息传送功能的详细信息。

## 客户端要点 {#essentials-for-client-side}

**撰写消息**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemessage</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>模板</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td>请参阅 <a href="configure-messaging.md">配置消息传送</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理配置</strong></td> 
   <td><a href="messaging.md">配置消息传送</a></td> 
  </tr> 
 </tbody> 
</table>

**消息列表** （用于收件箱、已发送和垃圾桶）

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>模板</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td>请参阅 <a href="configure-messaging.md">配置消息传送</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理配置</strong></td> 
   <td><a href="messaging.md">配置消息传送</a></td> 
  </tr> 
 </tbody> 
</table>

另请参阅 [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [配置消息传送](configure-messaging.md)

* [消息传送客户端API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) 对于SCF组件

* [消息传送API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) 服务

* [消息端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

>[!CAUTION]
>
>对于以下MessageBuilder方法，String参数必须*不*包含尾随斜杠“/”：
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>例如：
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### 社区站点 {#community-site}

使用向导创建的社区站点结构将在选择时包含消息传送功能。 请参阅 `User Management` 设置 [社区站点控制台](sites-console.md#user-management).

### 示例代码：消息接收通知 {#sample-code-message-received-notification}

例如，社交消息功能引发操作事件 `send`, `marking read`, `marking delete`. 可以捕获这些事件并对事件中包含的数据执行相应操作。

以下示例是一个事件处理程序，用于侦听 `message sent` 事件，并使用 `Day CQ Mail Service`.

要尝试服务器端示例脚本，您需要开发环境并能够构建OSGi包。

1. 以管理员身份登录 ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. 创建 `bundle node`in `/apps/engage/install` 具有任意名称，例如

   * **[!UICONTROL 符号名称]**:com.engage.media.social.messaging.messagingNotification
   * **[!UICONTROL 名称]**:入门教程消息通知
   * **[!UICONTROL 描述]**:向用户发送电子邮件通知的示例服务
   * **[!UICONTROL 包]**: `com.engage.media.social.messaging.notification`

1. 导航至 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. 删除 `Activator.java` 自动创建的类
   1. 创建类 `MessageEventHandler.java`
   1. 将下面的代码复制/粘贴到 `MessageEventHandler.java`

1. 单击 **[!UICONTROL 全部保存]**
1. 导航到 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` 并按照 `MessageEventHandler.java` 代码。
1. 构建包
1. 确保 `Day CQ Mail Service`OSGi服务已配置
1. 以演示用户身份登录，并向其他用户发送电子邮件
1. 收件人应收到一封关于新消息的电子邮件

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
