---
title: 社区评分和徽章
seo-title: Communities Scoring and Badges
description: AEM Communities评分和徽章让您能够识别和奖励社区成员
seo-description: AEM Communities scoring and badges lets you identify and reward community members
uuid: ca6f22d6-f25d-4f26-b589-81d1f2c830f9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b19b3c24-82a0-468c-a077-9f3edb96afc9
tagskeywords: scoring, badging, badges, gamification
role: Admin
exl-id: 54a4a053-ca44-451a-9a31-f1c1e8cb7002
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2905'
ht-degree: 2%

---

# 社区评分和徽章 {#communities-scoring-and-badges}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Communities评分和徽章功能提供了识别和奖励社区成员的功能。

评分和徽章的主要方面包括：

* [分配徽章](#assign-and-revoke-badges) 确定成员在社区中的作用

* [基本奖章](#enable-scoring) 以鼓励成员参与（创建的内容数量）
* [高级徽章奖励](advanced.md) 将成员标识为专家（创建的内容质量）

**注意** 授予徽章是 [默认情况下未启用](implementing-scoring.md#main-pars-text-237875536).

>[!CAUTION]
>
>当UI可用时，CRXDE Lite中可见的实施结构可能会发生更改。

## 徽章 {#badges}

徽章以会员的名称放置，以表明其角色或在社区中的地位。 徽章可以显示为图像或名称。 显示为图像时，该名称将作为辅助功能的替换文本包含在内。

默认情况下，徽章位于存储库中的

* /etc/community/badging/images

如果存储在其他位置，则每个人都应该可以读取它们。

在UGC中，对徽章是按照规则分配的还是获得的区别。 目前，已分配的徽章显示为文本，挣得的徽章显示为图像。

### 徽章管理UI {#badge-management-ui}

社区 [徽章控制台](badges.md) 提供添加自定义徽章的功能，该徽章可在会员获得（授予）或在社区中承担特定角色（分配）时为其显示。

### 分配的徽章 {#assigned-badges}

基于角色的徽章由管理员根据社区成员在社区中的角色分配给社区成员。

已分配（和已通知）的徽章存储在选定的 [SRP](srp.md) 和无法直接访问。 在GUI可用之前，分配基于角色的徽章的唯一方法就是使用代码或cURL来分配。 有关cURL说明，请参阅标题为 [分配和撤销徽章](#assign-and-revoke-badges).

该版本包含三个基于角色的徽章：

* 审查方

   `/etc/community/badging/images/moderator/jcr:content/moderator.png`

* 组管理器

   `/etc/community/badging/images/group-manager/jcr:content/group-manager.png`

* 特权成员

   `/etc/community/badging/images/privileged-member/jcr:content/privileged-member.png`

![chlimage_1-366](assets/chlimage_1-366.png)

### 奖章 {#awarded-badges}

评分服务根据适用于社区成员活动的规则，将基于奖励的徽章授予社区成员。

为了让徽章显示为对活动的奖励，必须做两件事：

* 标记必须 [已启用](#enable-badges-for-component) （对于功能组件）
* 评分和标记规则必须 [应用](#apply-rules-to-content) 到组件所在的页面（或上级）

该版本包含三枚奖励徽章：

* 金牌

   `/etc/community/badging/images/gold-badge/jcr:content/gold.png`

* 银牌

   `/etc/community/badging/images/silver-badge/jcr:content/silver.png`

* 铜牌

   `/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

![chlimage_1-367](assets/chlimage_1-367.png)

>[!NOTE]
>
>评分规则可配置为为标记为不适当的帖子分配负分，从而影响得分值。 但是，一旦获得徽章，就不会因得分减少或评分规则更改而自动删除该徽章。
>
>奖章的吊销方式与授予徽章相同。 请参阅 [分配和撤销徽章](#assign-and-revoke-badges) 中。 未来的改进将包括用于管理会员徽章的UI。

### 自定义徽章 {#custom-badges}

可使用 [徽章控制台](badges.md) 和在标记规则中分配或指定。

从徽章控制台安装后，自定义徽章会自动复制到发布环境。

## 启用评分 {#enable-scoring}

默认情况下，未启用评分。 徽章设置、授予评分和授奖的基本步骤是：

* 确定收入点的规则([评分规则](#scoring-rules))
* 对于每个评分规则累积的分数，分配 [徽章](#badges) ([乱码规则](#badging-rules))

* [将评分和标记规则应用到社区站点](#apply-rules-to-content)
* [为社区功能启用标记](#enable-badges-for-component)

请参阅 [快速测试](#quick-test) 部分，以使用论坛和评论的默认评分和标记规则为社区站点启用评分。

### 将规则应用到内容 {#apply-rules-to-content}

要启用评分和徽章，请添加属性 `scoringRules` 和 `badgingRules`到站点内容树中的任何节点。

如果网站已发布，则在应用所有规则并启用组件后，重新发布该网站。

适用于启用徽章的组件的规则是适用于当前节点或其上级的规则。

如果节点类型为 `cq:Page` （推荐），然后使用CRXDE|Lite将属性添加到 `jcr:content`节点。

| **属性** | **类型** | **描述** |
|---|---|---|
| 标记规则 | 字符串[] | 数组列表 [乱码规则](#badging-rules) |
| scoringRules | 字符串[] | 数组列表 [评分规则](#scoring-rules) |

>[!NOTE]
>
>如果评分规则似乎对奖励徽章没有任何影响，请确保评分规则未被徽章规则的scoringRules属性阻止。 请参阅标题为的部分 [标记规则](#badging-rules).

### 为组件启用徽章 {#enable-badges-for-component}

评分和标记规则仅对通过编辑组件配置启用标记的组件实例有效 [创作模式](author-communities.md).

布尔属性， `allowBadges`，则启用/禁用组件实例的徽章显示。 可以在 [组件编辑对话框](author-communities.md) 对于论坛，请选中标有的复选框，以便问题解答和注释组件 **显示徽章**.

#### 示例：论坛组件实例的allowBadges {#example-allowbadges-for-forum-component-instance}

![chlimage_1-368](assets/chlimage_1-368.png)

>[!NOTE]
>
>任何组件都可以覆盖以显示徽章，例如，使用在论坛、QnA和评论中找到的HBS代码。

## 评分规则 {#scoring-rules}

评分规则是评分的基础，用于授予徽章。

很简单，每个评分规则都是一个或多个子规则的列表。 评分规则将应用于社区站点内容，以识别在启用徽章时要应用的规则。

评分规则是继承的，但不是加性的。 例如：

* 如果页面2包含评分规则2，且其上级页面1包含评分规则1
* 对page2组件执行的操作将同时调用rule1和rule2
* 如果两个规则都包含相同的适用子规则 `topic/verb`:

   * 只有规则2中的子规则会影响分数
   * 两个子规则的得分不会一起添加

当有多个评分规则时，将分别为每个规则维护分数。

评分规则是类型的节点 `cq:Page` 的 `jcr:content`用于指定子规则列表的节点。

分数存储在SRP中。

>[!NOTE]
>
>最佳实践：唯一命名每个评分规则。
>
>评分规则名称应全局唯一；它们不应以相同的名称结尾。
>
>示例 *not* 要执行以下操作：\
>/etc/community/scoring/rules/site1/forums-scoring\
>/etc/community/scoring/rules/site2/forums-scoring

### 评分子规则 {#scoring-sub-rules}

评分子规则包含详细描述参与社区值的属性。

每个评分子规则标识

* 跟踪哪些活动
* 具体涉及哪些社区功能
* 分给多少分

默认情况下，会将积分授予执行操作的成员，除非子规则指定内容的所有者作为接收点( `forOwner`)。

每个子规则可以包含在一个或多个评分规则中。

子规则的名称通常遵循使用 *主题，对象* 和 *动词*. 例如：

* member-comment-create
* 成员接收表决

子规则是类型的节点 `cq:Page` 的 `jcr:content`指定节点 [动词和主题](#topics-and-verbs) .

<table> 
 <tbody> 
  <tr> 
   <th>属性</th> 
   <th>类型</th> 
   <th> 价值 描述</th> 
  </tr> 
  <tr> 
   <td><i><code>VERB</code></i></td> 
   <td>长整型</td> 
   <td> 
    <ul> 
     <li>必需；动词对应于事件操作</li> 
     <li>必须至少有一个动词属性</li> 
     <li>必须输入所有大写字母</li> 
     <li>可以有多个动词属性，但无重复项</li> 
     <li>值是要应用于此事件的分数</li> 
     <li>值可以是正数或负数</li> 
     <li>此版本中支持的动词列表位于 <a href="#topics-and-verbs">主题和动词</a> 部分</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>topics</code></td> 
   <td>字符串[]</td> 
   <td> 
    <ul> 
     <li>可选；将子规则限制为由事件主题标识的社区组件</li> 
     <li>如果指定，则：值是事件主题的多值字符串</li> 
     <li>此版本中的主题列表位于 <a href="#topics-and-verbs">主题和动词</a> 部分</li> 
     <li>默认为应用于与动词关联的所有主题</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>forOwner</code></td> 
   <td>布尔值</td> 
   <td> 
    <ul> 
     <li>可选；当成员根据自己拥有的内容执行操作时，与此无关</li> 
     <li>如果为true，则对所执行内容的所有者应用分数</li> 
     <li>如果为false，则将分数应用于执行操作的成员</li> 
     <li>默认为false</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>scoringType</code></td> 
   <td>字符串</td> 
   <td> 
    <ul> 
     <li>可选；识别评分引擎</li> 
     <li>如果为“基本”，则根据数量指定评分引擎 
      <ul> 
       <li>包含在版本中</li> 
      </ul> </li> 
     <li>如果为“高级”，则根据质量和数量指定评分引擎 
      <ul> 
       <li>需要 <a href="advanced.md">附加包</a></li> 
      </ul> </li> 
     <li>默认为“基本”</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

### 包含评分规则和子规则 {#included-scoring-rules-and-sub-rules}

该版本包含两个针对 [论坛功能](functions.md#forum-function) （论坛功能的“论坛”和“评论”组件各一个）：

1. /etc/community/scoring/rules/comments-scoring

   * subRules[] =

      /etc/community/scoring/rules/subrules/member-comment-create

      /etc/community/scoring/rules/subrules/member-receive-vote

      /etc/community/scoring/rules/subrules/member-give-vote

      /etc/community/scoring/rules/subrules/member-is-modared

1. /etc/community/scoring/rules/forums-scoring

   * subRules[] =

      /etc/community/scoring/rules/subrules/member-forum-create

      /etc/community/scoring/rules/subrules/member-receive-vote

      /etc/community/scoring/rules/subrules/member-give-vote

      /etc/community/scoring/rules/subrules/member-is-modared

**注释:**

* 两者兼有 `rules`和 `sub-rules` 节点类型为cq:Page

* `subRules`是字符串类型的属性[] 规则 `jcr:content` 节点

* `sub-rules` 可在各种评分规则之间共享
* `rules`应位于具有每个用户读取权限的存储库位置

   * 规则名称必须唯一，而不考虑位置

### 激活自定义评分规则 {#activating-custom-scoring-rules}

在创作环境中对评分规则或子规则所做的任何更改或添加操作需要在发布时安装。

## 标记规则 {#badging-rules}

标记规则通过指定以下内容将评分规则链接到徽章：

* 哪个评分规则
* 需要识别特定徽章的分数

标记规则是类型的节点 `cq:Page` 的 `jcr:content`将评分规则与得分和徽章关联的节点。

标记规则由强制性规则组成 `thresholds`属性，即映射到徽章的分数的有序列表。 必须按递增值排序分数。 例如：

* `1|/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * 一枚铜牌的成绩是1分

* `60|/etc/community/badging/images/silver-badge/jcr:content/silver.png`

   * 当积分达60分时，将颁发银牌

* `80|/etc/community/badging/images/gold-badge/jcr:content/gold.png`

   * 当积分达80分时，将发出金徽章

标记规则与评分规则相配对，评分规则可确定积分的累积方式。 请参阅标题为的部分 [将规则应用到内容](#apply-rules-to-content).

的 `scoringRules`标记规则上的属性只会限制哪些评分规则可以与该特定标记规则相配对。

>[!NOTE]
>
>最佳实践：创建每个AEM网站特有的标记图像。

![chlimage_1-369](assets/chlimage_1-369.png)

<table> 
 <tbody> 
  <tr> 
   <th>属性</th> 
   <th>类型</th> 
   <th>价值 描述</th> 
  </tr> 
  <tr> 
   <td>阈值</td> 
   <td>字符串[]</td> 
   <td><em>（必需）</em> 表单“number|path”的多值字符串 
    <ul> 
     <li>数值=分数</li> 
     <li>| =垂直线字符(U+007C)</li> 
     <li>path =标记图像资源的完整路径</li> 
    </ul> 必须对字符串进行排序，以便数字在值中增加，并且数字和路径之间不应出现空白空格。<br /> 示例条目：<br /> <code>80|/etc/community/badging/images/gold-badge/jcr:content/gold.png</code></td> 
  </tr> 
  <tr> 
   <td>badgingType</td> 
   <td>字符串</td> 
   <td><em>（可选）</em> 将评分引擎标识为“基本”或“高级”。 如果需要高级评分引擎，请参阅 <a href="advanced.md">高级评分和徽章</a>. 默认值为“基本”。</td> 
  </tr> 
  <tr> 
   <td> 
    <code>scoringRules </code></td> 
   <td>字符串[]</td> 
   <td>(<em>可选</em>)多值字符串，用于将标记规则限制为由评分规则标识的事件评分</td> 
  </tr> 
 </tbody> 
</table>

### 包含标记规则 {#included-badging-rules}

该版本中包含两个与 [论坛和评论评分规则](#includedscoringrules).

* /etc/community/badging/rules/comments-badging
* /etc/community/badging/rules/forums-badding

**注释:**

* `rules` 节点类型为cq:Page
* `rules`应位于具有每个用户读取权限的存储库位置

   * 规则名称必须唯一，而不考虑位置

### 激活自定义标记规则 {#activating-custom-badging-rules}

对创作环境中的标记规则或图像所做的任何更改或添加操作需要在发布时安装。

## 分配和撤销徽章 {#assign-and-revoke-badges}

可使用 [成员控制台](members.md#badges-tab) 或使用cURL命令以编程方式执行。

以下cURL命令显示HTTP请求分配和撤销徽章所需的内容。 基本格式为：

cURL -i -XPOST-H *标题* -u *签名* -F *操作* -F *标记* *member-profile-url*

*标题* = &quot;Accept:application/json&quot;\
要传递到服务器的自定义标头（必需）

*signin* = administrator-id:password\
例如：管理员：管理员

*操作* = &quot;:operation=social:assignBadge&quot; OR &quot;:operation=social:deleteBadge&quot;

*徽章* = &quot;badgeContentPath=*标记 — 图像 — 文件*&quot;

*标记 — 图像 — 文件* =徽章图像文件在存储库中的位置\
例如：/etc/community/badging/images/drocidator/jcr/content/moderator.png

*member-profile-url* =发布时成员配置文件的端点\
例如：https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>的 *member-profile-url*
>
>* 如果 [隧道服务](users.md#tunnel-service) 已启用
>* 可能是个模糊的随机名称 — 请看 [安全检查列表](../../help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) 关于可授权ID
>


### 示例： {#examples}

#### 分配审核者徽章 {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### 撤消分配的银徽章 {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/etc/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>使用cURL分配和撤销徽章适用于任何徽章图像，但在分配徽章（而非免费徽章）后，它们将被标记为已分配的徽章，并会相应地进行处理。

## 自定义组件的评分和徽章 {#scoring-and-badges-for-custom-components}

可通过将为自定义组件创建的事件主题与动词关联，为该组件创建评分和标记规则。

## 主题和动词 {#topics-and-verbs}

成员与社区功能交互时，会发送可触发异步侦听器（如通知和评分）的事件。

组件的SocialEvent实例将事件记录为 `actions`对于 `topic`. SocialEvent包括返回 `verb`与操作关联。 有 *n-1* 关系 `actions`和 `verbs`.

对于交付的社区组件，下表描述了 `verbs`为每个 `topic`可用于 [评分子规则](#scoring-sub-rules).

>[!NOTE]
>
>新的布尔属性， `allowBadges`，则启用/禁用组件实例的徽章显示。 可在更新后对其进行配置 [组件编辑对话框](author-communities.md) 通过标记为 **显示徽章**.

**[日历组件](calendar.md)**
SocialEvent `topic`= com/adobe/cq/social/calendar

| **动词** | **描述** |
|---|---|
| POST | 成员创建日历事件 |
| 添加 | 日历事件中的成员评论 |
| 更新 | 编辑成员的日历事件或评论 |
| 删除 | 会删除成员的日历事件或评论 |

**[注释组件](comments.md)**
SocialEvent `topic`= com/adobe/cq/social/comment

| **动词** | **描述** |
|---|---|
| POST | 成员创建评论 |
| 添加 | 成员对评论的回复 |
| 更新 | 会编辑会员评论 |
| 删除 | 会员评论已删除 |

**[文件库组件](file-library.md)**
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **动词** | **描述** |
|---|---|
| POST | 成员创建文件夹 |
| 附加 | 成员上传文件 |
| 更新 | 成员更新文件夹或文件 |
| 删除 | 成员删除文件夹或文件 |

**[论坛组件](forum.md)**
SocialEvent `topic`= com/adobe/cq/social/forum

| **动词** | **描述** |
|---|---|
| POST | 成员创建论坛主题 |
| 添加 | 成员对论坛主题的回复 |
| 更新 | 编辑会员的论坛主题或回复 |
| 删除 | 会员的论坛主题或回复被删除 |

**[日记帐组件](blog-feature.md)**
SocialEvent `topic`= com/adobe/cq/social/journal

| **动词** | **描述** |
|---|---|
| POST | 成员创建博客文章 |
| 添加 | 对博客文章的成员评论 |
| 更新 | 编辑会员的博客文章或评论 |
| 删除 | 会员的博客文章或评论会被删除 |

**[问题解答组件](working-with-qna.md)**
SocialEvent `topic` = com/adobe/cq/social/qna

| **动词** | **描述** |
|---|---|
| POST | 成员创建问题解答问题 |
| 添加 | 成员创建问题解答答案 |
| 更新 | 会员的问题解答问题或答案会进行编辑 |
| 选择 | 已选择会员的回答 |
| 取消选择 | 已取消选择会员的答案 |
| 删除 | 成员的问题解答问题或答案将被删除 |

**[审阅组件](reviews.md)**
SocialEvent `topic`= com/adobe/cq/social/review

| **动词** | **描述** |
|---|---|
| POST | 成员创建审阅 |
| 更新 | 编辑会员的审阅 |
| 删除 | 会员的审阅已删除 |

**[评级组件](rating.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/rating

| **动词** | **描述** |
|---|---|
| 添加评级 | 会员的内容已被评级 |
| 删除评级 | 会员的内容已被降级 |

**[投票组件](voting.md)**
SocialEvent `topic`= com/adobe/cq/social/tally/voting

| **动词** | **描述** |
|---|---|
| 添加投票 | 会员的内容已投票通过 |
| 删除投票 | 会员的内容已被否决 |

**启用审核的组件**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **动词** | **描述** |
|---|---|
| 拒绝 | 会员内容被拒绝 |
| 不当标志 | 会标记成员的内容 |
| 不标记为不适当 | 会员的内容未标记 |
| 接受 | 会员的内容由审核者批准 |
| 关闭 | 成员关闭对编辑和回复的评论 |
| 打开 | 成员重新打开注释 |

### 自定义组件事件 {#custom-component-events}

对于自定义组件，将实例化SocialEvent，以将组件的事件记录为 `actions`对于 `topic`.

为支持评分，SocialEvent需要覆盖方法 `getVerb()` 以便 `verb`为 `action`. 的 `verb` 为操作返回的值可以是常用值(例如 `POST`)或专用于组件(例如 `ADD RATING`)。 有 *n-1* 关系 `actions`和 `verbs`.

## 疑难解答 {#troubleshooting}

### 徽章未出现 {#badges-are-not-appearing}

如果已对网站内容应用了评分和徽章规则，但未为任何活动提醒徽章，请确保已为该组件实例启用徽章。

请参阅 [为组件启用徽章](#enable-badges-for-component).

### 评分规则无效 {#scoring-rule-has-no-effect}

如果对网站内容应用了评分和徽章规则，并且针对某些操作（而非其他操作）授予徽章，则检查徽章规则是否未限制其适用的评分规则。

请参阅 `scoringRules`财产 [标记规则](#badging-rules).

### 区分大小写的类型 {#case-sensitive-typo}

大多数属性和值（尤其是动词）都区分大小写。 在评分子规则中使用动词时，该动词必须全部为大写。

如果功能未按预期工作，请确保已正确输入数据。

## 快速测试 {#quick-test}

可以使用 [入门教程](getting-started.md) （参与）网站：

* 创作访问CRXDE Lite
* 浏览到基页：

   * /content/sites/engage/en/jcr:content

* 添加badgingRules属性：

   * **名称**: `badgingRules`
   * **类型**: `String`
   * 选择 **[!UICONTROL 多]**
   * 选择 **[!UICONTROL 添加]**
   * 输入 `/etc/community/badging/rules/forums-badging`
   * 选择 `+`
   * 输入 `/etc/community/badging/rules/comments-badging`
   * 选择 **[!UICONTROL 确定]**

* 添加scoringRules属性：

   * **名称**: `scoringRules`
   * **类型**: `String`
   * 选择 **[!UICONTROL 多]**
   * 选择 **[!UICONTROL 添加]**
   * 输入 `/etc/community/scoring/rules/forums-scoring`
   * 选择 `+`
   * 输入 `/etc/community/scoring/rules/comments-scoring`
   * 选择 **[!UICONTROL 确定]**

* 选择 **[!UICONTROL 全部保存]**

![chlimage_1-370](assets/chlimage_1-370.png)

接下来，确保论坛和评论组件允许显示徽章：

* 再次使用CRXDE Lite
* 浏览到论坛组件

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* 如有必要，添加allowBadges布尔属性，并确保其为true

   * **名称**: `allowBadges`
   * **类型**: `Boolean`
   * **值**: `true`

![chlimage_1-371](assets/chlimage_1-371.png)

下一个， [重新发布](sites-console.md#publishing-the-site) 社区站点。

最后，

* 浏览到发布实例上的组件
* 以社区成员身份登录(例如：weston.mccall@dodgit.com / password)
* 发布新论坛主题
* 必须刷新页面才能显示标记

   * 注销并作为其他社区成员登录(例如：aaron.mcdonald@mailinator.com / password)

* 选择论坛

这应会为社区成员赢得一枚铜牌，并在其论坛帖子中显示该徽章，因为第一个论坛 — 徽章规则的第一个阈值是1分。

![铜徽](assets/bronzebadge.png)

## 附加信息 {#additional-information}

有关 [评分和徽章要点](configure-scoring.md) 页面。

有关高级评分引擎的信息，请参阅 [高级评分和徽章](advanced.md).

可配置的排行榜 [组件](enabling-leaderboard.md) 和 [函数](functions.md#leaderboard-function) 简化了成员在社区网站上的显示及其得分情况。
