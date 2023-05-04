---
title: AEM 6.4中的向后兼容性
seo-title: Backward Compatibility in AEM 6.4
description: 了解如何使您的应用程序和配置与AEM 6.4兼容
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
exl-id: 5798100a-e03a-43f8-9189-ae51c06e192b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 1%

---

# AEM 6.4中的向后兼容性{#backward-compatibility-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

>[!NOTE]
>
>有关不在兼容包范围内的内容和配置更改列表，请参阅 [AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md).

在AEM 6.4中，开发所有功能时都考虑到了向后兼容性。

在大多数情况下，运行AEM 6.3的客户在进行升级时，不应该更改代码或自定义设置。 对于AEM 6.1和6.2客户，没有比升级到6.3期间面临的其他重大更改。

对于无法保持向后兼容功能的例外情况，可通过安装适用于6.3的兼容包来实现包和内容的向后兼容性（有关下载位置的详细信息，请参阅下面的设置）。 此兼容包将恢复与AEM 6.3兼容的应用程序的兼容性。

兼容包允许您在兼容模式下运行AEM，并根据新增的AEM功能推迟自定义开发：

>[!NOTE]
>
>请注意，兼容包只是一个临时解决方案，用于推迟兼容AEM 6.4所需的开发，仅当您在升级后无法立即通过开发解决兼容性问题时，才建议将其作为最后一个选项。 强烈建议在您决定继续基于6.4的自定义开发并使用完整的6.4功能后，切换到本机模式并卸载兼容包。

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

兼容包有两种模式： **已启用路由** 和 **路由已禁用**.

这允许以三种模式运行AEM 6.4:

**本机模式：**

本机模式适用于那些希望使用AEM 6.4的所有新增功能，并且已准备好进行一些开发以使其自定义功能与所有新增功能配合使用的客户。

这意味着在升级后，您可能需要立即对应用程序进行调整。

**兼容性模式：安装了启用路由的兼容包**

兼容性模式适用于自定义了无法向后兼容的界面的客户。 这允许AEM在兼容模式下运行，并针对与某些自定义代码不兼容的新AEM功能推迟所需的自定义开发。

**旧版模式：安装了禁用路由的兼容包**

旧版模式适用于具有基于兼容性包中已移出的AEM中旧版或已弃用代码的自定义界面的客户。

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## 如何设置 {#how-to-set-up}

AEM 6.3兼容包可以使用包管理器作为包进行安装。 您可以下载 [Software Distribution中的AEM 6.3兼容包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63) 网站。

安装兼容包后，可以使用OSGI配置中的交换机启用或禁用路由，如下所示：

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

安装并设置兼容包后，将根据所选的兼容模式来使用这些功能。
