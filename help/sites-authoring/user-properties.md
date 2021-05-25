---
title: 配置帐户环境
seo-title: 配置帐户环境
description: AEM 提供了用于配置帐户和创作环境的某些方面的功能
seo-description: AEM 提供了用于配置帐户和创作环境的某些方面的功能
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 95%

---

# 配置帐户环境{#configuring-your-account-environment}

AEM 提供了配置帐户和创作环境某些方面的功能。

使用[标题](/help/sites-authoring/basic-handling.md#the-header)和关联的[我的首选项](#my-preferences)对话框中的[User](/help/sites-authoring/user-properties.md#user-settings)选项，可以修改用户选项。

## 用户设置 {#user-settings}

在&#x200B;**用户**&#x200B;设置对话框中，您可以访问：

* 模拟为

   * 借助[模拟为](/help/sites-administering/security.md#impersonating-another-user)功能，用户可以代表其他用户工作。

* 个人资料

   * 提供一个指向您的[用户设置](/help/sites-administering/security.md)的便捷链接

* [我的首选项](/help/sites-authoring/user-properties.md#my-preferences)

   * 指定用户特有的各种首选项设置

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## 我的首选项 {#my-preferences}

**我的首选项**&#x200B;对话框可通过标题中的[用户](/help/sites-authoring/user-properties.md#user-settings)选项进行访问。

每个用户都可以为自己设置特定的属性。

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **语言**

   此选项定义要用于创作环境 UI 的语言。从可用列表中选择所需语言。

   此配置也可用于经典 UI。

* **窗口管理**

   此选项定义打开窗口的行为。选择：

   * **多窗口**（默认）

      * 页面将在新窗口中打开。
   * **单一窗口**

      * 页面将在当前窗口中打开。


* **显示适用于资产的桌面操作**

   此选项要求使用 AEM 桌面应用程序。

* **注释颜色**

   此选项定义创建注释时使用的默认颜色。

   * 单击颜色块可打开色板选择器以选择一种颜色。
   * 或者，可在字段中输入所需颜色的十六进制代码。

* **相对日期显示**

   为了提高可读性，AEM 会将过去七天内的日期显示为相对日期（例如三天前），而将更早的日期则显示为确切日期（例如 2017 年 3 月 20 日）。

   此选项定义系统中日期的显示方式。以下选项可供选择：

   * **始终显示确切日期**：将始终显示确切日期（从不显示相对日期）。
   * **1 天**：对于一天内的日期显示相对日期，其他情况则显示确切日期。
   * **7 天（默认）**：对于七天内的日期显示相对日期，其他情况则显示确切日期。
   * **1 个月**：对于一个月内的日期显示相对日期，其他情况则显示确切日期。
   * **1 年**：对于一年内的日期显示相对日期，其他情况则显示确切日期。
   * **始终显示相对日期**：从不显示确切日期，只显示相对日期。

* **启用快捷键**

   AEM 支持使用许多键盘快捷键，以便更高效地进行创作。

   * [用于编辑页面的键盘快捷键](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [控制台的键盘快捷键](/help/sites-authoring/keyboard-shortcuts.md)

   此选项可启用键盘快捷键。默认情况下，这些键盘快捷键处于启用状态，但也可以将其禁用，例如，当用户要求使用特定辅助功能时。

* **使用经典的创作体验**

   此选项可启用基于[经典 UI](/help/sites-classic-ui-authoring/home.md) 的页面创作。默认情况下将使用标准 UI。

* **启用资产主页**

   仅当系统管理员为整个组织启用了资产主页体验时，此选项才可用。
