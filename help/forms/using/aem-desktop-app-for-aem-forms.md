---
title: AEM桌面应用程序，AEM Forms
seo-title: AEM desktop app for AEM Forms
description: AEM桌面应用程序允许您将Adobe Experience Manager(AEM)Assets存储库和AEM Forms二进制文件映射到您系统上的网络目录。 进一步了解AEM桌面应用程序中支持的资产以及如何启用AEM Forms for AEM桌面应用程序。
seo-description: AEM desktop app lets you map the Adobe Experience Manager (AEM) Assets repository and AEM Forms binary files to a network directory on your system. Learn more about the assets supported in AEM desktop app and how to enable AEM Forms for AEM desktop app.
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
role: Admin
exl-id: 26cd0851-cadf-4a8f-b3bf-59f77671f584
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# AEM桌面应用程序，AEM Forms {#aem-desktop-app-for-aem-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM桌面应用程序允许您将Adobe Experience Manager(AEM)Assets存储库和AEM Forms二进制文件映射到您系统上的网络目录。 您可以在文件资源管理器中查看已同步的资产和二进制文件，并根据需要使用各种应用程序来编辑文件。 除了查看文件外，您还可以创建、上传和删除二进制文件。 您还可以直接从软件打开、编辑和保存文件。 例如，您可以直接从Designer中打开和编辑XDP文件。 您在本地对资产所做的更改会反映在AEM Assets存储库和AEM Forms UI中。

您可以从AEM实例下载应用程序。 有关下载应用程序的详细信息，请参阅 [AEM桌面应用程序发行说明](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html).

## AEM Forms桌面应用程序支持的AEM资产 {#aem-forms-assets-supported-in-aem-desktop-app}

您可以使用该应用程序同步以下类型的AEM Forms二进制文件：表单模板(.xdp)、PDF表单(.pdf)、文档(.pdf)、图像、XML架构(.xsd)、样式表(.xfs)。 应用程序将所有其他文件（不支持的文件）列为0字节文件。 将不受支持的文件列为0字节文件可确保用户知道AEM Forms服务器上存在其他可用资产。

>[!NOTE]
>
>文件名只能包含字母数字字符、连字符或下划线。

## 为AEM桌面应用程序启用AEM Forms {#enable-aem-forms-for-aem-desktop-app}

AEM桌面应用程序在Microsoft Windows上使用WebDAV协议，在Mac OS X上使用SMB1连接到AEM Forms服务器。 开箱即用地，AEM Forms服务器未启用与WebDAV或SMB客户端同步二进制文件和其他资产的功能。 执行以下步骤以启用AEM Forms for AEM桌面应用程序：

1. 以管理员身份登录AEM Forms。
1. 在创作实例中，单击 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager >工具]** ![锤子](assets/hammer.png) **[!UICONTROL >部署>操作> Web控制台]**. Web控制台将在新窗口中打开。
1. 在Web控制台窗口中，找到并打开 **[!UICONTROL FormsManager AddOn配置]** 选项。
1. 在FormsManager的“加载项配置”对话框中，取消选择 **[!UICONTROL 异步同步资源]** 复选框，然后单击 **[!UICONTROL 保存]**.
1. 重新启动AEM Forms服务器。 重新启动后，AEM Forms服务器将能够接受内容并与AEM桌面应用程序共享内容。
1. 打开应用程序并连接到AEM Forms服务器。

   成功连接后，应用程序将填充 `content/dam` 和 `content/dam/formsanddocuments` 文件夹。 除了将文件从上面的文件夹移动到本地文件夹（反之亦然）之外，您还可以使用应用程序在自动填充的文件夹之间移动内容。
