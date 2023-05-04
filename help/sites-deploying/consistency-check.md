---
title: 一致性和遍历检查
seo-title: Consistency and Traversal Checks
description: 了解如何执行一致性和遍历检查。
seo-description: Learn how to perform consistency and traversal checks.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Configuring
exl-id: 67dfa0f7-24ac-41ae-83c9-3bb1a8656502
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 2%

---

# 一致性和遍历检查{#consistency-and-traversal-checks}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

升级时，可能会因工作区不一致而出现问题。 您可以运行测试升级以查看这是否是问题，也可以运行一致性检查作为预防性操作。

如果您运行的测试升级因工作区不一致而失败，您将在crx-quickstart/logs/crx/error.log中看到类似以下内容的条目：

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## 执行一致性检查 {#perform-a-consistency-check}

要执行一致性检查，请导航到JMX Mbean** com.adobe.granite（存储库）**的管理页面。 从AEM主屏幕中，转到：

**“工具”>“Web控制台”>“主”（位于菜单栏上）>“JMX”>“com.adobe.granite（存储库）”**

在默认安装中，可在此处找到：  **[|显示我|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

在 **操作** 在页面的部分中，可找到两种方法： **`traversalCheck`** 和 **`consistencyCheck`**. 要执行检查，请单击操作并输入所需的参数。

![chlimage_1-117](assets/chlimage_1-117.png)
