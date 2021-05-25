---
title: 将注释添加到示例页面
seo-title: 将注释添加到示例页面
description: 将自定义注释添加到页面
seo-description: 将自定义注释添加到页面
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# 将注释添加到示例页面{#add-comment-to-sample-page}

现在，自定义注释系统的组件已位于应用程序目录(/apps)中，因此可以使用扩展组件。 要受影响的网站中评论系统的实例必须将其resourceType设置为自定义评论系统，并包含所有必需的客户端库。

## 识别所需的Clientlib {#identify-required-clientlibs}

对于扩展注释，还需要默认注释的样式和功能所必需的客户端库。

[社区组件指南](components-guide.md)标识所需的客户端库。 浏览组件指南并查看注释组件，例如：

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

请注意注释正确呈现和运行所需的三个客户端库。 在引用扩展注释的位置以及[扩展注释的客户端库](extend-create-components.md#create-a-client-library-folder)(`apps.custom.comments`)时，需要包含这些注释。

![chlimage_1-47](assets/chlimage_1-47.png)

## 将自定义注释添加到页面{#add-custom-comments-to-a-page}

由于每页只能有一个注释系统，因此创建示例页面更简单，如简短的[创建示例页面](create-sample-page.md)教程中所述。

创建后，进入设计模式并使自定义组件组可用，以允许将`Alt Comments`组件添加到页面。

要使注释正常显示和运行，必须将注释的客户端库添加到页面的clientlibs列表中（请参阅[Clientlibs for Communities Components](clientlibs.md)）。

### 示例页面{#comments-clientlibs-on-sample-page}上的注释Clientlibs

![示例页面上的注释Clientlibs](assets/chlimage_1-48.png)

### 作者：示例页面{#author-alt-comment-on-sample-page}上的Alt注释

![示例页面上的替换注释](assets/chlimage_1-49.png)

### 作者：示例页面注释节点{#author-sample-page-comments-node}

您可以通过查看示例页面`/content/sites/sample/en/jcr:content/content/primary/comments`中注释节点的属性来验证CRXDE中的resourceType。

![chlimage_1-50](assets/chlimage_1-50.png)

### 发布示例页面{#publish-sample-page}

将自定义组件添加到页面后，还需要(re)[发布页面](sites-console.md#publishing-the-site)。

### 发布：示例页面{#publish-alt-comment-on-sample-page}上的Alt注释

发布自定义应用程序和示例页面后，应该可以输入评论。 登录后，无论是使用[演示用户](tutorials.md#demo-users)还是管理员，都应该可以发布评论。

以下是aaron.mcdonald@mailinator.com发布评论：

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

现在，扩展组件在默认外观上工作正常，是时候修改外观了。
