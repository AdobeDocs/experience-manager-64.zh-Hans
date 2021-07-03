---
title: 如何编辑或添加元数据
description: 了解AEM Assets中的资产元数据，以及编辑资产元数据的各种方式。
contentOwner: AG
feature: 元数据
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 8%

---

# 如何编辑或添加元数据 {#how-to-edit-or-add-metadata}

元数据是有关可搜索资产的其他信息。 在您上传图像时，系统会自动提取该图像。 您可以编辑现有元数据或向现有字段添加新元数据属性（例如，当元数据字段为空时）。

由于公司需要可控且可靠的元数据词汇，因此AEM Assets不允许临时添加新的元数据属性。 尽管作者无法为资产添加新的元数据字段，但开发人员可以。 请参阅[为资产创建新元数据属性](meta-edit.md#editing-metadata-schema)。

## 编辑资产的元数据 {#editing-metadata-for-an-asset}

要编辑元数据，请执行以下操作：

1. 执行下列操作之一：

   * 从资产UI中，选择资产，然后单击/点按工具栏中的&#x200B;**[!UICONTROL 查看属性]**&#x200B;图标。
   * 从资产缩略图中，选择&#x200B;**[!UICONTROL 查看属性]**&#x200B;快速操作。
   * 在资产页面中，单击/点按工具栏中的&#x200B;**[!UICONTROL 查看属性]**&#x200B;图标![信息图标](assets/do-not-localize/info_icon.png)。

   资产页面会显示资产的所有元数据。 此元数据在上传（摄取）到AEM Assets后会自动提取。

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. 根据需要，在各个选项卡下对元数据进行编辑，完成后，单击／点按工具栏中的 **[!UICONTROL 保存]** ，以保存更改。 单击／点 **[!UICONTROL 按关闭]** ，以返回到资产Web界面。

   >[!NOTE]
   >
   >如果文本字段为空，则不存在现有的元数据集。 您可以在字段中输入一个值，然后进行保存以添加该元数据属性。

对资产元数据所做的任何更改都会作为资产数据的一部分写回原始二进制文件。 这是通过AEM元数据回写工作流完成的。 对现有属性（如`dc:title`）所做的更改会被覆盖，新创建的属性（包括自定义属性，如`cq:tags`）会与架构一起添加。

[技术要求中描述的平台和文件格式支持并启用XMP回写。](/help/sites-deploying/technical-requirements.md)

## 编辑元数据架构 {#editing-metadata-schema}

有关如何编辑元数据架构的详细信息，请参阅[编辑元数据架构表单](metadata-schemas.md#editing-metadata-schema-forms)。

## 在AEM中注册自定义命名空间 {#registering-a-custom-namespace-within-aem}

您可以在AEM中添加自己的命名空间。 正如存在预定义的命名空间（如cq、jcr和sling）一样，您也可以拥有用于存储库元数据和xml处理的命名空间。

1. 转到节点类型管理页面`https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`。
1. 单击或点按页面顶部的&#x200B;**[!UICONTROL 命名空间]**。 命名空间管理页面显示在窗口中。

1. 要添加命名空间，请单击或点按底部的&#x200B;**[!UICONTROL New]**。
1. 在XML命名空间约定中指定自定义命名空间（以URI的形式指定ID以及该ID的关联前缀），然后单击或点按&#x200B;**[!UICONTROL Save]**。

## 提示和限制 {#best-practices-limitations}

* 通过触屏UI更新的元数据更改了`dc`命名空间中的元数据属性。 通过HTTP API进行的任何更新都会更改`jcr`命名空间中的元数据属性。 请参阅[如何使用HTTP API](/help/assets/mac-api-assets.md#update-asset-metadata)更新元数据。

>[!MORELIKETHIS]
>
>* [关于资产中的元数据及其需求](metadata.md)

