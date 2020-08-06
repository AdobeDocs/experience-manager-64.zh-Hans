---
title: 论坛功能
seo-title: 论坛功能
description: 如何添加和配置论坛功能
seo-description: 如何添加和配置论坛功能
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# 论坛功能 {#forum-feature}

## 简介 {#introduction}

论坛功能为发布环境中的登录站点访客（社区成员）提供了一个区域，用于：

* 创建新主题
* 视图和回复主题
* 关注主题
* 搜索论坛
* 帮助审核论坛内容
* 将论坛主题从一个页面移动到另一个页面

文档的本节介绍

* 将论坛功能添加到AEM站点
* 组件的配置设 `Forum`置

## Adding a Forum to a Page {#adding-a-forum-to-a-page}

要在创作模 `Forum` 式下将组件添加到页面，请使用组件浏览器来查找

* `Communities / Forum`

将其拖动到应显示论坛的页面上。

有关必要的信息，请访 [问社区组件基础](basics.md)。

当包含 [所需的客户端库](essentials-forum.md#essentials-for-client-side) ，组件的显示 `Forum`方式如下：

![chlimage_1-60](assets/chlimage_1-60.png)

## 配置论坛 {#configuring-a-forum}

选择要访问的 `Forum` 已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### “设置”选项卡 {#settings-tab}

在“设 **[!UICONTROL 置]** ”选项卡下，指定主题和回复的设置：

* **[!UICONTROL 每页主题]**&#x200B;定义每页显示的主题／帖子数。 默认值为10。

* **[!UICONTROL 已审核]**&#x200B;如果选中，则发布主题和评论之前必须获得批准，然后才能在发布站点上显示这些主题和评论。 默认为未选中。

* **[!UICONTROL 关闭]**&#x200B;如果选中，则论坛将关闭到新主题和评论。 默认为未选中。

* **[!UICONTROL 富文本编]**&#x200B;辑器如果选中，则主题和注释可以输入标记。 默认为未选中。

* **[!UICONTROL 允许标记]**&#x200B;如果选中，允许成员向其帖子中添加标记标签(请参 **[!UICONTROL 阅标记字段]** 选项卡)。 默认为未选中。

* **[!UICONTROL 允许文件上]**&#x200B;载如果选中，允许将文件附件添加到主题或评论。 默认为未选中。

* **[!UICONTROL 允许以]**&#x200B;下如果选中，则为论坛帖子提供以下功能，允许成员 [收到](notifications.md) 新帖子的通知。 默认为未选中。

* **[!UICONTROL 允许固]**&#x200B;定如果选中，论坛主题可能被固定到主题列表的顶部。 默认为未选中。

* **[!UICONTROL 如果选中]**“允许特色内容”，则可以将该想法标识为特 [色内容](featured.md)。 默认为未选中。

* **[!UICONTROL 允许电子邮件订阅]**&#x200B;如果选中此选项，则允许成员通过电子邮件(订阅)通知[新帖子](subscriptions.md)。 需要 `Allow Following` 检查并配置电 [子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 最大文件大小]**&#x200B;仅在 
`Allow File Uploads` 的双曲余切值。 此字段将限制已上载文件的大小（以字节为单位）。 默认值为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**&#x200B;仅在 
`Allow File Uploads` 的双曲余切值。 以逗号分隔的文件扩展名列表，以“点”分隔。 例如： .jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 仅当选中“允许文件]**&#x200B;上传”时，最大附加图像文件大小才相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许线程化]**&#x200B;回复如果选中，则允许回复发布到主题的注释。 默认为未选中。

* **[!UICONTROL 允许用户删除注释和主题]**&#x200B;如果选中，允许成员删除他们发布的注释和主题。 默认为未选中。

* **[!UICONTROL 允许投票]**&#x200B;如果选中，则在主题中包含投票功能。 默认为未选中。

* **[!UICONTROL 显示痕迹导航]**&#x200B;如果选中，则在主题页面上显示导航的痕迹导航。 选中默认值。

* **[!UICONTROL 显示标记]**&#x200B;如果选中，则使用会员的博 [客条目](implementing-scoring.md) ，显示已获得和已分配的标记。 默认为未选中。

