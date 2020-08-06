---
title: Tag Essentials
seo-title: Tag Essentials
description: 标记概述
seo-description: 标记概述
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# Tag Essentials {#tag-essentials}

当AEM Communities组件配置为启用标记时，社区成员能够标记他们在发布环境中发布的内容。

发布环境中应用的标记的基础结构与在创作环境中应用于内容的标记的基础结构相同，如页面和资产：

* 有关创 [建和管](../../help/sites-administering/tags.md) 理标 [记的信息，请参阅管理标](tag-ugc.md) 记和标记用户生成的内容(UGC)。

* See [Tagging for Developers](../../help/sites-developing/tags.md) for information about the [tagging framework](../../help/sites-developing/framework.md) as well as including and extending tags in [custom applications](../../help/sites-developing/building.md).

* 有关 [如何向页面添加组件以在发布环境](tagcloud.md)`social tag cloud` 中突出显示应用于UGC的标记的作者信息，请参阅使用社交标记云。

* 有关 [目录的标记资源](tag-resources.md) ，请参阅标记启用资源。

配置社区站点或以下功能之 [一时](sites-console.md#tagging) ，可启用UGC标记：

* [博客](blog-feature.md)
* [日历](calendar.md)
* [文件库](file-library.md)
* [论坛](forum.md)
* [问题与解答](working-with-qna.md)

## 客户端必备工具 {#essentials-for-client-side}

### 社交标记云 {#social-tag-cloud}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/tagcloud</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.tagcloud</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td> 
  </tr>
  <tr>
   <td><strong>属性</strong></td> 
   <td>请参 <a href="tagcloud.md">阅使用社交标记云</a></td> 
  </tr>
 </tbody>
</table>

* [客户端自定义](client-customize.md)

## 服务器端必备工具 {#essentials-for-server-side}

* [社交标记云API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [社交标签管理器](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [服务器端自定义](server-customize.md)

## 标记搜索 {#tag-searching}

从功 [能包1](deploy-communities.md#latestfeaturepack) (FP1)开始，使用标签标题执行标 [签搜索](../../help/sites-developing/framework.md#tag-characteristics)。

在FP1之前，使用标记id执 [行搜索](../../help/sites-developing/framework.md#tagid)。
