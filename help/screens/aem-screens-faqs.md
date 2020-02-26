---
title: AEM Screens常见问题解答
seo-title: AEM Screens常见问题解答
description: 可查看本页以获取与AEM Screens项目相关的常见问题解答。
seo-description: 可查看本页以获取与AEM Screens项目相关的常见问题解答。
uuid: e394b1bd-1e63-4bd1-b669-923b2a298743
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: troubleshoot
discoiquuid: 558a7c2f-b32e-428e-89f6-123d72ca1108
translation-type: tm+mt
source-git-commit: 9f505017b80fe54e228daea9b248fb0a7db93ca2

---


# AEM Screens常见问题解答 {#aem-screens-faqs}

以下部分对与AEM Screens项目相关的几个常见问题解答提供了答案。

## 渠道管理 {#channel-management}

### 线上和线下渠道之间有何差异？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

“联机渠道”******&#x200B;将会在实时环境中显示更新的内容，而“脱机渠道”******&#x200B;则会显示缓存的内容。

### 如何在线建立渠道？ {#how-do-i-make-a-channel-online}

选择渠道，然后从操作栏中导航到渠道属性。 选 **中“渠道”选项卡下的“开发人员模式”** (强制 **渠道联机** )，以使渠道联机。

### “渠道角色”字段的用法是什么？ {#what-is-the-use-of-the-channel-role-field}

渠道角色是实际运行的渠道的抽象，这样作者可以直接专注于通用体验。 您可以将其视为一种在其上下文（显示或计划）中唯一标识渠道的标记。

### 如何实现实际的渠道分辨率？ {#how-does-actual-channel-resolution-happen}

对于 *静态引用*，分辨率只遵循指定的路径。

对于 *动态引用*，将渠道分配给显示屏（而非计划）后，会出现解析。 显示路径将变为渠道的上下文，并且分辨率将按以下方式（从高到低优先级）进行：

1. 显示屏有一个与引用的渠道名称匹配的子节点
1. 显示屏有一个与引用的渠道名称匹配的同级节点
1. 显示屏的父位置有一个与引用的渠道名称匹配的子节点
1. 显示屏的grand-parent位置有一个与引用的渠道名称匹配的子节点

依此类推，直到您到达位置文件夹并立即停在该位置（因此，您不能引用渠道文件夹中的渠道，例如，仅引用位置子树中的渠道）。

## 设备注册 {#device-registration}

### 如果我发现端点（如设备入门和注册请求），我可以编写大量设备的脚本并注册这些设备。 除了将其锁定到分支Wi-Fi之外，是否还可以保护这些请求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

当前仅可在作者实例上注册。 尽管注册服务未通过身份验证，但它将仅在AEM中创建待处理设备，并且不会实际注册设备或分配任何显示屏。

要注册设备（这意味着在AEM中为设备创建用户），您仍需要向AEM进行身份验证，并且当前需要手动按照注册向导完成注册。 理论上，恶意用户可能创建多个挂起的设备，但如果没有AEM登录，则无法注册任何设备。

### 是否可以通过某种身份验证方式将HTTP GET请求转换为HTTP POST? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

注册请求是POST请求。

建议从会话中获取设备ID，而不是作为参数传递。 这将清除服务器日志、浏览器缓存等。 它当前不是安全问题。 请注意，在语义上，当服务器上没有状态更改时，使用GET；当状态发生更改时，使用POST。

### 是否可以拒绝设备注册请求？

您无法拒绝注册请求。 注册请求应在Adobe Experience Manager Web Console中配置的超时后过期。

默认情况下，此值设置为一天并存储在内存缓存中。

## 设备监视和运行状况报告 {#device-monitoring-and-health-reports}

### 如果AEM Screens播放器显示空白屏幕，如何进行疑难解答？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

请检查以下可能性以排除空白屏幕问题：

* AEM无法推送脱机内容
* 渠道没有任何内容
* 当前时间不会显示任何资产

### 如果AEM Screens播放器无法注册且其状态显示为“失败”，该怎么办？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您需要启用Apache Sling引用过滤器允许空。 这是在AEM Screens播放器和AEM Screens服务器之间优化控制协议操作所必需的。

1. 导航到 **Adobe Experience Manager Web Console配置**
1. 选中**allow.empty **选项。
1. 单击&#x200B;**保存**。

### 如果在注册AEM Screens播放器时，设备显示FAILURE，而控制台日志显示ENAME_NOT_FOUND错误，如何进行疑难解答？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens服务器DNS，则可能会出现此问题。 您可以尝试使用IP地址进行连接。 要获取服务器的IP，请使用： *arp &lt;server_dns_name>*。

