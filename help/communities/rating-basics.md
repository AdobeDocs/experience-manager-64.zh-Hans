---
title: 评级要点
seo-title: Rating Essentials
description: 评级组件概述
seo-description: Rating component overview
uuid: 48ef61ad-be7a-4a6b-a284-23e5bb4f1671
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7dc3ef57-05c3-45d4-ace3-bb3ba6ea768b
exl-id: f722051c-9512-4420-b12e-cb20aa6759f7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 2%

---

# 评级要点 {#rating-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

评级组件， [计数](tally.md) 子类允许在社区成员中签名以对网站上的功能进行评级。

允许在同一页面上放置一个投票组件的多个实例；每个实例必须配置一个唯一 `tally name` 属性。

不支持匿名发布评级。 网站访客必须注册并登录才能仅参与一次评级。 已登录的访客（会员）可以随时更改其评级。

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td> 社交/计数/组件/hbs/评分</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>是 — 可在 <i>设计 </i>模式</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.rating</td> 
  </tr> 
  <tr> 
   <td> <strong>模板</strong></td> 
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td><p>请参阅 <a href="rating.md">使用评级</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [计数API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [计数端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 访问已发布的评级(UGC) {#accessing-posted-ratings-ugc}

UGC应使用其中一种标准审核方法进行审核。\
请参阅 [审核用户生成的内容](moderate-ugc.md).

自AEM 6.1 Communities起，使用 [公用商店](working-with-srp.md) 对于UGC，包括以编程方式访问UGC，而不考虑选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**.

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法
