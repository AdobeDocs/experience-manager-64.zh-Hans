---
title: 使用社交图
seo-title: Using Social Graph
description: 向页面添加以下组件
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 3%

---

# 使用社交图 {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

社区成员遵循的能力 [活动](activities.md) 并通过两个部分建立： `Follow`和 `Following`.

的 `Follow`组件必须与其他资源关联，并且此关联已针对社区成员和功能建立。

的 `Following`组件仅列出当前成员之后或当前成员后面的成员。 此社交图中的成员之间的关系包含在为 [社区网站](overview.md#communitiessites).

## 向页面添加以下内容 {#adding-following-to-a-page}

如果需要添加 `Following`组件到创作模式下的页面，找到组件 `Communities / Following` 并将其拖动到应显示社交图的页面上。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](essentials-socialgraph.md#essentials-for-client-side) 包含，这是 `Following` 组件将显示：

![chlimage_1-447](assets/chlimage_1-447.png)

## 配置以下内容 {#configuring-following}

目前，需要设置属性以确定组件是否显示 `follows`关系，或 `following`关系。

## 附加信息 {#additional-information}

有关 [社交图要点](essentials-socialgraph.md) 页面。
