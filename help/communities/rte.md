---
title: 富文本编辑器要点
seo-title: Rich Text Editor Essentials
description: 富文本编辑器功能概述
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 4%

---

# 富文本编辑器要点 {#rich-text-editor-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

富文本编辑器(RTE)提供了使用标记输入文本的功能。

对于社区组件，与 [创作环境中的富文本编辑器](../../help/sites-authoring/rich-text-editor.md)，则会影响在发布环境中输入的文本。

![chlimage_1-410](assets/chlimage_1-410.png)

## 启用富文本编辑器 {#enabling-rich-text-editor}

可以启用允许用户生成内容(UGC)的社区组件来允许RTE。 取决于组件是添加到页面还是包含在 [函数](functions.md)，默认情况下可能启用或未启用RTE。

如果未启用，只需输入 [创作编辑模式](sites-console.md#authoring-site-content)，选择要编辑的组件，然后选择 `Rich Text Editor` 复选框。

RTE可用于以下社区组件：

* [博客](blog-feature.md)
* [日程表](calendar.md)
* [评论](comments.md)
* [Filelibrary](file-library.md)
* [论坛](forum.md)
* [消息](configure-messaging.md)
* [问题与解答](working-with-qna.md)
* [审核](reviews.md)

## 自定义 {#customization}

可以自定义富文本编辑器，因为该实施基于 [CKEditor](https://www.ckeditor.com/).

社区组件的当前配置位于 `cq.social.  scf   clientlib`，位于

`/libs/clientlibs/social/commons/scf/ckrte.js`

不建议修改cq.social.scf clientlib，因为以后的升级可能会覆盖任何编辑。

### 示例自定义：内联链接 {#example-customization-inline-links}

出于安全考虑，默认情况下，超链接选项不会包含在呈现给成员的富文本图标集中。 在UGC中允许href时，故障诊断能力较强。

要将超链接选项添加到工具栏，请执行以下操作：

* 添加名为“ `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* 选择 **[!UICONTROL 全部保存]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
