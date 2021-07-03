---
title: 收藏集、片段和代码片段模板的多租户
description: 根据客户组织隔离CRX存储库中的内容，以防止未经授权的访问。
contentOwner: AG
feature: 收藏集
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 1%

---

# 收藏集、片段和代码片段模板的多租户 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

多租户功能允许您根据组织前缀和组织ID在CRX中分隔内容，以防止其他组织的用户对内容进行未经授权的访问。

Adobe Experience Manager(AEM)Assets将每个组织的数据存储在不同的路径中。 每个特定于组织的路径由组织前缀和组织ID来标识。
CRX中存储不同类型资产的传统位置中包含的附加内容。

例如，如果您创建名为`Demo`的文件夹，则AEM Assets默认会将该文件夹存储在CRX的`../content/dam/Demo`位置。 启用多租户功能后，可以在`../content/dam/<organization prefix>/<organization id>Demo`存储数据。

例如，对于分配给`aodpremium`组织的AEM Assets（按需）Adobe Marketing Cloud用户，您可以使用多租户功能配置以下`../content/dam/mac/aodpremiumDemo`路径，并分隔内容。 在此示例中，`mac`是组织前缀，`aodpremium`是组织ID。

根据用户的组织和ID，此符合条件的路径显示在AEM Assets界面和各种向导中，包括用于强制分段的移动和代码片段创建向导。

通过多租户功能，您可以划分以下类型的资产和组件：

* 收藏集
* 公共收藏集
* 目录（包括“添加/选择页面”向导）
* 模板
* 代码片段模板
* Lightbox
