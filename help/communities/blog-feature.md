---
title: 博客功能
seo-title: 博客功能
description: 以日志格式提供社区信息
seo-description: 以日志格式提供社区信息
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c

---


# 博客功能 {#blog-feature}

## 简介 {#introduction}

AEM Communities的博客功能已从创作活动转变为发布环境中发生的真正社区活动。

博客功能支持以日志格式提供社区信息。 博客条目由授权成员（注册、登录用户）在发布环境中创建。

博客功能提供：

* 在发布端创建博客文章和评论
* 富文本编辑
* 内联图像（支持拖放）
* 嵌入式社交网络内容([嵌入支持](blog-developer-basics.md#allowing-rich-media))
* 草稿模式
* 计划发布
* 代表起草(特权会 [员可以](users.md#privileged-members-group) 代表其他社区成员创建内容)
* [博客文章和评论的上下文内](moderate-ugc.md) 容和批量审核

文档的此部分描述了

* 将博客功能添加到AEM站点
* 博客组件的配置设置

>[!NOTE]
>
>组件和 `Journal`组件 `Journal Sidebar` 的标题 `Blog` 为和 `Blog Sidebar`。
>
>AEM 6.0及早期版本中的博客功能现已删除。 它基于模板，并且仅允许作者在创作环境中创建内容。

## 将博客组件添加到页面 {#adding-blog-components-to-a-page}

如果希望在创作模式下将博客添加到页面，请使用组件浏览器查找

* `Communities / Blog`
* `Communities / Blog Sidebar`

然后将它们拖动到应显示博客的页面上的位置。

有关必要的信息，请访 [问社区组件基础](basics.md)。

包括所 [需的客户端库](blog-developer-basics.md#essentials-for-client-side) ，组件的显示 `Blog`方式如下：

![chlimage_1-147](assets/chlimage_1-147.png)

以及显示 `Blog Sidebar` 方式：

![chlimage_1-148](assets/chlimage_1-148.png)

### 配置博客 {#configuring-blog}

选择要访问 `Blog` 的已放置组件，然后选择打 `Configure` 开编辑对话框的图标。

![配置图标](assets/chlimage_1-149.png)![博客设置](assets/Blog-configure.png)

#### 设置选项卡 {#settings-tab}

在“设 **[!UICONTROL 置]** ”选项卡下，指定博客的基本功能：

* **[!UICONTROL 允许附件缩]**&#x200B;览图如果选中此选项，则会创建附加图像的缩览图。

* **[!UICONTROL 最大附加缩略图]**&#x200B;大小附加缩略图图像的最大大小（以像素为单位）。 默认值是800 x 800。

* **[!UICONTROL 缩览图的最小图像大小]**&#x200B;用于为内联图像生成缩览图的图像的最小大小（以字节为单位）。 默认值为100000字节(100kb)。

* **[!UICONTROL 最大缩略图大]**&#x200B;小内联图像的缩略图最大大小（以像素为单位）。 默认值是800 x 800。

* **[!UICONTROL 允许特权成]**&#x200B;员如果选中此项，则仅允许特权成员创建内容。

* **[!UICONTROL 允许的特权成]**&#x200B;员添加允许创建内容的特权成员。

* **[!UICONTROL 在作者编辑模式下阻止用户生成的内容]**&#x200B;如果启用此功能，则在作者模式下编辑时会阻止用户生成的内容。

* **[!UICONTROL 日志标]**&#x200B;题要在页面上显示的博客标题。
   >注意:
   >日志标题用于自动创建博客的URL。 在此处指定的日志标题中，最多使用50个字符（另外5个字符）为博客创建URL。

* **[!UICONTROL 日志描述]**&#x200B;博客描述。

* **[!UICONTROL 每页主题数]**

   定义每页显示的博客条目／评论数。 默认值为10。

* **[!UICONTROL 已审核]**

   如果选中此项，则发布博客条目和评论必须经过批准，才能显示在发布站点上。 默认为未选中。

* **[!UICONTROL 关闭]**

   如果选中此项，则博客将关闭到新的博客条目和评论。 默认为未选中。

* **[!UICONTROL 富文本编辑器]**

   如果选中此项，则可以输入带有标记的博客条目和评论。 选中默认值。

* **[!UICONTROL 允许标记]**

   如果选中此项，则允许成员向其帖子中添加标记标签(请参阅 **[!UICONTROL 标记字段]** 选项卡)。 默认为未选中。

* **[!UICONTROL 允许文件上传]**

   如果选中此项，则允许将文件附件添加到博客条目或评论。 默认为未选中。

* **[!UICONTROL 最大文件大小]**

   仅在选中时 `Allow File Uploads` 相关。 此字段将限制已上载文件的大小（以字节为单位）。 默认为104857600(10 Mb)。

* **[!UICONTROL 允许的文件类型]**

   仅在选中时 `Allow File Uploads` 相关。 以逗号分隔的文件扩展名列表，带有“点”分隔符。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何文件类型，则不允许上传那些未指定的文件类型。 默认值未指定，因此允许所有文件类型。

* **[!UICONTROL 附加图像文件最大大小]**

   仅在选中“允许文件上传”时相关。 上传的图像文件可能具有的最大字节数。 默认为2097152(2 Mb)。

* **[!UICONTROL 允许回复]**

   如果选中此项，则允许回复发布到博客条目的评论。 默认为未选中。

* **[!UICONTROL 允许用户删除评论和主题]**

   如果选中此项，则允许成员删除他们发布的评论和博客条目。 默认为未选中。

* **[!UICONTROL 允许关注]**

   如果选中此项，请为博客文章加入以下功能，这允许成员收到 [新](notifications.md) 帖子的通知。 默认为未选中。

* **[!UICONTROL 允许电子邮件订阅]**

   如果选中此项，则允许会员通过电子邮件（订阅）通知[新帖子](subscriptions.md)。 需要 `Allow Following` 选中并配置电 [子邮件](email.md)。 默认为未选中。

* **[!UICONTROL 允许投票]**

   如果选中此项，请在博客条目中包含投票功能。 默认为未选中。

* **[!UICONTROL 显示徽章]**

   如果选中此项，则使用成员的 [博客条目](implementing-scoring.md) ，显示已获得和已分配的徽章。 默认为未选中。

* **[!UICONTROL 允许专题内容]**

   如果选中此项，该构思将被识别为特色 [内容](featured.md)。 默认为未选中。

#### “用户审核”选项卡 {#user-moderation-tab}

在“用户 **[!UICONTROL 审核]** ”选项卡下，指定审核设置：

* **[!UICONTROL 拒绝帖子]**

   如果选中此项，则允许受信任的成员审核者拒绝帖子并阻止帖子显示在公共论坛中。 默认为未选中。

* **[!UICONTROL 关闭／重新打开主题]**

   如果选中此项，则受信任的成员审核者可以关闭主题以进一步编辑和评论，也可以重新打开主题。 默认为未选中。

* **[!UICONTROL 旗标帖子]**

   如果选中此项，则允许成员将他人的主题或评论标记为不合适。 默认为未选中。

* **[!UICONTROL 标记原因列表]**

   如果选中此项，允许成员从下拉列表中选择其标记主题或评论为不适当的理由。 默认为未选中。

* **[!UICONTROL 自定义标志原因]**

   如果选中此项，则允许成员输入自己将主题或评论标记为不合适的原因。 默认为未选中。

* **[!UICONTROL 协调阈值]**

   输入在通知版主之前必须由成员标记主题或评论的次数。 默认值为1（一次）。

* **[!UICONTROL 标记限制]**

   输入主题或评论在公共视图中隐藏之前必须标记的次数。 如果设置为-1，则标记的主题或评论从不在公共视图中隐藏。 否则，此数字必须大于或等于审核阈值。 默认为5。

#### 标记字段选项卡 {#tag-field-tab}

在“标记 **[!UICONTROL 字段]** ”选项卡下，指定在“设置”选项卡上选中“允许标记 **[!UICONTROL ”时可应用的]** 标记 **** :

* **[!UICONTROL 允许的命名空间]**

   如果选中 `Allow Tagging` 了“设置”选项卡下 **[!UICONTROL 的选项]** ，则相关。 可应用的标记仅限于选定的命名空间类别中的标记。 命名空间列表包括“标准标记”（默认命名空间）和“包括所有标记”。 默认值为“无”选中，这意味着允许所有命名空间。

* **[!UICONTROL 建议限制]**

   输入要作为建议显示给发布到论坛的成员的标记数。 值-1表示没有限制。 默认值为0。

### 配置博客提要栏 {#configuring-blog-sidebar}

双击组件时，会 `Blog Sidebar` 打开一个编辑对话框。

在“日 **[!UICONTROL 记帐提要栏设置]** ”选项卡下，指定存档的日期格式以及要在提要栏中显示的条目类型：

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL 日期格式]**

   用于显示博客条目存档的格式。 该格式使用遵循Java约定的占位符。

   * yyyy:全年，如2015年
   * yy:短年份，比如15年
   * MMMMMM:整月，比如6月
   * 嗯：短月份，就象6月份
   * MM:月号，如06
   默认值为“yyyy MMMMM”，例如显示“2015年6月”

* **[!UICONTROL 视图类型]**

   要在提要栏中显示的博客条目的标题和类型。 选择是

   * 作者
   * 类别
   * 归档

* **[!UICONTROL 日志组件路径]**

   *（可选）* ，要从中列出博客文章的博客资源的位置。 如果留空，将使用同一页面上 `social/journal/components/hbs/journal` 显示的resourceType组件。

   * 例如，`/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL 建议限制]**

   要显示的博客文章数。 值-1表示无限制。 默认值为-1。

## 网站访客体验 {#site-visitor-experience}

在发布环境中，博客功能将按创建的降序显示最新的博客文章，后跟较旧的博客文章。 博客侧栏允许站点访问者应用过滤器以限制所显示的博客文章的选择。

博客文章后跟一个用于发布或查看评论的链接。

选择博客文章后，将显示博客文章和评论（如果启用）。

其他功能取决于站点访客是审查方、管理员、社区成员、特权成员还是匿名。

### 使用文章 {#working-with-articles}

创建新博客文章时，可以选择

1. 立即发布
1. 发布草稿
1. 在预定日期和时间发布

博客文章将显示在相应的选项卡（已发布、草稿或已计划）下，显示给能够在发布时创作的成员。

#### 版主和管理员 {#moderators-and-administrators}

当登录用户具有审查方或管理员权限时，他们可以对发布到博客的所有博客文章和评论执行 [仲裁任务](moderate-ugc.md) （组件的配置允许）。

![chlimage_1-152](assets/chlimage_1-152.png)

### 成员 {#members}

当登录用户是社区成员或特权 [成员](users.md#privileged-members-group) （具体取决于配置）时，他们可以选择创建 `New Article` 并发布新的博客文章。

具体而言，他们可以：

* 创建新博客文章
* 代表其他成员发布新的博客文章
* 将评论发布到博客文章
* 编辑他们自己的博客文章或评论
* 删除自己的博客文章或评论
* 标记他人的博客文章或评论

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### 匿名 {#anonymous}

未登录的站点访问者只能阅读张贴的博客文章和评论，如果支持，可翻译这些文章和评论，但不得添加博客文章或评论，也不得标记他人的文章或评论。

![chlimage_1-155](assets/chlimage_1-155.png)

## 附加信息 {#additional-information}

有关详细信息，请参阅面向开发 [人员的Blog](blog-developer-basics.md) Essentials页面。

有关审核博客条目和评论，请参阅审核 [用户生成的内容](moderate-ugc.md)。

有关标记博客条目和注释，请参阅标记 [用户生成的内容](tag-ugc.md)。

有关博客条目和注释的翻译，请参阅翻译 [用户生成的内容](translate-ugc.md)。
