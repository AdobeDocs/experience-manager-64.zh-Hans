---
title: 配置分段
seo-title: Configuring Segmentation
description: 了解如何为AEM Campaign配置分段。
seo-description: Learn how to configure segmentation for AEM Campaign.
uuid: f22e41b6-d9d9-4f18-9925-2d4aebc167b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 49c9c9ab-632a-40f7-8c30-d6a8c0f1b420
exl-id: 92302067-3500-41ca-9855-87f36148bfbc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 15%

---

# 配置分段{#configuring-segmentation}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>本文档介绍了与Client Context一起使用的分段配置。 要使用触屏UI通过ContextHub配置区段，请参阅 [使用ContextHub配置分段](/help/sites-administering/segmentation.md).

分段是创建营销活动时的主要考虑事项。请参阅 [分段术语表](/help/sites-authoring/segmentation-overview.md) 有关分段工作方式和关键术语的信息。

根据您收集到的有关网站访客的信息以及要实现的目标，您将需要定义目标内容所需的区段和策略。

之后，这些区段可用于为访客提供具体的目标内容。此内容在 [促销活动](/help/sites-authoring/personalization.md) 网站中的 此处定义的Teaser页面可以作为Teaser段落包含在任何页面上，并定义专用内容适用的访客区段。

AEM允许您轻松创建和更新区段、Teaser和营销活动。 它还允许您验证定义的结果。

的 **区段编辑器** 允许您轻松定义区段：

![segmenteditor-1](assets/segmenteditor-1.png)

您可以 **编辑** 每个区段指定 **标题**, **描述** 和 **提升** 因素。 使用Sidekick，您可以添加 **和** 和 **或** 用于定义 **区段逻辑**，然后添加所需的 **区段特征** 定义选择标准。

## 提升因子 {#boost-factor}

每个区段都有 **提升** 作为加权因子的参数；数字越大，表示将优先选择具有较低数字的区段。

* 最小值：`0`
* 最大值：`1000000`

## 区段逻辑 {#segment-logic}

以下逻辑容器现成可用，允许您构建区段选择的逻辑。 可以将它们从Sidekick拖到编辑器中：

<table> 
 <tbody> 
  <tr> 
   <td> AND 容器<br /> </td> 
   <td> 布尔 AND 运算符.<br /> </td> 
  </tr> 
  <tr> 
   <td> OR 容器<br /> </td> 
   <td> 布尔 OR 运算符.</td> 
  </tr> 
 </tbody> 
</table>

## 区段特征 {#segment-traits}

以下区段特征现成可用；可将它们从sidekick拖到编辑器中：

<table> 
 <tbody> 
  <tr> 
   <td> IP 范围<br /> </td> 
   <td>定义访客可以拥有的IP地址范围。<br /> </td> 
  </tr> 
  <tr> 
   <td> 页面点击<br /> </td> 
   <td>请求页面的频率。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 页面属性<br /> </td> 
   <td>访问页面的任何属性。<br /> </td> 
  </tr> 
  <tr> 
   <td> 引用关键字<br /> </td> 
   <td>与引荐网站中的信息匹配的关键词。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 脚本</td> 
   <td>要计算的Javascript表达式。<br /> </td> 
  </tr> 
  <tr> 
   <td> 区段引用 <br /> </td> 
   <td>引用其他区段定义。<br /> </td> 
  </tr> 
  <tr> 
   <td> 标记云<br /> </td> 
   <td>与所访问页面中的标记匹配的标记。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户年龄<br /> </td> 
   <td>从用户配置文件中获取。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户属性<br /> </td> 
   <td>用户配置文件中提供的任何其他信息。 </td> 
  </tr> 
 </tbody> 
</table>

