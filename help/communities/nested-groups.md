---
title: 创作嵌套组
seo-title: 创作嵌套组
description: 创建嵌套用户组
seo-description: 创建嵌套用户组
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc

---


# 创作嵌套组 {#authoring-nested-groups}

## 在创作时创建组 {#creating-groups-on-author}

在创作时，从全局导航

* 选择“ **[!UICONTROL 社区”>“站点”]**
* 选择 **[!UICONTROL Engage文件夹]** ，以将其打开
* 为“入门教程英语” **[!UICONTROL 站点选择卡]** 。
   * 选择卡图像
   * 不 *要选* 择图标

结果是到达“组”控 [制台](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

组函数将显示为创建组实例的文件夹。 选择“用户组”文件夹以将其打开。 发布时创建的组可见。

![chlimage_1-54](assets/chlimage_1-54.png)

## 创建主要艺术组 {#create-main-arts-group}

可以创建此组，因为参与的站点结构包括组功能。 站点默认配置的函数允 `Reference Template` 许选择任何已启用的组模板。 因此，为此新组选择的模板将是 `Reference Group`。

这些控制台与“社区站点”控制台非常相似。

* 选择 **[!UICONTROL 创建组]**
* `1 Community Group Template`:
   * 社区组标题：艺术
   * 社区组描述：不同艺术组的父组。
   * 社区组根： *保留为默认*
   * 其他可用社区组语言：使用下拉菜单选择可用的社区组语言。 该菜单显示创建父社区站点时所用的所有语言。 用户可以在这些语言中进行选择，以在此单步中创建多个区域设置的用户组。 在相应社区站点的“组”控制台中，以多种指定语言创建同一组。
   * 社区组名称：艺术
   * 模板：下拉选择 `Reference Group`
   * 选择 `Next`
      ![parenttentedgroup](assets/parenttonestedgroup.png)

使用以下设置继续浏览其他面板：

* **2设计**
   * 您可以更改设计或允许默认为父站点的设计
   * Select **[!UICONTROL Next]**
* **3设置**
   * **审核**
      * 留空（继承父站点）
   * **成员资格**
      * use default `Optional Membership`
   * **缩略图**
      * `optional`
   * 选择 `Next`
* Select **[!UICONTROL Create]**

### Arts Group中的嵌套组 {#nesting-groups-within-arts-group}

文 `groups` 件夹现在应包含两个组（可能需要刷新页面）。

![createcommunitygroup](assets/createcommunitygroup.png)

#### 发布组 {#publish-group}

在创建嵌套在组中的组之 `arts`前，将指针悬停在卡 `arts` 上，然后选择发布图标以发布它。

![chlimage_1-55](assets/chlimage_1-55.png)

等待确认已发布组。

![chlimage_1-56](assets/chlimage_1-56.png)

组 `arts` 还应包含一个文件 `groups` 夹，但该文件夹为空，可在其中创建新组。 导航到艺术组文件夹并创建3个嵌套用户组，每个用户组具有不同的会员资格设置：

1. 可见
   * 标题: `Visual Arts`
   * 名称: `visual`
   * 模板: `Reference Group`
   * 会员资格：选 `Optional Membership`择公共组，打开给所有成员
1. 听觉
   * 标题: `Auditory Arts`
   * 名称: `auditory`
   * 模板: `Reference Group`
   * 会员资格：选 `Required Membership`择一个打开的用户组，可供成员加入

1. 历史

   * 标题: `Art History`
   * 名称: `history`
   * 模板: `Reference Group`
   * 会员资格：选 `Restricted Membership`择一个秘密组（例如，只对受邀成员可见），邀请演 [示用户](tutorials.md#demo-users)`emily.andrews@mailinator.com`

刷新页面可查看所有三个嵌套用户组（子社区）。

如有必要，请从“社区站点”控制台中导航到嵌套组：

* 选择“ **[!UICONTROL 参与”文件夹]**
* 选择“ **[!UICONTROL 入门教程]** ”卡
* 选择 **[!UICONTROL 用户组文件夹]**
* 选择 **[!UICONTROL 艺术卡]**
* 选择 **[!UICONTROL 用户组文件夹]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 发布组 {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

发布主社区站点后，必须

* 单独发布每个组
   * 等待确认组已发布
* 发布嵌套在
   * 所有组都必须以自上而下的方式发布。

![chlimage_1-59](assets/chlimage_1-59.png)

## 发布体验 {#experience-on-publish}

登录时，可以体验不同的组，例如，使用的演 [示用户](tutorials.md#demo-users)

* 图稿／历史记录组成员：emily.andrews@mailinator.com
   * 受限（机密）组（艺术／历史记录）将可见
   * 可查看可选（公共）组
   * 可以加入受限（打开）组
* 组管理器：aaron.mcdonald@mailinator.com
   * 可查看可选（公共）组
   * 可以加入受限（打开）组
   * 将看不到受限（机密）组

访问创作的“社 [区成员”和“组”控制台](members.md) ，将其他用户添加到与社区组对应的各个成员组。
