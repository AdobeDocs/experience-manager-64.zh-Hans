---
title: 使用隐藏条件
seo-title: 使用隐藏条件
description: 隐藏条件可用于确定是否渲染组件资源。
seo-description: 隐藏条件可用于确定是否渲染组件资源。
uuid: 93b4f450-1d94-4222-9199-27b5f295f8e6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 104d1c64-b9b3-40f5-8f9b-fe92d9daaa1f
translation-type: tm+mt
source-git-commit: c0c0a7223ef70d3c19954bb2fc2a92dbad8ce049
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---


# 使用隐藏条件{#using-hide-conditions}

隐藏条件可用于确定是否渲染组件资源。 例如，当模板作者在模板编辑器中配置核心 [组件列表](https://helpx.adobe.com/experience-manager/core-components/using/list.html) ，并 [决定禁用选项以基于子页面构建列表时](/help/sites-authoring/templates.md) ，就会出现这种情况。 在设计对话框中禁用此选项会设置一个属性，这样在渲染列表组件时，将评估隐藏条件，并且不显示显示子页面的选项。

## 概述 {#overview}

对话会变得非常复杂，用户可能只使用一小部分可供自己使用的选项。 这可能为用户带来无数的用户界面体验。

通过使用隐藏条件，管理员、开发人员和超级用户可以根据一组规则隐藏资源。 此功能允许他们决定在作者编辑内容时应显示哪些资源。

>[!NOTE]
>
>根据表达式隐藏资源不会替换ACL权限。 内容将保持可编辑状态，但是不显示。

## 实施和使用详细信息 {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` 负责根据属性的存在和值过滤资 `granite:hide` 源，该属性位于要过滤的字段上。 实现 `/libs/cq/gui/components/authoring/dialog/dialog.jsp` 包括 `FilteringResourceWrapper.`

该实现利用Granite ELResolver [API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html) ，并通过ExpressionCustomizer `cqDesign` 添加一个自定义变量。

以下是设计节点上隐藏条件的几个示例，该节点位于内容 `etc/design` 策略下或作为内容策略。

```
${cqDesign.myProperty}
${!cqDesign.myProperty}
${cqDesign.myProperty == 'someText'}
${cqDesign.myProperty != 'someText'}
${cqDesign.myProperty == true}
${cqDesign.myProperty == true}
${cqDesign.property1 == 'someText' && cqDesign.property2 || cqDesign.property3 != 1 || header.myHeader}
```

定义隐藏表达式时，请牢记：

* 要有效，应表示找到属性的范围(例如， `cqDesign.myProperty`)。
* 值为只读。
* 函数（如果需要）应限于服务提供的给定集合。

## 示例 {#example}

隐藏条件的示例可在AEM中找到，尤其 [是核心](https://docs.adobe.com/content/help/zh-Hans/experience-manager-core-components/using/introduction.html) 组件。 例如，考虑 [列表核心组件](https://helpx.adobe.com/experience-manager/core-components/using/list.html)。

[使用模板编辑器](/help/sites-authoring/templates.md)，模板作者可以在设计对话框中定义页面作者可以使用的列表组件选项。 例如是否允许列表为静态列表、子页面列表、标记页面列表等。 可以启用或禁用。

如果模板作者选择禁用子页面选项，则会设置设计属性并针对其评估隐藏条件，这会导致该选项不为页面作者呈现。

1. 默认情况下，页面作者可以使用列表核心组件通过选择子页面选项来构建使用子页面 **的列表**。

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 在列表核心组件的设计对话框中，模板作者可以选择“禁 **用子项** ”选项，以阻止将基于子页面生成列表的选项显示给页面作者。

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 在t下创建策略节 `/conf/we-retail/settings/wcm/policies/weretail/components/content/lis`点，属性 `disableChildren` 设置为 `true`。
1. 隐藏条件定义为对话框属性节 `granite:hid`点上e属性的值 `/conf/we-retail/settings/wcm/policies/weretail/components/content/list`

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. 从设计配 `disableChildren` 置中提取该值，表达式的 `${cdDesign.disableChildren}` 计算结果 `false`为，这意味着该选项不会作为组件的一部分呈现。

   您可以在此处将隐藏表达式视图为 `granite:hide` GitHub中 [的属性值](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/list/v1/list/_cq_dialog/.content.xml#L40)。

1. 使用列表 **组件时** ，页面作者不再呈现子页面选项。

   ![chlimage_1-221](assets/chlimage_1-221.png)

