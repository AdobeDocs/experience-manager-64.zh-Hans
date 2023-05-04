---
title: 在自适应表单中使用SOM表达式
seo-title: Using SOM expressions in adaptive forms
description: 了解如何提取自适应表单面板的SOM表达式。
seo-description: Learn how to extract SOM expressions of a panel of an adaptive form.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
feature: Adaptive Forms
exl-id: e4680ede-6a02-4b8b-8a6f-9599a05da8e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 1%

---

# 在自适应表单中使用SOM表达式 {#using-som-expressions-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自适应表单建模为AEM页面，在AEM存储库中以JCR内容结构表示。 内容结构的关键元素是guideContainer节点。 在guideContainer下，有可能包含嵌套面板和字段的rootPanel。

您可以使用脚本对象模型(SOM)来引用特定文档对象模型(DOM)中的值、属性和方法。 DOM将内存对象和属性组织在树层次结构中。 SOM表达式引用字段/绘制元素和面板。

下图描述了在向表单添加组件时，自适应表单会转换为的节点结构。 例如，您可以在根面板中添加一个面板，并在面板中添加一个在运行时转换为DOM的单选按钮。 自适应表单中单选按钮字段的SOM表达式指定为 `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![DOM树](assets/hierarchy-1.png)

自适应表单中任何元素的SOM表达式的前缀为 `guide[0].guide1[0]`. 组件在节点结构层次中的位置用于导出其SOM表达式。

![带有两个单选按钮的DOM树](assets/hierarchy_radio_button.png)

当您更改自适应表单中单选按钮的位置时，SOM表达式会发生更改。 在创作模式下，您可以使用查看SOM表达式选项在AEM Forms中查看字段或元素的SOM表达式。 当您右键单击该字段或元素时，面板上会显示选项。

![在自适应表单中提取SOM表达式](assets/som-expressions.png)

在面板中，您可以从面板工具栏访问该功能。 该功能便于自适应表单作者编写脚本。

![使用面板工具栏提取SOM表达式](assets/som-expression.png)

中列出的一些API [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) 使用元素的SOM表达式。 例如，要以自适应形式将焦点放在特定字段，请将相应的SOM表达式传递到 `getFocus`中的API `guideBridge`.
