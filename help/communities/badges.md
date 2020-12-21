---
title: 标记控制台
seo-title: 标记控制台
description: 社区徽章控制台允许您添加自定义徽章，当会员获得（奖励）或在社区中承担特定角色（分配）时，这些徽章可显示给会员
seo-description: 社区徽章控制台允许您添加自定义徽章，当会员获得（奖励）或在社区中承担特定角色（分配）时，这些徽章可显示给会员
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# 标记控制台{#badges-console}

## 关于标记{#about-badges}

社区徽章控制台提供添加自定义徽章的功能，这些徽章可在会员获得（奖励）或在社区中承担特定角色（分配）时为其显示。

### 徽章可见性{#badge-visibility}

目前，社区会员获得或分配的徽章将与其姓名和头像一起出现在以下位置：

* 个人资料
* [论坛](forum.md)
* [问题与解答](working-with-qna.md)
* [排行榜](enabling-leaderboard.md)
* [构思](ideation-feature.md)

在创作环境中，要访问标记控制台

* 从全局导航：**[!UICONTROL 工具>社区>标记]**

此控制台显示当前可用的标记，以及可从中添加新标记。

![chlimage_1-242](assets/chlimage_1-242.png)

## 创建徽章 {#create-badge}

通过上传合适的小图像（72dpi，高度在26-32像素之间）并提供名称来创建标记。 徽章图像存储在`/etc/community/badging/images`的存储库中，并自动复制到发布环境。

如果发布环境是发布者的场，则必须配置[用户同步](sync.md)。

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 上传图像]**

   （*必需*）建议大小为32 x 32像素、72dpi的徽章图像，采用JPEG或PNG格式。

* **[!UICONTROL 名称]**

   （*必需*）徽章名称。 它是默认`Display Name`以及存储库节点名称。 如果`Name`不是有效的存储库节点名称，则将修改它。

* **[!UICONTROL 显示名称]**

   （*可选*）要在UI中显示徽章的名称。 默认值是为`Name`输入的未更改文本。

* **[!UICONTROL 描述]**

   （*可选*）徽章的说明。

## 附加信息 {#additional-information}

有关设置得分和徽章规则的详细信息，请参阅[得分和徽章](implementing-scoring.md)。

有关管理成员的标记，请参阅[成员控制台](members.md)。
