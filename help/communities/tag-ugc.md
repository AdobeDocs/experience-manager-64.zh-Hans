---
title: 标记用户生成的内容
seo-title: Tagging User Generated Content
description: 标记用户生成的内容(UGC)是社区成员如何帮助其他成员搜索内容的方式
seo-description: Tagging of user generated content (UGC) is how community members can help other members search for content
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
role: Admin
exl-id: 834df392-df38-498c-9e2a-489484e20e0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 5%

---

# 标记用户生成的内容 {#tagging-user-generated-content}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

标记用户生成的内容(UGC)是社区成员帮助其他成员搜索内容的一种方式。

通常，标记由作者和管理员在创作环境中应用。 标记UGC是唯一的，因为UGC标记由社区成员在发布环境中应用。

标记命名空间和分类对于两个应用程序都是相同的。

## 社区功能 {#communities-features}

可配置为允许标记的AEM Communities功能包括

* [博客](blog-feature.md)
* [日程表](calendar.md)
* [文件库](file-library.md)
* [论坛](forum.md#configuretheaddedforum)
* [问题与解答](working-with-qna.md)

## 管理标记 {#administering-tags}

请参阅 [管理标记](../../help/sites-administering/tags.md#tagging-console) 用于创建和管理标记命名空间和分类。

请参阅 [标记要点](tag.md) ，以了解开发人员信息。

请参阅 [使用Social标签云](tagcloud.md) 用于向页面添加Social标签云组件，以便于使用所应用的标签搜索已发布的UGC。

### 标记权限 {#tag-permissions}

默认权限设置为不允许发布环境中的每个人读取标记命名空间。

由于标记在发布环境中应用于UGC，因此需要为社区成员启用读取权限，以便他们能够选择要应用的标记。

请参阅 [设置标记权限](../../help/sites-administering/tags.md#setting-tag-permissions).

以下是管理员将读取权限应用到CRXDE时，CRXDE中的显示方式 `/etc/tag/discussions` 对于组 `*Community Engage Members*`.

![chlimage_1-74](assets/chlimage_1-74.png)
