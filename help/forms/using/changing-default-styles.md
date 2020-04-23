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

---


# 更改HTML5表单的默认样式 {#changing-default-styles-of-html-forms}

使用HTML5功能渲染HTML5表单，使用CSS完成渲染表单的样式设置。 HTML5表单的默认外观与其PDF再现类似。 开发人员可以使用自定义CSS更改HTML5表单的默认外观。

本文提供了更改HTML5表单样式的分步信息，而“样式简介”文章包含有关HTML5表单各种样式方面的 [详细信息](/help/forms/using/css-styles.md) 。 确保在执行本文中提到的步骤之前阅读样式文章的介绍。

以下两幅图像显示了默认样式和自定义样式之间的差异。

![图片-002-small](assets/pictures-002-small.png)

## 设置表单样式 {#style-your-forms}

1. **选择用户档案以添加自定义样式**

   访问URL上的CRX DE界面：https:// **&lt;server>:&lt;port>/crx/de** ，并创建用户档案或选择现有用户档案。 要了解如何创建用户档案，请参阅 [创建新用户档案](/help/forms/using/custom-profile.md)

1. **创建用于设置HTML5表单样式的CSS样式表**

   导览至创建用户档案渲染器的文件夹并创建CSS样式表文件。 要执行的步骤包括

   1. 右键单击文件夹，然后从菜 **单中选择** “创建 **文件** ”->“创建文件”
   要了解要在HTML5表单中为特定组件创建哪些CSS类，请参 [阅样式介绍](/help/forms/using/css-styles.md)。

1. **在“用户档案渲染器”中包含样式表**

   在CRX DE中打开“用户档案渲染器”页（jsp文件），并将CSS文件包含在XFA客户端库正下方的页面中。 执行这些步骤以将CSS文件包含在用户档案中。

   1. 在渲染器页面中搜索以下行：

      &lt;cq:includeClientLib类别=&quot;xfaforms.用户档案&quot; />

   1. 在上面的行下方插入以下内容以包含样式表：

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. 保存文件。

