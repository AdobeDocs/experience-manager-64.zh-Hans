---
title: 在Windows Vista上配置SSL
seo-title: Configuring SSL on Windows Vista
description: 了解如何在Windows Vista上配置SSL。
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 在Windows Vista上配置SSL {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

要在Windows Vista™上配置SSL，您需要一个包含RSA密钥的SSL证书进行身份验证。 您可以使用Java密钥工具创建证书。

>[!NOTE]
>
>Windows Vista无法与DSA密钥配合使用。

您可以使用包含创建证书和密钥库所需的所有信息的单个命令来运行密钥工具。

**创建SSL证书**

1. 在命令提示符下，导航到 *[JAVA主页]*/bin并键入以下命令以创建证书和密钥库：

   `keytool -genkey -keyalg RSA -dname "CN=`*主机名* `, OU=`*群组名称* `, O=`*公司名称* `,L=`*城市******名称* `, S=`*州* `, C=`*国家/地区代码* `" -alias`*&quot;LC证书&quot;* `-keypass` `*key*`*_**密码* `-keystore`*密钥重命名* `.keystore`

   >[!NOTE]
   >
   >替换 *[JAVA_HOME] 使用安装JDK的目录，并将斜体文本替换为与您的环境对应的值。*

1. 类型 `changeit` 作为密码。 此密码是Java安装的默认密码，系统管理员可能已更改此密码。
