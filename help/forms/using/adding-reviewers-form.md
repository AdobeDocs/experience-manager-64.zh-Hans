---
title: 将提交审阅者与表单关联
seo-title: 将提交审阅者与表单关联
description: 了解如何在AEM Forms中将提交审阅者与表单相关联。 关联的审阅者会审阅通过表单门户提交的表单。
seo-description: 了解如何在AEM Forms中将提交审阅者与表单相关联。 关联的审阅者会审阅通过表单门户提交的表单。
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# 将提交审阅者与表单关联 {#associating-submission-reviewers-with-a-form}

创建表单时，您可以指定通过表单门户查看表单提交情况并提供反馈的用户。 您的组织可以收集对已提交表单的反馈和返工。

AEM Forms允许您将审阅人组与表单关联。 添加到表单审阅组的用户可以查看此表单的提交情况并提供反馈。

分配给表单的审阅者组只能审阅指定表单的提交。

## 先决条件 {#prerequisite}

### 使用元数据架构编辑器为自适应表单启用提交审阅者组属性 {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

要将审阅者组与表单关联，请编辑自适应表单的元数据架构。 默认情况下，您不能将审阅者组添加到提交的表单。

要编辑元数据架构，请执行以下操作：

1. 在创作模式中，在Experience Manager下，单击工具> **[!UICONTROL 资产>元数据架构]**。
1. 在“架构表单”页中，导航到“表 **[!UICONTROL 单”>“在AEM中创作的表单]**”。

   页面的url为：

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. 选择“ **[!UICONTROL 自适应表单]** ”，然后单 **[!UICONTROL 击“编辑”]**。
1. 在“编辑表单”页面中，单击“高 **[!UICONTROL 级”]**。
1. 在“高级”选项卡中，拖放“构建表单” **[!UICONTROL 下可用的“单行文本]** ”组件。
1. 选择添加的文本组件以查看其设置。

   在“设置”下， `./jcr:content/metadata/form-submission-reviewer-group` 在“映射到属性”字段中输入。

   自适应表单的高级属性中的提交审阅者组字段将启用您在字段标签下指定的名称。

## 将提交审阅者与表单关联 {#associating-submission-reviewers-with-a-form-1}

要将提交审阅者与自适应表单关联，请创建审阅者组并向其添加用户。 在表单的高级属性中，在表单提交审阅者字段下添加创建的审阅者组。\
用户组允许您将不同的提交审阅者集与不同的自适应表单相关联。 此功能可防止未经授权的用户进行提交审阅。

在执行以下步骤之前，请参阅入门 [项目](/help/forms/using/adding-reviewers-form.md#prerequisite)。

要创建用户组并向其添加成员，请导航到工具> **[!UICONTROL 操作>安全>组]**。\
有关详细信息，请参 [阅用户管理和服务](/help/sites-administering/security.md)。\
确保将您创建的用户组添加为现成的用户组成员：表 **单提交审阅者**。 此用户组随AEM Forms一起提供，并且它可确保将用户添加为提交审阅者。

要将用户组与自适应表单关联，请执行以下操作：

1. 在创作模式中，导航到“表 **[!UICONTROL 单”>“表单和文档”]**。
1. 使用“选 **[!UICONTROL 择]** ”选项选择自适应表单，然后单击“查 **[!UICONTROL 看属性”]**。
1. 在表单的“属性”窗口中，单击“编 **[!UICONTROL 辑]**”，然后单击“ **[!UICONTROL 高级”]**。
1. 在提交审阅者组字段中输入组，然后单击“完 **[!UICONTROL 成”]**。

   将显示提交审阅者组字段，其名称与您在自适应表单的已编辑元数据架构中指定的名称相同。

>[!NOTE]
>
>复制用户和表单，以确保在AEM Forms的远程实施中用户和表单的可用性。
>
>确保将所有用户复制为远程实施中查看用户组的成员。

