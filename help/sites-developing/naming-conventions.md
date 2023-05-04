---
title: 命名约定
seo-title: Naming Conventions
description: 存储库中的节点受Java内容存储库的命名约定的约束
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 8%

---

# 命名约定{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

存储库中的节点受 [Java内容存储库](/help/sites-developing/the-basics.md#java-content-repository). 但是，AEM对页面节点的名称作了进一步的约定。

## 页面的命名约定 {#naming-conventions-for-pages}

这些命名约定在不同级别实施：

* JcrUtil:的AEM实施 [JCR实用程序](#jcr-utilities).
* PageManager:the [页面管理器](#page-manager) 提供页面级操作的方法。
* 根据使用的UI:

   * [标准触屏UI](#standard-ui)
   * [经典 UI](#classic-ui)

### JCR实用程序 {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) 是JCR实用程序的AEM实施。 验证名称时特别需要注意的是它所控制的字符映射和以下验证：

* `isValidName`

   * 检查名称是否不为空，并且只包含有效字符。
   * 可用于检查建议的名称是否有效。

* `createValidName`

   * 这会从任意字符串中创建有效标签。
   * 它可用于从标题创建名称。

### 页面管理器 {#page-manager}

[PageManager](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 提供页面级别操作的方法，具体依据 [JCRUtil](#jcr-utilities).

### 标准 UI {#standard-ui}

标准触屏UI:

* 在以下任一情况下，根据PageManager施加的限制验证名称：

   * 提供页面标题以转换为节点名称
   * 提供了显式节点名称

### 经典 UI {#classic-ui}

经典UI施加了更严格的限制：

* 在以下任一情况下验证显式节点名称时的名称：

   * 提供页面标题以转换为节点名称
   * 提供了显式节点名称

* 有效字符(在经典UI中创建页面时，即使在 `PageManagerImpl` 允许添加其他字符):

   * “a”到“z”
   * “A”到“Z”
   * “0”到“9”
   * _（下划线）
   * `-` （短划线/减号）
