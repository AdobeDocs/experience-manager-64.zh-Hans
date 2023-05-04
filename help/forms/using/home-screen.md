---
title: 主屏幕
seo-title: Home screen
description: AEM Forms应用程序主屏幕组件的描述
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 1%

---

# 主屏幕 {#home-screen}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

登录AEM Forms应用程序后，您将被重定向到主屏幕。

## 默认主屏幕 {#default-home-screen}

默认情况下，主屏幕显示所有表单，包括起点和任务(如果连接的服务器启用了AEM Forms工作流)以及关联的缩略图。 您可以在AEM Forms服务器中指定缩略图。

下图用默认主屏幕上基本组件的标注进行了说明。
![Forms应用程序主屏幕](assets/home-screen-1.png)
[单击放大](assets/home-screen-1-1.png)

1. **“菜单”按钮**:点按 **菜单** 按钮以导航到“任务”、“Forms”、“发件箱”和“设置”。 如果您的AEM Forms应用程序已连接到AEM Forms JEE服务器，则可以看到任务选项。 “任务”选项还存储从进程中的任务创建的草稿。 对于AEM Forms OSGi服务器，任务选项处于隐藏状态。 发件箱在与服务器同步之前会存储保存的表单和草稿。 应用程序启动后，发件箱中所有保存的表单和草稿都会上传到AEM Forms服务器 [与服务器同步](/help/forms/using/sync-app.md). 有关“设置”的信息，请参阅 [更新常规设置](/help/forms/using/update-general-settings.md).
1. **任务或表单**:点按要处理的列出任务或表单。
1. **水平省略号**:表示操作可用于表单。 点按省略号会显示作者提供的操作和描述。 的 **删除草稿** 和 **完成** 选项在您点按省略号时可见。
1. **“刷新”图标**:点按刷新图标，将您的应用程序与AEM Forms服务器同步。

## 自定义主屏幕 {#customizing-the-home-screen}

![常规设置](assets/gen-settings.png)

您可以从 **[常规设置](/help/forms/using/update-general-settings.md)** ，或从 **首选项** 选项卡。

对应用程序上的主屏幕设置所做的更改会影响当前已记录用户或当前移动设备用户的主屏幕。

但是，在HTML工作区中所做的更改会影响登录到AEM Forms服务器的所有AEM Forms应用程序用户。
