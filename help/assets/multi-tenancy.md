---
title: 收藏集、片段和代码片段模板的多租户
description: 根据客户组织隔离CRX存储库中的内容，以防止未经授权的访问。
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 2%

---

# 收藏集、片段和代码片段模板的多租户 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

多租户功能允许您根据组织前缀和组织ID在CRX中分隔内容，以防止其他组织的用户对内容进行未经授权的访问。

Adobe Experience Manager(AEM)Assets将每个组织的数据存储在不同的路径中。 每个特定于组织的路径由组织前缀和组织ID来标识。
CRX中存储不同类型资产的传统位置中包含的附加内容。

例如，如果您创建一个名为 `Demo`，则AEM assets默认会将文件夹存储在 `../content/dam/Demo` 位置。 启用多租户功能后，您可以在 `../content/dam/<organization prefix>/<organization id>Demo`.

例如，对于分配给的AEM Assets的Adobe Marketing Cloud用户（按需） `aodpremium` 组织中，您可以使用多租户功能配置以下路径 `../content/dam/mac/aodpremiumDemo`，将内容分隔开。 在本例中 `mac` 是组织前缀， `aodpremium` 是组织ID。

根据用户的组织和ID，此符合条件的路径显示在AEM Assets界面和各种向导中，包括用于强制分段的移动和代码片段创建向导。

通过多租户功能，您可以划分以下类型的资产和组件：

* 收藏集
* 公共收藏集
* 目录（包括“添加/选择页面”向导）
* 模板
* 代码片段模板
* 灯箱
