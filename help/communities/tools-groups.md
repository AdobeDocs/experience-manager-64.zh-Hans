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
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c

---


# 组模板 {#group-templates}

“组模板”控制台与“站点模板”控 [制台非常相似](sites.md) 。 两者都是构成社区站点的一系列预连接页面和功能的蓝图。 区别在于，站点模板适用于主社区，而组模板适用于社区组，即嵌套在主社区中的子社区。

通过包括“组”功能 [](functions.md#groups-function) （可能不是模板中的第一个或唯一功能），将社区组合并到站点模板中。

从Communities功 [能包1开始](deploy-communities.md#latestfeaturepack)，可以通过将“组”功能包含在组模板中来嵌套组。

当采取操作创建新社区组时，将选择该组的模板（结构）。 选择取决于将组功能添加到站点或组模板时的配置方式。

>[!NOTE]
>
>用于创建社区站点的控 [制台](sites-console.md)、社区站点 [模板](sites.md)、社区组模板 [](tools-groups.md)[](functions.md) 和社区功能的控制台仅在创作环境中使用。

## 组模板控制台 {#group-templates-console}

在创作环境中，要访问组模板控制台

* 从全局导航：“工 **[!UICONTROL 具”>“社区”>“组模板”]**

此控制台显示可从中创建社 [区站点的模板](sites-console.md) ，并允许创建新的组模板。

![石斑板](assets/groupstemplate.png)

## 创建组模板 {#create-goup-template}

要开始创建新用户组模板，请选择创 **[!UICONTROL 建]**

这将显示包含3个子面板的“站点编辑器”面板：

### 基本信息 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在“基本信息”面板上，将配置名称、说明以及是否启用或禁用模板：

* **[!UICONTROL 新组模板名称]**&#x200B;模板名称id

* **[!UICONTROL 说明]**&#x200B;模板说明

* **[!UICONTROL 禁用／启用]**&#x200B;控制模板是否可引用的切换开关

### 缩略图 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可选）选择上传图像图标，以向社区站点的创建者显示缩略图以及名称和说明。

### 结构 {#structure}

>[!CAUTION]
>
>如果使用AEM 6.1 Communities FP4或更早版本，请勿将组功能添加到组模板。
>
>嵌套组功能自Communities [FP1起可用](communities.md#latestfeaturepack)。
>
>仍不允许将“组”功能添加为模板中的第一个或唯一的函数。

![grptemplateeditor](assets/grptemplateeditor.png)

要添加社区功能，请按站点菜单链接的显示顺序从右侧向左拖动。 样式将在创建站点期间应用于模板。

例如，如果您想要论坛，请将论坛功能从库拖放到模板生成器下。 这将导致打开论坛配置对话框。 有关配置 [对话框的信息](functions.md) ，请参阅函数控制台。

根据此模板，继续拖放子社区站点（组）所需的任何其他社区功能。

![dragfunction](assets/dragfunctions.png)

将所有所需的功能放入模板生成器区域并进行配置后，选择 **[!UICONTROL 右上角的]** “保存”。

## 编辑组模板{#edit-group-template}

在主“组模板”控制台中查 [看社区组时](#group-templates-console)，可以选择现有的组模板进行编辑。

编辑组模板不会影响已通过模板创建的社区站点。 可以直接编 [辑社区站点的结](sites-console.md#modify-structure)构。

此过程提供的面板与创建 [组模板相同的面板](#create-goup-template)。
