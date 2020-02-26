---
title: 将AEM 3D与Autodesk 3ds Max集成
seo-title: 将AEM 3D与AutoDesk 3ds Max集成
description: 您可以选择将AEM 3D与Autodesk 3ds Max软件集成，以支持本机3ds Max文件(.MAX)。 目前不支持通过3ds Max进行渲染。
seo-description: 您可以选择将AEM 3D与Autodesk 3ds Max软件集成，以支持本机3ds Max文件(.MAX)。 目前不支持通过3ds Max进行渲染。
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# 将AEM 3D与Autodesk 3ds Max集成 {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>此任务是可选的，并且仅适用于Windows。

您可以选择将AEM 3D与Autodesk 3ds Max软件集成，以支持本机3ds Max文件(.MAX)。 目前不支持通过3ds Max进行渲染。

请参阅 [高级配置设置](advanced-config-3d.md)。

另请参 [阅将AEM 3D与AutoDesk Maya集成](integrate-maya-with-3d.md)。

**要将AEM 3D与Autodesk 3ds Max集成，请执行以下操作**:

1. 在安装了AEM作者节点的同一台服务器上安装Autodesk 3ds Max软件。

   安装后，请验证您是否可以打开和使用Maya，并且不存在许可问题。

   >[!NOTE]
   >
   >要避免访问被拒绝的问题，请使用与AEM相同的管理员用户帐户安装3ds Max。

1. 在3ds Max中，单击“ **[!UICONTROL 自定义”>“插件管理器”]**。

   找 `FBXMAX.DLU` 到并验证其 **[!UICONTROL 状态为]** [!UICONTROL **loaded**。

   关闭 **[!UICONTROL Plug-In Manager(增效工具管理器]** )对话框和3ds Max(3ds Max)。

1. 更新转换脚本。

   AEM使用命令行脚本调用3ds Max命令行实用程序 `3dsmaxcmd.exe`。 如果您安装了3ds Max 2016以外的版本，或者您将3ds max安装到了非标准位置，或者您将AEM安装在了其他分区或驱动器上，则必须编辑此脚本。

   1. 打开CRXDE Lite并导航到 `/libs/settings/dam/v3D/scripts/max`。
   1. 双击以 `export-fbx.bat` 打开它。
   1. 根据需要编辑脚本的第一行以反映实用程序的位 `3dsmaxcmd.exe` 置。 例如，如果使用3ds Max 2017，并且AEM安装在其他磁盘驱动器上：
   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. 在CRXDE lite页面的左上角附近，点按全 **[!UICONTROL 部保存]**。

   在CRXDE lite页面的左上角附近，点按全 **[!UICONTROL 部保存]**。

1. 删除工作文件夹（仅在以前尝试摄取。MAX文件时必需）。

   1. 在CRXDE Lite中，导航到 `/libs/settings/dam/v3D/Paths/maxWorkPath`。 默认情况下，此设置的值 `./MaxWork`为，它相对于AEM安装根文件夹。
   1. 登录到服务器本身，然后使用文件资源管理器导航到AEM安装根文件夹。
   1. 删除 **[!UICONTROL MaxWork]** 文件夹（包括其整个内容）（如果它存在）。

      下次摄取。MAX文件时，会自动重新创建文件夹。

1. 通过执行以下操作，为摄取启用3ds Max:

   1. 在CRXDE Lite中，导航到并 `/libs/settings/dam/v3D/assetTypes/max` 将“启用”属 **[!UICONTROL 性设置]** 为true:
   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. 在CRXDE lite页面的左上角附近，点按全 **[!UICONTROL 部保存]**。

## 测试AEM 3D与Autodesk 3ds Max的集成 {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. 打开AEM资产，然后将位 `.max` 于的文件上 `sample-3D-content/models` 传到 **[!UICONTROL test3d文件夹]** 。

   请注意，之前下载了sample-3D-content.zip以验证基本的3D功能。

1. 返回卡片视 **[!UICONTROL 图]** ，并观察已上传资产上显示的消息横幅。

   当3ds Max将本机3ds max格式转换为。FBX时，将显示“转换格式”横幅。

1. 处理完成后，在“详细信 `logo-sphere.max` 息”视图 **[!UICONTROL 中打开]** 。

   预览体验与预览体验相同 `logo_sphere.fbx`。

