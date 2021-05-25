---
title: 创作嵌套群组
seo-title: 创作嵌套群组
description: 创建嵌套群组
seo-description: 创建嵌套群组
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---

# 创作嵌套群组{#authoring-nested-groups}

## 在作者上创建组{#creating-groups-on-author}

在作者上，从全局导航

* 选择&#x200B;**[!UICONTROL 社区>站点]**
* 选择&#x200B;**[!UICONTROL engage文件夹]**&#x200B;以将其打开
* 选择&#x200B;**[!UICONTROL 快速入门Tutorial]**&#x200B;英语站点的卡
   * 选择卡片图像
   * 选择&#x200B;*不*&#x200B;的图标

结果将到达[组控制台](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

组函数将显示为在其中创建组实例的文件夹。 选择Groups文件夹以将其打开。 将显示在发布时创建的组。

![chlimage_1-54](assets/chlimage_1-54.png)

## 创建主要艺术组{#create-main-arts-group}

可以创建此组，因为参与的站点结构包含组功能。 站点`Reference Template`中函数的配置默认为允许选择任何已启用的组模板。 因此，为此新组选择的模板将为`Reference Group`。

这些控制台与“社区站点”控制台非常相似。

* 选择&#x200B;**[!UICONTROL 创建组]**
* `1 Community Group Template`:
   * 社区组标题：艺术
   * 社区组描述：不同艺术团体的家长组。
   * 社区组根：*lea as default*
   * 其他可用社区组语言：使用下拉菜单选择可用的社区组语言。 该菜单显示创建父社区站点的所有语言。 用户可以在这些语言中进行选择，以在此单步中的多个区域设置中创建组。 在相应社区站点的“组”控制台中，会以多种指定语言创建同一组。
   * 社区组名称：艺术
   * 模板：下拉选择`Reference Group`
   * 选择 `Next`

      ![parentonestedgroup](assets/parenttonestedgroup.png)

使用这些设置继续浏览其他面板：

* **2设计**
   * 您可以更改设计或允许默认使用父网站的设计
   * 选择&#x200B;**[!UICONTROL Next]**
* **3设置**
   * **审核**
      * 将留空（从父站点继承）
   * **成员资格**
      * 使用默认`Optional Membership`
   * **缩略图**
      * `optional`
   * 选择 `Next`
* 选择&#x200B;**[!UICONTROL 创建]**

### 艺术组{#nesting-groups-within-arts-group}中的嵌套组

`groups`文件夹现在应包含两个组（可能需要刷新页面）。

![createcommunitygroup](assets/createcommunitygroup.png)

#### 发布组 {#publish-group}

在创建嵌套在`arts`群组中的群组之前，将鼠标悬停在`arts`卡片上，然后选择发布图标以发布该群组。

![chlimage_1-55](assets/chlimage_1-55.png)

等待确认群组已发布。

![chlimage_1-56](assets/chlimage_1-56.png)

`arts`组还应包含`groups`文件夹，但文件夹为空，可以在其中创建新组。 导航到艺术组文件夹并创建3个嵌套组，每个组具有不同的成员资格设置：

1. 可视
   * 标题: `Visual Arts`
   * 名称: `visual`
   * 模板: `Reference Group`
   * 会员资格：选择`Optional Membership`
对所有成员开放的公共组
1. 听觉
   * 标题: `Auditory Arts`
   * 名称: `auditory`
   * 模板: `Reference Group`
   * 会员资格：选择`Required Membership`
一个开放的组，可供成员加入

1. 历史

   * 标题: `Art History`
   * 名称: `history`
   * 模板: `Reference Group`
   * 会员资格：选择`Restricted Membership`
仅对受邀成员可见（例如）的秘密组邀请 
[演示用户](tutorials.md#demo-users) `emily.andrews@mailinator.com`

刷新页面可查看所有三个嵌套群组（子社区）。

如有必要，请从“社区站点”控制台导航到嵌套的组：

* 选择&#x200B;**[!UICONTROL engage folder]**
* 选择&#x200B;**[!UICONTROL 快速入门Tutorial]**&#x200B;卡
* 选择&#x200B;**[!UICONTROL Groups文件夹]**
* 选择&#x200B;**[!UICONTROL 艺术卡]**
* 选择&#x200B;**[!UICONTROL Groups文件夹]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 发布组{#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

发布主社区网站后，需要

* 单独发布每个组
   * 等待确认群组已发布
* 发布父组后，再发布嵌套在
   * 所有群组都必须以自上而下的方式发布。

![chlimage_1-59](assets/chlimage_1-59.png)

## 发布体验{#experience-on-publish}

登录时，可能会体验到不同的组，例如使用[演示用户](tutorials.md#demo-users)的

* 艺术/历史组成员：emily.andrews@mailinator.com
   * 受限（秘密）组，艺术/历史，将可见
   * 可以查看可选（公共）群组
   * 可以加入受限（打开）组
* 组管理器：aaron.mcdonald@mailinator.com
   * 可以查看可选（公共）群组
   * 可以加入受限（打开）组
   * 将看不到受限（密钥）组

访问创作中的“社区” [“成员”和“组”控制台](members.md)，将其他用户添加到与社区组对应的各种成员组。
