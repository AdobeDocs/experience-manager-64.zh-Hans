---
title: 活动流要点
seo-title: 活动流要点
description: 成员执行的最近活动列表或单个内容线程上的最近活动列表
seo-description: 成员执行的最近活动列表或单个内容线程上的最近活动列表
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 活动流要点{#activity-stream-essentials}

已登录社区成员的活动，例如向论坛或博客发帖，被收集到流中，该流可以通过配置活动流组件以各种方式过滤和显示。

在社区成员关注感兴趣的帖子或其他社区成员时，跟踪功能又增加了一组活动。

所有[社区站点](overview.md#communitiessites)都包含登录成员的用户配置文件页面，该用户配置文件页面将以相同方式显示成员活动。

## 概念  {#concepts}

*活动流*&#x200B;是成员执行的最近活动的列表或单个内容线程（如论坛主题或博客）上的最近活动的列表。

成员可以通过跟踪其他个人或内容来跟踪活动流。

*新闻源*&#x200B;是将一个成员跟踪的活动流合并到单个流中。

[社交图](essentials-socialgraph.md)捕获一个成员与另一个成员的以下关系。

## 客户端{#essentials-for-client-side}的要点

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>社交/活动流/组件/hbs/活动流</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> 属性</strong></td> 
   <td>请参阅<a href="activities.md">活动流功能</a></td> 
  </tr>
 </tbody>
</table>

* [客户端自定义](client-customize.md)

## 服务器端{#essentials-for-server-side}的要点

* [活动流API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [活动流侦听器API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [服务器端自定义](server-customize.md)

### 活动流功能 {#activity-stream-function}

包含[活动流函数](functions.md#activity-stream-function)的社区站点结构，包括已配置的`activity streams`组件。
