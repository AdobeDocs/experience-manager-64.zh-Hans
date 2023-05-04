---
title: 使用投票
seo-title: Using Voting
description: 将投票组件添加到页面
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: 660a7106-0c21-4073-8319-4d6d20b9bc49
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 6%

---

# 使用投票 {#using-voting}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

的 `Voting` 组件是一个有用的工具，它允许社区成员对特定内容片段（如QnA组件中的答案）进行评级。 使用 `Voting` 组件中，成员选择向上或向下箭头来指示其意见。

## 向页面添加投票 {#adding-voting-to-a-page}

添加 `Voting` 组件添加到创作模式下的页面，可使用组件浏览器找到 `Communities / Voting` 并将其拖动到页面上的适当位置，例如相对于该功能的位置，供用户投票。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](essentials-voting.md#essentials-for-client-side) 包含，这是 `Voting` 组件。

![chlimage_1-307](assets/chlimage_1-307.png)

## 配置投票 {#configuring-voting}

选择已放置的 `Voting` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-308](assets/chlimage_1-308.png)

在 **[!UICONTROL 文本和标签]** 选项卡，指定用于记录投票的属性。

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL 正面响应标签]**
(
*必需*)正面响应的内部属性名称。

* **[!UICONTROL 负面响应标签]**
(
*必需*)负响应的内部属性名称。

* **[!UICONTROL 标签名称]**
(
*必需*)此投票组件实例的内部可识别属性名称。

## 网站访客体验 {#site-visitor-experience}

### 成员 {#members}

成员只可投一次票，但可随时改变投票。

### 匿名 {#anonymous}

不支持匿名投票。 网站访客必须注册（成为会员）并登录以参加一次投票。

## 附加信息 {#additional-information}

有关 [投票要点](essentials-voting.md) 页面。