>[!NOTE]
>
>可能需要同时检查和 `AllowThreaded Replies` 启用 `Allow users to Delete Comments and Topics` 对主题的注释。

### “用户审核”选项卡 {#user-moderation-tab}

在“用 **[!UICONTROL 户审核]** ”选项卡下，指定如何管理已发布的主题和回复（用户生成的内容）。 有关详细信息，请参 [阅调节用户生成的内容](moderate-ugc.md)。

* **[!UICONTROL 拒绝帖子]**&#x200B;如果选中，则允许受信任的成员审核者拒绝帖子并阻止帖子显示在公共论坛上。 默认为未选中。

* **[!UICONTROL 关闭／重新打开主]**&#x200B;题如果选中，受信任的成员审核者可以关闭主题以进一步编辑和评论，还可以重新打开主题。 默认为未选中。

* **[!UICONTROL 移动主题]**&#x200B;如果选中，则允许发布端版主移动主题。 选中默认值。

* **[!UICONTROL 标记帖子]**&#x200B;如果选中，则允许成员将其他人的主题或评论标记为不合适。 默认为未选中。

* **[!UICONTROL 标记原因列表]**&#x200B;如果选中，允许成员从下拉式列表中选择其标记主题或评论为不适当的原因。 默认为未选中。

* **[!UICONTROL 自定义标志原]**&#x200B;因如果选中，允许成员输入自己将主题或评论标记为不合适的原因。 默认为未选中。

* **[!UICONTROL 审核阈]**&#x200B;值输入在通知审核者之前，成员必须标记主题或评论的次数。 默认值为1（一次）。

* **[!UICONTROL 标记限]**&#x200B;制输入主题或评论在隐藏之前必须标记的次数，以避免公开视图。 如果设置为-1，则标记的主题或评论从不隐藏于公共视图。 否则，此数字必须大于或等于仲裁阈值。 默认值为5。

### 标记字段选项卡 {#tag-field-tab}

在“标 **[!UICONTROL 记”字段]** (Tag field)选项卡下 **[!UICONTROL ，根据所选的命名空间，在“设置”(Settings)选项卡下允许的情况下，]** 可以应用的标记会受到限制。

* **[!UICONTROL 允许的命名空间]**&#x200B;如果 `Allow Tagging` 在“设置”选项卡下选 **[!UICONTROL 中，则相]** 关。 可应用的标记仅限于所选命名空间类别内的标记。 命名空间的列表包括“标准标记”(默认命名空间)和“包括所有标记”。 默认值为“无”(none checked)，这意味着允许所有命名空间。

* **[!UICONTROL 建议限]**&#x200B;制输入要作为建议显示给论坛的成员发布的标记数。 默认为 
**-** 1（无限制）。

### 翻译选项卡 {#translation-tab}

在“翻 **[!UICONTROL 译]** ”选项卡下，如果为社区站点启用了翻译，则可以设置翻译来翻译整个主题或选定的帖子。

* **[!UICONTROL 全部翻译]**&#x200B;如果选中，论坛帖子将翻译为用户的首选语言。 默认为未选中。

### “排序设置”选项卡 {#sort-settings-tab}

在“排 **[!UICONTROL 序设置]** ”选项卡下，指定显示已发布注释时的排序方式。

* **[!UICONTROL 排序依据]**&#x200B;检查所有允许的排序选择： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Default is `Newest, Oldest, Last Updated`.

* **[!UICONTROL 设置为默]**&#x200B;认下拉选项，选择一个选中的排序选项作为默认选项显示。 默认为 
`Newest`。

* **[!UICONTROL 选择分析排序的时间]**&#x200B;选项下拉以选择其中一个 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Default is `All`.

## 附加信息 {#additional-information}

有关详细信息，请参阅“论 [坛基础工具](essentials-forum.md) ”页面。

有关审核已发布的主题和评论，请参 [阅审核用户生成的内容](moderate-ugc.md)。

有关标记已发布的主题和评论，请参 [阅标记用户生成的内容](tag-ugc.md)。

有关已发布主题和注释的翻译，请参阅 [翻译用户生成的内容](translate-ugc.md)。
