---
title: 更改外观(HBS)
seo-title: 改变外观
description: 修改HBS脚本
seo-description: 修改HBS脚本
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# 更改外观(HBS){#alter-the-appearance-hbs}

现在，应用程序目录(/apps)中的自定义注释系统的组件就位，并且resourceSuperType引用默认注释系统和注册的自定义模型/视图，因此可以修改实现。

对于简单的演示，将删除可视功能（发布评论的已登录用户显示的头像）。

>[!NOTE]
>
>要使用扩展，要受影响的网站(/content)中评论系统的实例必须将其resourceType设置为自定义评论系统。

## 修改HBS脚本{#modify-the-hbs-scripts}

使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 打开[/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 注释掉包含评论帖子的头像的标记（~行21）:

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* 打开[/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 注释掉包含下一个注释条目的头像的标记（~行44）:

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 选择&#x200B;**保存全部**

## 复制自定义应用程序{#replicate-custom-app}

修改应用程序后，必须重新复制自定义组件。

一种方法是

* 从主菜单

   * 选择&#x200B;**[!UICONTROL 工具>操作>复制]**
   * 选择 `Activate Tree`
   * 设置`Start Path`:至`/apps/custom`
   * 取消选中`Only Modified`
   * 选择`Activate`按钮

## 已发布示例页面{#view-modified-comment-on-published-sample-page}上的视图修改注释

[继续使](extend-sample-page.md#publish-sample-page) 用发布实例的体验（仍以同一用户身份登录），现在可以刷新发布环境中的页面以视图修改以删除头像：

![chlimage_1-81](assets/chlimage_1-81.png)

## 示例注释扩展包{#sample-comment-extension-package}

附加是本教程中创建的自定义注释应用程序的包。

[获取文件](assets/sample-comment-extension-6-1-fp3.zip)