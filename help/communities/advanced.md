---
title: 高级评分和徽章
seo-title: Advanced Scoring and Badges
description: 设置高级评分
seo-description: Setting up advanced scoring
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
role: Admin
exl-id: c9406aae-288e-4cdf-ac01-cb26b423639e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 1%

---

# 高级评分和徽章 {#advanced-scoring-and-badges}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

高级评分允许授予徽章，以将会员识别为专家。 高级评分根据数量分配点数 *和* 由成员创建的内容质量，而基本评分则仅根据创建的内容数量来分配点数。

此差异是由于用于计算得分的评分引擎所致。 基本评分引擎应用简单的数学。 高级评分引擎是一种自适应算法，用于奖励通过主题的自然语言处理(NLP)推导的、贡献了有价值和相关内容的活动成员。

除了内容相关性之外，评分算法还考虑成员活动，如投票和回答百分比。 虽然基本评分可以定量计算，但高级评分会通过算法来使用这些参数。

因此，高级评分引擎需要足够的数据来使分析有意义。 随着算法不断根据所创建内容的数量和质量进行调整，将不断重新评估成为专家的成就阈值。 此外， *衰减* 成员的较旧职位。 如果一名专家成员停止参与他们获得专家地位的主题事项，则在某个预先确定的时间点(见 [评分引擎配置](#configurable-scoring-engine))，他们可能会失去专家的地位。

设置高级评分与基本评分几乎相同：

* 基本和高级评分及标记规则包括 [应用于内容](implementing-scoring.md#apply-rules-to-content) 同样的方式
   * 基本和高级评分以及标记规则可应用于相同内容
* [为组件启用徽章](implementing-scoring.md#enable-badges-for-component) 泛型

在设置评分和标记规则方面的区别是：

* 可配置的高级评分引擎
* 高级评分规则：
   * `scoringType` 设置为 **[!UICONTROL 高级]**
   * 需要秒

* 高级标记规则：
   * `badgingType` 设置为 **[!UICONTROL 高级]**
   * `badgingLevels` 确定要授予的专家级数
   * 需要 `badgingPaths` 标记阵列，而不是阈值阵列映射到标记

>[!NOTE]
>
>要使用高级评分和标记功能，请安装 [专家识别包](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## 可配置评分引擎 {#configurable-scoring-engine}

高级评分引擎提供OSGi配置，其中包含影响高级评分算法的参数。

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 评分权重]**
对于主题，指定在计算得分时应给予最高优先级的动词。 可以输入一个或多个主题，但限于 **每个主题一个动词**. 请参阅 [主题和动词](implementing-scoring.md#topics-and-verbs).

   输入方式 `topic,verb` 逗号转义。 例如：

   `/social/forum/hbs/social/forum\,ADD`

   对于QnA和论坛组件，默认设置为ADD谓词。


* **[!UICONTROL 评分范围]**

   高级得分的范围由此值（最大可能得分）和0（最小可能得分）定义。

   默认值为100，因此评分范围为0-100。


* **[!UICONTROL 实体衰减时间间隔]**

   此参数表示所有实体得分被延迟的小时数。 在社区站点的得分中不再包含旧内容时，需要此参数。

   默认值为216000小时（~24年）。


* **[!UICONTROL 评分增长率]**

   这会指定分数。 介于0和评分范围之间，超出此范围后，增长会放缓以限制专家数量。

   默认值为 50。

## 高级评分规则 {#advanced-scoring-rules}

在基本评分中，获得徽章所需的数量已知。

在高级评分中，需要的数量会根据系统内的质量数据量不断调整。 评分会以类似于钟形曲线的方式持续计算。

如果成员在不再活动的主题上获得了专家徽章，则他们可能会因为随着时间的推移而衰减而丢失自己的徽章。

### 评分类型 {#scoringtype}

评分规则是一组评分子规则，每个子规则都声明 `scoringType`.

要调用高级评分引擎，请 `scoringType`应设置为 `advanced`.

请参阅 [评分子规则](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### 秒词 {#stopwords}

高级评分包会安装一个包含秒词文件的配置文件夹：

* `/etc/community/scoring/configuration/stopwords`

高级评分算法使用秒词文件中包含的词语列表来识别在内容处理期间被忽略的常见英语词语。

不希望修改此文件。

如果秒词文件缺失，则高级评分引擎将引发错误。

## 高级标记规则 {#advanced-badging-rules}

高级标记规则属性与 [基本标记规则属性](implementing-scoring.md#badging-rules).

无需将点与徽章图像关联，只需确定允许的专家数量和要授予的徽章图像即可。

![chlimage_1-262](assets/chlimage_1-262.png)

| **属性** | **类型** | **值描述** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | 字符串[] | （必需）标记图像的多值字符串，其数量最高为badgingLevels数量。 必须对徽章图像路径进行排序，以便将第一个路径授予最高专家。 如果徽章数少于badgingLevels所指示的徽章数，则数组中的最后一个徽章将填充数组的其余部分。 示例条目：/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| 标记级别 | 长整型 | （可选）指定要授予的专业技能级别。 例如，如果应该有专家和几乎是专家（两个徽章），则值应设置为2。 badgingLevel应与为badgingPath属性列出的与专家相关的徽章图像的数量相对应。 默认值为1。 |
| badgingType | 字符串 | （必需）将评分引擎标识为“基本”或“高级”。 设置为“高级”，否则默认为“基本”。 |
| scoringRules | 字符串[] | （可选）多值字符串，用于限制标记规则对列出的评分规则标识的事件进行评分。示例条目：/etc/community/scoring/rules/adv-comments-scoring默认无限制。 |

## 包含的规则和徽章 {#included-rules-and-badge}

### 包含的徽章 {#included-badge}

此测试版中包含一个基于奖励的专家徽章：

* 专家

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

为了让专家徽章显示为对活动的奖励，必须发生两件事：

* `badges` 必须启用该功能，例如论坛或QnA组件
* 必须将高级评分和标记规则应用于组件所在的页面（或上级）

请参阅以下基本信息：

* [启用组件标记](implementing-scoring.md#enable-badges-for-component)
* [应用规则](implementing-scoring.md#apply-rules-to-content)

### 包含评分规则和子规则 {#included-scoring-rules-and-sub-rules}

测试版中包含两个适用于 [论坛功能](functions.md#forum-function) （论坛和论坛功能的评论组件各一个）：

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-voting-rule-owner

      /etc/community/scoring/rules/subrules/adv-voting-rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-forums-rule

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-voting-rule-owner

**注释:**

* 两者兼有 `rules`和 `sub-rules` 节点类型 `cq:Page`
* `subRules` 是字符串类型的属性[] 规则 `jcr:content` 节点
* `sub-rules` 可在各种评分规则之间共享
* `rules` 应位于具有每个用户读取权限的存储库位置
   * 规则名称必须唯一，而不考虑位置

### 包含标记规则 {#included-badging-rules}

该版本中包含两个与 [高级论坛和评论评分规则](#included-scoring-rules-and-sub-rules).

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**注释:**

* `rules` 节点类型 `cq:Page`
* `rules`应位于具有每个用户读取权限的存储库位置
   * 规则名称必须唯一，而不考虑位置
