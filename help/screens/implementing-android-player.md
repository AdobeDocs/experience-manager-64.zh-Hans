---
title: 实施Android Player
seo-title: Android Player的实现
description: '可查看本页以了解Android Watchdog的实施，这是一种从崩溃中恢复播放器的解决方案。 '
seo-description: '可查看本页以了解Android Watchdog的实施，这是一种从崩溃中恢复播放器的解决方案。 '
uuid: 37527a6a-dcc5-4256-abeb-e1f95ff80be4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: e6ec1641-4323-4c79-b932-b857feb1df21
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# 实施Android Player {#implementing-android-player}

监视 ***程序*** (Watchdog)是一种从崩溃中恢复播放器的解决方案。 应用程序需要向监视服务注册自己，然后定期向其处于活动状态的服务发送消息。 如果看门狗服务在规定的时间内没有收到保持活动消息，则服务尝试重新启动设备以进行干净恢复（如果它具有足够的权限）或重新启动应用程序。

## 实施Android监视程序 {#implementing-android-watchdog}

由于Android的架构，重新启动设备需要应用程序具有系统权限。 为此，您需要使用制造商的签名密钥对应用程序进行签名，否则，监视程序将重新启动播放器应用程序，而不会重新启动设备。

### 使用制造商密钥的Android窗格标牌 {#signage-of-android-apks-using-manufacturer-keys}

要访问Android的某些特权API(如 *PowerManager* 或 *HDMIControlServices*)，您需要使用制造商的密钥对android apk进行签名。

>[!CAUTION]
>
>先决条件：
>
>在执行以下步骤之前，您应该已安装Android SDK。

请按照以下步骤使用制造商的密钥对android应用程序进行签名：

1. 从Google Play或 [AEM Screens播放器下载页面下载应用程序](https://download.macromedia.com/screens/) 。
1. 从制造商处获取平台密钥，以获 *取pk8* 和 *pem文件*

1. 在android sdk中使用查找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip对齐工具的路径
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalpid.apk
1. 使用 ***adb安装向设备安装aemscreensalpided.apk***

## Android监视程序实施 {#android-watchdog-implementation}

跨Android监视程序服务是使用 *AlarmManager作为cordova插件实现的*。

下图显示了监视服务的实现：

![chlimage_1-43](assets/chlimage_1-43.png)

**1. 初始化** 在初始化cordova插件时，将检查权限以查看我们是否具有系统权限，从而检查重新启动权限。 如果满足这两个条件，则会创建待重新引导的意图，否则将创建用于重新启动应用程序的待定意图（基于其启动活动）。

**2. 保持活动定时器** “保持活动定时器”用于每15秒触发一个事件。 在此情况下，您需要取消现有的待定意图（以重新启动或重新启动应用程序），并在将来相同的60秒内注册新的待定意图（实质上是延迟重新启动）。

>[!NOTE]
>
>在Android中， *AlarmManager* 用于注册pendingIntent ** ，即使应用程序已崩溃且其警报传送不精确于API 19(Kitkat)，也可以执行它。 在计时器的间隔和 *AlarmManager的pendingIntent的警报之间保* 留一定间距 ** 。

**3. 应用程序崩溃** -如果发生崩溃，AlarmManager注册的“重新引导的pendingIntent”不再重置，因此它将执行应用程序的重新引导或重新启动（具体取决于cordova插件初始化时可用的权限）。
