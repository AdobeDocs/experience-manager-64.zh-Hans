---
title: 启用表单门户组件
seo-title: 启用表单门户组件
description: 开箱即用，已禁用Forms门户组件。 启用文档服务和文档服务谓词组以启用Forms门户组件。
seo-description: 开箱即用，已禁用Forms门户组件。 启用文档服务和文档服务谓词组以启用Forms门户组件。
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
translation-type: tm+mt
source-git-commit: 2abf448e0231eb6fcd9295f498a24e81e1ead11a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# 启用表单门户组件 {#enabling-forms-portal-components}

现成的表单门户组件不可用。 要使组件显示在AEM Sidekick中可用组件的列表中，请执行以下步骤：

1. 登录您网站的作者实例并打开一个AEM Sites页面。

1. 对于使用静态模板的页面，请执行以下步骤：

   1. 在页面标题中，点 ![按画布下拉框](assets/canvas-drop-down.png) > **设计** ，以在设计模式下打开页面。
   1. 点按任何组件（带蓝色边框），然 ![后点按字段级](assets/field-level.png) ，以选择包含当前组件的段落系统。
   1. 在段落系统中，点 ![按settings_icon](assets/settings_icon.png) ，打开段落系统的“编辑”对话框。
   1. 从允许的组 **[!UICONTROL 件列表]**，启用“文档服务”和“ **[!UICONTROL 文档服务]** ”谓词组 **[!UICONTROL 件的复选框]** 。 点按 **[!UICONTROL 确定]**。

1. 对于使用动态模板的页面，请执行以下步骤：

   1. 在页面标题中，点 ![按属性](assets/properties.png) > **编辑模板** ，以打开页面模板。
   1. 点按 **布局容器** ，然后点 ![按源管理](assets/FeedManagement.png)。 在允 **许的组件** 选项卡中，启用 **文档服务和文档服务谓词** ，然后 ![点按aem_6_3_forms_save](assets/aem_6_3_forms_save.png)。

>[!NOTE]
>
>您还可以通过选择这些类别中的组件，从中启用特定组件。 有关组件及其用法的详细信息，请参 [阅创建表单门户页面](/help/forms/using/creating-form-portal-page.md)[和在页面中嵌入链接组件](/help/forms/using/embedding-link-component-page.md)。

现在，文档服务和文档服务谓词组件类别在组件浏览器中可用。 对使用相同模板的所有页面启用这些组件。

## 相关文章

* [启用表单门户组件](/help/forms/using/enabling-forms-portal-components.md)
* [创建表单门户页面](/help/forms/using/creating-form-portal-page.md)
* [使用API在网页上列表表单](/help/forms/using/listing-forms-webpage-using-apis.md)
* [使用草稿和提交组件](/help/forms/using/draft-submission-component.md)
* [自定义草稿和已提交表单的存储](/help/forms/using/draft-submission-component.md)
* [将草稿和提交组件与数据库集成的示例](/help/forms/using/integrate-draft-submission-database.md)
* [自定义表单门户组件的模板](/help/forms/using/customizing-templates-forms-portal-components.md)
* [在门户上发布表单简介](/help/forms/using/introduction-publishing-forms.md)
