---
title: 内容处置过滤器
seo-title: Content Disposition Filter
description: 了解如何使用内容处置过滤器来防止XSS攻击。
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 内容处置过滤器 {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

内容处置过滤器是一种针对SVG文件的XSS攻击的安全功能。

安装后，过滤器将阻止访问所有资产。 例如，您无法联机查看PDF。 本节将介绍如何根据需要配置过滤器。

## 配置内容处置过滤器 {#configure-content-disposition-filter}

您可以查看 [GitHub中的Apache Sling内容处置过滤器。](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

“内容处置过滤器”选项提供以下功能：

* **内容处置路径：** 应用筛选器的路径列表，后跟要在该路径上排除的mime类型列表。此路径必须是绝对路径，并且可以包含通配符(`*`)，以将每个资源路径与给定路径前缀匹配。 例如： `/content/*:image/jpeg,image/svg+xml` 会将过滤器应用到 `/content` 除jpg和svg图像外

* **排除的资源路径：** 排除的资源列表中，每个资源路径必须作为绝对和完全限定的路径提供。 不支持前缀匹配/通配符。

* **为所有资源路径启用：** 此标记控制是否为所有路径启用此过滤器，但“排除的资源路径”定义的排除路径除外。 将此值设置为“true”会导致忽略内容处置路径。 仅涵盖包含名为的属性的资源路径（与配置无关） `jcr:data` 或
   `jcr:content jcr:data`。
