---
title: 配置帐户环境
seo-title: Configuring your account environment
description: AEM提供了配置帐户和创作环境某些方面的功能
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 50%

---

# 配置帐户环境{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM 提供了配置帐户和创作环境某些方面的功能。

使用 [用户](/help/sites-authoring/user-properties.md#user-settings) 选项 [标题](/help/sites-authoring/basic-handling.md#the-header) 和关联的 [我的首选项](#my-preferences) 对话框，您可以修改用户选项。

## 用户设置 {#user-settings}

的 **用户** 通过设置对话框，您可以访问：

* 模拟为

   * 使用 [模拟为](/help/sites-administering/security.md#impersonating-another-user) 功能用户可以代表其他用户工作。

* 配置文件

   * 提供一个指向您的 [用户设置](/help/sites-administering/security.md))

* [我的偏好设置](/help/sites-authoring/user-properties.md#my-preferences)

   * 指定用户特有的各种首选项设置

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## 我的偏好设置 {#my-preferences}

**我的首选项**&#x200B;对话框可通过标题中的[用户](/help/sites-authoring/user-properties.md#user-settings)选项进行访问。

每个用户都可以为自己设置特定的属性。

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **语言**

   这定义了用于创作环境UI的语言。 从可用列表中选择所需的语言。

   此配置还用于经典UI。

* **窗口管理**

   这定义打开窗口的行为。 选择：

   * **多窗口** （默认）

      * 页面将在新窗口中打开。
   * **单窗口**

      * 页面将在当前窗口中打开。


* **显示适用于资产的桌面操作**

   此选项需要AEM桌面应用程序才能使用。

* **注释颜色**

   这定义了进行注释时使用的默认颜色。

   * 单击颜色块以打开样本选择器以选择一种颜色。
   * 或者，可在字段中输入所需颜色的十六进制代码。

* **相对日期显示**

   为了提高可读性，AEM会将过去七天内的日期呈现为相对日期（例如三天前），将旧日期呈现为确切日期（例如2017年3月20日）。

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

   此选项会启用键盘快捷键。 默认情况下，这些功能处于启用状态，但可以将其禁用（例如，如果用户具有特定的辅助功能要求）。

* **使用经典版创作体验**

   此选项将启用 [经典UI](/help/sites-classic-ui-authoring/home.md)基于的页面创作。 默认情况下，使用标准UI。

* **启用资产主页**

   仅当系统管理员为整个组织启用了资产主页体验时，此选项才可用。
