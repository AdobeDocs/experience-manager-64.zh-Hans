---
title: 配置同步调度程序
seo-title: Configuring the synchronization scheduler
description: 了解如何迁移和同步资产、配置同步调度程序以及使用文件夹来排列资产。
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---

# 配置同步调度程序 {#configuring-the-synchronization-scheduler}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

默认情况下，同步计划程序每3分钟运行一次，以通过LiveCycle工作台11同步存储库中修改和更新的所有资产。 同步过程完成后，包含表单和资源的应用程序将在AEM Forms用户界面中可见。

## 更改同步调度程序的间隔 {#change-interval-of-the-synchronization-scheduler}

执行以下步骤以更改同步调度程序的间隔：

1. 登录到AEM Configuration Manager。 配置管理器的URL是 `https://[Server]:[Port]/lc/system/console/configMgr`

1. 找到并打开 **FormsManager配置** 捆绑。

1. 为 **同步调度程序频率** 选项。

   频率的单位是分钟。 例如，要将调度程序配置为每60分钟运行一次，请指定60。

## 同步资产 {#synchronizing-assets}

您可以使用 **同步存储库中的资产** 选项来手动同步资产。 请执行以下步骤以手动同步资产：

1. 登录AEM Forms。 默认URL为 `https://[Server]:[Port]/lc/aem/forms/`.

   ![AEM Forms用户界面](assets/aem_forms_ui.png)

   **图：** *AEM Forms用户界面*

1. 单击 ![aem6forms_sync](assets/aem6forms_sync.png) 图标。 如果您在最后配置的路径上没有任何资产，则会出现如下所示的对话框。 单击 **开始** 启动同步。

   ![“同步”对话框](assets/migrate-and-syncronize.png)

   **图：** *“同步”对话框*

## 同步错误疑难解答 {#troubleshooting-synchronization-error}

您可以在工作流设计器(LiveCycle工作台)中创建新应用程序。

如果新创建的应用程序和位于/content/dam/formsanddocuments的文件夹具有相同的名称，则会出现错误“*根级别已存在与此应用程序同名的资产。*“ ”。

要解决冲突，请重命名应用程序，然后手动同步资产。

![“资产同步”对话框中的冲突](assets/sync-conflict.png)

**图：** *“资产同步”对话框中的冲突*
