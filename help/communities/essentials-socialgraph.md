---
title: 社交图要点
seo-title: Social Graph Essentials
description: 以下组件概述
seo-description: follow component and following component overview
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 3%

---

# 社交图要点 {#social-graph-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

社区成员遵循的能力 [活动](essentials-activities.md) 并通过两个部分建立：

的 `follow`组件必须与其他资源关联，并且已为 [社区网站](overview.md#communitiessites).

的 `following`组件列出当前成员之后或当前成员后面的成员。 该社区网站的用户配置文件中包含成员之间的关系社交图。

## 客户端要点 {#essentials-for-client-side}

### 关注 {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgraph/components/hbs/relationships</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> 属性</strong></td> 
   <td>请参阅 <a href="socialgraph.md">使用社交图</a></td> 
  </tr>
  <tr>
   <td><strong> 可选<br /> 属性</strong></td> 
   <td>
    <ul> 
     <li>名称: <strong><code>outgoing</code></strong></li> 
     <li>类型：布尔值</li> 
     <li>价值:<br /> 
      <ul> 
       <li><i>true </i>- <code>following</code> 组件将列出当前已登录成员的成员 <code>follows</code></li> 
       <li><i>false </i>- <code>following</code> 组件将列出 <code>follow </code>当前已登录的会员</li> 
      </ul> </li> 
    </ul> <p>默认为 <i>true</i> 属性缺失时。 当前，无法在创作模式下使用编辑对话框设置此属性。 必须将资产添加到的实例 <code>following </code>节点使用 <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### 关注 {#follow}

| **resourceType** | social/socialgraph/components/hbs/folling |
|---|---|
| [**可包含**](scf.md#add-or-include-a-communities-component) | 否 |
| **模板** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [客户端自定义](client-customize.md)

## 服务器端要点 {#essentials-for-server-side}

* [社交图API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [社交图端点](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [服务器端自定义](server-customize.md)
