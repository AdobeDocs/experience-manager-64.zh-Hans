---
title: 安全性
seo-title: Security
description: 应用程序安全性在开发阶段启动
seo-description: Application Security starts during the development phase
exl-id: 22c48f8c-38df-4c9b-88cf-67f6ae46e7e1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# 安全性{#security}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

应用程序安全性在开发阶段启动。 Adobe建议应用以下安全最佳实践。

## 使用请求会话 {#use-request-session}

遵循最低权限原则，Adobe建议使用绑定到用户请求的会话和适当的访问控制来完成每个存储库的访问。

## Protect反对跨站点脚本(XSS) {#protect-against-cross-site-scripting-xss}

跨站点脚本(XSS)允许攻击者将代码注入其他用户查看的网页中。 恶意Web用户可能会利用此安全漏洞绕过访问控制。

AEM在输出时应用过滤所有用户提供内容的原则。 在开发和测试过程中，防止XSS都是最优先的任务。

AEM提供的XSS保护机制基于 [AntiSamy Java库](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) 提供者 [OWASP（开放式Web应用安全项目）](https://www.owasp.org/). 默认AntiSamy配置可在

`/libs/cq/xssprotection/config.xml`

通过覆盖配置文件，您必须根据自己的安全需求调整此配置。 官员 [AntiSamy文档](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) 将为您提供实施安全要求所需的所有信息。

>[!NOTE]
>
>我们强烈建议您始终使用 [由AEM提供的XSSAPI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html).

此外，Web应用程序防火墙，例如 [适用于Apache的mod_security](https://www.modsecurity.org)，可以对部署环境的安全性提供可靠的中央控制，并防止以前未检测到的跨站点脚本攻击。

## 访问Cloud Service信息 {#access-to-cloud-service-information}

>[!NOTE]
>
>Cloud Service信息的ACL以及保护实例所需的OSGi设置将作为 [生产就绪模式](/help/sites-administering/production-ready.md). 虽然这意味着您无需手动进行配置更改，但仍建议您在部署开始之前先查看配置更改。

当您 [将AEM实例与Adobe Marketing Cloud集成](/help/sites-administering/marketing-cloud.md) 您使用 [Cloud Service配置](/help/sites-developing/extending-cloud-config.md). 有关这些配置的信息以及收集的任何统计信息都存储在存储库中。 如果您使用此功能，我们建议您查看此信息的默认安全性是否与您的要求相符。

Webservicesupport模块将统计信息和配置信息写入：

`/etc/cloudservices`

具有默认权限：

* 创作环境： `read` 表示 `contributors`

* 发布环境： `read` 表示 `everyone`

## Protect反对跨站点请求伪造攻击 {#protect-against-cross-site-request-forgery-attacks}

有关AEM用于缓解CSRF攻击的安全机制的更多信息，请参阅 [Sling反向链接过滤器](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) 安全检查表和 [CSRF保护框架文档](/help/sites-developing/csrf-protection.md).
