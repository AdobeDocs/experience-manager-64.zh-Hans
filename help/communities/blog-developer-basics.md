---
title: 博客要点
seo-title: 博客要点
description: 博客概述
seo-description: 博客概述
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# 博客要点{#blog-essentials}

自AEM 6.1 Communities起，博客即为社区活动。 博客文章现在从发布环境发布，以前，只能在创作环境中创建并发布博客文章。

现在，博客文章可由任何社区成员创建，除非仅限于特权成员。

本页提供了使用博客功能的基本信息。

>[!NOTE]
>
>博客功能的基础结构是日志功能。

## 客户端{#essentials-for-client-side}的要点

博客功能由两个主要组件组成，这些组件可通过添加[Blog函数](functions.md#blog-function)或在作者编辑模式下将组件添加到页面来使用。

### 博客 {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.voting<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> 属性</strong></td> 
   <td>请参阅<a href="blog-feature.md">博客功能</a></td> 
  </tr>
 </tbody>
</table>

### 博客侧栏 {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**可包含**](scf.md#add-or-include-a-communities-component) | 否 |
| [**clientlibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **模板** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **属性** | 请参阅[博客功能](blog-feature.md) |

* [客户端自定义](client-customize.md)

## 服务器端{#essentials-for-server-side}的要点

* [博客API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [博客端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 博客功能 {#blog-function}

包含[Bog函数](functions.md#blog-function)的社区站点结构将配置`Blog`和`Blog Sidebar`组件。 Blog函数支持标识[特权成员用户组](users.md#privileged-members-group)。

### 访问博客条目(UGC){#accessing-blog-entries-ugc}

UGC应使用其中一种标准审核方法进行审核。\
请参阅[审核用户生成的内容](moderate-ugc.md)。

自AEM 6.1 Communities起，使用[用于UGC的公共存储](working-with-srp.md)包括对UGC的编程访问，而不考虑所选的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**。

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC Essentials](srp-and-ugc.md)  - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法

## 主发布者{#primary-publisher}

当部署是发布场时，需要确定将轮询计划发布的文章的主发布者。

有关更多详细信息，请参阅[主发布者](deploy-communities.md#primary-publisher)。

## 允许富媒体{#allowing-rich-media}

AEM平台会阻止来自其他网站的链接，以防止XSS攻击，如

* [Protect反对跨站点脚本(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

自AEM 6.2起，之前手动进行的修改将包含在默认的AntiSamy配置文件中。

通过选择`Embed Media from External Sites`图标，富媒体嵌入到博客文章中： ![chlimage_1-471](assets/chlimage_1-471.png)
