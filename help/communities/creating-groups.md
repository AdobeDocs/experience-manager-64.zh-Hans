---
title: 社区组
seo-title: 社区组
description: 创建社区组
seo-description: 创建社区组
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87

---


# 社区组 {#community-groups}

社区组功能是允许从发布和创作环境中授权用户（社区成员和作者）在社区站点内动态创建子社区的功能。

当群组功能在社区站点结 [构中存在](functions.md#groups-function) 时，就会 [出现此功能](sites-console.md) 。

当动 [态创建社区组时](tools-groups.md) ，社区组模板可提供社区组页面的设计。

当该功能被添加到社区站点的结构或社区站点模板时，为该组功能选择一个或多个组模板。 此组模板列表会显示给从社区站点内动态创建新组的成员或作者。

## 创建新组 {#creating-a-new-group}

创建新社区组的能力取决于社区站点的存在，该站点包含组功能，如从创建的组 ` [Reference Site Template](sites.md)`。

下面的示例使用从创建的社区站点， `Reference Site Template` 如AEM Communities入 [门教程中所述](getting-started.md) 。

这是选择“组”菜单项时在发 **[!UICONTROL 布时]** 加载的页面：

![chlimage_1-236](assets/chlimage_1-236.png)

当您选择“新建 **[!UICONTROL 用户组]** ”图标时，将打开编辑对话框。

在“设 **[!UICONTROL 置]** ”选项卡下，您提供组的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 用户组名]**&#x200B;称要在社区站点上显示的用户组的标题。

* **[!UICONTROL 说明]**&#x200B;要在社区站点上显示的组的说明。

* **[!UICONTROL 邀请]**&#x200B;要邀请加入组的成员列表。 提前键入搜索将提供社区成员邀请的建议。

* **[!UICONTROL 用户组URL名]**&#x200B;称成为URL一部分的用户组页面的名称。

* **[!UICONTROL 打开用户]**&#x200B;组选 `Open Group` 择表示任何匿名站点访问者都可以查看内容，并将取消选择 `Member Only Group`。

* **[!UICONTROL 仅成员组]**&#x200B;选 `Member Only Group` 择此选项表示只有组成员可以查看内容，并将取消选择 `Open Group`。

在“模 **[!UICONTROL 板]** ”选项卡下，可以从社区组模板列表中进行选择，这些模板是在将组功能包括在社区站点的结构或社区站点模板中时指定的。

![chlimage_1-238](assets/chlimage_1-238.png)

在“图 **[!UICONTROL 像]** ”选项卡下，可以上传图像，以便在社区站点的“组”页面上显示组。 默认样式表将图像大小调整为170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

通过选择“ **[!UICONTROL 创建组]** ”按钮，将根据所选模板创建组的页面，并为成员身份创建用户组，此时将更新“组”页面以显示新的子社区。

例如，带有标题为“焦点组”的新子社区的“组”页面（已为其上传图像缩略图）将显示如下（仍以社区组管理员身份登录）:

![chlimage_1-240](assets/chlimage_1-240.png)

选择链 `Focus Group` 接将打开浏览器中的“焦点组”页面，该页面具有基于所选模板的初始外观，并在主社区站点的菜单下面包含子菜单：

![chlimage_1-241](assets/chlimage_1-241.png)

## Community Group Member List Component {#community-group-member-list-component}

该组 `Community Group Member List` 件供组模板的开发人员使用。

## 附加信息 {#additional-information}

有关详细信息，请参阅面向开 [发人员的“社区组](essentials-groups.md) Essentials”页。

有关社区组的其他信息，请访 [问管理用户和用户组](users.md)。
