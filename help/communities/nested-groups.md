---
title: 创作嵌套群组
seo-title: Authoring Nested Groups
description: 创建嵌套群组
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 3%

---

# 创作嵌套群组 {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 在创作时创建组 {#creating-groups-on-author}

在作者上，从全局导航

* 选择 **[!UICONTROL 社区>站点]**
* 选择 **[!UICONTROL 参与文件夹]** 打开
* 为 **[!UICONTROL 入门教程]**  英文网站
   * 选择卡片图像
   * 做 *not* 选择图标

结果是达到 [“组”控制台](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

组函数将显示为在其中创建组实例的文件夹。 选择Groups文件夹以将其打开。 将显示在发布时创建的组。

![chlimage_1-54](assets/chlimage_1-54.png)

## 创建主要艺术组 {#create-main-arts-group}

可以创建此组，因为参与的站点结构包含组功能。 站点的 `Reference Template` 默认为允许选择任何已启用的组模板。 因此，为此新组选择的模板将为 `Reference Group`.

这些控制台与“社区站点”控制台非常相似。

* 选择 **[!UICONTROL 创建群组]**
* `1 Community Group Template`:
   * 社区组标题：艺术
   * 社区组描述：不同艺术团体的家长组。
   * 社区组根： *默认保留*
   * 其他可用社区组语言：使用下拉菜单选择可用的社区组语言。 该菜单显示创建父社区站点的所有语言。 用户可以在这些语言中进行选择，以在此单步中的多个区域设置中创建组。 在相应社区站点的“组”控制台中，会以多种指定语言创建同一组。
   * 社区组名称：艺术
   * 模板：下拉选择 `Reference Group`
   * 选择 `Next`

      ![parentonestedgroup](assets/parenttonestedgroup.png)

使用这些设置继续浏览其他面板：

* **2设计**
   * 您可以更改设计或允许默认使用父网站的设计
   * 选择 **[!UICONTROL 下一个]**
* **3设置**
   * **审核**
      * 将留空（从父站点继承）
   * **成员资格**
      * 使用默认值 `Optional Membership`
   * **缩略图**
      * `optional`
   * 选择 `Next`
* 选择 **[!UICONTROL 创建]**

### 艺术组中的嵌套组 {#nesting-groups-within-arts-group}

的 `groups` 文件夹现在应包含两个组（可能需要刷新页面）。

![createcommunitygroup](assets/createcommunitygroup.png)

#### 发布组 {#publish-group}

在创建嵌套在 `arts`群组中，将鼠标悬停在 `arts` 卡片上，然后选择“发布”图标以发布它。

![chlimage_1-55](assets/chlimage_1-55.png)

等待确认群组已发布。

![chlimage_1-56](assets/chlimage_1-56.png)

的 `arts` 组还应包含 `groups` 文件夹，但是空的，可在其中创建新群组的文件夹。 导航到艺术组文件夹并创建3个嵌套组，每个组具有不同的成员资格设置：

1. 可视
   * 标题: `Visual Arts`
   * 名称: `visual`
   * 模板: `Reference Group`
   * 会员资格：选择 `Optional Membership`
对所有成员开放的公共组
1. 听觉
   * 标题: `Auditory Arts`
   * 名称: `auditory`
   * 模板: `Reference Group`
   * 会员资格：选择 `Required Membership`
一个开放的组，可供成员加入

1. 历史

   * 标题: `Art History`
   * 名称: `history`
   * 模板: `Reference Group`
   * 会员资格：选择 `Restricted Membership`
仅对受邀成员可见（例如）的秘密组邀请 
[演示用户](tutorials.md#demo-users) `emily.andrews@mailinator.com`

刷新页面可查看所有三个嵌套群组（子社区）。

如有必要，请从“社区站点”控制台导航到嵌套的组：

* 选择 **[!UICONTROL 参与文件夹]**
* 选择 **[!UICONTROL 入门教程]** 卡片
* 选择 **[!UICONTROL 组文件夹]**
* 选择 **[!UICONTROL 艺术卡]**
* 选择 **[!UICONTROL 组文件夹]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 发布组 {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

发布主社区网站后，需要

* 单独发布每个组
   * 等待确认群组已发布
* 发布父组后，再发布嵌套在
   * 所有群组都必须以自上而下的方式发布。

![chlimage_1-59](assets/chlimage_1-59.png)

## 发布体验 {#experience-on-publish}

登录后，可能会体验不同的群组，例如使用 [演示用户](tutorials.md#demo-users) 用于

* 艺术/历史组成员：emily.andrews@mailinator.com
   * 受限（秘密）组，艺术/历史，将可见
   * 可以查看可选（公共）群组
   * 可以加入受限（打开）组
* 组管理器：aaron.mcdonald@mailinator.com
   * 可以查看可选（公共）群组
   * 可以加入受限（打开）组
   * 将看不到受限（密钥）组

访问社区 [“成员”和“组”控制台](members.md) 创作时，将其他用户添加到与社区组对应的各个成员组。
