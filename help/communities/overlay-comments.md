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
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465

---


# 叠加注释组件 {#overlay-comments-component}

覆盖默认 [组件](client-customize.md#overlays) ，目的是全局更改组件的外观或行为，以便对组件的所有相对引用进行更改。 在/libs文件夹中搜索之前，它依赖sling的性质解析到/apps文件夹。 因此，组件的路径与默认组件的路径相同，只是它位于/apps文件夹中，而不是/libs文件夹中。

## 示例 {#example}

假定您要修改注释功能，以便它与您网站的设计相匹配，方法是更改注释标题，以便不再显示任何注释的头像。 隐藏头像的解决方案是使用CSS，或者如此处所述，在apps文件夹中覆盖header.jsp，这样包含头像的HTML就不会发送到客户端。

要叠加注释，您需要：

1. [评论页面](overlay-create-comments-page.md)
1. [创建节点](overlay-create-nodes.md)
1. [更改外观](overlay-alter-appearance.md)

