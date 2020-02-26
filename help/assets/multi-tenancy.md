---
title: 集合、片段和片段模板的多租约
description: 根据客户组织隔离CRX存储库中的内容，以防止未经授权的访问。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# 集合、片段和片段模板的多租约 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

通过多租赁功能，您可以根据组织前缀和组织ID在CRX中隔离内容，以保护内容免受其他组织用户的未授权访问。

Adobe Experience Manager(AEM)资产会将每个组织的数据存储在不同的路径中。 每个组织特定路径由组织前缀和组织ID标识。
它包含在CRX中存储不同类型资源的传统位置中。

例如，如果您创建了一个名为的文 `Demo`件夹，则默认情况下，AEM资产会将该文件夹存储在CRX `../content/dam/Demo` 中的位置。 启用多租赁功能后，您可以在存储数据 `../content/dam/<organization prefix>/<organization id>Demo`。

例如，对于分配给组织的AEM资产（按需）的Adobe Marketing cloud用户，您可以使用多租赁功能配置以下内容分 `aodpremium``../content/dam/mac/aodpremiumDemo`隔路径。 在此示例中 `mac` 是组织前缀， `aodpremium` 也是组织ID。

根据用户的组织和ID，此限定路径显示在AEM资产界面和各种向导中，包括用于强制分段的移动和代码片断创建向导。

通过多租赁功能，您可以分类以下类型的资产和组件：

* 收藏集
* 公共集合
* 目录（包括添加／选择页面向导）
* 模板
* 代码片断模板
* Lightbox
