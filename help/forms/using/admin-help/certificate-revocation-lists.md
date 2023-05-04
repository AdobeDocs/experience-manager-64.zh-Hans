---
title: 管理证书缩写列表
seo-title: Managing certificate revocationlists
description: 了解如何管理证书吊销列表。
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%

---

# 管理证书缩写列表{#managing-certificate-revocationlists}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

使用信任存储管理，您可以导入、编辑和删除证书吊销列表(CRL)。 支持Base64和DER编码的证书吊销列表。

## 导入CRL {#import-a-crl}

1. 在管理控制台中，单击设置>信任存储管理>证书吊销列表，然后单击导入。
1. 在别名框中，键入CRL的标识符。
1. 单击浏览以找到CRL，然后单击确定。

## 导出CRL {#export-a-crl}

1. 在管理控制台中，单击设置>信任存储管理>证书吊销列表。
1. 单击要导出的CRL的别名，然后单击“导出”。
1. 按照说明导出CRL。 CRL以Base64编码导出。
1. 单击确定。

## 删除CRL {#delete-a-crl}

1. 在管理控制台中，单击设置>信任存储管理>证书吊销列表。
1. 选中要删除的CRL的复选框，单击“删除”，然后单击“确定”。
