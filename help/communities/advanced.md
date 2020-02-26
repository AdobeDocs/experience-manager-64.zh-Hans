---
title: 高级评分和徽章
seo-title: 高级评分和徽章
description: 设置高级评分
seo-description: 设置高级评分
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc

---


# 高级评分和徽章 {#advanced-scoring-and-badges}

## 概述 {#overview}

高级评分允许授予徽章，以便将会员标识为专家。 高级评分根据成员创建的内 *容数量* 和质量分配积分，而基本评分只根据创建的内容数量分配积分。

此差异是由于用于计算得分的得分引擎所致。 基本评分引擎应用简单的数学。 高级评分引擎是一种自适应算法，它奖励通过主题的自然语言处理(NLP)推导的贡献有价值和相关内容的活动成员。

除了内容相关性外，评分算法还考虑成员活动，如投票和答案百分比。 虽然基本评分包括定量评分，但高级评分通过算法使用这些评分。

因此，高级评分引擎需要足够的数据来使分析变得有意义。 随着算法不断根据所创建内容的体积和质量进行调整，不断重新评估成为专家的成就阈值。 还有一个概念是 *老* 员额的衰败。 如果专家成员停止参与他们获得专家状态的主题事项，则在某个预定点(请参阅评分引擎配置 [](#configurable-scoring-engine))，他们可能失去其专家状态。

设置高级评分与基本评分基本相同：

* 基本和高级评分和徽章规则 [以相同方式应用于](implementing-scoring.md#apply-rules-to-content) 内容
   * 基本和高级评分和徽章规则可应用于相同内容
* [为组件启用标记](implementing-scoring.md#enable-badges-for-component) 是通用的

设置得分和徽章规则的区别是：

* 可配置的高级评分引擎
* 高级评分规则：
   * `scoringType` 设置为高 **[!UICONTROL 级]**
   * 需要秒

* 高级标记规则：
   * `badgingType` 设置为高 **[!UICONTROL 级]**
   * `badgingLevels` 设置为要授予的专家级别数
   * 需要 `badgingPaths` 标记阵列而不是阈值阵列映射点到标记

>[!NOTE]
>
>要使用高级评分和徽章功能，请安装“专 [家识别”包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)。

## 可配置的评分引擎 {#configurable-scoring-engine}

高级评分引擎提供OSGi配置，其中参数影响高级评分算法。

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 评分权重]**&#x200B;对于主题，指定在计算得分时应给予最高优先级的动词。 可以输入一个或多个主题，但每个主题限 **于一个动词**。 请参 [阅主题和动词](implementing-scoring.md#topics-and-verbs)。

   以逗号转 `topic,verb` 义的形式输入。 例如：

   `/social/forum/hbs/social/forum\,ADD`

   对于QnA和论坛组件，默认设置为ADD动词。


* **[!UICONTROL 评分范围]**

   高级得分的范围由此值（最高可能得分）和0（最低可能得分）定义。

   默认值为100，因此评分范围为0-100。


* **[!UICONTROL 实体衰减时间间隔]**

   此参数表示所有实体得分衰减后的小时数。 这要求不再在社区站点的分数中包含旧内容。

   默认值为216000小时（~24年）。


* **[!UICONTROL 评分增长率]**

   这将指定得分。 在0到评分范围之间，超过这个范围，增长会放缓，从而限制专家数量。

   默认值为 50。

## 高级评分规则 {#advanced-scoring-rules}

在基本得分中，获得徽章所需的数量是已知的。

在高级评分中，根据系统内的质量数据量不断调整所需数量。 评分以类似钟形曲线的方式持续计算。

如果会员在不再处于活动状态的主题上获得了专家徽章，则可能会因随时间的推移而失去其徽章。

### ScoringType {#scoringtype}

评分规则是评分子规则集合，每个评分子规则都声明 `scoringType`。

要调用高级评分引擎， `scoringType`应将其设置为 `advanced`。

请参 [阅评分子规则](implementing-scoring.md#scoring-sub-rules)。

![chlimage_1-261](assets/chlimage_1-261.png)

### 秒词 {#stopwords}

高级评分包会安装一个配置文件夹，其中包含一个秒词文件：

* `/etc/community/scoring/configuration/stopwords`

高级评分算法使用包含在秒词文件中的单词列表来识别在内容处理过程中忽略的常见英语单词。

不希望修改此文件。

如果秒词文件缺失，高级评分引擎将引发错误。

## 高级标记规则 {#advanced-badging-rules}

高级标记规则属性与基本标记 [规则属性不同](implementing-scoring.md#badging-rules)。

除了将点与徽章图像关联之外，只需确定允许的专家数量和要授予的徽章图像。

![chlimage_1-262](assets/chlimage_1-262.png)

| **属性** | **类型** | **值说明** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | String[] | （必需）徽章图像的多值字符串，最高可达badgingLevels的数量。 必须对徽章图像路径进行排序，以便将第一个路径授予最高专家。 如果标记数少于badgingLevels所指示的标记数，则数组中的最后一个标记将填充数组的其余部分。 示例条目：/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | 长整型 | （可选）指定要授予的专业知识级别。 例如，如果应该有专家和近乎专家（两个徽章），则值应设置为2。 badgingLevel应与为badgingPath属性列出的专家相关标记图像的数量相对应。 默认值为1。 |
| badgingType | 字符串 | （必需）将评分引擎标识为“基本”或“高级”。 如果设置为“advanced”，则默认值为“basic”。 |
| scoringRules | String[] | （可选）用于将标记规则限制为由列出的评分规则标识的评分事件的多值字符串。示例条目：/etc/community/scoring/rules/adv-comments-scoring默认值为无限制。 |

## 包含的规则和徽章 {#included-rules-and-badge}

### 包含的徽章 {#included-badge}

此测试版包含一个基于奖励的专家徽章：

* 专家

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

为了让专家徽章显示为活动的奖励，必须做两件事：

* `badges` 必须为功能（如论坛或问题与答案组件）启用
* 高级评分和标记规则必须应用于放置组件的页面（或上级）

请参阅以下基本信息：

* [为组件启用标记](implementing-scoring.md#enable-badges-for-component)
* [应用规则](implementing-scoring.md#apply-rules-to-content)

### 包括评分规则和子规则 {#included-scoring-rules-and-sub-rules}

测试版包含两个用于论坛功能的高级评 [分规则](functions.md#forum-function) （论坛和论坛功能的评论组件各一个规则）:

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-porting-rule-owner

      /etc/community/scoring/rules/subrules/adv-porting-rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-forums-rule

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-porting-rule-owner

**注释:**

* 节 `rules`点 `sub-rules` 和节点的类型 `cq:Page`
* `subRules` 是规则节点上字符串类型的属性[] ，该属 `jcr:content` 性
* `sub-rules` 可能在各种评分规则之间共享
* `rules` 应该位于存储库位置，并且每个人都具有读取权限
   * 规则名称必须唯一，而不管位置

### 包含徽章规则 {#included-badging-rules}

该版本包含两个与高级论坛和评论评分规则相 [对应的高级标记规则](#included-scoring-rules-and-sub-rules)。

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**注释:**

* `rules` 节点的类型 `cq:Page`
* `rules`应该位于存储库位置，并且每个人都具有读取权限
   * 规则名称必须唯一，而不管位置
