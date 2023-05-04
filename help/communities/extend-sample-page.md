---
title: 将注释添加到示例页面
seo-title: Add Comment to Sample Page
description: 将自定义注释添加到页面
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# 将注释添加到示例页面 {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

现在，自定义注释系统的组件已位于应用程序目录(/apps)中，因此可以使用扩展组件。 要受影响的网站中评论系统的实例必须将其resourceType设置为自定义评论系统，并包含所有必需的客户端库。

## 识别所需的Clientlib {#identify-required-clientlibs}

对于扩展注释，还需要默认注释的样式和功能所必需的客户端库。

的 [社区组件指南](components-guide.md) 标识所需的客户端库。 浏览组件指南并查看注释组件，例如：

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

请注意注释正确呈现和运行所需的三个客户端库。 在引用扩展注释的位置以及 [扩展注释的客户端库](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`)。

![chlimage_1-47](assets/chlimage_1-47.png)

## 向页面添加自定义注释 {#add-custom-comments-to-a-page}

由于每页只能有一个评论系统，因此创建示例页面更简单，如简短中所述 [创建示例页面](create-sample-page.md) 教程。

创建后，进入设计模式，并使自定义组件组可允许 `Alt Comments` 要添加到页面的组件。

要使评论正常显示和运行，必须将评论的客户端库添加到页面的clientlibslist(请参阅 [适用于社区组件的Clientlibs](clientlibs.md))。

### 示例页面上的注释Clientlibs {#comments-clientlibs-on-sample-page}

![示例页面上的注释Clientlibs](assets/chlimage_1-48.png)

### 作者：示例页面上的替换注释 {#author-alt-comment-on-sample-page}

![示例页面上的替换注释](assets/chlimage_1-49.png)

### 作者：示例页面注释节点 {#author-sample-page-comments-node}

您可以在CRXDE中通过查看示例页面的注释节点的属性来验证resourceType(位于 `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### 发布示例页面 {#publish-sample-page}

将自定义组件添加到页面后，还需要(re) [发布页面](sites-console.md#publishing-the-site).

### 发布：示例页面上的替换注释 {#publish-alt-comment-on-sample-page}

发布自定义应用程序和示例页面后，应该可以输入评论。 登录时，使用 [演示用户](tutorials.md#demo-users) 或管理员，则可以发布评论。

以下是aaron.mcdonald@mailinator.com发布评论：

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

现在，扩展组件在默认外观上工作正常，是时候修改外观了。
