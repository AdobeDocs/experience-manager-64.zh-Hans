---
title: 配置用户和用户组
seo-title: Configure Your Users and User Groups
description: 请阅读本页，了解用户角色以及如何配置用户和群组，以支持On-Demand Services移动应用程序的创作和管理。
seo-description: Follow this page to understand the user roles and how to configure your users and groups to support the authoring and mangement of your mobile On-Demand services app.
uuid: 461e1725-41dd-4883-92b9-a7e175660401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: c3c73e67-7f85-4308-b4cd-1b42d4f3f2d9
exl-id: 690ae90f-ecd9-4115-9882-ce88ae38df5b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---

# 配置用户和用户组 {#configure-your-users-and-user-groups}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（例如React）的项目使用SPA编辑器。 [了解详情](/help/sites-developing/spa-overview.md).

本章介绍用户角色以及如何配置用户和群组以支持移动设备应用程序的创作和管理。

## AEM Mobile应用程序用户和组管理 {#aem-mobile-application-users-and-group-administration}

### AEM Mobile应用程序内容作者（应用程序作者组） {#aem-mobile-application-content-authors-app-author-group}

应用程序作者组的成员负责创作AEM移动应用程序内容，包括页面、文本、图像和视频。

#### 组配置 — 应用程序作者 {#group-configuration-app-authors}

1. 创建一个名为“app-authors”的新用户组：

   导航到用户Admin Console: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   在用户组控制台中，选择“+”按钮以创建组。

   将此组的ID设置为“应用程序作者”，表示它是特定于在AEM中创作移动应用程序的特定类型的作者用户组。

1. 将成员添加到组：作者

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. 现在，您已创建应用程序作者用户群组，接下来可以通过 [用户管理控制台](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. 以下内容允许您添加到AEM内容作者组：

   （读）开

   * /app
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### AEM Mobile应用程序管理员组（应用程序管理员组） {#aem-mobile-application-administrators-group-app-admins-group}

应用程序管理员组的成员可以使用应用程序作者附带的相同权限创作应用程序内容 **和** 此外，还负责：

* 暂存、发布和清除应用程序ContentSync OTA更新

>[!NOTE]
>
>权限决定了AEM应用程序命令中心中某些用户操作的可用性。
>
>您会注意到，有些选项对于应用程序作者而言不可用，而应用程序管理员则可用。

### 组配置 — 应用程序管理员 {#group-configuration-app-admins}

1. 创建一个名为应用程序管理员的新组。
1. 将以下组添加到新的应用程序管理员组：

   * content-authors
   * 工作流用户

   ![chlimage_1-169](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >使用PhoneGap Build服务远程构建需要工作流用户

1. 导航到 [权限控制台](http://localhost:4502/useradmin) 和添加管理cloudservices的权限

   * （读取、修改、创建、删除、复制）/etc/cloudservices/mobileservices

1. 在同一“权限”控制台上，添加用于暂存、发布和清除应用程序内容更新的权限；

   * （读取、修改、创建、删除、复制）/etc/packages/mobileapp
   * /var/contentsync上的（读取）

   >[!NOTE]
   >
   >包复制用于将应用程序更新从创作实例发布到发布实例

   >[!CAUTION]
   >
   >/var/contentsync访问被拒绝OOTB。
   >
   >省略“读取”权限可能会导致生成和复制空的更新包。

1. 根据需要向此组添加成员
1. 导出内容或上传

   * （读取）在/etc/contentsync上访问导出模板
   * 在/var上读取)到，用于在读取时遍历路径
   * （读、写、修改、删除）/var/contentsync上用于写入、读取和清理ContentSync缓存的导出内容

### 其他资源 {#additional-resources}

要详细了解创建AEM Mobile On-demand Services应用程序的其他两个角色和职责，请参阅以下资源：

* [为AEM Mobile On-demand Services开发AEM内容](/help/mobile/aem-mobile-on-demand.md)
* [为AEM Mobile On-demand Services应用程序创作AEM内容](/help/mobile/mobile-apps-ondemand.md)
