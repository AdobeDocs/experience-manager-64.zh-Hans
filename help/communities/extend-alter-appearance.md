---
title: 更改外观(HBS)
seo-title: 更改外观
description: 修改HBS脚本
seo-description: 修改HBS脚本
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 更改外观(HBS){#alter-the-appearance-hbs}

现在，应用程序目录(/apps)中自定义注释系统的组件就位，并且resourceSuperType引用默认注释系统并注册了自定义模型/视图，因此可以修改实施。

对于简单的演示，会删除视觉功能（发布评论的已登录用户显示的头像）。

>[!NOTE]
>
>要使用该扩展，要受影响的网站(/content)中评论系统的实例必须将其resourceType设置为自定义评论系统。

## 修改HBS脚本{#modify-the-hbs-scripts}

使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 打开[/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 注释掉包含评论帖子头像的标记（~第21行）：

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* 打开[/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 注释掉包含下一个评论条目的头像的标记（~第44行）：

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 选择&#x200B;**Save All**

## 复制自定义应用程序{#replicate-custom-app}

修改应用程序后，需要重新复制自定义组件。

一种方法是

* 从主菜单

   * 选择&#x200B;**[!UICONTROL 工具>操作>复制]**
   * 选择 `Activate Tree`
   * 设置`Start Path`:至`/apps/custom`
   * 取消选中`Only Modified`
   * 选择`Activate`按钮

## 查看已发布示例页面{#view-modified-comment-on-published-sample-page}上的已修改注释

[继续发](extend-sample-page.md#publish-sample-page) 布实例上的体验（仍以同一用户身份登录），现在可以在发布环境中刷新页面以查看修改以删除头像：

![chlimage_1-81](assets/chlimage_1-81.png)

## 示例注释扩展包{#sample-comment-extension-package}

附加的是在本教程中创建的自定义注释应用程序包。

[获取文件](assets/sample-comment-extension-6-1-fp3.zip)
