---
title: 下载XFA或PDF表单模板
seo-title: Download an XFA or a PDF form template
description: 您可以将表单从存储库导出到本地系统，并将下载的表单迁移到新存储库。
seo-description: You can export forms from the repository to the local system and migrate the downloaded forms to new repository.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
role: Admin
exl-id: 68d881c6-7507-4018-b40e-205604221d0c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# 下载XFA或PDF表单模板 {#download-an-xfa-or-a-pdf-form-template}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如名称所示，下载操作允许您将表单从存储库导出到本地系统。 与上传操作结合使用，此操作可帮助您将表单从一个存储库迁移到另一个存储库。

在AEM Forms中，以下资产类型支持下载操作：

* 表单模板(XFA Forms)
* PDF forms
* 文档(平面PDF文件)

AEM Forms支持单独或在包含一个或多个受支持表单的文件夹中下载这些表单类型。

除了这些资产外，您还可以下载 `Resource` 资产类型（如果资产存在于文件夹中）。 提供此功能后，您可以下载XFA表单引用的资源以及表单。

## 下载一个或多个表单 {#download-one-or-more-forms}

1. 登录到AEM Forms用户界面(位于 `https://<server>:<port>/aem/forms.html`.

1. 导航到要下载的资产所在的位置。

1. 选择资产。 单击 **[!UICONTROL 下载]** ![aem6forms_download](assets/aem6forms_download.png) 图标。

   >[!NOTE]
   >
   >您只能选择一个表单进行下载。 如果要下载多个表单，则必须将其下载为文件夹。

1. 在出现的对话框中，单击 **[!UICONTROL 下载]**.

   AEM Forms会生成包含选定文件或选定文件夹的ZIP文件。

   如果您正在下载文件夹，则文件夹内受支持的资产会按其现有层次结构进行下载。

   ZIP文件将保存到 `Downloads` 文件夹。

## 上传操作的相关注意事项 {#related-considerations-for-the-upload-operation}

* 您可以将ZIP文件上传到同一存储库或其他存储库中的任何其他位置
* 文件夹中资产的层次结构将在上传操作期间保留
* 下载前对下载的资产所做的任何元数据更改都会在上传时反映出来
