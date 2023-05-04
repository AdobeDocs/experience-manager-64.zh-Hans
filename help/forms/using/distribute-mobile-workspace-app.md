---
title: 分发AEM Forms应用程序
seo-title: Distribute AEM Forms app
description: 使用移动设备管理(MDM)在移动设备上大规模部署应用程序。
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 1%

---

# 分发AEM Forms应用程序 {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

移动设备管理(MDM)支持在移动设备上大规模部署应用程序。

>[!NOTE]
>
>此分发仅适用于iOS和Android设备。

## MDM解决方案通常提供的主要功能： {#main-features-generally-provided-by-mdm-solutions}

* 在企业环境中启用设备注册
* 允许配置和更新设备设置
* 强制实施安全合规性。
* 安全地移动访问公司资源

MDM解决方案与移动应用程序管理相结合，允许您在企业的移动设备上管理内部、公共和购买的应用程序。

MDM管理员可以将ipa和apk文件上传到MDM服务器，并控制能够访问ipa或apk文件的用户。 管理员还可以控制与每个应用程序对应的配置文件设置。

## 影响AEM Forms应用程序的配置文件设置 {#profile-settings-affecting-the-aem-forms-app-br}

您设备上的以下配置文件设置将影响您设备上AEM Forms应用程序的运行：

* **允许使用相机** 在 **设备功能** 部分

如果禁用 **允许使用相机**，的相机功能 [照片批注](/help/forms/using/add-attachments.md) 将不起作用。 您需要启用此选项才能在应用程序中使用相机。

* **设备上需要密码** 在密码策略部分

启用 **应用程序数据加密**，则建议您启用 **密码** 设备上。 如果未在设备上设置密码，则存储在设备上的应用程序数据不会加密。
