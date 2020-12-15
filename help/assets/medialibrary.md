---
title: 比较AEM Assets和AEM媒体库的可用功能
description: 关于AEM Assets和AEM媒体库的常见问题，包括差异。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---


# AEM Assets 与 AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager(AEM)资产是AEM平台的一个组成部分。 这种顺畅集成被视为AEM的一个主要优势，它确保了内容作者在内容管理方面的一致性和高工作效率。

## 常见问题 {#frequently-asked-questions}

### 什么是AEM Assets?{#what-is-aem-assets}

AEM Assets是AEM Platform上的一个应用程序，它允许我们的客户在基于Web的存储库中管理其数字资产(图像、视频、文档和音频剪辑)。 AEM Assets包括元数据支持、演绎版、数字资产管理查找器和AEM Assets管理UI。

### 什么是AEM媒体库？{#what-is-the-aem-media-library}

AEM媒体库是AEM WCM内容存储库的指定部分，存储图像和其他共享资源。 媒体库使用AEM WCM的数字资产管理功能。

### 我从不属于AEM WCM的AEM Assets得到什么？{#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

只有AEM Assets的客户才能使用的独特功能有：

1. 能够提取和编辑除标题、标记和描述之外的元数据。
1. “AEM Assets管理员”，单击`siteadmin`旁边的第二个按钮即可从欢迎屏幕访问。
1. 与数字资产管理相关的所有工作流步骤，即AEM资产摄取、AEM Assets删除、AEM Assets子资产处理、AEM Assets元数据提取。
1. 包括`dam` im包空间的库。

使用这些功能需要获得有效的AEM Assets许可。

### AEM Assets是否提供单独的包？{#is-aem-assets-available-as-a-separate-package}

否. 为了简化安装和部署，所有AEM应用程序和加载项都在一个包中提供，其中包含所有功能。 这并不表示您有权使用包中的所有功能。

#### 我想编辑数字资产的元数据。 我需要AEM Assets吗？{#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

如果您计划编辑除标题、描述和标记之外的元数据，则需要授权AEM Assets。

#### 我想在导入时自动调整图像大小。 我需要AEM Assets吗？{#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

否. 调整静态图像的大小和自动工作流程驱动的转换以及管理再现的能力是AEM媒体库的一部分。 这些功能不需要AEM Assets许可证。

### 我想使用自定义的图像组件调整图像大小。 我需要AEM Assets吗？{#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

图像组件是AEM WCM的一部分。 图像组件(也由AEM Assets使用)使用的图形库是AEM平台的一部分，不需要AEM Assets许可证。

### 如果我未授权AEM Assets，如何阻止我的用户使用AEM Assets?{#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

您可以从AEM中删除所有特定于AEM Assets的工作流、组件、分类、选项和AEM Assets管理员。 这样做可防止用户意外使用您未授权的AEM Assets功能。

### 我要向页面添加图像，并要裁切和调整这些图像的大小。 我需要AEM Assets吗？{#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

对于此用例，无需购买AEM Assets，即使使用媒体库也不需要在网站上使用图像，因为智能图像组件允许将图像直接上传到页面。

>[!MORELIKETHIS]
>
>* [功能差异的详细列表](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

