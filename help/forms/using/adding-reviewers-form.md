---
title: 将提交审阅人与表单关联
seo-title: Associating submission reviewers with a form
description: 了解如何在AEM Forms中将提交审阅人与表单关联。 相关审阅人会审核通过表单门户提交的表单。
seo-description: Learn how to associate submission reviewers with a form in AEM Forms. Associated reviewers review a form submitted via forms portal.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Adaptive Forms
exl-id: b45d844e-acf9-4da2-b54e-08c67aa183a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# 将提交审阅人与表单关联  {#associating-submission-reviewers-with-a-form}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在创建表单时，您可以指定通过表单门户查看表单提交情况并提供反馈的用户。 贵组织可以收集对已提交表单的反馈和返工。

AEM Forms允许您将审阅人组与表单关联。 添加到表单审核组的用户可以查看此表单提交情况并提供反馈。

分配给表单的审阅者组只能审核指定表单的提交。

## 先决条件 {#prerequisite}

### 使用元数据架构编辑器启用自适应表单的提交审阅者组属性 {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

要将审阅人组与表单关联，请编辑自适应表单的元数据架构。 默认情况下，您无法将审核者组添加到已提交的表单中。

要编辑元数据架构，请执行以下操作：

1. 在创作模式下，在Experience Manager下，单击 **[!UICONTROL 工具> Assets >元数据架构]**.
1. 在架构Forms页面中，导航到 **[!UICONTROL Forms > Forms在AEM中创作]**.

   页面的url为：

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. 选择 **[!UICONTROL 自适应表单]** 单击 **[!UICONTROL 编辑]**.
1. 在“编辑表单”页面中，单击 **[!UICONTROL 高级]**.
1. 在高级选项卡中，拖放 **[!UICONTROL 单行文本]** 组件在“构建表单”下可用。
1. 选择添加的文本组件可查看其设置。

   在设置下，输入 `./jcr:content/metadata/form-submission-reviewer-group` 在映射到属性字段中。

   自适应表单的高级属性中的提交审核者组字段将启用，并使用您在字段标签下指定的名称。

## 将提交审阅人与表单关联 {#associating-submission-reviewers-with-a-form-1}

要将提交审阅人与自适应表单关联，请创建审阅人组并将用户添加到该组。 在表单高级属性的表单提交审核者字段下添加已创建的审核者组。\
用户组允许您将不同的提交审阅人集与不同的自适应表单相关联。 此功能可防止未经授权的用户进行提交审核。

在执行以下步骤之前，请参阅 [先决条件](/help/forms/using/adding-reviewers-form.md#prerequisite).

要创建群组并向其添加成员，请导航到 **[!UICONTROL 工具>操作>安全>组]**.\
有关更多信息，请参阅 [用户管理和服务](/help/sites-administering/security.md).\
确保将创建的组添加为现成用户组的成员： **forms-submission-reviewers**. 此用户组随AEM Forms一起提供，它可确保将用户添加为提交审阅人。

要将用户组与自适应表单关联，请执行以下操作：

1. 在创作模式下，导航到 **[!UICONTROL Forms > Forms与文档]**.
1. 使用 **[!UICONTROL 选择]** 选项以选择自适应表单，然后单击 **[!UICONTROL 查看属性]**.
1. 在表单的“属性”窗口中，单击 **[!UICONTROL 编辑]**，然后单击 **[!UICONTROL 高级]**.
1. 在提交审核者组字段中输入组，然后单击 **[!UICONTROL 完成]**.

   将显示提交审核者组字段，其中包含您在自适应表单的编辑元数据架构中指定的名称。

>[!NOTE]
>
>复制用户和表单，以确保在AEM Forms的远程实施中提供用户和表单。
>
>确保将所有用户复制为远程实施中审核用户组成员。
