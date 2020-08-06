---
title: 在We.Retail中试用可编辑的模板
seo-title: 在We.Retail中试用可编辑的模板
description: 'null'
seo-description: 'null'
uuid: 0d4b97cb-efcc-4312-a783-eae3ecd6f889
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 3cc8ac23-98ff-449f-bd76-1203c7cbbed7
translation-type: tm+mt
source-git-commit: c0c0a7223ef70d3c19954bb2fc2a92dbad8ce049
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 11%

---


# 在We.Retail中试用可编辑的模板{#trying-out-editable-templates-in-we-retail}

有了可编辑的模板，创建和维护模板不再只是开发人员的任务。 一种称为模板作者的高级用户现在可以创建模板。 开发人员仍需要设置环境、创建客户端库和创建要使用的组件，但是，在这些基础知识到位后，模板作者就可以灵活地创建和配置模板，而无需开发项目。 

We.Retail中的所有页面都基于可编辑的模板，允许非开发人员调整和自定义模板。

## 尝试 {#trying-it-out}

1. 编辑语言主控分支的“设备”页面。

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html

1. 请注意，模式选择器不再优惠设计模式。 We.Retail的所有页面都基于可编辑的模板，要改变可编辑模板的设计，必须在模板编辑器中编辑这些模板。
1. 从页面 **信息菜单** ，选择 **编辑模板**。
1. 您现在正在编辑“主页”模板。

   页面的结构模式允许您修改模板的结构。 例如，这包括布局容器中允许的组件。

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. 为布局容器配置策略以定义允许在容器中使用的组件。

   策略与设计配置相同。

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. 在布局容器的设计对话框中，您可以

   * 选择现有策略或为容器创建新策略
   * 选择容器中允许的组件
   * 定义将资产拖动到容器时要放置的默认组件

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. 返回到模板编辑器中，您可以在布局容器中编辑文本组件的策略。

   这允许您：

   * 选择现有策略或为容器创建新策略
   * 定义使用此组件时页面作者可用的功能，如

      * 允许粘贴源
      * 格式选项
      * 允许的段落样式
      * 允许的特殊字符

   许多基于核心组件的组件允许通过可编辑的模板在组件级别配置选项，从而消除了开发人员进行自定义的需求。

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. 返回到模板编辑器后，您可以使用模式选择器更改为 **初始内容** ，以定义页面上需要哪些内容。

   **布局** 模式可以像在普通页面上一样使用，以定义模板的布局。

## 更多信息 {#more-information}

有关详细信息，请参阅创作文档创 [建页面模板](/help/sites-authoring/templates.md) ，或开发人员文档页 [面模板——可编辑](/help/sites-developing/page-templates-editable.md) ，以了解可编辑模板的完整技术详细信息。

您可能还希望调查核 [心组件](/help/sites-developing/we-retail-core-components.md)。 有关核心组件 [功能的概述](https://docs.adobe.com/content/help/zh-Hans/experience-manager-core-components/using/introduction.html) ，请参阅创作文档核心组件，有关技术概 [述，请参阅开发文档](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) 开发核心组件。

