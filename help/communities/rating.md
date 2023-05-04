---
title: 使用评级
seo-title: Using Ratings
description: 向页面添加评级组件
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 3%

---

# 使用评级 {#using-ratings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

的 `Rating`组件可单独使用，也可与其他社区功能结合使用。 此组件允许已登录的社区成员通过对内容进行评级来表达其意见。

## 向页面添加评级 {#adding-a-rating-to-a-page}

添加 `Rating`组件到创作模式下的页面，找到组件 `Communities / Rating` 并将其拖动到页面上的适当位置，如相对于要评级的成员的特征的位置。

有关必要信息，请访问 [社区组件基础知识](basics.md).

当 [所需的客户端库](rating-basics.md#essentials-for-client-side) 包含，这是 `Rating` 组件。

![chlimage_1-493](assets/chlimage_1-493.png)

## 配置评级 {#configuring-rating}

选择已放置的 `Rating` 要访问和选择的组件 `Configure` 图标，打开编辑对话框。

![chlimage_1-494](assets/chlimage_1-494.png)

在 **[!UICONTROL 文本和标签]** 选项卡，您可以指定评级的内部标识符。

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL 计数名称]**
(*必需*)的简单名称 `Rating`用于唯一标识此实例。 必须是存储库的有效节点名称。

## 网站访客体验 {#site-visitor-experience}

### 成员 {#members}

每个成员只允许一个评级。 会员可随时更改其评级。

### 匿名 {#anonymous}

不支持匿名发布评级。 网站访客必须注册（成为会员）并登录以参与。

## 附加信息 {#additional-information}

有关 [评级要点](rating-basics.md) 页面。
