---
title: 'AEM Forms中的占位符文本 '
seo-title: 'AEM Forms中的占位符文本 '
description: 占位符文本旨在在控件没有值时帮助用户输入数据。 它可以是示例值或预期格式的简要说明。
seo-description: 占位符文本旨在在控件没有值时帮助用户输入数据。 它可以是示例值或预期格式的简要说明。
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: 自适应表单
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 1%

---

# AEM Forms中的占位符文本{#placeholder-text-in-aem-forms}

占位符文本表示一个单词或短短语。 它旨在在控件没有值时帮助用户输入数据。 占位符文本可以是示例值或预期格式的简要说明。 占位符文本在用户输入值之前显示，在用户输入或选择值时，会将其删除。

>[!NOTE]
>
>如果指定占位符文本，则其值必须不包含任何新行字符。

![包含和不包含占位符文本的日期组件](assets/dat-picker-place-holder-text.png)

**A.带有** 占位符文本的日期组 **件B.** 不带占位符文本的日期组件

AEM Forms支持“密码”框、“日期选取器”、“数字”框和“文本框”字段的占位符文本。\
本机HTML5日期小组件不支持占位符文本。 要指定占位符文本，请执行以下操作：

1. 右键单击支持占位符文本的组件，然后单击&#x200B;**编辑**。 此时将出现“编辑组件”对话框。

1. 打开&#x200B;**标题和文本**&#x200B;选项卡。
1. 在&#x200B;**占位符文本框**&#x200B;中指定单词或短短语。 单击&#x200B;**确定**。

>[!NOTE]
>
>Microsoft Internet Explorer 9不支持占位符文本。
