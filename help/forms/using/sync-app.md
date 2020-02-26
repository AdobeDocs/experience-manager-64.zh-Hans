---
title: 同步应用程序
seo-title: 同步应用程序
description: 将移动设备上的AEM Forms应用程序与AEM Forms服务器同步。
seo-description: 将移动设备上的AEM Forms应用程序与AEM Forms服务器同步。
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18

---


# 同步应用程序 {#synchronizing-the-app}

## 同步应用程序 {#synchronizing-the-app-1}

应用程序中的表单将从AEM Forms服务器下载。 表单将下载在“任务”和“表单”选项卡下。 从表单创建的草稿下载到草稿选项卡中，从任务创建的草稿下载到任务选项卡中。 对于OSGi服务器上的独立表单，表单和草稿分别以“表单”和“草稿”选项卡下载。

完成并提交表单后，如果应用程序处于联机状态，则表单将立即上传回AEM Forms服务器。 同步应用程序时，将从服务器获取表单。 但是，如果应用程序处于联机状态，草稿会立即与服务器同步。

默认情况下，当您与AEM Forms服务器联机时，您的应用程序每15分钟同步一次。 但是，您可以选择更改同步频率。 或者，您也可以随时手动同步应用程序。

**手动同步应用程序**

点按主屏 ![幕右下角的](assets/sync-app.png) “同步”按钮sync-app。

**更改同步频率**

1. 要转到“设置”屏幕，请点按“主页”屏幕左上角的菜单按钮，然后点按“设 **置”**。
1. 在设置屏幕中，点按常规选项卡。

   ![“常规设置”窗口中的同步频率设置](assets/gen-settings-1.png)

1. 在“同步频率”选项上，点按“同步频率”右侧的值。
1. 在下拉列表中，选择新的同步频率。

### 技术规范 {#technical-specifications}

* 将脱机应用程序数据提交到AEM Forms服务器的主逻辑包含在runtime/offline/util/offline.js中。
* 在。js中，对processOfflineSubmittedSavedTasks(...)函数的调用将保存的／已提交的任务发送到服务器。 它还处理同步过程中的任何错误或冲突。 如果任务提交失败，则应用程序上的任务将标记为失败。 此外，任务仍保留在发件箱中。
* syncSubmittedTask()和syncSavedTask()函数对单个任务执行操作。
* 在用户选择将脱机状态同步到服务器或通过后台线程自动同步后，任务列表组件将启动对processOfflineSubmittedSavedTasks()函数的调用。

[联系支持](https://www.adobe.com/account/sign-in.supportportal.html)
