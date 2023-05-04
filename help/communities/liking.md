---
title: 使用称赞
seo-title: Using Liking
description: 添加和配置称赞组件
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 6%

---

# 使用称赞 {#using-liking}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

的 `Liking`组件是一个有用的工具，它允许用户对特定内容（如论坛中的评论）发表意见。 使用 `Liking`组件中，成员选择心图标以指示积极意见。

## 向页面添加称赞 {#adding-liking-to-a-page}

添加 `Liking` 组件添加到创作模式下的页面，可使用组件浏览器找到

* `Communities / Liking`

并将其拖动到页面上的位置，如用户喜欢的相对于该功能的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](essentials-liking.md#essentials-for-client-side) 包含，这是 `Liking` 组件。

![chlimage_1-93](assets/chlimage_1-93.png)

## 配置称赞 {#configuring-liking}

选择已放置的 `Liking` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-94](assets/chlimage_1-94.png)

在 **[!UICONTROL 文本和标签]** 选项卡，指定用于记录称赞的属性。

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL 正面响应标签]**
(
*必需*)正向响应的属性名称。

* **[!UICONTROL 负面响应标签]**
(
*必需*)负响应的属性名称。

* **[!UICONTROL 标签名称]**
(
*必需*)此投票组件实例的内部可识别属性名称。

## 网站访客体验 {#site-visitor-experience}

### 成员 {#members}

会员可以随时更改其样式。

### 匿名 {#anonymous}

不支持匿名称赞。 网站访客必须注册（成为会员）并登录以参与称赞。

## 附加信息 {#additional-information}

有关 [称赞要点](essentials-liking.md) 页面。
