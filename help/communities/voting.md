---
title: 使用投票
seo-title: 使用投票
description: 将投票组件添加到页面
seo-description: 将投票组件添加到页面
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---


# 使用投票{#using-voting}

`Voting`组件是一个有用的工具，它允许社区成员对特定内容（如问题与答案组件中的答案）进行评级。 对于`Voting`组件，成员选择向上或向下箭头以指示其意见。

## 向页面{#adding-voting-to-a-page}添加投票

要在创作模式下将`Voting`组件添加到页面，请使用组件浏览器找到`Communities / Voting`并将其拖动到页面上的位置，如用户要投票时相对于该功能的位置。

有关必要的信息，请访问[社区组件基础知识](basics.md)。

当包含[必需的客户端库](essentials-voting.md#essentials-for-client-side)时，将显示`Voting`组件。

![chlimage_1-307](assets/chlimage_1-307.png)

## 配置投票{#configuring-voting}

选择要访问的已放置`Voting`组件，然后选择打开编辑对话框的`Configure`图标。

![chlimage_1-308](assets/chlimage_1-308.png)

在&#x200B;**[!UICONTROL 文本和标签]**&#x200B;选项卡下，指定用于记录投票的属性。

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL 正面响应标签]**
(
*必需*)正响应的内部属性名称。

* **[!UICONTROL 负面响应标签]**
(
*必需*)负响应的内部属性名称。

* **[!UICONTROL 标签名称]**
(
*必需*)此投票组件实例的内部可识别属性名称。

## 站点访客体验{#site-visitor-experience}

### 成员 {#members}

成员只能投一票，但可随时更改其投票。

### 匿名 {#anonymous}

不支持匿名投票。 网站访客必须注册（成为会员）并登录一次以参加投票。

## 附加信息 {#additional-information}

有关开发人员的详细信息，请参阅[Poting Essentials](essentials-voting.md)页面。
