---
title: 标记控制台
seo-title: 标记控制台
description: 社区标记控制台允许您添加自定义标记，这些标记可在会员获得（奖励）或在社区中承担特定角色（分配）时为会员显示
seo-description: 社区标记控制台允许您添加自定义标记，这些标记可在会员获得（奖励）或在社区中承担特定角色（分配）时为会员显示
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b

---


# 标记控制台 {#badges-console}

## 关于标记 {#about-badges}

社区标记控制台提供添加自定义标记的功能，这些标记可在会员获得（奖励）或在社区中承担特定角色（已分配）时显示。

### 徽章可见性 {#badge-visibility}

当前，社区会员赚取或分配的标记将与其姓名和头像一起显示在以下位置：

* 个人资料
* [论坛](forum.md)
* [问题与解答](working-with-qna.md)
* [排行榜](enabling-leaderboard.md)
* [构思](ideation-feature.md)

在创作环境中，要访问标记控制台

* 从全局导航：“工 **[!UICONTROL 具”>“社区”>“标记”]**

此控制台显示当前可用的标记以及可以从中添加新标记。

![chlimage_1-242](assets/chlimage_1-242.png)

## 创建徽章 {#create-badge}

通过上传合适的小图像（72dpi，高度在26-32像素之间）并提供名称来创建标记。 徽章图像存储在位于的存储库中， `/etc/community/badging/images` 并会自动复制到发布环境中。

如果发布环境是发布者的农场，则必须配置用 [户同步](sync.md)。

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 上传图像]**

   (必&#x200B;*需*)建议大小为32 x 32像素、JPEG或PNG格式为72dpi的徽章图像。

* **[!UICONTROL 名称]**

   (必&#x200B;*需*)徽章名称。 它是默认的 `Display Name` 和存储库节点名称。 如果该 `Name` 节点不是有效的存储库节点名称，则将对其进行修改。

* **[!UICONTROL 显示名称]**

   (可&#x200B;*选*)在UI中为徽章显示的名称。 默认值是为输入的未更改文本 `Name`。

* **[!UICONTROL 描述]**

   (*可选*)徽章的说明。

## 附加信息 {#additional-information}

有关设置得分和徽章规则的详细信息，请参阅 [得分和徽章](implementing-scoring.md)。

有关管理成员的标记，请参阅 [成员控制台](members.md)。
