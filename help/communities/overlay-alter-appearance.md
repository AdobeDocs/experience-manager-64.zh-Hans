---
title: 更改外观
seo-title: Alter the Appearance
description: 修改脚本
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 2%

---

# 更改外观 {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 修改脚本 {#modify-the-script}

comment.hbs脚本负责为每个注释创建整体HTML。

要在每个已发布评论旁边不显示头像，请执行以下操作：

1. 复制 `comment.hbs`从 `libs`to `apps`
   1. 选择 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 选择 **[!UICONTROL 复制]**
   1. 选择 `/apps/social/commons/components/hbs/comments/comment`
   1. 选择 **[!UICONTROL 粘贴]**
1. 打开覆盖的 `comment.hbs`
   * 双击节点  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. 找到以下行，并删除或注释它们：

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

删除这些行，或在其周围添加“&lt;!>—&#39;和&#39;—>&#39;来注释掉它们。 此外，还会添加字符“xxx”作为头像所在位置的视觉指示器。

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 复制叠加 {#replicate-the-overlay}

使用复制工具将覆盖的评论组件推送到发布实例。

>[!NOTE]
>
>一种更为可靠的复制形式是在包管理器和 [激活](../../help/sites-administering/package-manager.md#replicating-packages) 它。 可以导出和存档资源包。

在全局导航中，选择 **[!UICONTROL 工具>部署>复制]** 然后 **[!UICONTROL 激活树]**.

对于开始路径，输入 `/apps/social/commons` 选择 **[!UICONTROL 激活]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## 查看结果 {#view-results}

如果您以管理员身份登录发布实例，例如以管理员/管理员身份登录http://localhost:4503/crx/de ，则可以验证覆盖的组件是否位于此处。

如果您注销，并重新登录为 `aaron.mcdonald@mailinator.com/password` 刷新页面后，您会发现发布的评论不再显示为头像，而是显示一个简单的“xxx”。

![chlimage_1-43](assets/chlimage_1-43.png)
