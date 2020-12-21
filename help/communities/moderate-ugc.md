---
title: 协调社区内容
seo-title: 协调社区内容
description: 协调概念和操作
seo-description: 协调概念和操作
uuid: a24d09e7-3260-4eec-844e-97e6849c94d8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d11b8fc8-5e98-4a77-a536-d445ac88e1b3
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 1%

---


# 协调社区内容{#moderating-community-content}

## 概述 {#overview}

当成员(在站点访客中签名)通过与以下社区组件之一的交互从已发布的社区站点发布内容时，会创建社区内容，也称为用户生成内容(UGC):

* [博客](blog-feature.md):成员发布博客文章或评论
* [日历](calendar.md):成员发布日历事件或评论
* [评论](comments.md):成员发布评论或回复评论
* [论坛](forum.md):成员发布新主题或回复主题
* [构思](ideation-feature.md):成员发布想法或评论
* [问题解答](working-with-qna.md):成员可创建问题或回答问题
* [评论](reviews.md):成员在对项目进行评级时发布评论

UGC的适度有助于识别积极贡献以及限制消极贡献（如垃圾邮件和谩骂性语言）。 UGC可以从多个环境中审核：

* [批量审核控制台](moderation.md)

   管理员和[社区管理者](users.md)可以在公共环境下以及作者环境下通过管理员访问协调控制台。 当社区内容存储在[公用商店](working-with-srp.md)中时，这是可能的。

* [上下文协调](in-context.md)

   发布环境中的审核可由管理员和社区审核者直接在发布内容的页面上执行。

## 协调操作{#moderation-actions}

可以对已发布内容(UGC)执行的操作会因用户身份和环境而异。 下表使用以下术语根据用户身份描述各种角色：

* `Admin`\
   属于[community-administrators](users.md)组的用户
