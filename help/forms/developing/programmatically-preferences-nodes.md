---
title: 以编程方式管理PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: 使用首选项管理器服务API(Java)以编程方式管理首选项节点。
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 以编程方式管理首选项节点 {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本主题介绍如何使用首选项管理器服务API(Java)以编程方式管理首选项节点。

您可以从管理员UI手动更改配置设置。 要更改选项，请导航到 `Home>Settings>User Management> Configuration>Manual Configuration`. 导入 `config.xml` 进行更改后，您会注意到除在节点进行的更改外的所有更改 `/Adobe/Adobe Experience Manager Forms/Config/UM persist` 丢失。 用户管理导入和导出的预览不支持更改其他组件的配置设置。 现在，可以使用 `PreferencesManagerServiceClient` API。

**步骤摘要**&#x200B;要以编程方式管理“首选项”节点，请执行以下步骤：

1. 包括项目文件。
1. 创建PreferencesManagerService客户端
1. 调用适当的角色或权限操作

**包含项目文件**

在开发项目中包含必需的文件。 如果您使用Java创建客户端应用程序，请包含必要的JAR文件。 如果您使用的是Web服务，请确保包含代理文件。

**创建PreferencesManagerService客户端**

在以编程方式执行用户管理首选项管理器服务操作之前，必须创建首选项管理器服务客户端。 使用Java API，可通过创建PreferencesManagerServiceClient对象来完成此操作。

**调用适当的角色或权限操作**

创建服务客户端后，可以调用首选项管理器操作。 服务客户端允许您读取和设置权限。
