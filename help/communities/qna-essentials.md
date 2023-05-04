---
title: 问题解答要点
seo-title: QnA Essentials
description: 问题和回答论坛功能
seo-description: Questions and answers forum feature
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: 99f8afda-1771-471b-bd0c-99960a453bc9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---

# 问题解答要点 {#qna-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页提供了处理问题和答案(QnA)论坛功能的基本信息。

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">可包含</a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientlibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.voting<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> 模板</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> css</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> 属性</td> 
   <td>请参阅 <a href="working-with-qna.md">问题解答论坛功能</a></td> 
  </tr>
 </tbody>
</table>

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [问题解答API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [问题解答端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [服务器端自定义](server-customize.md)

### 问题与解答功能 {#qna-function}

包含 [问题解答函数](functions.md#qna-function) 将配置 `QnA` 组件，以及影响审核和标记的设置。 QnA函数支持识别 [特权成员用户组](users.md#privileged-members-group).

### 访问QnA论坛帖子(UGC) {#accessing-qna-forum-posts-ugc}

UGC应使用其中一种标准审核方法进行审核。\
请参阅 [审核用户生成的内容](moderate-ugc.md).

自AEM 6.1 Communities起，使用 [公用商店](working-with-srp.md) 对于UGC，包括以编程方式访问UGC，而不考虑选择的存储选项（如ASRP、MSRP或JSRP）。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**.

请参阅：

* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [SRP和UGC要点](srp-and-ugc.md) - SRP实用程序方法和示例
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 将已弃用的实用程序方法映射到当前SRP实用程序方法
