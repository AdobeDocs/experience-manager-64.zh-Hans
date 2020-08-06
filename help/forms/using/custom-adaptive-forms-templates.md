---
title: 创建自定义自适应表单模板
seo-title: 创建自定义自适应表单模板
description: 本文介绍如何创建自定义自适应表单模板。
seo-description: 本文介绍如何创建自定义自适应表单模板。
uuid: 8f8c770f-984c-48e8-978c-7cdfcd1af95b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c6115b64-e06f-4b5e-b7f9-876553c7627f
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---


# 创建自定义自适应表单模板 {#creating-a-custom-adaptive-form-template}

## 前提条件 {#prerequisites}

* 了解AEM页面 [模板](/help/sites-authoring/templates.md) 和自 [适应表单创作](https://helpx.adobe.com/aem-forms/6-1/introduction-forms-authoring.html)

* 理解AEM客 [户端库](/help/sites-developing/clientlibs.md)

## Adaptive form template {#adaptive-form-template}

自适应表单模板是专用的AEM页面模板，具有用于创建自适应表单的某些属性和内容结构。 模板具有预配置的布局、样式和基本的初始内容结构。

创建表单后，对原始模板内容结构的任何更改不会反映在表单中。

## 默认自适应表单模板 {#default-adaptive-form-templates}

AEM快速入门提供以下自适应表单模板：

* 基本： 允许您使用左侧的选项卡布局创建多选项卡自适应表单，在该布局中，您可以按任意顺序访问选项卡。
* 基本与Adobe Sign: 允许您创建包含多个选项卡和向导的表单。 它使用左侧选项卡布局，允许您按任意顺序访问选项卡。 它使用Adobe Document Cloud设计服务进行签名和验证。
* 空白模板： 允许您创建不带任何页眉、页脚和初始内容的表单。 您可以添加文本框、按钮和图像等组件。 空白模板允许您创建可嵌入AEM站 [点页面的表单](/help/forms/using/embed-adaptive-form-aem-sites.md)。

这些模板将属 `sling:resourceType` 性设置为相应的页面组件。 页面组件呈现CQ页面，其中包含自适应表单容器，而自适应表单则呈现自适应表单。

下表枚举了模板与页面组件之间的关联：

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>模板</strong></p> </td> 
   <td><p><strong>页面组件</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/调查</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/simpleEnrommentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/base</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/tabbedEnrommentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/tabbedrent</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/afaddon/templates/advancedEnrommentTemplate</p> </td> 
   <td><p>/libs/fd/afaddon/components/page/advancedenrollment</p> </td> 
  </tr> 
 </tbody> 
</table>

## 使用模板编辑器创建自适应表单模板 {#creating-an-adaptive-form-template-using-template-editor}

您可以使用模板编辑器指定自适应表单的结构和初始内容。 例如，您希望所有表单作者在登记表单中都有几个文本框、导航按钮和提交按钮。 您可以创建一个模板，作者可以使用该模板创建与其他登记表单一致的表单。 AEM模板编辑器允许您：

* 在结构层中添加表单的页眉和页脚组件
* 提供表单的初始内容。
* 指定主题。
* 指定提交、重置和导航等操作。

有关详细信息，请参阅 [模板编辑器](/help/forms/using/template-editor.md)。

## 从CRXDE创建自适应表单模板 {#creating-an-adaptive-form-template-from-crxde}

您可以创建模板并使用它创建自适应表单，而不是使用可用的模板。 自定义模板基于引用自适应表单容器和页面元素（如页眉和页脚）的各种页面组件。

您可以使用网站的基本页面组件创建这些组件。 或者，您也可以扩展现成模板所使用的自适应表单的页面组件。

请执行以下步骤以创建自定义模板，如simpleEngrolmentTemplate。

1. 导航到创作实例上的CRXDE Lite。

1. 在/apps目录下，为应用程序创建文件夹结构。 例如，如果应用程序名称为mycompany，则创建一个具有此名称的文件夹。 通常，应用程序文件夹包含组件、配置、模板、src和安装目录。 在此示例中，创建组件、配置和模板文件夹。

1. 导览至文件夹/libs/fd/af/templates。
1. 复制节 `simpleEnrollmentTemplate` 点。
1. 导航到文件夹/apps/mycompany/templates。 右键单击它，然后选择“ **[!UICONTROL 粘贴”]**。
1. 如有必要，请重命名您复制的模板节点。 例如，将其重命名为登记模板。

1. 导航到位置/apps/mycompany/templates/engrolment-template。

1. 修改节 `jcr:title` 点的 `jcr:description` 属性和属 `jcr:content` 性，以区分模板与您复制的模板。

1. 已修 `jcr:content` 改模板的节点包含 `guideContainer` 和 `guideformtitle` 组件。 `guideContainer` 是包含自适应表单的容器。 组 `guideformtitle` 件显示应用程序名称、说明等。

   您可以包 `guideformtitle`含自定义组件或组件，而不 `parsys` 是。 例如，删除 `guideformtitle`并添加自定义组件或组 `parsys` 件节点。 确保组件 `sling:resourceType` 的属性引用组件，并且在页面文件中定义了相同的 `component.jsp` 属性。

1. 导航到位置/apps/mycompany/templates/engrolment-template/jcr:content。

1. 打开 **[!UICONTROL “属性]** ”选项卡，将属性 `cq:designPath` 的值更改为/etc/designs/mycompany。

1. 现在为类型创建/etc/designs/mycompany节 `cq:Page` 点。

## 创建自适应表单页面组件 {#create-an-adaptive-form-page-component}

自定义模板的样式与默认模板的样式相同，因为模板引用页面组件/libs/fd/af/components/page/base。 您可以在节点/apps/mycompany/ `sling:resourceType` templates/enromment-template/jcr:content中找到组件引用作为属性。 由于基础是核心产品组件，请不要修改此组件。

1. 导航到节点/apps/mycompany/templates/enrmont-template/jcr:content，将属性值修改 `sling:resourceType` 为/apps/mycompany/components/page/entrumentpage
1. 将节点/libs/fd/af/components/page/base复制到文件夹/apps/mycompany/components/page。

1. 将复制的组件重命名为 `enrollmentpage`。

1. **(仅当您已有内容页面** )如果您有网站的现有组件，请执行以 `contentpage`下步骤(a-d)。 如果您没有网站的 `contentpage`现有组件，则可 `resourceSuperType`以保留该属性以指向OOTB基页。

   1. 对于节 `enrollmentpage` 点，将属性的值设 `sling:resourceSuperType` 置为mycompany/components/page/contentpage。 组 `contentpage` 件是站点的基本页面组件。 其他页面组件可以扩展它。 删除脚本文 `enrollmentpage`件， `head.jsp`除 `content.jsp`外、和 `library.jsp`。 在本 `sling:resourceSuperType` 例中，该组 `contentpage` 件包括所有此类脚本。 页眉（包括导航栏和页脚）是从组件继承 `contentpage` 的。

   1. Open the file `head.jsp`.

      JSP文件包含该行 `<cq.include script="library.jsp"/>`。

      文 `library.jsp` 件包含客 `guide.theme.simpleEnrollment` 户端库，它包含自适应表单的样式。

      页面组 `enrollmentpage` 件有一个 `head.jsp` 专用文件，它覆 `head.jsp` 盖组件的 `contentpage` 文件。

   1. 将组件的文 `head.jsp` 件中的所 `contentpage` 有脚本包 `head.jsp` 含到组件的 `enrollmentpage` 文件。
   1. 在脚本 `content.jsp` 中，您可以添加其他页面内容或对在页面呈现时包含的其他组件的引用。 例如，如果添加自定义组 `applicationformheader`件，请确保在JSP文件中添加对该组件的以下引用：

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      同样，如果在模板节 `parsys` 点结构中添加组件，也应包括自定义组件。

## 创建自适应表单客户端库 {#creating-an-adaptive-form-client-library}

新模 `head.jsp` 板的组 `enrollmentpage` 件的文件包括客户端库 `guide.theme.simpleEnrollment`。 默认模板还使用此客户端库。 使用以下方法更改新模板中的样式：

* 定义自定义主题，并将默认主 `guide.theme.simpleEnrollment` 题替换为自定义主题。
* 在/etc/designs/mycompany下定义新的客户端库。 在jsp页中的默认主题条目后加入客户端库。 在此客户端库中包含所有被覆盖的样式和其他Java Script文件。

>[!NOTE]
>
>主题是指包含在用于渲染自适应表单的页面组件中的客户端库。 客户端库主要控制自适应表单的外观。

