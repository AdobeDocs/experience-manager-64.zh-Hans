---
title: 适用于社区组件的Clientlibs
seo-title: 适用于社区组件的Clientlibs
description: 社区的客户端库
seo-description: 社区的客户端库
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Clientlibs for Communities组件{#clientlibs-for-communities-components}

## 简介 {#introduction}

文档的此部分介绍如何将客户端库(clientlibs)添加到社区组件的页面。

有关基本信息，请访问：

* [使用客户端库，](../../help/sites-developing/clientlibs.md) 该库提供使用详细信息以及调试工具
* [SCF的Clientlib在自定](client-customize.md#clientlibs) 义SCF组件时提供有用信息
* [博客：AEM客户端库（如示例所示）](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## 为何需要Clientlibs {#why-clientlibs-are-required}

组件正常运行(JavaScript)和样式(CSS)需要Clientlibs。

当某个功能存在[社区函数](functions.md)时，所有必需的组件和配置（包括所需的clientlib）都将出现在社区站点中。 只有当其他组件可供作者使用时，才需要添加其他clientlib。

当缺少所需的clientlib时， [将社区组件添加到页面](author-communities.md)可能会导致javascript错误以及意外外观。

### 示例：未使用Clientlibs {#example-placed-reviews-without-clientlibs}进行审阅

![chlimage_1-244](assets/chlimage_1-244.png)

### 示例：使用Clientlibs {#example-placed-reviews-with-clientlibs}进行审阅

![chlimage_1-245](assets/chlimage_1-245.png)

## 识别所需的Clientlibs {#identifying-required-clientlibs}

面向开发人员的基本功能信息可识别所需的客户端库。

此外，从AEM实例浏览到[社区组件指南](components-guide.md)可访问组件所需的clientlib类别列表。

例如，在[Reviews页面](http://localhost:4502/content/community-components/en/reviews.html)的最顶部列出了所需的clientlib

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## 添加必需的Clientlibs {#adding-required-clientlibs}

当需要向页面添加社区组件时，如果组件尚不存在，则需要为该组件添加所需的clientlib。

使用[CRXDE|Lite](#using-crxde-lite)修改社区站点页面的现有clientlibslist。

要使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)为社区站点添加clientlib，请执行以下操作：

* 浏览到[https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* 在要添加组件的页面上找到`clientlibslist`节点

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* 选择`clientlibslist`节点

   * 找到字符串[]属性`scg:requiredClientLibs`
   * 选择其`Value`以访问字符串数组对话框

      * 根据需要向下滚动
      * 选择`+`以进入新的客户端库

         * 重复以添加更多客户端库
      * 选择&#x200B;**[!UICONTROL OK]**
   * 选择&#x200B;**[!UICONTROL Save All]**



>[!NOTE]
>
>如果网站不是社区网站，则需要发现网站正在使用的客户端库的存在或位置。

使用[AEM Communities](getting-started.md)快速入门示例（其中`site-name`为&#x200B;*engage*），添加reviews组件时，clientliblist的显示方式如下：

![chlimage_1-248](assets/chlimage_1-247.png)
