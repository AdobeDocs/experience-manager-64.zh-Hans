---
title: 组模板
seo-title: 组模板
description: 如何访问“组模板”控制台
seo-description: 如何访问“组模板”控制台
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: 管理员
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 2%

---


# 组模板 {#group-templates}

“组模板”控制台与[“站点模板”](sites.md)控制台非常相似。 两者都是构成社区站点的一套预连线页面和功能的蓝图。 区别在于，站点模板用于主社区，而组模板用于社区组，即嵌套在主社区中的子社区。

通过将[Groups函数](functions.md#groups-function)（可能不是模板中的第一个或仅有的函数）包含到站点模板中，将社区组合并到站点模板中。

从Communities [功能包1](deploy-communities.md#latestfeaturepack)开始，可以通过将Groups功能包含在组模板中来嵌套组。

在采取操作创建新社区组时，将选择该组的模板（结构）。 选择取决于在将组功能添加到站点或组模板时如何配置。

>[!NOTE]
>
>创建[社区站点](sites-console.md)、[社区站点模板](sites.md)、[社区组模板](tools-groups.md)和[社区功能](functions.md)的控制台仅供创作环境使用。

## 组模板控制台{#group-templates-console}

在创作环境中，要访问组模板控制台

* 从全局导航：**[!UICONTROL 工具>社区>组模板]**

此控制台显示可从中创建[社区站点](sites-console.md)的模板，并允许创建新的组模板。

![组板](assets/groupstemplate.png)

## 创建组模板{#create-goup-template}

要开始创建新组模板，请选择&#x200B;**[!UICONTROL 创建]**

这将显示包含3个子面板的“站点编辑器”面板：

### 基本信息 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在“基本信息”面板上，将配置模板的名称、说明以及启用还是禁用模板：

* **[!UICONTROL 新组模板名]**
称模板名称ID

* **[!UICONTROL 说]**
明模板说明

* **[!UICONTROL 禁用/启]**
用切换开关控制模板是否可引用

### 缩略图 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可选）选择“上传图像”图标，以便向社区站点的创建者显示缩略图以及名称和说明。

### 结构 {#structure}

>[!CAUTION]
>
>如果使用AEM 6.1 Communities FP4或更早版本，请勿将组功能添加到组模板。
>
>嵌套组功能自Communities [FP1](communities.md#latestfeaturepack)起可用。
>
>仍不允许将组函数添加为模板中的第一个或唯一函数。

![grptemplateeditor](assets/grptemplateeditor.png)

要添加社区功能，请按站点菜单链接的显示顺序从右侧向左拖动。 样式将在创建站点时应用于模板。

例如，如果您想要论坛，请将论坛功能从库中拖放到模板生成器下。 这将导致打开论坛配置对话框。 有关配置对话框的信息，请参见[函数控制台](functions.md)。

根据此模板，继续拖放子社区站点（组）所需的任何其他社区功能。

![drag函数](assets/dragfunctions.png)

将所有所需的函数放入模板生成器区域并进行配置后，选择右上角的&#x200B;**[!UICONTROL 保存]**。

## 编辑组模板{#edit-group-template}

在主[“组模板”控制台](#group-templates-console)中查看社区组时，可以选择现有的组模板进行编辑。

编辑组模板不会影响已通过模板创建的社区站点。 可以直接[编辑社区站点](sites-console.md#modify-structure)的结构。

此过程提供与创建组模板](#create-goup-template)相同的面板。[
