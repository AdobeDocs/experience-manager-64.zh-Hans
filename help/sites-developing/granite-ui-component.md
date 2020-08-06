---
title: 创建新的Granite UI字段组件
seo-title: 创建新的Granite UI字段组件
description: Granite UI提供一系列设计用于表单的组件，称为字段
seo-description: Granite UI提供一系列设计用于表单的组件，称为字段
uuid: cf26e057-4b0c-45f4-8975-2c658517f20e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 94b9eeee-aae3-4b28-9d6f-1be0e4acd982
translation-type: tm+mt
source-git-commit: 26b7692b839e8395d090137e4f85b008171bbfc0
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# 创建新的Granite UI字段组件{#creating-a-new-granite-ui-field-component}

Granite UI提供一系列设计用于表单的组件； 这些词在 *Granite* UI词汇中称为字段。 标准的Granite表单组件可从以下位置获得：

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>这些Granite UI表单字段用于组件对话框时特别 [受关注](/help/sites-developing/developing-components.md)。

>[!NOTE]
>
>有关字段的完整详细信息，请参 [阅Granite UI文档](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)。

使用Granite UI Foundation框架开发和／或扩展Granite组件。 它包含两个元素：

* 服务器端：

   * 基础组件集合

      * 基础——模块化、可合成、可分类、可重用
      * 组件——吊具组件
   * 帮助应用程序开发的帮助者


* 客户端：

   * 一个客户端库集合，提供一些词汇（即HTML语言的扩展），通过超媒体驱动的UI实现通用交互模式

通用Granite UI组 `field` 件由两个感兴趣的文件组成：

* `init.jsp`: 处理通用处理； 标记、描述并提供呈现字段时需要的表单值。
* `render.jsp`: 这是执行字段实际呈现的地方，并且需要覆盖自定义字段； 包含 `init.jsp`。

如需更多详 [细信息，请参阅Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) UI文档——字段。

有关示例，请参阅：

* `cqgems/customizingfield/components/colorpicker`

   * 由代码示 [例提供](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>由于此机制使用JSP，因此i18n和XSS不是现成的。 这意味着您需要国际化并摆脱字符串。 以下目录包含标准实例中的通用字段，您可以将这些字段用作引用：
>
>`/libs/granite/ui/components/foundation/form` 目录

## 为组件创建服务器端脚本 {#creating-the-server-side-script-for-the-component}

您的自定义字段应仅覆 `render.jsp` 盖脚本，您在该脚本中为组件提供标记。 您可以将JSP（即渲染脚本）视为标记的包装器。

1. 创建使用属性继承 `sling:resourceSuperType` 的新组件：

   `/libs/granite/ui/components/foundation/form/field`

1. 覆盖脚本：

   `render.jsp`

   在此脚本中，您需要生成超媒体标记（即包含超媒体支付的富集标记），以便客户端知道如何与生成的元素交互。 这应遵循Granite UI服务器端的编码样式。

   自定义时，您必须履行的唯 *一合同* ，是使用以下方式从请求中读取(在 `init.jsp`中初始化)表单值：

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class"); 
   ```

   有关详细信息，请参阅开箱即用的Granite UI字段的实现； 例如 `/libs/granite/ui/components/foundation/form/textfield`,

   >[!NOTE]
   >
   >目前，JSP是首选的脚本编写方法，因为在HTL中很难实现将信息从一个组件传递到另一个组件（在表单／字段的上下文中比较频繁）。

## 为组件创建客户端库 {#creating-the-client-library-for-the-component}

要向组件添加特定的客户端行为，请执行以下操作：

1. 创建类别的clientlib `cq.authoring.dialog`。
1. 创建类别的clientlib `cq.authoring.dialog` 并在其中 `JS`定义 `CSS` 您的/。

   在clientlib中 `JS`定 `CSS` 义您的/。

   >[!NOTE]
   >
   >目前，Granite UI不提供可直接用于添加JS行为的现成监听器或挂钩。 因此，要向组件添加其他JS行为，您必须对自定义类实施JS挂接，然后在标记生成过程中将其分配给组件。

