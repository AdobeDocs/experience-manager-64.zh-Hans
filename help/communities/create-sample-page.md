---
title: 创建示例页面
seo-title: Create a Sample Page
description: 创建社区站点示例
seo-description: Create a Sample community site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
exl-id: 00ac29fb-cc8f-4dd9-a261-839a4bf664c2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 创建示例页面 {#create-a-sample-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自AEM 6.1 Communities起，创建示例页面的最简单方法是创建一个简单的社区站点，该站点只包含一个页面功能。

这将包含一个Parsys组件，以便您能够 [为创作启用组件](basics.md#accessing-communities-components).

对示例组件进行探索的另一个选项是使用 [社区组件指南](components-guide.md).

## 创建社区站点 {#create-a-community-site}

这与创建新站点(如 [开始使用AEM Communities](getting-started.md).

主要区别在于，本教程将创建一个新的社区站点模板，该模板仅包含 [页面函数](functions.md#page-function) 以便创建一个简单的社区站点，该站点不包含其他功能（除了所有社区站点的基本预布线功能之外）。

### 创建新网站模板 {#create-new-site-template}

要开始使用，请创建一个简单的 [社区站点模板](sites.md).

从创作实例的全局导航中，选择 **[!UICONTROL 工具>社区>网站模板]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* 选择 `Create button`
* 基本信息

   * `Name`:单页模板
   * `Description`:由单个页面函数组成的模板。
   * 选择 `Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* 结构

   * 拖动 `Page` 函数添加到模板生成器
   * 对于配置函数详细信息，输入

      * `Title`:单页
      * `URL`: 页

![chlimage_1-84](assets/chlimage_1-84.png)

* 选择 **`Save`** 对于配置
* 选择 **`Save`** 网站模板

### 创建新社区站点 {#create-new-community-site}

现在，根据简单的网站模板创建一个新的社区网站。

创建网站模板后，从全局导航中选择 **[!UICONTROL 社区>站点]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* 选择 **`Create`** 图标

* 步骤 `1 - Site Template`

   * `Title`:简单社区站点
   * `Description`:一个社区站点，包含一个用于实验的页面。
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`:样本

      * url = http://localhost:4502/content/sites/sample
   * `Template`:选择 `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* 选择 `Next`
* 步骤 `2 - Design`

   * 选择任意设计

* 选择 `Next`
* 选择 `Next`

   （接受所有默认设置）

* 选择 `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## 发布站点 {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

从 [社区站点控制台](sites-console.md)，选择发布图标以发布站点，默认情况下为http://localhost:4503 。

## 在编辑模式下打开作者网站 {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

选择打开的网站图标以在编辑模式下查看网站。

URL将为 [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

在简单的主页上，您可以查看通过社区功能和模板预先连接的内容，并播放添加和配置社区组件的过程。

## 在发布时查看网站 {#view-site-on-publish}

发布页面后，在 [发布实例](http://localhost:4503/content/sites/sample/en.html) 以匿名站点访客、已登录成员或管理员身份试用这些功能。 除非管理员登录，否则在创作环境中显示的“管理”链接将不会显示在发布环境中。
