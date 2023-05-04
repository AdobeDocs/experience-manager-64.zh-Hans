---
title: 工作总揽
seo-title: Assignments Essentials
description: 启用社区的工作总揽功能概述
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 12%

---

# 工作总揽 {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页提供了使用的分配功能的基本信息 [启用社区](overview.md#enablement-community) 站点。

分配功能是将支持资源和学习路径分配给支持社区的成员的功能。

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> 属性</strong></td> 
   <td>请参阅 <a href="assignments.md">工作分配功能</a></td> 
  </tr>
 </tbody>
</table>

### 完成和成功状态 {#completion-and-success-status}

“完成”和“成功”状态用于“工作总揽”的报表以及状态横幅。

完成状态:

* 未指定
* 未开始（新）
* 进行中
* 完成

成功状态:

* 未知
* 通过
* 失败

完成状态和成功状态的唯一可能组合包括：

| **完成** | **成功** |
|---|---|
| 未启动 | 未知 |
| 进行中 | 未知 |
| 完成 | 通过 |
| 完成 | 失败 |

## 服务器端要点 {#essentials-for-server-side}

### 指定任务功能 {#assignments-function}

包含 [分配函数](functions.md#assignments-function)，包括已配置的 ` [assignments](assignments.md)` 组件。

### 参考API {#reference-apis}

* [启用API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [报表API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [报表分析API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
