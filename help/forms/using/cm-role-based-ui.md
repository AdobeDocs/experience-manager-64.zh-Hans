---
title: 在通信管理中不发布基于角色的用户界面
seo-title: 在通信管理中不发布基于角色的用户界面
description: 在通信管理中不发布基于角色的用户界面
seo-description: 在通信管理中不发布基于角色的用户界面
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: e077347bc202b6a411006032c68aa4a3152be7c5
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---


# 在通信管理{#do-not-publish-role-based-user-interface-in-correspondence-management}中不发布基于角色的用户界面

在AEM中，管理员可以为不同用户组提供基于角色的访问权限，以对不同资源执行各种操作。 例如，创建或编辑数据字典的功能只能提供给特定用户组中的用户，而其他用户只能视图和使用数据字典。

AEM界面会根据用户的访问级别显示创建或编辑资产类型等选项。 例如，如果用户没有创建数据字典的权限，则创建数据字典的选项不会显示在UI中。

尽管CRX允许您为用户和用户组帐户配置访问权限，但本文是关于基于角色或用户组的访问权限。

有关用户组、权限、访问控制列表以及管理用户和用户组的详细信息，请参阅[用户管理和安全](/help/sites-administering/security.md)。

## 管理权限{#managing-permissions}

1. 确保要为其管理权限的用户已添加到相关用户组。

   例如，用户John Doe被添加到组`agents`和`cm-creditcard`。 有关详细信息，请参阅将用户或用户组添加到用户组。 有关详细信息，请参阅[管理用户和用户组](/help/communities/users.md)。

   ![]()

1. 创建适合允许预期权限的文件夹。

   例如，如果企业有住房抵押、信用卡和保险部门，则可以创建名为`HomeMortgage`、`CreditCard,`和`Insurance`的文件夹，以保留相关资产，并有选择地向代理商提供仅与其部门相关的资产的访问权限。

1. 要访问AEM WCM安全性，请执行下列操作之一：

   1. 从欢迎屏幕或AEM中的各个位置，单击安全图标：

   1. 直接导航到`https://[server]:[port]/useradmin`。 请确保以管理员身份登录到AEM。

      ![]()
   左侧的树将列表系统中当前的所有用户和用户组。 您可以选择要显示的列，对列的内容进行排序，甚至通过将列标题拖动到新位置来更改列的显示顺序。

   这些选项卡提供对各种配置的访问：

1. 在左树列表中，多次点按相关组的名称，然后选择“权限”选项卡。

   要查找组的名称，您可以在提供的空间中键入组的名称。

1. 在权限选项卡中，导航到要添加权限的路径。 Corresponcesing Management文件夹位于`content/apps/cm/`文件夹下。

   选中“成员”列中要对该路径具有权限的成员的复选框。 清除要删除其权限的成员的复选框。 您对单元格进行更改时，单元格中会出现一个红色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >文件夹中指定的权限将取代其子文件夹中指定的权限。

1. 点按保存。
1. 步骤文本
1. 步骤文本
1. 步骤文本

