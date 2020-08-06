---
title: 代码陷阱
seo-title: 代码陷阱
description: 为AEM开发时应避免的常见编码陷阱
seo-description: 为AEM开发时应避免的常见编码陷阱
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
translation-type: tm+mt
source-git-commit: 835f1ba1f196c6c6303019f0cc310cad850e1682
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---


# 代码陷阱{#code-pitfalls}

## 避免Java代码中的Sling绑定 {#avoid-sling-bindings-in-java-code}

在90%的情况下，Sling Bindings是访问服务的不恰当方式。 您应该使用 *@Reference**或@Incrite注释* 。

## 避免Java代码中的线程。中断 {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt是危险的* ，因为当在错误的时间调用时，它可能会关闭文件，包括Lucene文件和永久缓存文件。

## 避免将Java同步与ReadWriteLocks混合 {#avoid-mixing-java-synchronization-with-readwritelocks}

这会导致代码最终陷入死锁的竞赛条件。
