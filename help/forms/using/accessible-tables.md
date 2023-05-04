---
title: 在HTML5表单中创建可访问的复杂表
seo-title: Create accessible complex tables in HTML5 forms
description: 了解如何在HTML5表单中创建无障碍表。
seo-description: Learn how to create accessible tables in HTML5 forms.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: Mobile Forms
exl-id: a3337bb1-635c-4dc9-b438-3a829d4a9e03
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 1%

---

# 在HTML5表单中创建可访问的复杂表 {#create-accessible-complex-tables-in-html-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

HTML5 Forms中表的默认实施使用HTMLDIV元素来呈现表。 呈现涉及使用ARIA角色来满足无障碍性要求。

为避免屏幕阅读器存在的辅助功能问题，这些屏幕阅读器不完全支持与数据表一起使用的ARIA角色，HTML5 Forms为表提供了替代呈现版本。 这些表基于Designer中引入的新表格式，该格式还支持：

* 行标题
* 行范围

要在HTML5 Forms中使用新格式，请将表标记为复杂。 要将表标记为复杂，请添加 `extras` 标记，如下所示：

```
</extras>
 <text name="complexTable">1</text>
 </extras>
```

标记为 *complexTable* 遵循本机HTML呈现版本，并为某些屏幕阅读器提供更好的辅助功能支持。  要创建行范围，请选择同一列中表的连续单元格，右键单击所选内容，然后单击 **[!UICONTROL 合并单元格]**.

***注意：**创建行跨度仅适用于最左侧的单元格。*

要将行标记为行标题，请选择行中的所有单元格，右键单击所选内容，然后单击 **[!UICONTROL 标记标题]**.

要将单元格标记为列标题，请选择列中的任意单元格，右键单击所选内容，然后单击 **[!UICONTROL 标记标题]**.

新 *可访问表* 格式：

* 如果表中使用了rowspan，则不支持可扩展字段
* 不支持嵌套表（表单元格中的表）
* 对行跨度的支持仅限于标题行和标题单元格
* 支持仅限于常规表格
* 不支持在行数> 1的表中预填充数据
