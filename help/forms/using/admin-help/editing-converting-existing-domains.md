---
title: 编辑和转换现有域
seo-title: Editing and converting existing domains
description: 了解如何从域管理页面更改现有域的设置。 将现有企业域转换为混合域，或将混合域转换为混合域。
seo-description: Learn how to change the settings for existing domains from the Domain Management page. Convert an existing enterprise domain to a hybrid domain or vice versa.
uuid: 4cc9547e-b4ec-4588-b1cf-18720f06149a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 44dec184-3ef7-4ba6-a87f-ad171d3cb188
exl-id: 07ca7715-f7b3-40e0-95bc-e05f0662ed08
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# 编辑和转换现有域{#editing-and-converting-existing-domains}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以从“域管理”页面更改现有域的设置。 您还可以将现有企业域转换为混合域。

## 编辑现有域 {#edit-an-existing-domain}

1. 在管理控制台中，单击设置>用户管理>域管理。
1. 单击要编辑的域名。
1. 要更改域名，请在“名称”(Name)框中更改文本。
1. 要更改企业域或混合域的身份验证信息，请单击页面底部的相应身份验证名称。 在“编辑身份验证”页面上，根据需要更改设置。 (请参阅 [身份验证设置](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. 要更改企业域的目录信息，请单击页面底部的相应目录名称。 在“编辑目录”页面中，根据需要更改设置。 (请参阅 [添加目录或自定义SPI](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. 完成更改后，单击确定。

## 将企业域转换为混合域 {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. 在管理控制台中，单击设置>用户管理>域管理。
1. 单击要转换的企业域名称。
1. 单击转换为混合域。
1. 查看显示的有关用户和组数据以及用户身份验证的信息，然后单击确定。
1. 编辑混合域的设置，然后单击“确定”。

>[!NOTE]
>
>如果要转换的企业域不包含目录设置，则任何LDAP身份验证设置都将丢失。

## 将混合域转换为企业域 {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. 在管理控制台中，单击设置>用户管理>域管理。
1. 单击要转换的混合域的名称。
1. 单击转换到企业域。
1. 查看显示的有关用户和组数据以及用户身份验证的信息，然后单击确定。
1. 单击“添加目录”并配置所需的目录信息。 (请参阅 [添加目录或自定义SPI](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
