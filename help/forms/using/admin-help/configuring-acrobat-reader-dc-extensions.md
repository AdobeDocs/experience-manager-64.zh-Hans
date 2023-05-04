---
title: 为数据捕获配置Acrobat Reader DC扩展
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: 了解如何配置Acrobat Reader DC扩展以进行数据捕获。
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# 为数据捕获配置Acrobat Reader DC扩展 {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如果AEM Forms安装的用户使用Content Services的数据捕获功能（已弃用），则建议您为这些用户创建具有只读访问权限的角色。

***注释**:Adobe®LiveCycle® Content Services ES（已弃用）是随LiveCycle一起安装的内容管理系统。 它使用户能够设计、管理、监控和优化以人为中心的流程。 内容服务（已弃用）支持将于12/31/2014终止。

数据捕获要求您分配用户角色以访问SampleReaderExtensionsCredential。 您可以分配标准的“信任管理员”角色，但请考虑，此角色为一般的非管理用户提供了强大的管理员权限，这些权限可以控制PKI信任设置和管理PKI凭据，这可能会危及您在生产环境中安装AEM表单的安全性。 建议AEM Forms系统管理员创建一个仅授予信任存储的只读访问权限的角色，并将此新角色分配给使用数据捕获的非管理员用户。

## 为数据捕获用户创建角色 {#create-a-role-for-data-capture-users}

1. 在管理控制台中，单击设置>用户管理>角色管理，然后单击新建角色。
1. 在相应字段中输入角色名称（例如，Data Capture User）和说明，然后单击“下一步”。
1. 在角色权限屏幕上，单击查找权限，然后从可用权限列表中选择凭据读取。
1. 单击“确定”，然后单击“完成”。

## 分配数据捕获角色 {#assign-the-data-capture-role}

1. 在管理控制台中，单击设置>用户管理>角色管理，然后单击查找。
1. 单击您创建的数据捕获用户角色。
1. 在角色用户/群组选项卡上，单击查找用户/群组。
1. 在“查找用户和群组”屏幕上，单击“查找”，选择需要数据捕获用户角色的用户，然后单击“确定”。
1. 在“编辑角色”屏幕上，单击“保存”。
