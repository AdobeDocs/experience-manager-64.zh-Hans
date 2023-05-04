---
title: 日历要点
seo-title: Calendar Essentials
description: 日历功能概述
seo-description: Calendar feature overview
uuid: 14ff7a83-b2a7-4f7e-8ee7-88f336329a1a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 88932a3c-ba7f-47ba-9e0b-206755c2d42e
exl-id: cdf5e5d3-a78c-4f32-ad40-665876392a97
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 3%

---

# 日历要点 {#calendar-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页提供了有关使用日历功能的基本信息。

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/calendar/components/hbs/calendar</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.calendar</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td>/libs/social/calendar/components/hbs/calendar/calendar.hbs</td> 
   <td> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td>/libs/social/calendar/components/hbs/calendar/clientlibs/css/calendar.css<br /> /libs/social/calendar/components/hbs/calendar/clientlibs/css/jqueryui.css</td> 
  </tr>
  <tr>
   <td><strong> 属性</strong></td> 
   <td>请参阅 <a href="calendar.md">使用日历</a></td> 
  </tr>
 </tbody>
</table>

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [日历API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [日历端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 日历功能 {#calendar-function}

包含 [日历函数](functions.md#calendar-function) 将配置c `alendar`组件。 日历功能支持识别 [特权成员用户组](users.md#privileged-members-group).

### 访问日历帖子(UGC) {#accessing-calendar-posts-ugc}

自AEM 6.1 Communities起，使用 [公用商店](working-with-srp.md) 对于UGC，包括以编程方式访问UGC，而不考虑选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**.

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法
