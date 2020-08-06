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
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# 组模板 {#group-templates}

“组模板”控制台与“站点模板”控 [制台非常](sites.md) 相似。 这两者都是构建社区站点的一套预连接页面和功能的蓝图。 区别在于站点模板适用于主社区，而组模板适用于社区组，即嵌套在主社区中的子社区。

社区组通过包含“组”功能(可能不是模板中的第 [一个或仅](functions.md#groups-function) “组”功能)被并入站点模板中。

从“社区 [”功能包](deploy-communities.md#latestfeaturepack)1开始，可以通过将“组”功能包含在组模板中来嵌套组。

当采取操作创建新社区组时，将选择该组的模板（结构）。 选择取决于在添加到站点或组模板时如何配置组功能。

>[!NOTE]
>
>创建社区站点的控 [制台](sites-console.md)、社 [区站点模板](sites.md)、社 [区组模板](tools-groups.md)[和社区功](functions.md) 能的控制台仅在作者环境中使用。

## 组模板控制台 {#group-templates-console}

在创作环境中，要访问组模板控制台

* 从全局导航： **[!UICONTROL “工具”>“社区”>“组模板”]**

此控制台显示可从中创建社 [区站点](sites-console.md) 的模板，并允许创建新的组模板。

![石斑](assets/groupstemplate.png)

## 创建组模板 {#create-goup-template}

要开始创建新组模板，请选择创 **[!UICONTROL 建]**

这将显示包含3个子面板的站点编辑器面板：

### 基本信息 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在“基本信息”面板上，将配置名称、说明以及是否启用或禁用模板：

* **[!UICONTROL 新组模板名称]**&#x200B;模板名称id

* **[!UICONTROL 说明]**&#x200B;模板说明

* **[!UICONTROL 禁用／启用]**&#x200B;切换开关控制模板是否可引用

### 缩略图 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可选）选择上传图像图标，以便向社区站点的创建者显示缩略图以及名称和说明。

### 结构 {#structure}

>[!CAUTION]
>
>如果使用AEM 6.1 Communities FP4或更早版本，请勿将组功能添加到组模板。
>
>嵌套组功能自Communities FP1 [起可用](communities.md#latestfeaturepack)。
>
>仍不允许将“组”函数添加为模板中的第一个或唯一函数。

![grptemplateeditor](assets/grptemplateeditor.png)

要添加社区功能，请按站点菜单链接的显示顺序从右侧向左拖动。 样式将在创建站点时应用于模板。

例如，如果您想要论坛，请将论坛功能从库拖放到模板生成器下。 这将导致打开论坛配置对话框。 有关配置 [对话框](functions.md) ，请参阅函数控制台。

根据此模板，继续拖放子社区站点（组）所需的任何其他社区功能。

![拖曳功能](assets/dragfunctions.png)

将所有所需的功能拖放到模板生成器区域并进行配置后， **[!UICONTROL 选择]** 右上角的“保存”。

## 编辑组模板{#edit-group-template}

在主组模板控制台中查 [看社区组时](#group-templates-console)，可以选择现有的组模板进行编辑。

编辑组模板不会影响已通过模板创建的社区站点。 可以直接编 [辑社区站点](sites-console.md#modify-structure)的结构。

此过程提供的面板与创 [建组模板相同](#create-goup-template)。
