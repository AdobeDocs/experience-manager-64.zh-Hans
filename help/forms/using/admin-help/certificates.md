---
title: 管理证书
seo-title: Managing certificates
description: 了解如何导入和导出证书以及编辑其信任设置。
seo-description: Learn how to import and export a certificate and edit its trust settings.
uuid: 46b1dbe5-517c-4294-bb52-cc6700a768e8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fd531c0-5206-4be0-a450-13e0dc806068
exl-id: b8d4f35b-dc9c-4e0a-b855-f49275d4ac1f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---

# 管理证书 {#managing-certificates}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

使用信任存储管理，您可以导入、编辑和删除您信任的服务器上用于验证数字签名和证书身份验证的证书。 您可以导入和导出任意数量的证书。 导入证书后，您可以编辑信任设置和信任存储类型。 组合信任存储类型时，请考虑以下选项：

* **使用CA进行证书身份验证的信任：** 对于CRL验证，还请选择“对身份的信任”。
* **使用ICA进行证书身份验证的信任：** 仅选择“信任”作为标识。 ICA不应受到证书身份验证的信任。 如果您信任ICA进行证书身份验证，则ICA将成为用于路径构建的CA。 如果ICA同时受到证书身份验证和身份的信任，则CA供应商证书将被忽略，因为ICA将成为CA。
* **对具有HTTP的OCSP服务器的信任：** 如果OSCP响应服务器位于HTTPs位置，则还必须选择“信任SSL连接”。 如果OSCP响应程序需要CRL验证，请确保您还选择“信任身份”。
* **Adobe根：** 请勿选择SSL连接或OCSP服务器信任存储类型。 Adobe根对于SSL连接和OCSP服务器不可信。 Adobe不颁发OCSP和SSL证书。 Adobe根被隐式信任，别名为=&quot;ADOBEROOT&quot;。

仅支持X509v3证书。 此证书类型可以以二进制DER编码文件（.cer文件）或包含同一DER编码证书(包括X509证书(以隐私增强邮件(PEM)格式)的Base64编码版本的文本文件提供。

完成签名验证所需的证书必须位于同一存储（HSM或数据库）中。

您还可以使用信任管理器API导入和删除证书。 有关详细信息，请参阅 [使用AEM表单进行编程](https://www.adobe.com/go/learn_aemforms_programming_63).

## 导入证书 {#import-a-certificate}

1. 在管理控制台中，单击 **[!UICONTROL 设置>信任存储管理>证书]**.
1. 单击导入，然后在信任存储类型下，选择以下选项之一：

   * **信任SSL连接：** 指定AEM表单可以使用证书通过SSL连接到外部系统。
   * **信任认证签名：** 指定证书在用于验证作者数字签名的文档签名操作中是可信的。
   * **签名信任：** 指定证书在非作者数字签名的文档签名操作中是可信的。
   * **信任证书身份验证：** 指定AEM Forms使用证书来使用证书或智能卡身份验证来验证用户。
   * **OCSP服务器信任：** 指定AEM表单可以使用证书连接到外部OCSP响应器
   * **身份信任：** 指定证书可用于信任除上述指定类型以外的其他信息。

   >[!NOTE]
   >
   >信任存储隐式信任Adobe根证书以进行证书验证、签名、认证签名和身份。

1. 在别名框中，键入证书的标识符。
1. 单击 **[!UICONTROL 浏览]** 找到证书，然后单击 **[!UICONTROL 确定]**.

## 导出证书 {#export-a-certificate}

1. 在管理控制台中，单击 **[!UICONTROL 设置>信任存储管理>证书]**.
1. 单击要导出的证书的别名。 的 **[!UICONTROL 证书详细信息]** 页面。
1. 单击 **[!UICONTROL 导出]**，请按照导出证书的说明操作，然后单击 **[!UICONTROL 确定]**.

## 编辑证书的信任设置和信任存储类型 {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. 在管理控制台中，单击 **[!UICONTROL 设置>信任存储管理>证书]**.
1. 单击要编辑的证书的别名。
1. 单击 **[!UICONTROL 更新证书]**.
1. 要更改证书的别名，请在别名框中键入新名称。
1. 要更新证书的信任存储类型，请选择相应的信任存储类型。
1. 要更新策略限制，请在证书策略框中键入策略信息，然后单击 **[!UICONTROL 确定]**.

## 删除证书 {#delete-a-certificate}

1. 在管理控制台中，单击 **[!UICONTROL 设置>信任存储管理>证书]**.
1. 选中要删除的证书的复选框，单击 **[!UICONTROL 删除]**，然后单击 **[!UICONTROL 确定]**.
