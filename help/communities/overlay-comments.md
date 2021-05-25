---
title: 叠加注释组件
seo-title: 叠加注释组件
description: 叠加注释组件概述
seo-description: 叠加注释组件概述
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# 叠加注释组件{#overlay-comments-component}

[覆盖](client-customize.md#overlays)默认组件的意图是全局更改组件的外观或行为，以便对组件进行所有相对引用。 在/libs文件夹中搜索之前，它依赖于sling的性质来解析到/apps文件夹。 因此，组件的路径与默认组件的路径相同，不同之处在/apps文件夹中，而不是/libs文件夹中。

## 示例 {#example}

假定您想要修改评论功能，使其与您网站的设计相匹配，方法是更改评论标题，以便不再显示任何评论的头像。 用于隐藏头像的解决方案是使用CSS，或者，如此处所述，在apps文件夹中叠加header.jsp，以便包含头像的HTML永远不会发送到客户端。

要叠加评论，您需要：

1. [“评论”页面](overlay-create-comments-page.md)
1. [创建节点](overlay-create-nodes.md)
1. [更改外观](overlay-alter-appearance.md)
