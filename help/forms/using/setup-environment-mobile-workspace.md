---
title: 为AEM Forms应用程序设置环境
seo-title: Set up environment for AEM Forms app
description: 用于构建和部署AEM Forms应用程序的硬件、软件和许可证。
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# 为AEM Forms应用程序设置环境 {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您需要以下硬件、软件和许可证才能构建和部署AEM Forms应用程序：

## 对于Windows设备 {#for-windows-devices}

* Microsoft Windows 8.1或Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## 对于iOS设备 {#for-ios-devices}

* 运行Mac OS X 10.9.5或更高版本的基于英特尔的Apple Mac
* iOS SDK 8.4或更高版本
* Xcode版本：适用于OS X或更高版本的Xcode 6.4
* iOS开发人员企业计划的会员资格
* 用于分发内部iOS应用程序的企业证书
* Apple iPad与iOS 8.4或更高版本

## 对于Android设备 {#for-android-devices}

* Android开发工具包（ADT包），可从 [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* 如果在MAC系统上设置了环境，则应将ADT安装在Applications文件夹中。
* 如果ADT安装在MAC上的任何其他位置，或者如果环境是在Windows系统上设置的，则需要在 `local.properties` 文件 `src\android` 文件夹（位于已提取的源存档中） `mobileworkspace-src.zip`. 在此文件中，将 `sdk.dir` 变量到桌面上的ADT SDK位置。

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip包含PhoneGap SDK 5.0。请确保未预安装PhoneGap SDK。
