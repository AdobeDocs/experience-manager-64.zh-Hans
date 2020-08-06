---
title: 'AEM Forms占位符文本 '
seo-title: 'AEM Forms占位符文本 '
description: 占位符文本旨在帮助用户在控件没有值时输入数据。 它可以是示例值或对预期格式的简要说明。
seo-description: 占位符文本旨在帮助用户在控件没有值时输入数据。 它可以是示例值或对预期格式的简要说明。
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
translation-type: tm+mt
source-git-commit: a417e571d7c3b8da8f38f3d1ad814610636eabbc
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# AEM Forms占位符文本 {#placeholder-text-in-aem-forms}

占位符文本表示单词或短短语。 它旨在帮助用户在控件没有价值时输入数据。 占位符文本可以是示例值或预期格式的简要说明。 占位符文本在用户输入值之前显示，在用户输入或选择值时将删除该文本。

>[!NOTE]
>
>占位符文本（如果指定）必须具有不包含新行字符的值。

![包含和不包含占位符文本的日期组件](assets/dat-picker-place-holder-text.png)

**A.带占位符** 文本的日期组 **件B.** 不带占位符文本的日期组件

AEM Forms支持密码框、日期选取器、数字框和文本框字段的占位符文本。\
本机HTML5日期构件不支持占位符文本。 要指定占位符文本，请执行以下操作：

1. 右键单击支持占位符文本的组件，然后单击“编 **辑”**。 将出现编辑组件对话框。

1. 打开标 **题和文本选项** 卡。
1. 在“占位符”文本框中指 **定单词或短短语**。 单击&#x200B;**确定**。

>[!NOTE]
>
>Microsoft Internet Explorer 9不支持占位符文本。

