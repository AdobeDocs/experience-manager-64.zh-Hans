---
title: 升级后卸载的过时包列表
seo-title: List of Obsolete Bundles Uninstalled After the Upgrade
description: 详细列出了升级到AEM 6.3时自动卸载的包。
seo-description: A list detailing the bundles that are automatically uninstalled when upgrading to AEM 6.3.
uuid: b015e857-31c1-4982-b71c-f3201b49ec8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 797a6f3b-d2a8-4835-81ab-a1602677417f
feature: Upgrading
exl-id: 0f075a01-f286-4e16-9061-4e902c553eb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 2%

---

# 升级后卸载的过时包列表{#list-of-obsolete-bundles-uninstalled-after-the-upgrade}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>如果您的代码依赖于这些包，请确保与Adobe支持部门联系，并请求为受影响区域提供兼容包。

升级到AEM 6.3时，将自动卸载以下包，具体取决于从哪个AEM版本执行升级：

**AEM 6.1:**

* org.eclipse.equinox.region，版本1.1.0.v20120522-1841，活动
* org.apache.sling.installer.factory.subsystems，版本1.0.0，活动
* org.apache.aries.subsystem.core，版本1.2.0，活动
* org.apache.aries.subsystem.api，版本1.1.0，活动
* org.apache.felix.resolver，版本1.0.0，活动
* org.osgi.service.subsystem.region.context.0，版本1.0.0，活动
* com.adobe.cq.cq-creativecloud-cloudims，版本0.0.10，活动
* com.adobe.cq.cq-creativecloud-commons，版本0.0.8，活动
* com.adobe.cq.cq-creativecloud-filesync，版本0.0.12，已安装
* com.adobe.cq.cq-creativecloud-storage，版本0.0.8，已安装
* biz.aQute.bndlib，版本1.43.0，活动
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活动
* com.day.cq.mcm.cq-mcm-silverpop-integration，版本1.2.2，活动

**AEM 6.0:**

* org.apache.sling.discovery.impl，版本1.1.6，活动
* com.adobe.granite.installer.patch，版本0.4.0，活动
* biz.aQute.bndlib，版本1.43.0，活动
* com.day.cq.cq-jobs-core，版本5.4.0，活动
* com.day.cq.cq-opensocial，版本5.7.2，活动
* com.day.cq.cq-pinauthhandler，版本1.1.2，活动
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活动
* com.day.cq.mcm.cq-mcm-silverpop-integration，版本1.1.6，活动
* com.day.cq.wcm.cq-wcm-mobile-phonegap-build-integration，版本5.7.18，活动

**CQ 5.6.1:**

* biz.aQute.bndlib，版本1.43.0，活动
* com.day.cq.cq-pinauthhandler，版本1.0.0，活动
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活动
* com.day.crx.crxde-support，版本2.3.14，已安装
* com.day.cq.mcm.cq-mcm-silverpop-integration，版本1.0.2，活动

**CQ 5.6.0:**

* com.day.cq.cq-pinauthhandler，版本1.0.0，活动
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活动
* com.day.crx.crxde-support，版本2.3.14，已安装
