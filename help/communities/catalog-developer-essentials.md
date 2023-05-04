---
title: 目录要点
seo-title: Catalog Essentials
description: 目录概述
seo-description: Catalog overview
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
exl-id: 1e0a7cab-39b9-4c90-810c-c93fb76c3869
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---

# 目录要点 {#catalog-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页提供了有关使用启用社区站点的目录功能的基本信息。

目录功能（当包含在社区站点中时）允许社区成员浏览并选择目录中列出的支持资源。

的 [ `enablement catalog` 组件](catalog.md) 允许社区成员访问 [启用资源](resources.md). 使用AEM标记是管理目录中启用资源外观的重要部分。

请参阅 [标记支持资源](tag-resources.md).

## 客户端要点 {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/catalog</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>可包含</strong></a></td> 
   <td>否</td> 
  </tr> 
  <tr> 
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.catalog<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr> 
  <tr> 
   <td> <strong>模板</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/catalog.hbs<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/clientlibs/catalog.css</td> 
  </tr> 
  <tr> 
   <td><strong> 属性</strong></td> 
   <td>请参阅 <a href="catalog.md">目录功能</a></td> 
  </tr> 
 </tbody> 
</table>

## 服务器端要点 {#essentials-for-server-side}

### 目录功能 {#catalog-function}

包含 [目录函数](functions.md#catalog-function)，包括已配置的 `enablement catalog` 组件。

### 预过滤器 {#pre-filters}

将目录功能添加到社区站点后，可以通过指定预过滤器来限制目录中显示的支持资源和学习路径。 这可以通过在网站的目录资源实例中设置属性来完成。

使用 [启用教程](getting-started-enablement.md):

* 在作者时
* 使用 [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md)

   * 例如 [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* 导航到目录页面上的目录资源

   * 例如，`/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`

* 添加子过滤器节点

   * 选择 `catalog`节点
   * 选择 **[!UICONTROL 创建节点]**

      * 名称: `filters`
      * 类型: `nt:unstructured`
   * 选择 **[!UICONTROL 全部保存]**


* 添加 `se_resource-tags` 属性 `filters` 节点

   * 选择 `filters` 节点
   * 添加多属性

      * 名称: `se_resource-tags`
      * 类型：字符串
      * 值： *&lt;enter a=&quot;&quot; span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />TagID](#pre-filter-tagids)>*[
      * 选择 **[!UICONTROL 多]**
      * 选择 **[!UICONTROL 添加]**

         * 在弹出对话框中，选择 `+` 添加其他预过滤标记ID

* 重新发布社区站点

![chlimage_1-189](assets/chlimage_1-189.png)

#### 预过滤标记ID {#pre-filter-tagids}

预过滤器 [标记ID](../../help/sites-developing/framework.md#tagid) 必须完全匹配应用于启用资源的标记。 这些参数在 `resources` 作为属性值的网站文件夹 `se_resource-tags`.

![chlimage_1-190](assets/chlimage_1-190.png)

### 参考API {#reference-apis}

* [启用API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [报表API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [报表分析API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/model/api/package-summary.html)
