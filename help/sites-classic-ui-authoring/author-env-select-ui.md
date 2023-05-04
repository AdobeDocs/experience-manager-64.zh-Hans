---
title: 选择您的UI
seo-title: Selecting your UI
description: 为了方便用户创作，触屏UI允许在必要时切换到经典UI。
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 997040d4-cf8f-4240-8423-a98d562aae02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 2%

---

# 选择您的UI{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

由于触屏优化UI取代了经典UI，因此AEM实例的用户或管理员必须做出积极决定，以继续使用经典UI。 由于经典UI不再进行维护，因此创作用户无法简单地从经典UI切换到触屏UI中的等效UI。

为了方便用户创作，触屏UI允许在必要时切换到经典UI。 请参阅 [选择您的UI](/help/sites-authoring/select-ui.md) ，以了解详细信息。

>[!NOTE]
>
>从以前版本升级的实例将保留经典UI用于页面创作。
>
>升级后，页面创作不会自动切换到触屏优化UI，但您可以使用 [OSGi配置](/help/sites-deploying/configuring-osgi.md) 的 **WCM创作UI模式服务** ( `AuthoringUIMode` 服务)。 请参阅 [编辑器的UI覆盖](#uioverridesfortheeditor).

## 为实例配置默认UI {#configuring-the-default-ui-for-your-instance}

系统管理员可以使用配置启动和登录时显示的UI [根映射](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

该设置可能会被用户默认设置或会话设置所覆盖。
