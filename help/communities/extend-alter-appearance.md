---
title: 更改外观(HBS)
seo-title: Alter the Appearance
description: 修改HBS脚本
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 2%

---

# 更改外观(HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

现在，应用程序目录(/apps)中自定义注释系统的组件就位，并且resourceSuperType引用默认注释系统并注册了自定义模型/视图，因此可以修改实施。

对于简单的演示，会删除视觉功能（发布评论的已登录用户显示的头像）。

>[!NOTE]
>
>要使用该扩展，要受影响的网站(/content)中评论系统的实例必须将其resourceType设置为自定义评论系统。

## 修改HBS脚本 {#modify-the-hbs-scripts}

使用 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 打开 [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * 注释掉包含评论帖子头像的标记（~第21行）：

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* 打开 [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * 注释掉包含下一个评论条目的头像的标记（~第44行）：

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* 选择 **全部保存**

## 复制自定义应用程序 {#replicate-custom-app}

修改应用程序后，需要重新复制自定义组件。

一种方法是

* 从主菜单

   * 选择 **[!UICONTROL 工具>操作>复制]**
   * 选择 `Activate Tree`
   * 已设置 `Start Path`:to `/apps/custom`
   * 取消选中 `Only Modified`
   * 选择 `Activate` 按钮

## 在已发布的示例页面上查看已修改的注释 {#view-modified-comment-on-published-sample-page}

[继续体验](extend-sample-page.md#publish-sample-page) 在发布实例上（仍以同一用户身份登录），现在可以在发布环境中刷新页面以查看修改以删除头像：

![chlimage_1-81](assets/chlimage_1-81.png)

## 示例注释扩展包 {#sample-comment-extension-package}

附加的是在本教程中创建的自定义注释应用程序包。

[获取文件](assets/sample-comment-extension-6-1-fp3.zip)
