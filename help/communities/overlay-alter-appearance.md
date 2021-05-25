---
title: 更改外观
seo-title: 更改外观
description: 修改脚本
seo-description: 修改脚本
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 更改外观{#alter-the-appearance}

## 修改脚本{#modify-the-script}

comment.hbs脚本负责为每个注释创建整体HTML。

要在每个已发布评论旁边不显示头像，请执行以下操作：

1. 将`comment.hbs`从`libs`复制到`apps`
   1. 选择 `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. 选择&#x200B;**[!UICONTROL Copy]**
   1. 选择 `/apps/social/commons/components/hbs/comments/comment`
   1. 选择&#x200B;**[!UICONTROL 粘贴]**
1. 打开覆盖的`comment.hbs`
   * 双击`/apps/social/commons/components/hbs/comments/comment folder`中的节点`comment.hbs`
1. 找到以下行，并删除或注释它们：

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

删除这些行，或用&#39;&lt;!—&#39;和&#39;—>&#39;来注释掉它们。 此外，还会添加字符“xxx”作为头像所在位置的视觉指示器。

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## 复制叠加{#replicate-the-overlay}

使用复制工具将覆盖的评论组件推送到发布实例。

>[!NOTE]
>
>一种更可靠的复制形式是在包管理器中创建一个包，并[activate](../../help/sites-administering/package-manager.md#replicating-packages)它。 可以导出和存档资源包。

在全局导航中，选择&#x200B;**[!UICONTROL 工具>部署>复制]**，然后选择&#x200B;**[!UICONTROL 激活树]**。

对于开始路径，输入`/apps/social/commons`并选择&#x200B;**[!UICONTROL 激活]**。

![chlimage_1-42](assets/chlimage_1-42.png)

## 查看结果{#view-results}

如果您以管理员身份登录发布实例，例如以管理员/管理员身份登录http://localhost:4503/crx/de ，则可以验证覆盖的组件是否位于此处。

如果注销并重新登录为`aaron.mcdonald@mailinator.com/password`并刷新页面，您会发现发布的评论不再显示为头像，而是显示一个简单的“xxx”。

![chlimage_1-43](assets/chlimage_1-43.png)
