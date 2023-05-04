---
title: 适用于社区组件的Clientlibs
seo-title: Clientlibs for Communities Components
description: 社区的客户端库
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 1%

---

# 适用于社区组件的Clientlibs {#clientlibs-for-communities-components}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

文档的此部分介绍如何将客户端库(clientlibs)添加到社区组件的页面。

有关基本信息，请访问：

* [使用客户端库](../../help/sites-developing/clientlibs.md) 提供了使用详细信息以及调试工具
* [用于SCF的Clientlibs](client-customize.md#clientlibs) 它在自定义SCF组件时提供了有用的信息

## 为何需要Clientlibs {#why-clientlibs-are-required}

组件正常运行(JavaScript)和样式(CSS)需要Clientlibs。

当存在 [社区功能](functions.md) 对于功能，社区站点中将提供所有必需的组件和配置，包括所需的clientlib。 只有当其他组件可供作者使用时，才需要添加其他clientlib。

当缺少所需的clientlib时， [向页面添加社区组件](author-communities.md) 可能会导致javascript错误以及意外外观。

### 示例：未使用Clientlibs进行审阅 {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### 示例：使用Clientlibs进行审阅 {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## 确定所需的Clientlib {#identifying-required-clientlibs}

面向开发人员的基本功能信息可识别所需的客户端库。

此外，从AEM实例浏览到 [社区组件指南](components-guide.md) 提供对组件所需clientlib类别列表的访问权限。

例如，在 [“审阅”页面](http://localhost:4502/content/community-components/en/reviews.html) 列出的必需clientlibs

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## 添加必需的Clientlibs {#adding-required-clientlibs}

当需要向页面添加社区组件时，如果组件尚不存在，则需要为该组件添加所需的clientlib。

使用 [CRXDE|Lite](#using-crxde-lite) 修改社区站点页面的现有clientlibslist。

要为社区站点添加clientlib，请使用 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 浏览到 [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* 找到 `clientlibslist` 节点。

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* 使用 `clientlibslist` 选定节点

   * 找到字符串[] 属性 `scg:requiredClientLibs`
   * 选择其 `Value` 访问字符串数组对话框

      * 根据需要向下滚动
      * 选择 `+` 输入新的客户端库

         * 重复以添加更多客户端库
      * 选择 **[!UICONTROL 确定]**
   * 选择 **[!UICONTROL 全部保存]**



>[!NOTE]
>
>如果网站不是社区网站，则需要发现网站正在使用的客户端库的存在或位置。

使用 [开始使用AEM Communities](getting-started.md) 示例，其中 `site-name` is *参与*，添加审阅组件时，clientliblist的显示方式如下：

![chlimage_1-247](assets/chlimage_1-247.png)
