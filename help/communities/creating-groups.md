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
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---


# 社区组 {#community-groups}

社区组功能是允许通过发布和作者环境授权用户（社区成员和作者）在社区站点内动态创建子社区的功能。

当社区站点结构中 [存在组](functions.md#groups-function) 功能时， [即存在此功能](sites-console.md) 。

社 [区组模板](tools-groups.md) ，在动态创建社区组时提供社区组页面的设计。

当该功能被添加到社区站点的结构或社区站点模板时，为该组功能选择一个或多个组模板。 此组模板列表将呈现给从社区站点动态创建新组的成员或作者。

## Creating a New Group {#creating-a-new-group}

创建新社区组的能力取决于社区站点的存在，该站点包含组功能，如从创建的组 ` [Reference Site Template](sites.md)`。

下面的示例使用从创建的社区站点，如 `Reference Site Template` 《AEM Communities入 [门》教程所述](getting-started.md) 。

选择“组”菜单项时，此页 **[!UICONTROL 面在发]** 布时加载：

![chlimage_1-236](assets/chlimage_1-236.png)

选择“新建 **[!UICONTROL 组”图]** 标时，将打开一个编辑对话框。

在“设 **[!UICONTROL 置]** ”选项卡下，您提供组的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 组名称]**&#x200B;要在社区站点上显示的组的标题。

* **[!UICONTROL 说明]**&#x200B;要在社区站点上显示的组的说明。

* **[!UICONTROL 邀]**&#x200B;请成员列表邀请加入组。 预先键入搜索将提供社区成员邀请的建议。

* **[!UICONTROL 组URL名]**&#x200B;称成为URL一部分的组页面的名称。

* **[!UICONTROL 打开组选]**&#x200B;择 
`Open Group` 指示任何匿名网站访客可能视图内容，并将取消选择 `Member Only Group`。

* **[!UICONTROL 仅成员组选]**&#x200B;择 
`Member Only Group` 表示只有组成员可以视图内容，并将取消选择 `Open Group`。

在“模 **[!UICONTROL 板]** ”选项卡下，可以从社区组模板的列表中进行选择，这些模板是在将组功能包括在社区站点的结构或社区站点模板中时指定的。

![chlimage_1-238](assets/chlimage_1-238.png)

在“图 **[!UICONTROL 像]** ”选项卡下，可以上传要在社区站点的“组”页面上为组显示的图像。 默认样式表将图像大小调整为170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

通过选 **[!UICONTROL 择“创建组]** ”按钮，将根据所选模板创建组的页面，并为成员创建用户组，此时将更新“组”页面以显示新的子社区。

例如，带有标题为“焦点组”的新子社区的“组”页面（已为其上传图像缩略图）将显示如下（仍以社区组管理员身份登录）:

![chlimage_1-240](assets/chlimage_1-240.png)

选择链 `Focus Group` 接将在浏览器中打开“焦点组”页面，该页面具有基于所选模板的初始外观，并在主社区站点的菜单下包含一个子菜单：

![chlimage_1-241](assets/chlimage_1-241.png)

## Community Group Member List Component {#community-group-member-list-component}

该组 `Community Group Member List` 件供组模板的开发人员使用。

## 附加信息 {#additional-information}

有关详细信息，请参阅“社 [区组必备工具](essentials-groups.md) ”页面。

有关社区组的其他信息，请访 [问管理用户和用户组](users.md)。
