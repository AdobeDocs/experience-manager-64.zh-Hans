---
title: 审核凭据使用信息
seo-title: Review credential use information
description: 了解如何查看凭据使用信息。
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 2%

---

# 审核凭据使用信息 {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

凭据包含描述其预期用途的信息，这些用途可通过Acrobat Reader DC扩展最终用户Web应用程序访问。 您可以使用此信息来确定安装的凭据类型（评估或生产）及其有效日期。

1. 打开Web浏览器并输入以下URL:

   http://localhost网站：*[端口]*/ReaderExtensions(其中 *[端口]* 是您的应用程序服务器的端口号)

1. 使用默认用户名和密码登录：

   用户名：管理员

   密码：密码

   >[!NOTE]
   >
   >您必须具有管理员或超级用户权限才能使用默认用户名和密码登录。 要允许其他用户访问Acrobat Reader DC扩展，请在“用户管理”中创建用户帐户，并向用户授予Acrobat Reader DC扩展的“Web应用程序”角色。

1. 从“选择凭据”列表中选择凭据别名，并查看“过期日期”和“预期使用通知”中包含的信息。

>[!NOTE]
>
>凭据的过期日期还可在管理控制台的“设置”>“信任存储管理”>“本地凭据”页面的“过期日期”下找到。