您可以使用布尔运算符OR和AND组合这些特征(请参阅 [创建新区段](#creating-a-new-segment))以定义选择此区段的确切方案。

当整个语句的计算结果为true时，此区段即已解析。 在适用多个区段的情况下，也将使用 **[Boost](/help/sites-administering/campaign-segmentation.md#boost-factor)** 因素。

>[!CAUTION]
>
>区段编辑器不检查任何循环引用。例如，区段A引用了另一个区段B，而这反过来又引用了区段A。您必须确保区段不包含任何循环引用。

>[!NOTE]
>
>具有 **_i18n** 后缀由作为个性化UI clientlib一部分的脚本设置。 只有在发布时不需要UI，才会在作者上加载所有与UI相关的clientlib。
>
>因此，在创建具有此类属性的区段时，通常需要依赖 **browserFamily** 例如，而不是 **browserFamily_i18n**.

## 创建新区段 {#creating-a-new-segment}

要定义新区段，请执行以下操作：

1. 在边栏中，选择 **工具>操作>配置**.
1. 单击 **分段** 页面，然后导航到所需的位置。
1. 创建 [新页面](/help/sites-authoring/managing-pages.md) 使用 **区段** 模板。
1. 打开新页面以查看区段编辑器：

   ![screen_shot_2012-02-02at101726am](assets/screen_shot_2012-02-02at101726am.png)

1. 使用Sidekick或上下文菜单(通常单击鼠标右键，然后选择 **新建……** 打开“插入新组件”窗口)以查找所需的区段特征。 然后将其拖动到 **区段编辑器** 它将显示在默认位置 **和** 容器。
1. 双击新特征以编辑特定参数；例如，鼠标位置：

   ![screen_shot_2012-02-02at103135am-1](assets/screen_shot_2012-02-02at103135am-1.png)

1. 单击 **确定** 要保存定义，请执行以下操作：
1. 您可以 **编辑** 区段定义，以为其提供 **标题**, **描述** 和 **[提升](/help/sites-administering/campaign-segmentation.md#boost-factor)** 因素：

   ![screen_shot_2012-02-02at103547am](assets/screen_shot_2012-02-02at103547am.png)

1. 根据需要添加更多特征。 您可以使用 **和容器** 和 **OR容器** 下面的组件 **区段逻辑**. 利用区段编辑器，您可以删除不再需要的特征或容器，或将它们拖动到语句中的新位置。

## 使用 AND 和 OR 容器 {#using-and-and-or-containers}

您可以在AEM中构建复杂区段。 了解以下几个基本要点：

* 定义的顶级始终是最初创建的AND容器；无法更改，但对区段定义的其余部分没有影响。
* 确保容器的嵌套有意义。可以将容器视为布尔表达式的括号。

以下示例用于选择以下任一访客：

男，16至65岁

或

女性，16至62岁

由于主运算符是OR，因此您需要从 **OR容器**. 在此中，您有2个AND语句，对于每个语句，您都需要 **和容器**，您可以在其中添加单个特征。

![screen_shot_2012-02-02at105145am-1](assets/screen_shot_2012-02-02at105145am-1.png)

## 测试区段的应用程序 {#testing-the-application-of-a-segment}

定义区段后，可借助 **[Client Context](/help/sites-administering/client-context.md)**:

1. 选择要测试的区段。
1. 按 **[Ctrl-Alt-C](/help/sites-authoring/keyboard-shortcuts.md)** 打开 **[Client Context](/help/sites-administering/client-context.md)**，显示已收集的数据。 出于测试目的，您可以 **编辑** 某些值，或 **加载** 另一个用户档案，以了解其影响。

1. 根据定义的特征，当前页面可用的数据可能与区段定义匹配，也可能与区段定义不匹配。 匹配的状态显示在定义下方。

例如，简单的区段定义可以基于用户的年龄和性别。 加载特定用户档案会显示区段已成功解析：

![screen_shot_2012-02-02at105926am-1](assets/screen_shot_2012-02-02at105926am-1.png)

或者不：

![screen_shot_2012-02-02at110019am-1](assets/screen_shot_2012-02-02at110019am-1.png)

>[!NOTE]
>
>将立即解析所有特征，尽管大多数特征仅在页面重新加载时发生变化。鼠标位置的更改会立即显示，因此可用于测试。

此类测试也可在内容页面上执行，并与 **Teaser** 组件。

Teaser段落上的鼠标悬停将显示已应用的区段，无论这些区段当前是否解析，以及选择当前Teaser实例的原因：

![chlimage_1-408](assets/chlimage_1-408.png)

## 使用区段 {#using-your-segment}

区段当前在 [促销活动](/help/sites-authoring/personalization.md). 它们用于控制特定目标受众看到的实际内容。 请参阅 [了解区段](/help/sites-authoring/segmentation-overview.md) 以了解更多信息。
