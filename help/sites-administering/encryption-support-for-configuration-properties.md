---
title: 对配置属性的加密支持
seo-title: Encryption Support for Configuration Properties
description: 对配置属性的加密支持
seo-description: null
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
exl-id: 077a940d-19de-4d19-ad99-61f465e68205
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---

# 对配置属性的加密支持{#encryption-support-for-configuration-properties}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

此功能允许将所有OSGi配置属性存储在受保护的加密表单中，而不是明文。 Web控制台UI中的表单用于使用系统范围的加密主控密钥从明文创建加密文本。

添加了OSGi配置插件支持，以便在服务使用属性之前对其进行解密。

>[!NOTE]
>
>期望加密值的服务需要使用IsProtected检查来在尝试解密之前查看值是否已加密，因为该值可能已解密。

## 启用加密支持 {#enabling-encryption-support}

这些步骤说明如何加密Mail服务的SMTP密码。 您可以为要加密的OSGI属性完成这些步骤。

1. 转到AEM Web Console(位于 *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. 在左上角，转到 **主 — 加密支持**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. 的 **Adobe Experience Manager Web控制台加密支持** 页面。

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. 在 **纯文本** 字段，输入要保护的敏感数据的文本。
1. 选择 **Protect**. “受保护”文本显示为加密文本。

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. 复制步骤5中的受保护文本，并将其粘贴到OSGI表单值中。 在本例中，加密 **SMTP密码** 添加到 *Day CQ Mail Service*.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. 保存Day CQ Mail Service属性。 SMTP密码现在将作为加密值发送。

## 解密支持 {#decryption-support}

AEM现在提供了配置插件来解密配置属性。 此AEM插件将自动解密和检索明文属性。
