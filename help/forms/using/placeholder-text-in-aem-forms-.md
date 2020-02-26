---
title: 'AEM Forms中的占位符文本 '
seo-title: 'AEM Forms中的占位符文本 '
description: 占位符文本旨在帮助用户在控件没有值时输入数据。 它可以是示例值或预期格式的简短说明。
seo-description: 占位符文本旨在帮助用户在控件没有值时输入数据。 它可以是示例值或预期格式的简短说明。
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
translation-type: tm+mt
source-git-commit: a417e571d7c3b8da8f38f3d1ad814610636eabbc

---


# AEM Forms中的占位符文本 {#placeholder-text-in-aem-forms}

占位符文本表示单词或短短语。 它旨在帮助用户在控件没有值时输入数据。 占位符文本可以是示例值或预期格式的简短说明。 占位符文本在用户输入值之前显示，在用户输入或选择值时将删除它。

>[!NOTE]
>
>如果指定，占位符文本必须具有一个不包含新行字符的值。

![带有和不带占位符文本的日期组件](assets/dat-picker-place-holder-text.png)

******答：包含占位符文本** B的日期组件。不带占位符文本的日期组件

AEM Forms支持“密码”框、“日期选取器”、“数字”框和文本框字段的占位符文本。\
原生HTML5日期构件不支持占位符文本。 指定占位符文本：

1. 右键单击支持占位符文本的组件，然后单击“编 **辑”**。 将出现编辑组件对话框。

1. 打开“标 **题和文本** ”选项卡。
1. 在“占位符”文本框中指定单词或 **短短语**。 单击&#x200B;**确定**。

>[!NOTE]
>
>Microsoft Internet Explorer 9不支持占位符文本。

