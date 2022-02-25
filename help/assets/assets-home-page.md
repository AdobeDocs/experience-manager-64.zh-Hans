---
title: '"[!DNL Experience Manager Assets] 主页体验”'
description: 个性化资产主页，以获得丰富的欢迎屏幕体验，包括有关资产近期活动的快照。
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: d9cfb5376210234b3b05877509c273c52d9cecf3
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager Assets] 主页体验 {#aem-assets-home-page-experience}

个性化 [!DNL Experience Manager Assets] 提供丰富的欢迎屏幕体验的主页，包括有关资产近期活动的快照。

的 [!DNL Adobe Experience Manager Assets] 主页提供了丰富且个性化的欢迎屏幕体验，其中包括最近查看或上传的资产等活动的快照。

默认情况下，资产主页处于禁用状态。 要启用此功能，请执行以下步骤：

1. 访问 [!DNL Experience Manager] 配置管理器，单击 **[!UICONTROL “工具”>“操作”>“Web控制台”]**.
1. 打开 **Day CQ DAM事件记录器** 服务。
1. 选择 **[!UICONTROL 启用此服务]** 启用活动记录。

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. 从 **事件类型** 列表中，选择要记录的事件并保存更改。

   >[!CAUTION]
   >
   >启用“已查看的资产”、“已查看的项目”和“已查看的收藏集”选项，可显着增加已记录事件的数量。

1. 打开 **[!UICONTROL DAM资产主页功能标记]** 配置管理器中的服务 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 选择 **[!UICONTROL isEnabled.name]** 选项来启用资产主页功能。 保存更改。

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. 打开 **[!UICONTROL 用户首选项]** 对话框，然后选择 **[!UICONTROL 启用资产主页]**. 保存更改。

   ![user_preferences](assets/user_preferences.png)

启用资产主页后，从导航页面导航到资产用户界面。

![home_page](assets/home_page.png)

点按/单击 **[!UICONTROL 单击此处配置体验链接]** 添加用户名、背景图像和配置文件图像。

资产主页包括以下部分：

* 欢迎区
* 构件区域

**欢迎区**

如果您的用户档案存在，欢迎部分会显示一条发送给您的欢迎消息。 此外，它还会显示您的配置文件图片和欢迎图像（如果已配置）。

如果您的配置文件不完整，欢迎部分会显示一条通用的欢迎消息和配置文件图片的占位符。

**构件区域**

此部分显示在欢迎部分的下方，并在以下部分下显示现成小组件：

* 活动
* 最近
* 发现

**活动**:在本节中， **我的活动** 小组件显示登录用户通过资产（包括不含演绎版的资产）执行的近期活动，例如资产上传、下载、资产创建、编辑、评论、批注和共享。

**最近**:的 **最近查看的** 此部分下的小组件显示登录用户最近访问的实体，包括文件夹、收藏集和项目。

**Discover**:的 **新建** 此部分下的小组件会显示最近上传到的资产和演绎版 [!DNL Assets] 实例。

要启用清除用户活动数据的功能，请启用 **DAM事件清除服务** 从配置管理器。 启用此服务后，系统将删除超过指定数量的登录用户活动。

“欢迎”屏幕提供了简单的导航辅助工具，例如工具栏上用于访问文件夹、收藏集和目录的图标。

>[!NOTE]
>
>启用Day CQ DAM事件记录器和DAM事件清除服务可增加对JCR的写入操作和搜索索引，这会显着增加 [!DNL Experience Manager] 服务器。 上的附加负载 [!DNL Experience Manager] 服务器会影响其性能。

>[!CAUTION]
>
>捕获、筛选和清除资产主页所需的用户活动会对性能产生开销。 因此，管理员应该为目标用户有效地配置主页。
>
>Adobe建议执行批量操作的管理员和用户避免使用资产主页功能来阻止用户活动的增加。 此外，管理员还可以通过配置 **Day CQ DAM事件记录器** 从配置管理器。
>
>如果使用该功能，Adobe建议您根据服务器负载计划清除频率。
