---
title: 在AEM中开发移动应用程序
seo-title: 在AEM中开发移动应用程序
description: 可查看本页以开始在AEM中使用Adobe PhoneGap企业开发移动应用程序。
seo-description: 可查看本页以开始在AEM中使用Adobe PhoneGap企业开发移动应用程序。
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
translation-type: tm+mt
source-git-commit: 55b6a113bcb4d39b7eb100f21a05b9b44e3fe1c3
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# 在AEM中开发移动应用程序 {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（如React）的项目使用SPA编辑器。 [了解更多](/help/sites-developing/spa-overview.md).

AEM利用Adobe PhoneGap和Adobe出版解决方案，使您能够创建和管理内容丰富的和基于实用程序的跨平台移动应用程序：

* 在一个位置管理所有公司移动应用程序。
* 在开发和暂存环境中审核应用程序，无需复杂的资源调配用户档案，也无需额外努力构建和上传用于共享的应用程序。
* 使用AEM创作环境为您的应用程序创建和管理丰富内容。
* 将HTML5与Adobe PhoneGap结合使用，借助设备本机功能创造丰富的体验。
* 通过Cordova WebViews将HTML5 Web视图引入新的或预先存 **在的本** 机应用程序。
* 在所有投放渠道（包括Web、移动-Web、移动-App和印刷）中创建、策划和共享丰富的多媒体内容。

AEM与AdobePhoneGap Build服 **[务集成](https://build.phonegap.com/)**，以简化应用程序构建和部署过程。

**AdobeContentSync** 使用户能够轻松地将Over-the-Air(OTA)的页面和内容更新下载到他们的设备，而无需重新安装应用程序或从appStore、Google Play或其他应用程序源下载。

**Adobe Analytics** 完全集成到AEM应用程序中，允许详细跟踪分发、地理位置、操作系统、设备、点击流、iBeacon跟踪等。

## 创建应用程序 {#creating-apps}

开发人员可以使用 [AEM PhoneGap Starter](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) Kit以及https://github.com/adobe-marketing-cloud-apps通过PhoneGap引导AEM应用 [](https://github.com/adobe-marketing-cloud-apps) 程序（包括运行Cordova Webviews的参考本机应用程序）中的其他资源。

Starter Kit Git存储库的自述文件包含使用Starter Kit的教程：

* 自定义品牌
* 制作示例构建和部署目标
* 源代码控制存储库配置
* 安装并部署到本地或远程AEM实例
* 从AEM卸载

>[!NOTE]
>
>GitHub和“厨房水槽”源上可 [以找](https://github.com/adobe-marketing-cloud-apps) 到其他参考实施 [源](https://github.com/blefebvre/aem-phonegap-kitchen-sink)。

## 为IOS 9和HTTP主机进行开发 {#developing-for-ios-and-http-hosts}

IOS开发人员应注意到在iOS 9上运行的Cordova应用程序存在一个未解决的问题。 此问题会阻止向不安全的主机(如http://localhost:4502 **)发出请求。 此问题将通过即将发布的cordova-ios（由Cordova CLI使用）解决，但同时提供两种解决方法：

1. 作为立即的解决方法，您仍可以无问题地使用任何iOS 8模拟器。
1. 如果必须使用iOS 9，则可以手动编辑您的应用程序-Info.plist(在“&lt;app `cordova platform add ios` root>/platforms/ios/&lt;app name>/&lt;app name>-Info.plist”文件中运行后找到)，以包含以下属性：

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>有关“App Transport Security”的详细信息，请参阅Apple iOS9预发 [行文档的下一节](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) ，以及此 [“堆栈溢出”讨论](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/)。

## 在AEM中开发移动应用程序 {#developing-mobile-applications-in-aem-1}

* [启动AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [构建移动应用程序](/help/mobile/building-app-mobile-phonegap.md)
* [构建应用程序](/help/mobile/phonegap-structure-an-app.md)
* [使用“应用程序”控制台创建和编辑应用程序](/help/mobile/phonegap-apps-console.md)
* [单页应用程序](/help/mobile/phonegap-single-page-applications.md)
* [使用PhoneGap CLI开发应用程序](/help/mobile/phonegap-apps-pg-cli.md)
* [访问设备功能](/help/mobile/phonegap-access-device-features.md)
* [使用Adobe移动分析跟踪应用程序性能](/help/mobile/phonegap-intro-to-app-analytics.md)
* [将Adobe Analytics添加到您的移动应用程序](/help/mobile/phonegap-add-analytics-to-apps.md)
* [推送通知](/help/mobile/phonegap-push-notifications.md)
* [AEM Mobile内容个性化](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [应用剖析](/help/mobile/phonegap-apps-arch.md)
* [你的混合应用准备好迎接AEM Mobile了吗？](/help/mobile/phonegap-adding-content-to-imported-app.md)

### 其他资源 {#additional-resources}

要了解管理员和开发人员的角色和职责，请参阅以下资源：

* [使用AEM为Adobe PhoneGap企业进行创作](/help/mobile/phonegap.md)
* [通过AEM为Adobe PhoneGap企业管理内容](/help/mobile/administer-phonegap.md)
