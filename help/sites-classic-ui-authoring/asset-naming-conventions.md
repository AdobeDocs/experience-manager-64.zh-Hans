---
title: 资产测试的命名约定
seo-title: Naming conventions for assets
description: 存储库中的节点受Java内容存储库的命名约定的约束。 但是，Adobe Experience Manager对资产节点的名称作了进一步的约定。
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---

# 资产测试的命名约定{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

存储库中的节点受 [Java内容存储库](/help/sites-developing/the-basics.md#java-content-repository). 但是，Adobe Experience Manager对资产节点的名称作了进一步的约定。

## 经典 UI {#classic-ui}

经典UI施加了更严格的限制：

* 在以下任一情况下验证明确的节点名称时的资产名称：

   * 提供资产标题以将其转换为节点名称
   * 提供了显式节点名称

* 有效字符（在经典UI中创建资产时，实际上只有这些字符才有效）：

   * “a”到“z”
   * “A”到“Z”
   * “0”到“9”
   * _（下划线）
   * `-` （短划线/减号）
