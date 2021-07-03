---
title: 专用文件夹共享
description: 了解如何在Adobe Experience Manager(AEM)Assets中创建专用文件夹，并将其与其他用户共享，以及如何为其分配各种权限。
contentOwner: AG
feature: 协作
role: User
exl-id: b6aa3cba-4085-47ac-a249-7461baee2a00
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 26%

---

# 专用文件夹共享 {#private-folder-sharing}

您可以在Adobe Experience Manager(AEM)Assets用户界面中创建专供您使用的专用文件夹。 您可以将此专用文件夹共享给其他用户，并为其分配各种权限。 根据您分配的权限级别，用户可以在文件夹中执行各种任务，例如查看文件夹中的资产或编辑资产。

1. 在“资产”控制台中，点按/单击工具栏中的&#x200B;**[!UICONTROL 创建]** ，然后从菜单中选择&#x200B;**[!UICONTROL 文件夹]**。

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 在&#x200B;**[!UICONTROL 添加文件夹]**&#x200B;对话框中，输入文件夹的标题和名称（可选），然后选择&#x200B;**[!UICONTROL 专用]**。

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. 点按/单击&#x200B;**[!UICONTROL 创建]**。在UI中创建专用文件夹。

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. 要与其他用户共享文件夹并为用户分配权限，请选择文件夹，然后单击/点按工具栏中的&#x200B;**[!UICONTROL 属性]**&#x200B;图标。

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >在您共享文件夹之前，任何其他用户都看不到该文件夹。

1. 在“文件夹属性”页面的&#x200B;**[!UICONTROL 添加用户]**&#x200B;列表中选择一个用户，在您的专用文件夹上为该用户分配角色，然后单击&#x200B;**[!UICONTROL 添加]**。

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >对于您向其共享文件夹的用户，您可以分配各种角色，例如“编辑者”‘、“所有者”或“查看者”。如果为用户分配“所有者”角色，则用户对该文件夹具有“编辑者”权限。 此外，用户还可以与他人共享该文件夹。 如果您为用户分配了“编辑者”角色，则用户可以编辑您专用文件夹中的资产。 如果您为用户分配了“查看者”角色，用户就只能查看您专用文件夹中的资产。

1. 单击&#x200B;**[!UICONTROL 保存]**。根据您分配的角色，用户在登录 AEM Assets 时便会被分配一组针对您的专用文件夹所拥有的权限。
1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;以关闭确认消息。
1. 您向用户共享文件夹时，用户会收到共享通知。使用用户的凭据登录AEM Assets以查看通知。

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. 点按/单击通知图标以打开通知列表。

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. 单击/点按管理员共享的专用文件夹的条目，以打开该文件夹。

>[!NOTE]
>
>要创建专用文件夹，您需要对要在其中创建专用文件夹的父文件夹具有读取和编辑ACL权限。 如果您不是管理员，则在&#x200B;*/content/dam*&#x200B;上默认不会为您启用这些权限。 在这种情况下，请先获取用户ID/组的这些权限，然后再尝试创建专用文件夹或查看文件夹设置。
