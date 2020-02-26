---
title: Messaging Essentials
seo-title: Messaging Essentials
description: 消息传递组件概述
seo-description: 消息传递组件概述
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c

---


# Messaging Essentials {#messaging-essentials}

本页记录了使用消息传递组件在网站上包含消息传递功能的详细信息。

## 客户端必备工具 {#essentials-for-client-side}

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
   <td>请参阅 <a href="configure-messaging.md">配置消息</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理员配置</strong></td> 
   <td><a href="messaging.md">配置消息传递</a></td> 
  </tr> 
 </tbody> 
</table>

**邮件列表** （针对收件箱、已发送和废纸篓）

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
   <td>请参阅 <a href="configure-messaging.md">配置消息</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理员配置</strong></td> 
   <td><a href="messaging.md">配置消息传递</a></td> 
  </tr> 
 </tbody> 
</table>

另请参阅 [客户端自定义](client-customize.md)

## 服务器端必备工具 {#essentials-for-server-side}

* [配置消息传递](configure-messaging.md)

* [用于SCF组件的消息客户端](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) API

* [服务的消息](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) API

* [消息传送端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

>[!CAUTION]
>
>对于以下MessageBuilder方法，String参数必须*not *包含尾随斜杠“/”:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>
例如：
>
>
```>
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```>



### 社区站点 {#community-site}

使用向导创建的社区站点结构将在选中时包含消息传递功能。 请参 `User Management` 阅“社区 [站点”控制台的设置](sites-console.md#user-management)。

### 示例代码：收到的消息通知 {#sample-code-message-received-notification}

社交消息功能为操作抛出事 `send`件， `marking read`例如 `marking delete`。 可以捕获这些事件并对事件中包含的数据执行操作。

以下示例是一个事件处理函数，它监听该事件，并 `message sent` 使用该事件向所有消息收件人发送电子邮件 `Day CQ Mail Service`。

要试用服务器端范例脚本，您需要一个开发环境并能够构建OSGi捆绑包。

1. Login as an administrator to ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. 创建 `bundle node`具有 `/apps/engage/install` 任意名称的In，如

   * **[!UICONTROL 符号名称]**:com.engage.media.social.messaging.MessagingNotification
   * **[!UICONTROL 名称]**:入门教程消息通知
   * **[!UICONTROL 说明]**:用于在用户收到消息时向用户发送电子邮件通知的示例服务
   * **[!UICONTROL 包]**: `com.engage.media.social.messaging.notification`

1. 导航至 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. 删除自 `Activator.java` 动创建的类
   1. 创建类 `MessageEventHandler.java`
   1. 将以下代码复制／粘贴到 `MessageEventHandler.java`

1. 单击“ **[!UICONTROL 全部保存”]**
1. 导航到 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` 并添加代码中编写的所有导入语句 `MessageEventHandler.java` 。
1. 构建捆绑包
1. 确保 `Day CQ Mail Service`OSGi服务已配置
1. 以一个演示用户身份登录，并向另一个用户发送电子邮件
1. 收件人应收到一封关于新邮件的电子邮件

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