* `Moderator`
社区审核者 [组](users.md#publishenvironmentusersandgroups) 的成员(具 [有审核者](in-context.md#moderatorpermissions))
* `Creator`\
   发布内容的用户
* `Member`\
   没有特殊权限的登录用户
* `Visitor`
匿名用户

<table> 
 <tbody>
  <tr>
   <td> </td> 
   <td><strong>管理员</strong></td> 
   <td><strong>审查方</strong></td> 
   <td><strong>创建者</strong></td> 
   <td><strong>成员</strong></td> 
   <td><strong>访客</strong></td> 
   <td><strong>事件<br />已触发</strong></td> 
   <td><strong>预审</strong></td> 
  </tr>
  <tr>
   <td><strong>编辑/<br />删除</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>剪切</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>拒绝</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>关闭/<br />重新打开</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X<br /> </td> 
  </tr>
  <tr>
   <td><strong>标记/<br />取消标记</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>允许</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X</td> 
  </tr>
 </tbody>
</table>

### 编辑／删除{#edit-delete}

帖子发布后，创建者、管理员或社区审查方可以编辑或删除该帖子。

删除UGC后，它将从存储库中删除，并且可能无法恢复。

### 剪切 {#cut}

管理员或社区主持人可以将一个或多个论坛主题或问题解答问题从一个位置移到另一个位置。 这包括从一个社区站点到另一个社区站点，前提是同一成员在这两个站点上都具有审核权限。

通过选择“剪切”动作，内容将复制到剪贴板。 可以将多个帖子作为组复制并移动到新位置。

![](assets/cutugc.png) ![cutugcputbackugc](assets/putbackugc.png)

在另一个位置，当剪贴板中存在内容时，“新建帖子”旁会显示“粘贴”按钮，其编号标识将粘贴的帖子数。 “粘贴”按钮包含一个选项，用于清除剪贴板而不是粘贴。

![chlimage_1-218](assets/chlimage_1-218.png) ![chlimage_1-219](assets/chlimage_1-219.png)

### 拒绝 {#deny}

审查方可能不允许UGC在已发布的站点上保持可见。 对于管理员和社区版主，帖子仍可用，并添加垃圾邮件批注。

### 关闭／重新打开{#close-reopen}

“关闭”操作在整个对话线程（论坛主题或初始评论）上运行，并且包括所有后续帖子或回复。

关闭后，不仅无法进行进一步的回复，也不允许执行任何审核操作。

要执行任何操作，主题或评论必须重新打开。

关闭／重新打开操作可由管理员或社区版主执行。

### 标记／取消标记{#flag-unflag}

标记是任何已登录成员（内容创建者除外）的一种方法，用于指示帖子内容存在问题。 标记后，将显示一个取消标记图标，允许同一成员取消标记内容。

可以将上下文内协调配置为允许成员在标记帖子时选择原因。 可以配置可选标志原因的列表，包括是否可以输入自定义原因。 标记原因与UGC一起保存，但该原因不会触发任何特定操作。 只有标记数才会触发通知。 标记内容会按此方式添加注释，以便版主可以对其执行操作。

系统跟踪所有已标记的标志以及标志原因，并在达到阈值时发送事件。 如果社区审查方允许使用UGC，则会存档这些标志。 在允许和存档后，如果有后续的标记，则会将其存档，就像以前没有标记一样。

### 允许 {#allow}

“允许”操作是已标记、已拒绝或未在预审核系统中批准的UGC的选项。 “允许”操作将清除任何已标记或已拒绝／垃圾邮件状态，并存档任何已标记的数据。

## 常见协调概念{#common-moderation-concepts}

### 预协调{#premoderation}

UGC预先审核后，在审核操作批准之前，发布的站点上不会显示该帖子。 在创建[社区站点](sites-console.md)期间，选中框` [Content is Premoderated](sites-console.md#moderation)`将为整个站点启用预审核。 将组件放置到页面上后，可以使用编辑对话框中的设置将支持仲裁的组件配置为进行预仲裁：

* [评](comments.md) 论和评 [论](reviews.md)

   在&#x200B;**[!UICONTROL 用户协调]**&#x200B;选项卡上，选中&#x200B;**[!UICONTROL 预协调]**

* [论坛](forum.md)、 [QnA](ideation-feature.md)和日历设置 [戳](working-with-qna.md)、检查 [](calendar.md)  ****  **[!UICONTROL 已审核]**

### 垃圾邮件检测{#spam-detection}

垃圾邮件检测是一种自动协调功能，通过将提交的用户生成的内容标记为垃圾邮件，来过滤器出不可期待的部分内容。 启用后，它会根据预先配置的垃圾文字集合来识别用户生成的内容是否是垃圾信息。 默认的垃圾邮件字词在

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`。

但是，要自定义或扩展默认的垃圾邮件字词，请通过[overlay](overlay-comments.md)在/apps目录中创建一组默认的垃圾邮件字词结构。

用户生成的包含垃圾邮件的帖子（跨所有内容类型，如博客、论坛和评论）在帖子上方标有“此帖子被分类为垃圾邮件”文本。

审查方可以查看此类帖子并标记相同以允许或拒绝在网站上显示。 可以对这些帖子执行上下文审核操作或通过批量审核UI执行审核操作。

![垃圾邮件检测](assets/spamdetection.png)

要启用垃圾邮件检测引擎，请执行以下步骤：

1. 转到`/system/console/configMgr`打开[Web控制台](http://localhost:4502/system/console/configMgr)。

1. 找到&#x200B;**[!UICONTROL AEM Communities自动协调]**&#x200B;配置并编辑它。
1. 添加`SpamProcess`条目。

![垃圾邮件](assets/spamprocess.png)

>[!NOTE]
>
>垃圾邮件检测只针对英语区域设置实施。

### 情绪 {#sentiment}

情绪根据帖子(UGC)中存在的正反关键字（[口语](#configuringwatchwords)）的数量计算。

情绪分析使用一组预配置规则并计算UGC的情绪。 默认规则位于`/libs/cq/workflow/components/workflow/social/sentiments/rules.`

规则生成的值从1（所有负数，无正数字）到10（所有正数字，无负数字）。 情绪值为5是中性情绪，是默认值。

/libs组件中定义的规则有：

* 规则1:如果没有正字并且至少有一个负字，则将值设置为1
* 规则2:如果没有负词且至少有一个正词，则将值设置为10
* 规则3:如果负词多于正词，则将值设置为3
* 规则4:如果正词多于负词，请将值设置为8

要覆盖或添加规则，请在/apps目录中按照默认规则的结构创建一组规则。 编辑情绪配置以标识规则的位置。

分析后，情绪会与UGC一起存储。

从[批量审核控制台](moderation.md)中，可以根据情绪是否为负、中性还是正性来筛选和视图UGC。

#### 标语{#watchwords}

AEM communities提供*观察词分析器*作为评估[情绪](#sentiment)过程中的步骤。 口号对情绪值的贡献是，在发布的内容中使用的负面和正面的口号以及禁止的词汇进行比较。

#### 配置情绪和标语{#configure-sentiment-and-watchwords}

可以自定义正反两个口号的列表，就像情绪规则一样。

默认的观察字列表可以作为存储库中节点的属性输入，这与默认列表类似，或者通过使用单词配置OSGi服务`sentimentprocess.name`来覆盖默认值。

也可以修改&#x200B;**sentimentprocess.name**&#x200B;以引用自定义情绪规则集的位置。

要配置情绪和标语：

* 在创作实例上
* 以管理员身份登录
* 打开[Web控制台](http://localhost:4502/system/console/configMgr)
* 找到`sentimentprocess.name`
* 选择要在编辑模式下打开的配置

![情感过程](assets/sentimentprocess.png)

* **正**
言词用逗号分隔的词列表，可产生覆盖默认值的正面情绪。默认为空列表。

* **负**
面标语用逗号分隔的词列表，产生覆盖默认值的负面情绪。默认为空列表。

* **观察字节点的显**
式路径包含默认值的节点的存储库位置 
`positive` 和指 `negative` 定默认观察字的属性。默认值为`/libs/settings/community/watchwords/default`。

* **情绪**
规则用于基于正反表词计算情绪的规则的存储库位置。默认为 
`/libs/cq/workflow/components/workflow/social/sentiments/rules` （但是，不再涉及任何工作流）。

以下是将`Explicit Path to Watchwords Node`设置为`/libs/settings/community/watchwords/default`时默认观察词的自定义条目示例。

![crxde](assets/crxde.png)

### 审查方权限{#moderator-permissions}

以下权限在分配给同一资源时统称为&#x200B;**`moderator permissions`**:

* `Read`
* **`Modify`**
* `Create`
* `Delete`
* `Replicate`

