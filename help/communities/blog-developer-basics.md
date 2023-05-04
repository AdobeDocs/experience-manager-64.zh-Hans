---
title: 博客要点
seo-title: Blog Essentials
description: 博客概述
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# 博客要点 {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自AEM 6.1 Communities起，博客即为社区活动。 博客文章现在从发布环境发布，以前，只能在创作环境中创建并发布博客文章。

现在，博客文章可由任何社区成员创建，除非仅限于特权成员。

本页提供了使用博客功能的基本信息。

>[!NOTE]
>
>博客功能的基础结构是日志功能。

## 客户端要点 {#essentials-for-client-side}

博客功能由两个主要组件组成，这些组件可通过添加 [博客功能](functions.md#blog-function) 或者，在创作编辑模式下通过将组件添加到页面来执行此操作。

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
   <td>请参阅 <a href="blog-feature.md">博客功能</a></td> 
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
| **属性** | 请参阅 [博客功能](blog-feature.md) |

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [博客API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [博客端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 博客功能 {#blog-function}

包含 [Bog函数](functions.md#blog-function) 将配置 `Blog` 和 `Blog Sidebar` 组件。 博客功能支持识别 [特权成员用户组](users.md#privileged-members-group).

### 访问博客条目(UGC) {#accessing-blog-entries-ugc}

UGC应使用其中一种标准审核方法进行审核。\
请参阅 [审核用户生成的内容](moderate-ugc.md).

自AEM 6.1 Communities起，使用 [公用商店](working-with-srp.md) 对于UGC，包括以编程方式访问UGC，而不考虑选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**.

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法

## 主发布者 {#primary-publisher}

当部署是发布场时，需要确定将轮询计划发布的文章的主发布者。

请参阅 [主发布者](deploy-communities.md#primary-publisher) 以了解更多详细信息。

## 允许富媒体 {#allowing-rich-media}

AEM平台会阻止来自其他网站的链接，以防止XSS攻击，如

* [Protect反对跨站点脚本(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

自AEM 6.2起，之前手动进行的修改将包含在默认的AntiSamy配置文件中。

通过选择 `Embed Media from External Sites` 图标：  ![chlimage_1-471](assets/chlimage_1-471.png)
