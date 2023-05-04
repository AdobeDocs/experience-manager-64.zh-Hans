---
title: 组模板
seo-title: Group Templates
description: 如何访问“组模板”控制台
seo-description: How to access the Group Templates console
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 2%

---

# 组模板 {#group-templates}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

“组模板”控制台与 [网站模板](sites.md) 控制台。 这两种方案都为一系列预布线页面和功能提供了蓝图，这些页面和功能构成了社区站点。 区别在于，站点模板适用于主社区，而组模板适用于社区组（嵌套在主社区中的子社区）。

通过将 [组函数](functions.md#groups-function) （它可能不是模板中的第一个或唯一的函数）。

截至社区 [功能包1](deploy-communities.md#latestfeaturepack)，则可以通过在组模板中包含组函数来嵌套组。

在采取措施创建新社区组时，将选择该组的模板（结构）。 选择取决于在添加到网站或群组模板时如何配置群组功能。

>[!NOTE]
>
>用于创建 [社区站点](sites-console.md), [社区网站模板](sites.md), [社区组模板](tools-groups.md) 和 [社区功能](functions.md) 只能在创作环境中使用。

## 组模板控制台 {#group-templates-console}

在创作环境中，访问组模板控制台

* 从全局导航： **[!UICONTROL 工具>社区>组模板]**

此控制台显示 [社区网站](sites-console.md) 可创建，并允许创建新组模板。

![组板](assets/groupstemplate.png)

## 创建组模板 {#create-goup-template}

要开始创建新组模板，请选择 **[!UICONTROL 创建]**

这将显示包含3个子面板的站点编辑器面板：

### 基本信息 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在“基本信息”面板上，配置了模板的名称、说明以及是启用还是禁用了模板：

* **[!UICONTROL 新组模板名称]**
模板名称id

* **[!UICONTROL 描述]**
模板描述

* **[!UICONTROL 已禁用/已启用]**
控制模板是否可引用的切换开关

### 缩略图 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可选）选择上传图像图标，以向社区站点的创建者显示缩略图以及名称和描述。

### 结构 {#structure}

>[!CAUTION]
>
>如果使用AEM 6.1 Communities FP4或更早版本，请勿将组函数添加到组模板。
>
>嵌套的组功能自Communities起可用 [FP1](communities.md#latestfeaturepack).
>
>仍不允许将组函数添加为模板中的第一个或唯一函数。

![grtemplateeditor](assets/grptemplateeditor.png)

要添加社区功能，请按网站菜单链接的显示顺序从右侧向左拖动。 样式将在站点创建期间应用于模板。

例如，如果您想要论坛，请将论坛函数从库中拖放到模板生成器下。 这将导致打开论坛配置对话框。 请参阅 [函数控制台](functions.md) 以了解有关配置对话框的信息。

根据此模板，继续拖放子社区站点（组）所需的任何其他社区功能。

![拖动功能](assets/dragfunctions.png)

将所有所需函数放入模板生成器区域并进行配置后，选择 **[!UICONTROL 保存]** 在右上角。

## 编辑组模板 {#edit-group-template}

在主 [组模板控制台](#group-templates-console)，则可以选择现有的组模板进行编辑。

编辑组模板不会影响已使用该模板创建的社区站点。 可以直接 [编辑社区站点](sites-console.md#modify-structure)的结构。

此过程提供与 [创建组模板](#create-goup-template).
