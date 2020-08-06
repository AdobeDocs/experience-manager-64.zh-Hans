---
title: Blog Essentials
seo-title: Blog Essentials
description: 博客概述
seo-description: 博客概述
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---


# Blog Essentials {#blog-essentials}

自AEM 6.1 Communities起，博客即为社区活动。 博客文章现在从发布环境发布，以前，博客文章只能在作者环境中创建并发布。

现在，博客文章可由任何社区成员创建，除非仅限于特权成员。

本页提供使用博客功能的基本信息。

>[!NOTE]
>
>博客功能的基础结构是日志功能。

## 客户端必备工具 {#essentials-for-client-side}

博客功能由两个主要组件组成，这两个组件可通过添加 [Blog功能](functions.md#blog-function) ，或在作者编辑模式下将组件添加到页面来使用。

### 博客 {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>社交/日志/组件/hbs/日志</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.porting<br /> cq.social.hbs.日志</td> 
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
   <td>查看 <a href="blog-feature.md">博客功能</a></td> 
  </tr>
 </tbody>
</table>

### 博客侧栏 {#blog-sidebar}

| **resourceType** | 社交/日志/组件/hbs/侧栏 |
|---|---|
| [**可包含&#x200B;**](scf.md#add-or-include-a-communities-component) | 否 |
| [**clientlibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **模板** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **属性** | 查看 [博客功能](blog-feature.md) |

* [客户端自定义](client-customize.md)

## 服务器端必备工具 {#essentials-for-server-side}

* [博客API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [博客端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 博客功能 {#blog-function}

包含Bog功能的社区站 [点结构](functions.md#blog-function) 将配置 `Blog` 和组 `Blog Sidebar` 件。 Blog函数支持标识特权 [成员用户组](users.md#privileged-members-group)。

### 访问博客条目(UGC) {#accessing-blog-entries-ugc}

UGC应使用一种标准的协调方法进行仲裁。\
请参 [阅调节用户生成的内容](moderate-ugc.md)。

自AEM 6.1社区起，使用UGC的公 [用商店](working-with-srp.md) ，包括以程序方式访问UGC，而不管选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**。

请参阅：

* [存储资源提供程序概述](srp.md) -简介和存储库使用概述
* [SRP和UGC Essentials](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md) —— 编码指南
* [SocialUtils重构](socialutils.md) -将已弃用的实用程序方法映射到当前SRP实用程序方法

## 主发布者 {#primary-publisher}

当部署为发布场时，必须标识将轮询要发布的文章的主发布者。

有关更 [多详细信息](deploy-communities.md#primary-publisher) ，请参阅主发布者。

## 允许富媒体 {#allowing-rich-media}

AEM平台阻止来自其他网站的链接，以防止XSS攻击，如

* [Protect反对跨站点脚本(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

从AEM 6.2开始，之前手动进行的修改将包括在默认的AntiSamy配置文件中。

通过选择以下图标，富媒体嵌入在博客文 `Embed Media from External Sites` 章中：  ![chlimage_1-471](assets/chlimage_1-471.png)

