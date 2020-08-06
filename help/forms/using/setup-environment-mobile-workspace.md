---
title: 为AEM Forms应用程序设置环境
seo-title: 为AEM Forms应用程序设置环境
description: 用于构建和部署AEM Forms应用程序的硬件、软件和许可证。
seo-description: 用于构建和部署AEM Forms应用程序的硬件、软件和许可证。
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# 为AEM Forms应用程序设置环境 {#set-up-environment-for-aem-forms-app}

您需要以下硬件、软件和许可证才能构建和部署AEM Forms应用程序：

## 对于Windows设备 {#for-windows-devices}

* Microsoft Windows 8.1或Windows 10
* Microsoft Visual Studio 2015
* 适用于Apache Cordova的Microsoft Visual Studio工具

## 对于iOS设备 {#for-ios-devices}

* 运行Mac OS X 10.9.5或更高版本的基于Intel的Apple Mac
* iOS SDK 8.4或更高版本
* Xcode版本： 适用于OS X或更高版本的Xcode 6.4
* iOS开发人员企业项目的会员资格
* 用于分发内部iOS应用程序的企业证书
* 带iOS 8.4或更高版本的Apple iPad

## 对于Android设备 {#for-android-devices}

* Android Development Toolkit（ADT捆绑包），可从https://developer.android.com/sdk/index.html下 [载](https://developer.android.com/sdk/index.html)
* 如果环境在MAC系统上设置，则ADT应安装在“Applications”（应用程序）文件夹中。
* 如果ADT安装在MAC上的任何其他位置，或者环境是在Windows系统上设置的，则需要在解压缩的源存档中的文件夹中更新 `local.properties` ADT `src\android` SDK路径 `mobileworkspace-src.zip`。 在此文件中，将变 `sdk.dir` 量指向桌面上的ADT SDK位置。

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip包含PhoneGap SDK 5.0。请确保未预安装PhoneGap SDK。
