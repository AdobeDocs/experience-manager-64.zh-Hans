---
title: 集合、片段和片段模板的多租户
description: 根据客户组织隔离CRX存储库中的内容，以防止未经授权的访问。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 1%

---


# 集合、片段和片段模板的多租户 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

通过多租赁功能，您可以根据组织前缀和组织ID在CRX中隔离内容，以防止其他组织的用户对内容进行未经授权的访问。

Adobe Experience Manager(AEM)资产将每个组织的数据存储在不同的路径中。 每个组织特定路径由组织前缀和组织ID标识。
它包含在传统位置，在该位置，不同类型的资源存储在CRX中。

例如，如果您创建名为的文件夹， `Demo`默认情况下，AEM assets会将该文件夹存储 `../content/dam/Demo` 在CRX中的位置。 启用多租赁功能后，您可以在存储数据 `../content/dam/<organization prefix>/<organization id>Demo`。

例如，对于分配给组织的Adobe Marketing Cloud（按需）用户 `aodpremium` ，您可以使用多租赁功能配置以下内容路径， `../content/dam/mac/aodpremiumDemo`分离内容。 在此示例 `mac` 中是组织前缀 `aodpremium` ，也是组织ID。

根据用户的组织和ID，此限定路径显示在AEM Assets界面和各种向导中，包括用于强制分割的移动和片段创建向导。

通过多租赁功能，您可以划分以下类型的资产和组件：

* 收藏集
* 公共集合
* 目录（包括添加／选择页面向导）
* 模板
* 片段模板
* Lightbox
