---
title: 称赞要点
seo-title: Liking Essentials
description: 称赞组件概述
seo-description: Liking component overview
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
exl-id: 509d1fb4-a88d-4438-a618-ba063adb6fb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 2%

---

# 称赞要点 {#liking-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

称赞组件， [计数](tally.md) 子类是一个有用的工具，它允许成员通过简单选择心图标来对特定内容段表达积极意见。

允许在同一页面上放置多个称赞组件实例；每个实例必须配置一个唯一 `tally name` 属性。

不支持匿名发布类似。 网站访客必须注册并登录才能参与称赞。 已登录的访客（会员）可以随时打开和关闭。

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>社交/计数/组件/hbs/称赞</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>是 — 可在 <i>设计 </i>模式</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.liking</td> 
  </tr> 
  <tr> 
   <td> <strong>模板</strong></td> 
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td><p>请参阅 <a href="liking.md">使用称赞</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [计数API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [计数端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 访问已发布的投票(UGC) {#accessing-posted-voting-ugc}

UGC应使用其中一种标准审核方法进行审核。\
请参阅 [审核用户生成的内容](moderate-ugc.md).

自AEM 6.1 Communities起，使用 [公用商店](working-with-srp.md) 对于UGC，包括以编程方式访问UGC，而不考虑选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**.

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法
