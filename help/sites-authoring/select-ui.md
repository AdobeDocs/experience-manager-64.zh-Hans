---
title: 选择您的 UI
seo-title: 选择您的 UI
description: 配置您在 AEM 中工作时将使用的界面
seo-description: 配置您在 AEM 中工作时将使用的界面
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 70%

---


# 选择您的 UI{#selecting-your-ui}

## 了解UI

使用创作环境您可以：

* [创作](/help/sites-authoring/author.md)（包括[页面创作](/help/sites-authoring/author-environment-tools.md)、[资产管理](/help/assets/home.md)和[社区](/help/communities/author-communities.md)）

* 在网站上生成和维护内容时所需的[管理](/help/sites-administering/home.md)任务

提供的两种图形用户界面可以实现此操作。这两种用户界面通过任何主流浏览器均可访问：

1. 触屏优化 UI

   * 这是现代的默认AEM UI。
   * 主色调为灰色，且采用整洁的平面界面。
   * 专为在触屏和桌面设备上使用而设计，外观在所有设备上均相同，只是[查看和选择资源的方式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)略有不同（分别采用点按和单击方式）。

      * 桌面设备：

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * 平板电脑设备（或不到 1024 像素宽的台式机）：

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. 经典 UI

   * 这是旧式 UI，已在 AEM 中使用多年。
   * 主色调为绿色。
   * 专为在桌面设备上使用而设计。
   * 以下文档重点介绍新式 UI。有关在经典 UI 中进行创作的信息，请参阅[经典 UI 创作文档](/help/sites-classic-ui-authoring/classicui.md)。

   ![chlimage_1-232](assets/chlimage_1-232.png)

## 切换UI

Although the touch-enabled UI is now the standard UI and [feature parity](../release-notes/touch-ui-features-status.md) has been nearly reached with the administration and editing of sites, there may be times when the user wishes to switch to the [classic UI](/help/sites-classic-ui-authoring/classicui.md). 可使用几个选项进行切换。

>[!NOTE]
>
>有关与经典 UI 的功能对等性状态的详细信息，请参阅[触屏优化 UI 功能对等性](../release-notes/touch-ui-features-status.md)文档。

您可以在多个位置定义要使用的 UI：

* [配置实例的默认UI](#configuring-the-default-ui-for-your-instance) —— 这将设置用户登录时显示的默认UI，但用户可以覆盖此设置，为其帐户或当前会话选择其他UI。

* [为您的帐户设置经典UI创作](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) -这将设置编辑页面时用作默认UI的UI，但用户可以覆盖此设置，为其帐户或当前会话选择其他UI。

* [将当前会话切换为经典UI](#switching-to-classic-ui-for-the-current-session) —— 此操作会将当前会话切换为经典UI。

* 对于[页面创作，系统会重写某些与 UI 有关的设置](#ui-overrides-for-the-editor)。

>[!CAUTION]
>
>切换到经典 UI 的各种选项无法立即开箱即用，必须对您的实例进行专门配置。
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

>[!NOTE]
>
>对于从以前版本升级而来的实例，页面创作将继续使用经典 UI。
>
>After upgrade, page authoring will not be automatically switched to the touch-enabled UI, but you can configure this using the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). 请参阅[编辑器的 UI 重写](#ui-overrides-for-the-editor)。

## 配置实例的默认 UI {#configuring-the-default-ui-for-your-instance}

系统管理员可以通过使用[根映射](/help/sites-deploying/osgi-configuration-settings.md)配置启动和登录时显示的 UI。

该设置可能会被用户默认设置或会话设置所重写。

## 为您的帐户设置经典 UI 创作 {#setting-classic-ui-authoring-for-your-account}

每个用户都可以访问[用户首选项](/help/sites-authoring/user-properties.md)来定义自己是否希望使用经典 UI 进行页面创作（而不是默认 UI）。

该设置可能会被会话设置所重写。

## 将当前会话切换为经典 UI {#switching-to-classic-ui-for-the-current-session}

使用触屏优化 UI 时，桌面用户可能想要还原到经典（仅限桌面）UI。将当前会话切换到经典 UI 的方法有多种。

* **导航链接**

   >[!CAUTION]
   >
   >用于切换到经典 UI 的该选项无法立即开箱即用，必须对您的实例进行专门配置。
   >
   >
   >See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

   如果启用该选项，那么每当您将鼠标悬停在适用的控制台上时，都会显示一个图标（一个显示器符号），点按/单击它将在经典 UI 中打开相应的位置。

   例如，从&#x200B;**站点**&#x200B;到&#x200B;**站点管理员**&#x200B;的链接：

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   The classic UI can be accessed using the URL for the welcome screen at `welcome.html`. For example:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >触屏优化 UI 可以通过 `sites.html` 访问。例如：
   >
   >
   >`http://localhost:4502/sites.html`

### 编辑页面时切换为经典 UI {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>用于切换到经典 UI 的该选项无法立即开箱即用，必须对您的实例进行专门配置。
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

如果已启用，**打开经典 UI** 将可从&#x200B;**页面信息**&#x200B;对话框中访问：

![chlimage_1-49](assets/chlimage_1-49.png)

### 编辑器的 UI 重写 {#ui-overrides-for-the-editor}

创作页面时，系统可能会重写用户或系统管理员定义的设置。

* 创作页面时：

   * Use of the classic editor is forced when accessing the page using `cf#` in the URL. 例如：

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Use of the touch-enabled editor is forced when using `/editor.html` in the URL or when using a touch device. 例如：

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* 任何强制操作都是临时的，而且仅对浏览器会话有效

   * A cookie set will be set dependent on whether touch-enabled ( `editor.html`) or classic ( `cf#`) is used.

* 在通过 `siteadmin` 打开页面时，将检查以下各项是否存在：

   * Cookie
   * 用户首选项
   * 如果两者都不存在，则将默认使用 [WCM 创作 UI 模式服务](/help/sites-deploying/configuring-osgi.md)（**服务**）的 `AuthoringUIMode`OSGi 配置中设置的定义。

>[!NOTE]
>
>如果[用户已经为页面创作定义了首选项](#setting-classic-ui-authoring-for-your-account)，那么更改 OSGi 属性不会覆盖该设置。

>[!CAUTION]
>
>由于使用 Cookie，如之前所述，建议不要执行以下操作：
>
>* 手动编辑 URL - 非标准 URL 可能会导致未知情况和功能缺失。
>* 同时打开两种模式的编辑器 - 例如，在不同的窗口中打开。

>



