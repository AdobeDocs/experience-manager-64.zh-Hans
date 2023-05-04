---
title: 排行榜功能
seo-title: Leaderboard Feature
description: 向页面添加排行榜组件
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 7%

---

# 排行榜功能 {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

的 `Leaderboard` 组件提供了根据获得的分数（基本评分）或其专业知识（高级评分）对成员进行排名以了解成员在社区内如何进行交互的能力。

在将排行榜组件包含到页面之前，需要配置 [社区评分和徽章](implementing-scoring.md).

此文档部分描述

* 添加 `Leaderboard` 组件 [社区网站](overview.md#community-sites)

* 的配置设置 `Leaderboard` 组件

## 向页面添加排行榜 {#adding-a-leaderboard-to-a-page}

添加 `Leaderboard` 组件到创作模式下的页面，找到组件

* `Communities / Leaderboard`

并将其拖动到页面上的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

首次将组件放置在社区站点的页面上时，组件的显示方式如下：

![chlimage_1-8](assets/chlimage_1-8.png)

## 配置排行榜 {#configuring-leaderboard}

选择已放置的 `Leaderboard` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### “设置”选项卡 {#settings-tab}

在 **[!UICONTROL 设置]** 选项卡，指定显示与成员相关的信息：

* **[!UICONTROL 显示名称]**
为展示板显示的描述性名称，反映为显示徽章和得分而选择的规则。

   默认为 `Leaderboard`，如果未输入任何内容。

* **[!UICONTROL 徽章]**
如果选中此选项，则标记图标的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 标记名称]**
如果选中此项，则标志名称的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 使用头像]**
如果选中此项，则会将成员的头像图像包含在排行榜中，旁边是其名称链接到其成员配置文件的位置。

   默认为未选中。

### “规则”选项卡 {#rules-tab}

在 **[!UICONTROL 规则]** 选项卡，以及其评分和标记规则

* **[!UICONTROL 规则位置]**
（必需）配置评分/标记规则的位置。

* **[!UICONTROL 评分规则]**
（必需）生成要显示的分数的特定规则。

* **[!UICONTROL 标记规则]**
（必需）生成要显示标记的特定规则。

* **[!UICONTROL 显示限制]**
每页要显示的成员数。

   默认值为10。

## 示例：参与者领导板 {#example-participants-leaderboard}

该排行榜会报告应用基本评分规则的结果。

排行榜组件配置：

* **[!UICONTROL 设置]** 选项卡：

   * 显示名称 = `Participation Board`
   * `checked`:

      * 徽章
      * 徽章名称
      * 使用头像

* **[!UICONTROL 规则]** 选项卡：

   * 规则位置 = `/content/sites/communities/jcr:content`
   * 评分规则 = `/etc/community/scoring/rules/forums-scoring`
   * 徽章规则 = `/etc/community/badging/rules/reference-badging`
   * 显示限制 = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## 示例：专家领导板 {#example-experts-leaderboard}

此排行榜会报告应用高级评分规则所产生的结果。

排行榜组件配置：

* **[!UICONTROL 设置]** 选项卡：

   * 显示名称 = `Expertise Board`
   * `checked`:

      * 徽章
      * 使用头像

* **[!UICONTROL 规则]** 选项卡：

   * 规则位置 = `/content/sites/communities/jcr:content`
   * 评分规则 = `/etc/community/scoring/rules/adv-forums-scoring`
   * 徽章规则 = `/etc/community/badging/rules/adv-forums-badging`
   * 显示限制 = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## 附加信息 {#additional-information}

有关 [排行榜要点](leaderboard.md) 页面。

有关创建规则的说明，请参阅 [社区评分和徽章](implementing-scoring.md) 页面。
