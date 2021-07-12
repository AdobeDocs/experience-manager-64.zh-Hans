---
title: 徽章控制台
seo-title: 徽章控制台
description: 社区徽章控制台允许您添加自定义徽章，这些徽章可在成员获得（授予）或在社区中承担特定角色（已分配）时为其显示
seo-description: 社区徽章控制台允许您添加自定义徽章，这些徽章可在成员获得（授予）或在社区中承担特定角色（已分配）时为其显示
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---

# 徽章控制台 {#badges-console}

## 关于徽章 {#about-badges}

社区徽章控制台提供了添加自定义徽章的功能，当会员获得（授予）或在社区中承担特定角色（分配）时，可向其显示自定义徽章。

### 徽章可见性 {#badge-visibility}

目前，社区成员获得或分配的徽章将与其姓名和头像一起显示在以下位置：

* 个人资料
* [论坛](forum.md)
* [问题与解答](working-with-qna.md)
* [排行榜](enabling-leaderboard.md)
* [构思](ideation-feature.md)

在创作环境中，访问徽章控制台

* 从全局导航：**[!UICONTROL 工具>社区>徽章]**

此控制台会显示当前可用的徽章，以及可从中添加新徽章的徽章。

![chlimage_1-242](assets/chlimage_1-242.png)

## 创建徽章 {#create-badge}

通过上传合适的小图像（72dpi，高度在26-32像素之间）并提供名称来创建标记。 标记图像存储在位于`/etc/community/badging/images`的存储库中，并会自动复制到发布环境。

如果发布环境是发布者的场，则需要配置[用户同步](sync.md)。

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 上传图像]**

   （*必需*）JPEG或PNG格式的72dpi建议大小为32 x 32像素的标记图像。

* **[!UICONTROL 名称]**

   （*必需*）标记名称。 它是默认的`Display Name`以及存储库节点名称。 如果`Name`不是有效的存储库节点名称，则会对其进行修改。

* **[!UICONTROL 显示名称]**

   （*可选*）要在UI中显示标记的名称。 默认为为`Name`输入的未更改文本。

* **[!UICONTROL 描述]**

   （*可选*）标记的描述。

## 附加信息 {#additional-information}

有关设置评分和标记规则的详细信息，请参阅[评分和徽章](implementing-scoring.md)。

有关管理成员的徽章，请参阅[成员控制台](members.md)。
