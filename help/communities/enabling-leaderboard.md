---
title: 排行榜功能
seo-title: 排行榜功能
description: 向页面添加排行榜组件
seo-description: 向页面添加排行榜组件
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 6%

---

# 排行榜功能{#leaderboard-feature}

## 简介 {#introduction}

`Leaderboard`组件提供了根据获得的分数（基本评分）或其专业知识（高级评分）对成员进行排名，从而了解成员在社区内的交互情况的能力。

在将排行榜组件包含到页面之前，必须配置[社区评分和徽章](implementing-scoring.md)。

此文档部分描述

* 将`Leaderboard`组件添加到[社区站点](overview.md#community-sites)

* `Leaderboard`组件的配置设置

## 向页面{#adding-a-leaderboard-to-a-page}添加排行榜

要在创作模式下向页面添加`Leaderboard`组件，请找到该组件

* `Communities / Leaderboard`

并将其拖动到页面上的位置。

有关必要信息，请访问[社区组件基础知识](basics.md)。

首次将组件放置在社区站点的页面上时，组件的显示方式如下：

![chlimage_1-8](assets/chlimage_1-8.png)

## 配置排行榜{#configuring-leaderboard}

选择要访问的已放置的`Leaderboard`组件，然后选择`Configure`图标以打开编辑对话框。

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### “设置”选项卡{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;选项卡下，指定显示与成员相关的信息：

* **[!UICONTROL 显示]**
名称为展示板显示的描述性名称，反映为显示徽章和得分而选择的规则。

   如果未输入任何内容，则默认值为`Leaderboard`。

* ****
徽章如果选中此选项，则徽章图标的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 徽章]**
名称如果选中此选项，则徽章名称的列将包含在排行榜中。

   默认为未选中。

* **[!UICONTROL 使]**
用头像如果选中此选项，则会将成员的头像图像包含在排行榜中，旁边是其成员配置文件的名称链接。

   默认为未选中。

### “规则”选项卡{#rules-tab}

在&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡下，社区网站及其评分和标记规则

* **[!UICONTROL 规则位置]**
（必需）配置评分/标记规则的位置。

* **[!UICONTROL 评分规则]**
（必需）生成要显示的得分的特定规则。

* **[!UICONTROL 标记规则]**
（必需）生成要显示标记的特定规则。

* **[!UICONTROL 显示]**
Limit每页要显示的成员数。

   默认值为10。

## 示例：参与者排行榜{#example-participants-leaderboard}

该排行榜会报告应用基本评分规则的结果。

排行榜组件配置：

* **** 设置选项卡：

   * 显示名称 = `Participation Board`
   * `checked`:

      * 徽章
      * 徽章名称
      * 使用头像

* **** 规则选项卡：

   * 规则位置 = `/content/sites/communities/jcr:content`
   * 评分规则 = `/etc/community/scoring/rules/forums-scoring`
   * 徽章规则 = `/etc/community/badging/rules/reference-badging`
   * 显示限制 = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## 示例：专家领导小组{#example-experts-leaderboard}

此排行榜会报告应用高级评分规则所产生的结果。

排行榜组件配置：

* **** 设置选项卡：

   * 显示名称 = `Expertise Board`
   * `checked`:

      * 徽章
      * 使用头像

* **** 规则选项卡：

   * 规则位置 = `/content/sites/communities/jcr:content`
   * 评分规则 = `/etc/community/scoring/rules/adv-forums-scoring`
   * 徽章规则 = `/etc/community/badging/rules/adv-forums-badging`
   * 显示限制 = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## 附加信息 {#additional-information}

有关更多信息，请参阅[Ledroboard Essentials](leaderboard.md)页面，供开发人员使用。

[社区评分和徽章](implementing-scoring.md)页面上为管理员提供了创建规则的说明。
