---
title: Forms 6.4中的存储库重组
seo-title: Forms Repository Restructuring in AEM 6.4
description: 了解如何进行必要的更改，以便迁移到AEM 6.4 for Forms中的新存储库结构。
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 7%

---

# Forms 6.4中的存储库重组{#forms-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如父项中所述 [AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md) 页面，升级到AEM 6.4的客户应使用此页面来评估与影响AEM Forms解决方案的存储库更改相关的工作量。 某些更改在AEM 6.4升级过程中需要工作，而其他更改可能会推迟到6.5升级。

**升级6.4版**

* [杂项](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**6.5升级之前**

* [EchosignCloud Service配置](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [RecaptchaCloud Service配置](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [TypekitCloud Service配置](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [杂项](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## 升级6.4版 {#with-upgrade}

### 杂项 {#misc}

| **上一位置** | `/etc/clientlibs/fd/fp` |
|---|---|
| **新位置** | `/libs/fd/fp/components` |
| **重组指导** | 自定义代码中对旧版位置的任何显式引用都必须更新到新位置。 |
| **注释** | 不应修改或扩展这些客户端库。 |

| **上一位置** | `/etc/clientlibs/fd/rte` |
|---|---|
| **新位置** | `/libs/fd/rte` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/authoring/clientlibs` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **新位置** | `/libs/fd/xfaforms/clientlibs/` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/runtime/clientlibs` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/af` |
|---|---|
| **新位置** | `/libs/fd/af/runtime/clientlibs` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **新位置** | `/libs/fd/expeditor/clientlibs` |
| **重组指导** | 对于客户端库中可通过绝对路径引荐的资源，您需要在新资产中使用较新的路径。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **新位置** | `/libs/fd/fmaddon` |
| **重组指导** | 从不建议或支持更改这些clientlib。 如果已对这些clientlib进行了修改，则应回滚它们以使用AEM提供的代码。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/aep` |
|---|---|
| **新位置** | `/var/fd/content/annotations` |
| **重组指导** | 从不建议或支持更改这些clientlib。 如果已对这些clientlib进行了修改，则应回滚它们以使用AEM提供的代码。 |
| **注释** | 不适用 |

## 6.5升级之前 {#prior-to-upgrade}

### EchosignCloud Service配置 {#echosign-cloud-service-configuration}

| **上一位置** | `/etc/cloudservices/echosign` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **重组指导** | 的 [延迟内容迁移](/help/sites-deploying/lazy-content-migration.md) 实用程序。 |
| **注释** | 不适用 |

### RecaptchaCloud Service配置 {#recaptcha-cloud-service-configurations}

| **上一位置** | `/etc/cloudservices/recaptcha` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **重组指导** | 的 [延迟内容迁移](/help/sites-deploying/lazy-content-migration.md) 实用程序。 |
| **注释** | 不适用 |

### TypekitCloud Service配置 {#typekit-cloud-service-configurations}

| **上一位置** | `/etc/cloudservices/typekit` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **重组指导** | 的 [延迟内容迁移](/help/sites-deploying/lazy-content-migration.md) 实用程序。 |
| **注释** | 不适用 |

### 杂项 {#misc-1}

| **上一位置** | `/etc/cloudservices/fdm` |
|---|---|
| **新位置** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **重组指导** | 的 [延迟内容迁移](/help/sites-deploying/lazy-content-migration.md) 实用程序。 |
| **注释** | 不适用 |

| **上一位置** | `/etc/designs/fd/fp` |
|---|---|
| **新位置** | `/libs/fd/fp` |
| **重组指导** | 对/etc模板的任何引用最终应当进行更新，以指向其 `/libs` 对应。 |
| **注释** | 不适用 |
