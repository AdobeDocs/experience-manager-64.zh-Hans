---
title: Assignments Essentials
seo-title: Assignments Essentials
description: 支持社区的任务功能概述
seo-description: 支持社区的任务功能概述
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---


# Assignments Essentials {#assignments-essentials}

本页提供了使用Enablement Community站点的任务功能的基 [本信息](overview.md#enablement-community) 。

分配功能是将支持资源和学习路径分配给支持社区的成员。

## 客户端必备工具 {#essentials-for-client-side}

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
   <td>查看 <a href="assignments.md">任务功能</a></td> 
  </tr>
 </tbody>
</table>

### 完成和成功状态 {#completion-and-success-status}

“完成”和“成功”状态用于“任务”上的报告和状态横幅。

完成状态:

* 未指定
* 未开始（新）
* 进行中
* 完成

成功状态:

* 未知
* Pass
* 失败

完成状态和成功状态的唯一可能组合是：

| **完成** | **成功** |
|---|---|
| 未启动 | 未知 |
| 进行中 | 未知 |
| 完成 | Pass |
| 完成 | 失败 |

## 服务器端必备工具 {#essentials-for-server-side}

### 指定任务功能 {#assignments-function}

包含“分配”功能的社区 [站点结构](functions.md#assignments-function)，包括已配置的 ` [assignments](assignments.md)` 组件。

### 参考API {#reference-apis}

* [Enablement API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [报告API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [报告分析API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)