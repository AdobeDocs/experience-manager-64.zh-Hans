---
title: 使用内容属性导出内容
seo-title: Using Content Properties to Export Content
description: 以下页面显示了应用程序属性和节点。
seo-description: The following page shows App Properties and Nodes.
uuid: 73f1832f-e457-47d0-a0e1-80af90897d31
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a3006835-b1d2-47d6-959a-cdb692e34e1e
exl-id: 27aa405d-2388-4f91-85d0-1a8709e0d5d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 5%

---

# 使用内容属性导出内容{#using-content-properties-to-export-content}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建议对需要基于单页应用程序框架的客户端渲染（例如React）的项目使用SPA编辑器。 [了解详情](/help/sites-developing/spa-overview.md).

应用程序表示为 *cq:Pages* 在AEM中。

它们共享在任何 *cq:Page* 除了下面显示的其他支持集成的属性之外，

## 应用程序属性 {#app-properties}

下表显示 **应用程序属性和节点**.

<table>
 <tbody>
  <tr>
   <td><strong>属性名称</strong></td>
   <td><strong>类型</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td>dps-cloudConfig</td>
   <td>字符串：路径</td>
   <td><p>配置的移动设备按需Cloud Service的路径。 用于AEM Mobile到Mobile On-Demand操作（API调用）</p> <p>当作者选择按需移动设备Cloud Service将应用程序与关联时，可通过管理连接拼贴配置此关联。</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>字符串：路径</td>
   <td><p>应用程序导出配置的路径。 导出配置是一个文件夹，其中包含2个子ContentSync导出配置模板；</p> <p><i>dps-article</i>:用于导出文章内容的ContentSync导出配置</p> <p><i>dps-HTMLResources</i>:用于导出应用程序/文章共享资源的ContentSync导出配置</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>字符串</td>
   <td><p>此应用程序已链接/绑定到的Mobile On-Demand项目的ID/URI。</p> <p>当作者从关联的Mobile On-DemandCloud Service的可用项目列表中选择项目时，可通过管理连接拼贴配置此关联。</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>字符串</td>
   <td>应用程序标题。</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>字符串</td>
   <td>内容类型.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>日期</td>
   <td>上次将共享资源从AEM上传到AEM Mobile的日期。</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploadedBy</td>
   <td>字符串：userid</td>
   <td>上次将共享资源请求从AEM上传到AEM Mobile的用户ID。</td>
  </tr>
  <tr>
   <td>pge-dashboard-config</td>
   <td>字符串：路径</td>
   <td>功能板配置的路径。 可以根据需要将路径重定向到自定义功能板配置。</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>字符串：路径</td>
   <td><p>cq的路径：已扩展或已扩展的组件 <i>mobileapps/core/components/instance。</i></p> <p>这可提供应用程序目录中的存在和渲染情况。</p> </td>
  </tr>
 </tbody>
</table>

您可以使用 ***内容属性*** 创建内容。 请参阅以下资源以创建和导出文章和共享资源：

* [内容属性](/help/mobile/content-properties.md)
* [创建文章导出配置](/help/mobile/creating-article-export-configuration.md)
* [创建共享资源导出配置](/help/mobile/creating-shared-resources-export-configuration.md)
