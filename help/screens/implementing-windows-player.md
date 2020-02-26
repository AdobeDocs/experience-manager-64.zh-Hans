---
title: 实施Windows 10 Player
seo-title: 实施Windows 10 Player
description: '可查看本页以了解有关配置AEM Screens Windows 10播放器的信息。 '
seo-description: '可查看本页以了解有关配置AEM Screens Windows 10播放器的信息。 '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# 实施Windows 10 Player{#implementing-windows-player}

本节介绍有关配置AEM Screens Windows 10播放器的信息。 它提供配置文件的信息以及可用选项，以及用于开发和测试的设置的建议。

## 安装Windows Player {#installing-windows-player}

要实施适用于AEM Screens的Windows播放器，请安装适用于AEM Screens的Windows播放器。

访问 [**AEM 6.4播放器下载页&#x200B;**](https://download.macromedia.com/screens/)。

### Ad-Hoc方法 {#ad-hoc-method}

用于安装最新Windows Player(*.exe*)的临时方法，请访问 [**AEM 6.4播放器下载页&#x200B;**](https://download.macromedia.com/screens/)。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左 **侧操作菜单导航到** “配置”，然后输入要连接到的AEM实例的位置（地址）并单击“保 **存”**。

1. 单击左侧操 **作菜单中** 的“注册”链接以完成设备注册过程。

### 使用一个配置注册多个Windows 10播放器 {#registering-multiple-windows-players-with-one-configuration}

安装Windows播放器后，可以使用一个配置注册多个播放器。

>[!NOTE]
>
>**Windows Player批量注册**
>
>实施Windows播放器时，无需手动配置每个播放器。 相反，您可以在配置JSON文件经过测试并准备好部署后更新它。
>
>配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍必须手动注册每个播放器。

请按照以下步骤配置Windows 10播放器：

1. 安装Windows Player。
1. 在 ***%appdata%\com.aem.screens.player\config.json下查找配置文件***。
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性 {#policy-attributes}

下表汇总了包含示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| 服务器 | 指向Adobe Experience Manager(AEM)服务器的URL。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在完全配置并在生产中设置为false。 |
| enableOSD | 启用渠道切换器UI，让用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将其设置为false。 |
| enableActivityUI | 启用此选项可显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |

#### 示例策略JSON文件 {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

