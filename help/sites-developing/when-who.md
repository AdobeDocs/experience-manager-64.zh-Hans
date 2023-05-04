---
title: 测试 — 何时与谁一起进行？
seo-title: Testing - when and with whom?
description: 测试和项目开发的各个阶段可能涉及各种角色
seo-description: Various roles can be involved in testing and at various stages of project development
uuid: 431e8f06-80eb-4fb3-a4c7-2580608b0a1c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 6148f8e6-ab62-4eb8-8a2d-c431b8318000
exl-id: cba4a814-052b-4b9f-96f2-8c80b2766ecc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 1%

---

# 测试 — 何时与谁一起进行？{#testing-when-and-with-whom}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

测试和项目开发的各个阶段可能涉及各种角色。

<table> 
 <tbody> 
  <tr> 
   <td>测试团队</td> 
   <td>负责…… </td> 
   <td>时间...</td> 
  </tr> 
  <tr> 
   <td>开发团队</td> 
   <td>开发团队负责您的单元测试和一些集成测试。</td> 
   <td>这些测试在链中处于首位，但在开发过程中会重复/扩展这些测试。</td> 
  </tr> 
  <tr> 
   <td>质量保证团队</td> 
   <td><p>您将需要质量保证团队（无论规模大小如何）来进行功能和性能测试。</p> <p>这些是中性的专业测试人员 — 软件的黄金法则始终规定，开发人员绝不应测试自己的工作。</p> <p>此团队的成员可能来自“日”项目团队、合作伙伴和/或您的客户团队。</p> </td> 
   <td><p>第一个函数版本应当提供给测试人员（尽快切合实际地提供）。 尽管提前发布临时版本可能会产生大量错误，但它可以就关键问题提供早期反馈。</p> </td> 
  </tr> 
  <tr> 
   <td>客户测试团队</td> 
   <td><p>根据所选项目模型，可能会为客户团队成员（特别是客户站点的作者）计划参与测试。</p> <p>优势在于：</p> 
    <ul> 
     <li><p>为客户提供正在开发的项目的体验。</p> </li> 
     <li><p>提供客户的早期反馈。</p> </li> 
     <li><p>用户往往根据以往的经验来表达自己的需求；让客户尽早参与测试，可增加他们对新项目的体验， <i>动手</i> 体验。</p> </li> 
    </ul> </td> 
   <td><p>同样，早期参与也是好事，不过客户使用的任何版本都应该是稳定的，并且具有合理的功能。</p> <p>第一印象始终很重要。</p> </td> 
  </tr> 
 </tbody> 
</table>
