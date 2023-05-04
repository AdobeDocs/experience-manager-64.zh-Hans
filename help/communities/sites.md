---
title: 站点模板
seo-title: Site Templates
description: 如何访问“站点模板”控制台
seo-description: How to access the Site Templates console
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 3%

---

# 站点模板 {#site-templates}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

“站点模板”控制台与 [组模板](tools-groups.md) console，专注于社区组感兴趣的功能。

>[!NOTE]
>
>用于创建 [社区站点](sites-console.md), [社区网站模板](sites.md), [社区组模板](tools-groups.md) 和 [社区功能](functions.md) 只能在创作环境中使用。

## 站点模板控制台 {#site-templates-console}

在创作环境中，访问社区站点控制台

* 从全局导航： **[!UICONTROL 工具>社区>网站模板]**

此控制台显示 [社区网站](sites-console.md) 可创建，并允许创建新站点模板。

![chlimage_1-18](assets/chlimage_1-18.png)

## 创建站点模板 {#create-site-template}

要开始创建新网站模板，请选择 `Create`.

这将显示包含3个子面板的站点编辑器面板：

### 基本信息 {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

在“基本信息”面板上，配置了模板的名称、说明以及是启用还是禁用了模板：

* **[!UICONTROL 社区站点模板名称]**
模板名称id

* **[!UICONTROL 社区站点模板描述]**
模板描述

* **[!UICONTROL 已禁用/已启用]**
控制模板是否可引用的切换开关

### 缩略图 {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

（可选）选择上传图像图标，以向社区站点的创建者显示缩略图以及名称和描述。

### 结构 {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

要添加社区功能，请按网站菜单链接的显示顺序从右侧向左拖动。 样式将在站点创建期间应用于模板。

例如，如果您想要某个主页，请将库中的Page函数拖放到模板生成器下。 这将导致打开页面配置对话框。 请参阅 [函数控制台](functions.md) 以了解有关配置对话框的信息。

继续拖放基于此模板的社区站点所需的任何其他社区功能。

页面函数提供一个空页面。 群组功能提供在社区站点内创建群组站点（子社区）的功能。

>[!CAUTION]
>
>组函数必须 *not* be *第一，也是唯一* 函数。
>
>任何其他函数，例如 [页面函数](functions.md#page-function)，必须先包含并列出。

![chlimage_1-22](assets/chlimage_1-22.png)

### 组功能的组模板 {#group-templates-for-groups-function}

在站点模板中包含组功能时，配置要求指定在发布环境中创建新组时允许的组模板选项。

>[!CAUTION]
>
>组函数必须 *not* be *第一，也是唯一* 函数。

![chlimage_1-23](assets/chlimage_1-23.png)

通过选择两个或更多社区组模板，在社区中实际创建新组时，可向组管理员提供选择。

![chlimage_1-24](assets/chlimage_1-24.png)

## 编辑站点模板 {#edit-site-template}

在主 [站点模板控制台](#site-templates-console)，则可以选择要编辑的现有网站模板。

此过程提供与 [创建网站模板](#create-site-template).
