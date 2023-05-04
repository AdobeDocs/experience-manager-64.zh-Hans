---
title: 更改HTML5表单的默认样式
seo-title: Changing default styles of HTML5 forms
description: HTML5表单样式基于CSS。 您可以更改表单的默认样式。
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# 更改HTML5表单的默认样式 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

HTML5表单使用HTML5功能进行渲染，并且渲染的表单的样式是使用CSS完成的。 HTML5表单的默认外观与其PDF呈现版本类似。 开发人员可以使用自定义CSS更改HTML5表单的默认外观。

本文提供了用于更改HTML5表单样式的分步信息，以及 [样式简介](/help/forms/using/css-styles.md) 文章包含有关HTML5表单各种样式方面的详细信息。 在执行本文中所述的步骤之前，请确保已阅读样式文章简介。

以下两幅图像显示了默认样式与自定义样式之间的差异。

![图片–002小](assets/pictures-002-small.png)

## 设置表单样式 {#style-your-forms}

1. **选择用于添加自定义样式的配置文件**

   在URL中访问CRX DE界面： **https://&lt;server>:&lt;port>/crx/de** 创建用户档案或选择现有用户档案。 要了解如何创建用户档案，请参阅 [创建新用户档案](/help/forms/using/custom-profile.md)

1. **创建CSS样式表以为HTML5表单设置样式**

   导航到在其中创建配置文件渲染器并创建CSS样式表文件的文件夹。 要遵循的步骤包括

   1. 右键单击文件夹并选择 **创建** -> **创建文件** 菜单
   要了解要为HTML5表单中的特定组件创建的CSS类，请参阅 [样式简介](/help/forms/using/css-styles.md).

1. **在“配置文件渲染器”中包含样式表**

   在CRX DE中打开“配置文件渲染器”页面（jsp文件），并将CSS文件包含在XFA客户端库正下方的页面中。 执行这些步骤以将CSS文件包含在配置文件中。

   1. 在渲染器页面中搜索以下行：

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. 在上面的行下方插入以下内容以包含样式表：

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. 保存文件。
