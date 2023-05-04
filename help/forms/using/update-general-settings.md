---
title: 更新常规设置
seo-title: Updating general settings
description: 更新AEM Forms应用程序设置（如“主页”屏幕），并获取“起点和附件”选项
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# 更新常规设置 {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过AEM Forms应用程序的常规设置，您可以指定设置，如获取附件、脱机模式、登陆屏幕、默认类别和自动保存频率。

## 更新应用程序中的“常规”设置 {#working-with-the-form}

将应用程序与AEM Forms服务器同步后，所有表单和定义的任务都会下载到您的移动设备。

开箱即用的AEM Forms应用程序解决方案不会在同步应用程序时下载与每个表单关联的附件。

在“常规”选项卡中，更改下载附件、脱机模式、登陆屏幕、自动保存和同步设置。 您可以更改 [主屏幕](/help/forms/using/home-screen.md) 的URL。

**导航到设置屏幕上的常规选项卡**

1. 要转到设置屏幕，请点按主屏幕左上角的菜单按钮，然后点按 **设置**.
1. 在设置屏幕中，点按常规选项卡。

   ![AEM Forms应用程序中的常规设置](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >这些选项在不同移动设备上的显示方式可能不同。

### 常规设置 {#general-settings}

您可以对应用程序的设置进行以下更改。

* **获取任务附件**:指定在将每个任务下载到您的应用程序时是否下载关联的附件。

* **脱机模式**:启用或禁用AEM Forms应用程序的离线服务。 请参阅 [在脱机模式下工作](/help/forms/using/work-offline-mode.md) 以了解详细信息。

* **登陆屏幕**:设置开始位置([主屏幕](/help/forms/using/home-screen.md))。

   可用选项：

   * Forms
   * 任务
   * 收藏夹

* **默认类别**:允许您选择要在主屏幕中显示的表单类别。 选择“全部”后，您可以在主屏幕中看到所有表单。 类别是根据应用程序中加载的表单来填充的。 Forms基于AEM Forms服务器中指定的表单设置，在应用程序中可用。

* **自动保存频率**:设置 [移动设备应用程序保存表单数据](/help/forms/using/autosave-data-app.md) 本地。

* **同步频率**:设置 [移动设备应用程序已同步](/help/forms/using/sync-app.md) 在联机模式下使用AEM Forms服务器。

**清除本地数据**:清除数据库，包括设备中所有用户的设置和本地数据以及文件存储。

>[!NOTE]
>
>清除缓存会立即将您从应用程序中注销。
>
>但是，系统将提示您确认清除缓存操作。
