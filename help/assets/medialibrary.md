---
title: 比较AEM资产和AEM媒体库中的可用功能
description: 有关AEM资产和AEM媒体库的常见问题解答，包括差异。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968

---


# AEM Assets 与 AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager(AEM)资产是AEM平台的一个组成部分。 这一顺畅集成被视为AEM的一个主要优势，可确保内容作者的内容管理一致性和高工作效率。

## 常见问题 {#frequently-asked-questions}

### 什么是AEM资产？ {#what-is-aem-assets}

AEM资产是AEM Platform上的一个应用程序，它允许我们的客户在基于Web的存储库中管理其数字资产(图像、视频、文档和音频剪辑)。 AEM资产包括元数据支持、演绎版、数字资产管理查找器和AEM资产管理UI。

### 什么是AEM媒体库？ {#what-is-the-aem-media-library}

AEM媒体库是AEM WCM内容存储库中存储图像和其他共享资源的指定部分。 媒体库使用AEM WCM的数字资产管理功能。

### 我从不属于AEM WCM的AEM资产中获得什么？ {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

仅AEM资产客户可使用的独特功能包括：

1. 能够提取和编辑除标题、标记和描述之外的元数据。
1. AEM资产管理员，可从欢迎屏幕中单击旁边的第二个按钮 `siteadmin`。
1. 与数字资产管理相关的所有工作流步骤，即AEM资产摄取、AEM资产删除、AEM资产子资产处理、AEM资产元数据提取。
1. 包括im包空 `dam` 间的库。

使用这些功能需要AEM资产的有效许可证。

### AEM资产是否可作为单独的包提供？ {#is-aem-assets-available-as-a-separate-package}

否. 为简化安装和部署，所有AEM应用程序和加载项都在一个包中提供，并包含所有功能。 这并不意味着您有权使用包中的所有功能。

#### 我想编辑数字资产的元数据。 我是否需要AEM资产？ {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

如果您计划编辑除标题、说明和标记之外的元数据，则需要为AEM资产授予许可。

#### 我想在导入时自动调整图像大小。 我是否需要AEM资产？ {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

否. 调整静态图像的大小和自动工作流驱动的转换以及管理再现的能力是AEM媒体库的一部分。 这些功能不需要AEM Assets许可证。

### 我想使用自定义的图像组件调整图像大小。 我是否需要AEM资产？ {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

图像组件是AEM WCM的一部分。 图像组件（也由AEM资产）使用的图形库是AEM平台的一部分，不需要AEM资产许可证。

### 如果我未获得AEM资产的许可，如何阻止我的用户使用AEM资产？ {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

您可以从AEM中删除所有特定于AEM资产的工作流、组件、分类、选项和AEM资产管理员。 这样做可以防止用户意外使用您未授权的AEM资产功能。

### 我要向页面添加图像，并要裁切这些图像和调整其大小。 我是否需要AEM资产？ {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

在此用例中，无需购买AEM资产，即使使用媒体库也不需要在网站上使用图像，因为智能图像组件允许将图像直接上传到页面。

>[!MORELIKETHIS]
>
>* [详细列表功能差异](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