### AMS是否建议在所有设备上实施Android监视程序？ 看门狗(Cordova)插件是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用纯Android API的跨平台Android监视程序已是应用程序的一部分。 不需要任何其他软件，但根据您使用的设备，您可能需要关闭apk以获得完整电源循环(Powermanager api)的系统权限。 如果它没有使用制造商键进行辞任，它将退出并重新启动应用程序，但不会重新启动电源循环。

有关如何实施Android Player的详细信息，请参阅实 [**施Android Player **](implementing-android-player.md)。

### Adobe/AMS建议哪些第三方远程监视和警报工具（软件）用于监视每台设备？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根据您不需要的监视和警报，如果设备在一段时间内未ping通知，AEM Screens通知服务会通知您一项新功能。 第三方工具取决于您的操作系统(OS)、其功能和客户的特定需求。

有关可监控设备活动的更多信息，请参阅 [**AEM Screens通知服务&#x200B;**](screens-notifications-service.md)。

### 使用带有智能同步的发布设备拓扑，设备是否仍直接连接到快照和心跳功能的创作实例？

否，设备未直接连接到作者。 它们会报告到发布实例，作者将轮询发布实例以获取更新。

## AEM Screens 播放器 {#aem-screens-player}

### 如何将ChromeOS播放器安装为Chrome浏览器插件？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可以在开发人员模式下作为Chrome浏览器插件安装，无需实际的Chrome播放器设备。 要进行安装，请执行以下步骤：

1. 单 [击此处](https://download.macromedia.com/screens/) ，下载最新的Chrome Player。
1. 解压缩并将其保存到磁盘上。
1. 打开Chrome浏览器，单击3点菜单，然后从右上角选择 **More Tools** —> **Extensions** （更多工具—>扩展），或直接导航到 ***chrome://extensions***。
1. 从右上角 **打开“开发** 人员”模式。
1. 单击左上角的**Load Unpacked **并加载解压缩的Chrome Player。
1. 检查 **AEM Screens Chrome Player** plugin（如果扩展列表中提供）。
1. 打开新选项卡，单击左上 **角的** “应用程序”图标，或直接导航到 ***chrome://apps***。
1. 单击“ **AEM Screens** Plugin”以启动Chrome Player。 默认情况下，播放器以全屏模式启动。 按 **Esc** 退出全屏模式。

### 如何对Screens播放器无法通过具有自定义错误处理程序的发布实例进行身份验证进行疑难解答？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

当AEM Screens播放器启动时，当播放器收到 ***404错误时，它向/content/screens/svc.ping.json***&#x200B;发出请求。 播放器启动身份验证请求以针对发布实例进行身份验证。 如果发布实例中有自定义错误处理程序，请确保在/content/screens/svc.ping.json上返回匿名用户的404状 ***态代码***。

### 如何在Android播放器中设置设备屏幕保持打开状态？

按照以下步骤在任何Android播放器上打开“保持清醒”:

1. 导航到Android播放器设置->关 **于**
1. 点按内部版本号7次，以在“设置”中启用“开发人员选项”
1. 导航到开发 **人员选项**
1. 启用 **保持清醒**

### 如果从AEM发送更新且播放器处于脱机状态，是否存在重试机制以检查设备是否恢复联机以传送更新的内容？ 还有，它试了多久？

从即将进入的设备发出的下一个ping命令将看到上次修改时间，该时间比它所拥有的时间更新，并将下载此新内容。
它将永远尝试，直到ping成功。

### 使用资产 {#using-assets}

### 如何在大于2GB的AEM Screens渠道中使用视频？ {#how-to-use-videos-in-an-aem-screens-channel-larger-than-gb}

默认情况下，AEM资产触屏UI不允许您上传任何大于2 GB的资产，因为AEM Screens渠道中存在文件大小限制。 但是，您可以通过进入CRXDE Lite并在/apps目录下创建一个节点来覆盖此限制。

要详细了解如何在 */apps* 目录中配置文件大小上限（例如，30GB），请参阅 *Managing Video Assets（管理视频资产）中的Configuration（配置）以上传大于2 GB*[的视频资产](/help/assets/managing-video-assets.md)。

### 常规疑难解答提示 {#general-troubleshooting}

### 如何禁用Livefyre以避免A/P屏幕错误？

为避免日志错误，请禁用Livefyre:

**禁用Livefyre捆绑包：**

1. 导航至 `http://<host>:<port>/system/console/bundles`
1. 搜索AEM Livefyre捆绑包： *com.adobe.cq.social.cq-social-livefyre*
1. 单击 **停止**。

**禁用Livefyre poller:**

1. 在CRXDE Lite中，导航到 */etc/importers/polling/livefyre-poller/jcr:content*
1. 添加新的已启用属性的类型Boolean
1. 将 **enabled属性设置为****false**
