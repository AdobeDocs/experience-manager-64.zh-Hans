---
title: CSRF保护框架
seo-title: CSRF保护框架
description: 该框架利用令牌来保证客户端请求的合法性
seo-description: 该框架利用令牌来保证客户端请求的合法性
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
translation-type: tm+mt
source-git-commit: 97db2126a4a20d82f964102d9ae3afcac94d830c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# CSRF保护框架{#the-csrf-protection-framework}

除了Apache Sling推荐人过滤器，Adobe还提供新的CSRF保护框架来防止此类攻击。

该框架利用令牌来保证客户端请求的合法性。 令牌在将表单发送到客户端时生成，并在表单发回到服务器时验证。

>[!NOTE]
>
>匿名用户的发布实例上没有令牌。

## 要求 {#requirements}

### 依赖关系 {#dependencies}

任何依赖依赖关系的组 `granite.jquery` 件都将自动从CSRF保护框架受益。 如果任何组件的情况不是这样，则必须先声明一个依赖关系，然 `granite.csrf.standalone` 后才能使用框架。

### 复制加密密钥 {#replicating-crypto-keys}

为了利用令牌，您需要将二进制文件复 `/etc/keys/hmac` 制到部署中的所有实例。 将HMAC密钥复制到所有实例的一种简便方法是创建一个包含密钥的包，并通过包管理器在所有实例上安装它。

>[!NOTE]
>
>确保您还进行必要 [的调度程序配](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) 置更改，以使用CSRF保护框架。

>[!NOTE]
>
>如果将清单缓存与Web应用程序一起使用，请确保向清单中添&#x200B;**加“&amp;ast;**”，以确保令牌不使CSRF令牌生成调用脱机。 有关详细信息，请查阅此 [链接](https://www.w3.org/TR/offline-webapps/)。
>
>有关CSRF攻击及其缓解方法的详细信息，请参 [阅跨站点请求伪造OWASP页](https://owasp.org/www-community/attacks/csrf)。
