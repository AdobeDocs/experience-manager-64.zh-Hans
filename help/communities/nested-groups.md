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
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---


# 创作嵌套组{#authoring-nested-groups}

## 在作者上创建组{#creating-groups-on-author}

在作者中，从全局导航

* 选择&#x200B;**[!UICONTROL 社区>站点]**
* 选择&#x200B;**[!UICONTROL Engage文件夹]**&#x200B;以将其打开
* 为&#x200B;**[!UICONTROL Getting Started Tutorial]** English站点选择卡
   * 选择卡图像
   * *不*&#x200B;选择一个图标

结果是到达[组控制台](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

组函数将显示为创建组实例的文件夹。 选择要打开的组文件夹。 将显示在发布时创建的组。

![chlimage_1-54](assets/chlimage_1-54.png)

## 创建主要艺术组{#create-main-arts-group}

可以创建此组，因为参与的站点结构包含组功能。 站点`Reference Template`中的函数配置默认为允许选择任何已启用的组模板。 因此，为此新组选择的模板将是`Reference Group`。

这些控制台与“社区站点”控制台非常相似。

* 选择&#x200B;**[!UICONTROL 创建组]**
* `1 Community Group Template`:
   * 社区组标题：艺术
   * 社区组描述：不同艺术组的父组。
   * 社区组根：*保留为默认*
   * 其他可用社区组语言：使用下拉菜单选择可用的社区组语言。 该菜单显示创建父社区站点时使用的所有语言。 用户可以在这些语言中进行选择，在此单步中创建多语言环境的用户组。 在相应社区站点的“组”控制台中以多种指定语言创建同一组。
   * 社区组名称：艺术
   * 模板：下拉选择`Reference Group`
   * 选择 `Next`

      ![parenttentedgroup](assets/parenttonestedgroup.png)

使用以下设置继续浏览其他面板：

* **2设计**
   * 您可以更改设计或允许默认为父站点的设计
   * 选择&#x200B;**[!UICONTROL 下一步]**
* **3设置**
   * **审核**
      * 留空（继承父站点）
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

在创建嵌套在`arts`组中的组之前，请将指针悬停在`arts`卡上，然后选择发布图标进行发布。

![chlimage_1-55](assets/chlimage_1-55.png)

等待确认组已发布。

![chlimage_1-56](assets/chlimage_1-56.png)

`arts`组还应包含`groups`文件夹，但该文件夹为空，可在其中创建新组。 导航到艺术组文件夹并创建3个嵌套用户组，每个用户组具有不同的成员资格设置：

1. 可视
   * 标题: `Visual Arts`
   * 名称: `visual`
   * 模板: `Reference Group`
   * 会员资格：选择`Optional Membership`
公开给所有成员的公共组
1. 听觉
   * 标题: `Auditory Arts`
   * 名称: `auditory`
   * 模板: `Reference Group`
   * 会员资格：选择`Required Membership`
一个开放用户组，可供成员加入

1. 历史

   * 标题: `Art History`
   * 名称: `history`
   * 模板: `Reference Group`
   * 会员资格：选择`Restricted Membership`
仅对受邀成员可见（例如）的机密组，邀请 
[演示用户](tutorials.md#demo-users) `emily.andrews@mailinator.com`

刷新页面以查看所有三个嵌套组（子社区）。

如有必要，请从“社区站点”控制台中导航到嵌套组：

* 选择&#x200B;**[!UICONTROL Engage folder]**
* 选择&#x200B;**[!UICONTROL Getting Started Tutorial]**&#x200B;卡
* 选择&#x200B;**[!UICONTROL 组文件夹]**
* 选择&#x200B;**[!UICONTROL 艺术卡]**
* 选择&#x200B;**[!UICONTROL 组文件夹]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 发布组{#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

发布主社区站点后，必须

* 单独发布每个组
   * 正在等待确认组已发布
* 发布嵌套在
   * 所有组都必须以自上而下的方式发布。

![chlimage_1-59](assets/chlimage_1-59.png)

## 发布体验{#experience-on-publish}

登录时，可以体验不同的组，例如，使用[演示用户](tutorials.md#demo-users)

* 图稿／历史记录组成员：emily.andrews@mailinator.com
   * 受限（秘密）组（艺术／历史记录）将可见
   * 可以查看可选（公共）组
   * 可以加入受限（打开）组
* 组管理器：aaron.mcdonald@mailinator.com
   * 可以查看可选（公共）组
   * 可以加入受限（打开）组
   * 将看不到受限（秘密）组

访问作者的“社区[成员和组”控制台](members.md)，将其他用户添加到与社区组对应的各种成员组。
