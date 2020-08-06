---
title: 在通信管理中不发布基于角色的用户界面
seo-title: 在通信管理中不发布基于角色的用户界面
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 1%

---


# 在通信管理中不发布基于角色的用户界面 {#do-not-publish-role-based-user-interface-in-correspondence-management}

在AEM中，管理员可以为不同用户组提供基于角色的访问权限，以对不同资源执行各种操作。 例如，创建或编辑数据字典的功能只能提供给特定用户组中的用户，而其他用户只能视图和使用数据字典。

AEM界面会根据用户的访问级别显示创建或编辑资产类型等选项。 例如，如果用户没有创建数据字典的权限，则创建数据字典的选项不会显示在UI中。

尽管CRX允许您为用户和用户组帐户配置访问权限，但本文是关于基于角色或用户组的访问权限。

有关用户组、权限、访问控制列表以及管理用户和用户组的详细信息，请参 [阅用户管理和安全](/help/sites-administering/security.md)。

## 管理权限 {#managing-permissions}

1. 确保要为其管理权限的用户已添加到相关用户组。

   例如，用户John Doe添加到组 `agents` 和 `cm-creditcard`。 有关详细信息，请参阅将用户或用户组添加到用户组。 For more information, see [Managing Users and User Groups](/help/communities/users.md).

   ![]()

1. 创建适合允许预期权限的文件夹。

   例如，如果企业有住房抵押、信用卡和保险部门，则可以创建名为的文件夹 `HomeMortgage`, `CreditCard,`并保留相 `Insurance` 关资产，并有选择地向代理商提供仅与其部门相关的资产。

1. 要访问AEM WCM安全性，请执行下列操作之一：

   1. 从欢迎屏幕或AEM中的各个位置，单击安全图标：

   1. 直接导航到 `https://[server]:[port]/useradmin`。 请确保以管理员身份登录到AEM。

      ![]()
   左侧的树将列表系统中当前的所有用户和用户组。 您可以选择要显示的列，对列的内容进行排序，甚至通过将列标题拖动到新位置来更改列的显示顺序。

   这些选项卡提供对各种配置的访问：

1. 在左树列表中，多次点按相关组的名称，然后选择“权限”选项卡。

   要查找组的名称，您可以在提供的空间中键入组的名称。

1. 在权限选项卡中，导航到要添加权限的路径。 “Corresponcesing Management”文件夹位于该文 `content/apps/cm/` 件夹下。

   选中“成员”列中要对该路径具有权限的成员的复选框。 清除要删除其权限的成员的复选框。 您对单元格进行更改时，单元格中会出现一个红色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >文件夹中指定的权限将取代其子文件夹中指定的权限。

1. 点按保存。
1. 步骤文本
1. 步骤文本
1. 步骤文本

