---
title: 配置属性的加密支持
seo-title: 配置属性的加密支持
description: 'null'
seo-description: 'null'
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# 配置属性的加密支持{#encryption-support-for-configuration-properties}

## 概述 {#overview}

此功能允许以受保护的加密形式存储所有OSGi配置属性，而不是明文。 Web控制台UI中的表单用于使用系统范围的加密主控密钥从明文创建加密文本。

添加了OSGi配置插件支持，以便在服务使用属性之前对其进行解密。

>[!NOTE]
>
>期望已加密值的服务需要使用IsProtected检查，以在尝试解密之前查看该值是否已加密，因为它可能已被解密。

## 启用加密支持 {#enabling-encryption-support}

这些步骤说明如何为邮件服务加密SMTP密码。 您可以完成要加密的OSGI属性的这些步骤。

1. 转到AEM Web控制台(位 *于https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr)*
1. 在左上角，转到主- **加密支持**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. 将显 **示“Adobe Experience ManagerWeb控制台加密** 支持”页。

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. 在纯 **文本字段中** ，输入要保护的敏感数据的文本。
1. 选择 **Protect**。 “受保护”文本显示为加密文本。

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. 从Step#5复制受保护文本并将其粘贴到OSGI表单值中。 在此示例中，加密 **的SMTP** 口令会添 *加到Day CQ邮件服务*。

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. 保存Day CQ邮件服务属性。 SMTP密码现在将作为加密值发送。

## 解密支持 {#decryption-support}

AEM现在提供配置插件来解密配置属性。 此AEM插件将自动解密和检索明文属性。
