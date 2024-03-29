---
title: 为表单字段创作上下文内帮助
seo-title: Authoring in-context help for form fields
description: AEM Forms允许您将上下文内帮助作为文本或富媒体（包括视频）添加到自适应表单字段和面板。
seo-description: AEM Forms allows you to add in-context help to adaptive form fields and panels, as text or rich media, including videos.
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
feature: Adaptive Forms
exl-id: 0c761c0c-fbe4-4129-8a90-c4ef1127a762
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 1%

---

# 为表单字段创作上下文内帮助 {#authoring-in-context-help-for-form-fields}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

有时，填写表单的最终用户不确定如何填写特定表单字段的详细信息。 为解决此类问题，自适应表单支持向表单字段添加文本或富上下文帮助。 它有助于改善表单填写体验，并避免最终用户出现任何歧义。

本文讨论了在创作自适应Forms时，表单作者如何添加上下文内帮助。

## 添加上下文帮助 {#add-in-context-help}

您可以使用侧栏属性选项卡的“帮助内容”部分中的以下选项指定上下文内帮助。

* [简短描述](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [长描述](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![表单字段的上下文帮助](assets/descriptions.png)

>[!NOTE]
>
>长描述将覆盖短描述。 如果同时指定了这两者，则只会显示“长描述”。

### 简短描述 {#short-description}

简短描述字段用于提供有关填写表单字段的快速提示和简短提示。 将鼠标悬停在“简短描述”字段上时，在该字段中指定的文本将显示为工具提示。

![有关为表单字段添加上下文内帮助的简短说明](assets/tooltip.png)

>[!NOTE]
>
>选择 **始终显示简短描述** ，以在字段下永久显示帮助文本。

![字段下的永久短上下文帮助](assets/short1.png)

### 长描述 {#long-description}

作为上下文帮助，您可以使用长描述字段指定长文本或嵌入富媒体内容（包括视频）。 例如，下图显示了如何作为上下文帮助嵌入视频。

![将富媒体添加为表单字段的上下文帮助](assets/long-descriptions.png)

添加长描述将显示 **?** 图标。 单击图标可显示在长描述部分中添加的内容。

![富媒体上下文内帮助示例](assets/photoshop.png)

### 面板级帮助 {#panel-level-help}

除了表单字段的上下文内帮助之外，您还可以在面板编辑对话框的帮助内容选项卡中在面板级别指定帮助。

![为表单面板添加上下文内帮助](assets/panel-level-help.png)

为面板添加帮助时，将显示 **?** 图标。 单击图标可显示在面板编辑对话框的“帮助内容”部分添加的内容。

![表单面板级别的上下文内帮助示例](assets/photoshop-1.png)
