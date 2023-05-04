---
title: 如何编辑或添加元数据
description: 了解中的资产元数据 [!DNL Experience Manager] 资产，以及编辑资产元数据的各种方式。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 8%

---

# 如何编辑或添加元数据 {#how-to-edit-or-add-metadata}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

元数据是有关可搜索资产的其他信息。 在您上传图像时，系统会自动提取该图像。 您可以编辑现有元数据或向现有字段添加新元数据属性（例如，当元数据字段为空时）。

因为公司需要可控且可靠的元数据词汇， [!DNL Experience Manager] 资产不允许临时添加新的元数据属性。 尽管作者无法为资产添加新的元数据字段，但开发人员可以。 请参阅 [为资产创建新元数据属性](meta-edit.md#editing-metadata-schema).

## 编辑资产的元数据 {#editing-metadata-for-an-asset}

要编辑元数据，请执行以下操作：

1. 执行下列操作之一：

   * 从资产UI中，选择资产，然后单击/点按 **[!UICONTROL 查看属性]** 图标。
   * 从资产缩略图中，选择 **[!UICONTROL 查看属性]** 快速操作。
   * 在资产页面中，单击/点按 **[!UICONTROL 查看属性]** 图标 ![信息图标](assets/do-not-localize/info_icon.png) 中。

   资产页面会显示资产的所有元数据。 此元数据在上传（摄取）到 [!DNL Experience Manager] 资产。

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. 根据需要，在各个选项卡下对元数据进行编辑，完成后，单击／点按工具栏中的 **[!UICONTROL 保存]** ，以保存更改。 单击／点 **[!UICONTROL 按关闭]** ，以返回到资产Web界面。

   >[!NOTE]
   >
   >如果文本字段为空，则不存在现有的元数据集。 您可以在字段中输入一个值，然后进行保存以添加该元数据属性。

对资产元数据所做的任何更改都会作为资产数据的一部分写回原始二进制文件。 这是通过AEM元数据回写工作流完成的。 对现有属性所做的更改(例如 `dc:title`)和新创建的属性(包括 `cq:tags`)与架构一起添加。

支持并启用XMP的回写功能，这些功能包括 [技术要求。](/help/sites-deploying/technical-requirements.md)

## 编辑元数据架构 {#editing-metadata-schema}

有关如何编辑元数据架构的详细信息，请参阅 [编辑元数据架构表单](metadata-schemas.md#editing-metadata-schema-forms).

## 在中注册自定义命名空间 [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

您可以在AEM中添加自己的命名空间。 正如存在预定义的命名空间（如cq、jcr和sling）一样，您也可以拥有用于存储库元数据和xml处理的命名空间。

1. 转到节点类型管理页面 `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. 单击或点按 **[!UICONTROL 命名空间]** 的双曲余切值。 命名空间管理页面显示在窗口中。

1. 要添加命名空间，请单击或点按 **[!UICONTROL 新建]** 在底部。
1. 在XML命名空间约定中指定自定义命名空间（以URI形式指定ID以及ID的关联前缀），然后单击或点按 **[!UICONTROL 保存]**.

## 提示和限制 {#best-practices-limitations}

* 通过触屏UI更新的元数据更改了 `dc` 命名空间。 通过HTTP API进行的任何更新都会更改 `jcr` 命名空间。 请参阅 [如何使用HTTP API更新元数据](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [关于资产中的元数据及其需求](metadata.md)

