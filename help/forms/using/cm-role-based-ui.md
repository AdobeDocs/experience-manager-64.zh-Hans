---
title: 在通信管理中不发布基于角色的用户界面
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: 在通信管理中不发布基于角色的用户界面
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# 在通信管理中不发布基于角色的用户界面 {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在AEM中，管理员可以提供基于角色的访问权限，以访问不同的用户组，从而对不同的资源执行各种操作。 例如，创建或编辑数据字典的功能仅可用于特定用户组中的用户，而其他用户只能查看和使用数据字典。

AEM界面会根据用户的访问级别显示相应选项，例如创建或编辑资产类型。 例如，如果用户没有创建数据字典的权限，则创建数据字典的选项不会显示在UI中。

尽管CRX允许您为用户和群组帐户配置访问权限，但本文介绍了基于角色或用户群组的访问权限。

有关群组、权限、访问控制列表以及管理用户和群组的更多信息，请参阅 [用户管理和安全](/help/sites-administering/security.md).

## 管理权限 {#managing-permissions}

1. 确保要为其管理权限的用户已添加到相关用户组。

   例如，用户John Doe会添加到群组中 `agents` 和 `cm-creditcard`. 有关更多信息，请参阅将用户或组添加到组。 有关更多信息，请参阅 [管理用户和用户组](/help/communities/users.md).

   ![]()

1. 创建适合允许预期权限的文件夹。

   例如，如果企业具有住房抵押、信用卡和保险部门，则可以创建名为 `HomeMortgage`, `CreditCard,`和 `Insurance` 保留相关资产，并有选择地向代理人提供与其部门有关的资产。

1. 要访问AEM WCM安全性，请执行以下操作之一：

   1. 从欢迎屏幕或AEM中的各个位置，单击安全图标：

   1. 直接导航到 `https://[server]:[port]/useradmin`. 确保您以管理员身份登录AEM。

      ![]()
   左侧树列出了系统中当前的所有用户和组。 您可以选择要显示的列，对列的内容进行排序，甚至通过将列标题拖动到新位置来更改列的显示顺序。

   通过选项卡，可以访问各种配置：

1. 在左侧树列表中，双击相关群组的名称，然后选择权限选项卡。

   要找到组的名称，您可以在提供的空格中键入组的名称。

1. 在“权限”选项卡中，导航到要向其添加权限的路径。 通信管理文件夹位于 `content/apps/cm/` 文件夹。

   选中要拥有该路径权限的成员列中的复选框。 清除要删除其权限的成员的复选框。 在您对进行更改的单元格中，会出现一个红色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >文件夹中指定的权限将取代其子文件夹中指定的权限。

1. 点按保存。
1. 步骤文本
1. 步骤文本
1. 步骤文本

