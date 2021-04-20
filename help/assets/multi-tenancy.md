---
title: 集合、片段和片段模板的多租赁
description: 根据客户组织隔离CRX存储库中的内容，以防止未经授权的访问。
contentOwner: AG
feature: Collections
role: Architect,Administrator,Leader
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 1%

---


# 集合、片段和片段模板的多租赁{#multi-tenancy-for-collections-snippets-and-snippet-templates}

多租赁功能允许您根据组织前缀和组织ID在CRX中隔离内容，以保护内容免遭其他组织的用户未经授权的访问。

Adobe Experience Manager(AEM)资产会将每个组织的数据存储在不同的路径中。 每个组织特定路径由组织前缀和组织ID标识。
这包括在CRX中存储不同类型资源的传统位置中。

例如，如果您创建名为`Demo`的文件夹，则默认情况下，AEM assets会将该文件夹存储在CRX的`../content/dam/Demo`位置。 启用多租赁功能后，可在`../content/dam/<organization prefix>/<organization id>Demo`存储数据。

例如，对于分配给`aodpremium`组织的AEM Assets（按需）的Adobe Marketing Cloud用户，您可以使用多租赁功能配置到`../content/dam/mac/aodpremiumDemo`的以下路径，分离内容。 在此示例中，`mac`是组织前缀，`aodpremium`是组织ID。

根据用户的组织和ID，此限定路径显示在AEM Assets界面和各种向导中，包括用于强制分段的移动和片段创建向导。

通过多租赁功能，您可以分类以下类型的资产和组件：

* 收藏集
* 公共集合
* 目录（包括“添加/选择页面”向导）
* 模板
* 片段模板
* Lightbox
