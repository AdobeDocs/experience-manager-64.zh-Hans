---
title: 在We.Retail中尝试响应式布局
seo-title: Trying out Responsive Layout in We.Retail
description: 在We.Retail中尝试响应式布局
seo-description: null
uuid: d9613655-f54e-458f-9175-d07bb868f58b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 2d374e88-ea09-43d5-986c-5d77b0705b93
exl-id: ccb792f7-e837-4790-818f-e2c446328e71
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 2%

---

# 在We.Retail中尝试响应式布局{#trying-out-responsive-layout-in-we-retail}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

所有We.Retail页面均使用布局容器组件来实施响应式设计。 布局容器提供了一个段落系统，允许您在响应式网格内放置组件。 此网格可根据设备/窗口大小和格式重新排列布局。 该组件与 **布局** 模式，用于创建和编辑依赖于设备的响应式布局。

## 尝试 {#trying-it-out}

1. 编辑语言主控分支“体验”部分的“北极冲浪”页面。

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html

1. 切换到 **预览** 查看呈现给网站访客的页面。 向下滚动到文章的内容 *挪威北部的阿洛哈神灵*.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. 调整浏览器窗口的大小，并在布局根据大小调整而动态调整时进行观察。

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. 切换到布局模式。 模拟器工具栏会自动显示，允许您根据目标设备规划布局。

   选择组件时，编辑菜单中会显示浮动和隐藏选项，以及组件的调整大小手柄。

   ![chlimage_1-180](assets/chlimage_1-180.png)

1. 抓取并拖动组件的大小调整手柄会自动显示布局网格，以帮助您调整大小。

   ![chlimage_1-181](assets/chlimage_1-181.png)

## 更多信息 {#further-information}

有关详细信息，请参阅创作文档 [响应式布局](/help/sites-authoring/responsive-layout.md) 或管理员文档 [配置布局容器和布局模式](/help/sites-administering/configuring-responsive-layout.md) 以了解完整的技术详细信息。
