---
title: 根据使用的模板显示组件
seo-title: Displaying components based on the template used
description: 创建表单时，了解如何根据所选模板在侧栏中启用组件。
seo-description: When you create a form, learn how you can enable components in the sidebar based on the template selected.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
exl-id: a4cee2e6-a56f-4355-8176-b3ed7478a775
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 2%

---

# 根据使用的模板显示组件 {#displaying-components-based-on-the-template-used}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

当表单作者使用 [模板](/help/forms/using/template-editor.md)，则表单作者可以根据模板策略查看和使用特定组件。 您可以指定模板内容策略，以便选择表单作者在创作表单时看到的组件组。

## 更改模板的内容策略 {#changing-the-content-policy-of-a-template}

创建模板时，会在 `/conf` 在内容存储库中。 基于您在 `/conf` 目录，模板的路径是： `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

根据模板的内容策略，执行以下步骤以在侧栏中显示组件：

1. 打开CRXDE lite。

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. 在CRXDE中，导航到创建模板的文件夹。

   例如：`/conf/<your-folder>/`

1. 在CRXDE中，导航到： `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   要选择一组组件，需要新的内容策略。 要创建新策略，请复制并粘贴默认策略，然后对其重命名。

   默认内容策略的路径是： `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   在 `gridFluidLayout` 文件夹中，复制并粘贴默认策略，然后对其进行重命名。 例如：`myPolicy`。

   ![复制默认策略](assets/crx-default1.png)

1. 选择您创建的新策略，然后选择 **组件** 右侧面板中的属性（类型） `string[]`.

   选择并打开组件属性后，您会看到编辑组件对话框。 在编辑组件对话框中，您可以使用 **+** 和 **-** 按钮。 您可以添加组件组，其中包含您希望作者使用的表单中的组件。

   ![在策略中添加或删除组件](assets/add-components-list1.png)

   添加组件组后，单击 **确定** 要更新列表，请单击 **全部保存** 并刷新。

1. 在模板中，将内容策略从默认更改为您创建的新策略。 ( `myPolicy` )。

   要更改策略，请在CRXDE中，导航到 `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   在 `cq:policy` 属性，更改 `default` 到新策略名称( `myPolicy`)。

   ![更新了模板内容策略](assets/updated-policy.png)

   使用模板创建表单时，您可以在侧栏中看到添加的组件。
