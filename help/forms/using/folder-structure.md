---
title: 了解文件夹结构
seo-title: Understanding the folder structure
description: 如何了解要自定义的AEM Forms工作区源代码的文件夹结构。
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%

---

# 了解文件夹结构 {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM Forms工作区组件是使用Backbone在MVC架构上设计的。 每个组件都有一个用于：

* 模型，其中包含业务逻辑。
* 模板，即包含界面控件的HTML文件。
* 视图，它充当模板的Controller类。

所有组件的资产都放置在下面描述的文件夹结构中。 要访问资产，请登录CRXDE Lite并浏览 `/libs/ws/js/runtime/`.

**模型** 包含骨干型号。

**视图** 包含骨干视图。

**模板** 仅包含组件的HTML模板。

**路由** 包含通用路由。 路由内的“模板”文件夹包含HTML代码和对组件的引用。

**服务** 包含用于在REST端点上调用Adobe Experience Manager服务器API的服务接口。

**util** 包含可由多个组件使用的通用实用程序。
