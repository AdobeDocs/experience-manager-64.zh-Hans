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
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# 将AEM 3D与Autodesk 3ds Max集成 {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>此任务是可选的，仅适用于Windows。

您可以选择将AEM 3D与Autodesk 3ds Max软件集成，以支持本机3ds Max文件(.MAX)。 目前不支持通过3ds Max进行渲染。

请参 [阅高级配置设置](advanced-config-3d.md)。

另请参 [阅将AEM 3D与AutoDesk Maya集成](integrate-maya-with-3d.md)。

**要将AEM 3D与Autodesk 3ds Max集成，请**:

1. 在安装AEM作者节点的服务器上安装Autodesk 3ds Max软件。

   安装后，请验证您是否可以打开和使用Maya，并且不存在许可问题。

   >[!NOTE]
   >
   >要避免访问被拒绝问题，请使用与AEM相同的管理员用户帐户安装3ds Max。

1. 在3ds Max中，单击“ **[!UICONTROL 自定义”>“插件管理器”]**。

   找到 `FBXMAX.DLU` 并验证其 **[!UICONTROL 状态]** 已 **[!UICONTROL 加载]**。

   关闭“ **[!UICONTROL 插件管理器]** ”对话框和3ds Max。

1. 更新转换脚本。

   AEM使用命令行脚本调用3ds Max命令行实用程序 `3dsmaxcmd.exe`。 如果安装的不是3ds Max 2016版本，或者将3ds Max安装到非标准位置，或者如果将AEM安装到其他分区或驱动器，则必须编辑此脚本。

   1. 打开CRXDE Lite并导航到 `/libs/settings/dam/v3D/scripts/max`。
   1. 多次单 `export-fbx.bat` 击以打开它。
   1. 根据需要编辑脚本的第一行，以反映实用程序的 `3dsmaxcmd.exe` 位置。 例如，如果使用3ds Max 2017，并且AEM安装在其他磁盘驱动器上：

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. 在CRXDE Lite页面的左上角附近，点按全部 **[!UICONTROL 保存]**。

   在CRXDE Lite页面的左上角附近，点按全部 **[!UICONTROL 保存]**。

1. 删除工作文件夹（仅当以前尝试摄取。MAX文件时，才必需）。

   1. 在CRXDE Lite中，导航到 `/libs/settings/dam/v3D/Paths/maxWorkPath`。 默认情况下，此设置的值 `./MaxWork`是相对于AEM install根文件夹。
   1. 登录到服务器本身，然后使用文件资源管理器导航到AEM install根文件夹。
   1. 删除 **[!UICONTROL MaxWork]** 文件夹（包括其整个内容）（如果它存在）。

      下次摄取。MAX文件时，会自动重新创建文件夹。

1. 通过执行以下操作，启用3ds Max进行摄取：

   1. 在CRXDE Lite中，导 `/libs/settings/dam/v3D/assetTypes/max` 航到并将“启 **[!UICONTROL 用]** ”属性设置为true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. 在CRXDE Lite页面的左上角附近，点按全部 **[!UICONTROL 保存]**。

## 测试AEM 3D与Autodesk 3ds Max的集成 {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. 打开AEM Assets，然 `.max` 后将位于test3d文 `sample-3D-content/models` 件 **[!UICONTROL 夹中的文件上传]** 。

   请注意，sample-3D-content.zip之前是为验证基本3D功能而下载的。

1. 返回卡 **[!UICONTROL 视图]** ，观察已上传资产上显示的消息横幅。

   当3ds Max将本机3ds Max格式转换为。FBX时，将显示“转换格式”横幅。

1. 处理完成后，在“详细信 `logo-sphere.max` 息”视图 **[!UICONTROL 中打开]** 。

   预览体验与体验相同 `logo_sphere.fbx`。

