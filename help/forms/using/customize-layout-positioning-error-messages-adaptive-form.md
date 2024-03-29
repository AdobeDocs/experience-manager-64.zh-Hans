---
title: 自定义自适应表单错误消息的布局和位置
seo-title: Customize layout and positioning of error messages of an adaptive form
description: 您可以自定义自适应的错误消息的布局和位置。
seo-description: You can customize layout and positioning of the error messages of an adaptive for.
uuid: 18b6d770-8b68-4aa0-b866-6325a6ceabcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: e1431ad9-3bae-4ac3-97e2-96dcbfce1f71
exl-id: a57bd3c4-2d50-4089-8279-1e403e9469bf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 1%

---

# 自定义自适应表单错误消息的布局和位置 {#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以自定义自适应表单错误消息的布局和位置。 您可以执行以下自定义：

* 自定义字段标题的位置和布局，而无需对相应的CSS属性进行任何更改
* 自定义内联错误消息的位置
* 自定义动态帮助指示器的内容
* 自定义字段组件（标题、小组件、简短描述、长描述和帮助指示器组件）的位置，而无需对相应的CSS属性进行任何更改

## 自定义字段布局 {#customize-layout-of-fields}

您可以自定义单个字段或所有字段的布局，以更改题注和错误消息的位置。 执行以下步骤以将自定义布局应用到字段：

### 自定义单个字段的布局 {#customize-layout-of-a-single-field}

执行以下步骤以将自定义布局应用于单个字段：

1. 在中打开表单 **样式** 模式。 要在样式模式下打开表单，请在页面工具栏中点按 ![画布下拉列表](assets/canvas-drop-down.png) > **样式**.
1. 在侧栏中，在 **表单对象**，选择字段并点按编辑按钮 ![edit-button](assets/edit-button.png).
1. 选择要自定义的字段的状态，并指定该状态的样式。

   ![指定字段的内联样式](assets/edit-error-state.png)

### 自定义表单所有字段的布局 {#customize-layout-of-all-the-fields-of-a-form}

借助AEM Forms，您现在可以创建主题并将其应用于表单。 主题编辑器允许您在一个位置指定表单组件的样式。 创建主题时，可在组件级别指定样式。 有关主题的更多信息，请参阅 [AEM Forms主题](/help/forms/using/themes.md).

使用主题编辑器创建主题以自定义表单中所有字段的布局。 创建主题后，请执行以下步骤以将其应用于表单：

1. 在编辑模式下打开您的表单。
1. 在编辑模式下，选择一个组件，然后点按 ![字段级别](assets/field-level.png) > **自适应表单容器**，然后点按 ![cppr](assets/cmppr.png).
1. 在侧栏中自适应表单主题下，选择使用主题编辑器创建的主题。

## 创建自定义字段布局 {#create-a-custom-field-layout}

1. 打开CRXDE lite。 默认URL为 `https://[Server]:[Port]/crx/de`.
1. 将字段布局从/libs/fd/af/layouts/field节点（例如defaultFieldLayout）复制到/apps节点（例如/apps/af-field-layout）。
1. 重命名复制的节点和defaultFieldLayout.jsp文件。 例如，errorOnRight.jsp。

1. 更改复制节点的qtip和jcr:description属性的值。 例如，将属性的值更改为Error On Right

1. 要添加新样式和行为，请在/etc节点中创建客户端库。

   例如，在/etc/af-field-layout-clientlib位置，创建节点client-library。 添加值af.field.errorOnRight的categories属性，以及使用以下代码的style.less文件：

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. 要增强外观和行为，请包括在布局文件(errorOnRight.jsp)中创建的客户端库。
1. 打开字段的编辑对话框，选择 **样式** 选项卡。 在 **配置字段布局** 下拉框中，选择新创建的布局，然后单击 **确定**.

ErrorOnRight.zip包包含用于在字段右侧显示错误消息的代码。

[获取文件](assets/erroronright.zip)
