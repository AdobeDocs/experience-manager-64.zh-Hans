---
title: 删除Geometrixx站点
seo-title: Removing the Geometrixx Sites
description: 了解如何删除示例Geometrixx内容。
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 删除Geometrixx站点{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM附带一组示例Geometrixx网站。 您可以通过 **包管理器**.

与geometrixx相关的单个包包括：

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

要删除单个资源包，请单击 **卸载** 包裹上。

还有一个超级套餐：

* `cq-geometrixx-all-pkg-5.6.12.zip`

此包包含上述所有单个包。 要同时删除所有与geometrixx相关的内容，请单击 **卸载** 在这个包上。 超级包将进入“卸载”状态，并且所有单个包都将从包管理器视图中消失。

您现在有一个“空”AEM实例，而没有任何演示网站。

>[!NOTE]
>
>升级时，将自动重新安装geometrixx站点。 如果您不想要这些示例，则可能需要在升级后删除geometrixx网站。
