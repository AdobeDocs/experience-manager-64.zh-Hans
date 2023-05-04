---
title: 代码缺陷
seo-title: Code pitfalls
description: 为AEM开发时需要避免的常见编码陷阱
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 4%

---

# 代码缺陷{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 避免在Java代码中绑定Sling {#avoid-sling-bindings-in-java-code}

在90%的情况下，Sling绑定是获取服务访问权限的不适当方式。 相反，您应使用 *@Reference* 或 *@Inject* 批注。

## 避免Java代码中的线程。中断 {#avoid-thread-interrupt-in-java-code}

*线程。中断* 是危险的，因为当在错误的时间调用时，可能会关闭文件（包括Lucene文件和永久缓存文件）。

## 避免将Java同步与ReadWriteLocks混合 {#avoid-mixing-java-synchronization-with-readwritelocks}

这可能会导致代码最终会陷入死锁的争用情况。
