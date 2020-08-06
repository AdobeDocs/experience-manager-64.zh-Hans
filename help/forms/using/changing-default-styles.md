---
title: 更改HTML5表单的默认样式
seo-title: 更改HTML5表单的默认样式
description: HTML5表单样式基于CSS。 您可以更改表单的默认样式。
seo-description: HTML5表单样式基于CSS。 您可以更改表单的默认样式。
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# 更改HTML5表单的默认样式 {#changing-default-styles-of-html-forms}

使用HTML5功能渲染HTML5表单，使用CSS完成渲染表单的样式设置。 HTML5表单的默认外观与其PDF再现类似。 开发人员可以使用自定义CSS更改HTML5表单的默认外观。

本文提供更改HTML5表单样式的分步信息，“样式 [简介](/help/forms/using/css-styles.md) ”文章包含有关HTML5表单各种样式方面的详细信息。 确保在执行本文所述的步骤之前阅读样式文章的简介。

以下两幅图像显示了默认样式和自定义样式之间的差异。

![图片-002-small](assets/pictures-002-small.png)

## 设置表单样式 {#style-your-forms}

1. **选择用户档案以添加自定义样式**

   访问URL上的CRX DE界面： **https://&lt;server>:&lt;port>/crx/de** ，创建用户档案或选择现有用户档案。 要了解如何创建用户档案，请参 [阅创建新用户档案](/help/forms/using/custom-profile.md)

1. **创建用于设置HTML5表单样式的CSS样式表**

   导览至创建用户档案渲染器的文件夹，并创建CSS样式表文件。 要执行的步骤包括

   1. 右键单击文件夹，然后从 **菜单中选择** “创建 **”-** >“创建文件”。
   要了解要在HTML5表单中为特定组件创建哪些CSS类，请参 [阅样式介绍](/help/forms/using/css-styles.md)。

1. **在用户档案渲染器中包含样式表**

   在CRX DE中打开“用户档案渲染器”页（jsp文件），并在XFA客户端库正下方的页面中包含CSS文件。 执行这些步骤以将CSS文件包含在用户档案中。

   1. 在渲染器页面中搜索以下行：

      &lt;cq:includeClientLib类别=&quot;xfaforms.用户档案&quot; />

   1. 在上面的行下面插入以下内容以包含样式表：

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. 保存文件。

