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
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# 社区组 {#community-groups}

社区组功能是允许子社区由发布和创作环境中的授权用户（社区成员和作者）在社区站点内动态创建。

当[groups函数](functions.md#groups-function)在[社区站点](sites-console.md)结构中存在时，即存在此功能。

[社区组模板](tools-groups.md)在动态创建社区组时提供社区组页面的设计。

当将功能添加到社区站点的结构或社区站点模板时，为组功能选择一个或多个组模板。 此组模板列表将呈现给从社区站点中动态创建新组的成员或作者。

## 创建新组{#creating-a-new-group}

能否创建新的社区组取决于社区站点的存在，该站点包含组功能，例如从` [Reference Site Template](sites.md)`创建的社区站点。

以下示例使用从`Reference Site Template`创建的社区站点，如[AEM Communities](getting-started.md)快速入门教程中所述。

选择&#x200B;**[!UICONTROL Groups]**&#x200B;菜单项时，在发布时加载的页面如下：

![chlimage_1-236](assets/chlimage_1-236.png)

选择&#x200B;**[!UICONTROL 新建组]**&#x200B;图标时，将打开一个编辑对话框。

在&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡下，提供组的基本功能：

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL 群组]**
名称要在社区网站上显示的群组的标题。

* ****
描述要在社区网站上显示的群组描述。

* ****
邀请邀请加入群组的成员列表。提前键入搜索将提供社区成员邀请的建议。

* **[!UICONTROL 群组URL]**
名称成为URL一部分的群组页面的名称。

* **[!UICONTROL 打开组选]**
择 
`Open Group` 表示任何匿名网站访客都可以查看内容，并将取消选择该内 `Member Only Group`容。

* **[!UICONTROL 仅成员组选]**
择 
`Member Only Group` 仅指示组成员可以查看内容并将取消选择该内 `Open Group`容。

在&#x200B;**[!UICONTROL Template]**&#x200B;选项卡下，可以从社区组模板列表中进行选择，这些模板是在社区站点的结构或社区站点模板中包含群组功能时指定的。

![chlimage_1-238](assets/chlimage_1-238.png)

在&#x200B;**[!UICONTROL Image]**&#x200B;选项卡下，可以上传图像以在社区站点的“组”页面上显示组。 默认样式表会将图像的大小调整为170 x 90像素。

![chlimage_1-239](assets/chlimage_1-239.png)

通过选择&#x200B;**[!UICONTROL 创建组]**&#x200B;按钮，将根据所选模板创建组的页面，并为成员创建用户组，此时将更新“组”页面以显示新的子社区。

例如，标题为“焦点组”的新子社区的“组”页面（已上传图像缩略图）将如下所示（仍以社区组管理员身份登录）：

![chlimage_1-240](assets/chlimage_1-240.png)

选择`Focus Group`链接将在浏览器中打开焦点组页面，该页面具有基于所选模板的初始外观，并在主社区站点的菜单下包含子菜单：

![chlimage_1-241](assets/chlimage_1-241.png)

## 社区组成员列表组件{#community-group-member-list-component}

`Community Group Member List`组件供组模板的开发人员使用。

## 附加信息 {#additional-information}

有关更多信息，请参阅面向开发人员的[Community Group Essentials](essentials-groups.md)页面。

有关社区组的其他信息，请访问[管理用户和用户组](users.md)。
