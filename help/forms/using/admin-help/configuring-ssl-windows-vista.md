---
title: 在Windows Vista上配置SSL
seo-title: 在Windows Vista上配置SSL
description: 了解如何在Windows Vista上配置SSL。
seo-description: 了解如何在Windows Vista上配置SSL。
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# 在Windows Vista {#configuring-ssl-on-windows-vista}上配置SSL

要在Windows Vista™上配置SSL，您需要一个带RSA密钥的SSL证书进行身份验证。 您可以使用Java密钥工具创建证书。

>[!NOTE]
>
>Windows Vista无法使用DSA密钥。

您可以使用包含创建证书和密钥库所需的所有信息的单个命令运行keytool。

**创建SSL证书**

1. 在命令提示符下，导航到&#x200B;*[JAVA HOME]*/bin并键入以下命令以创建证书和密钥库：

   `keytool -genkey -keyalg RSA -dname "CN=`*主机* `, OU=`*名* `, O=`*组名* `,L=`*称公司名称城*&#x200B;市 `, S=`** `, C=`******名称*国家／地* `" -alias`*区代码&quot;LC证书* `-keypass` `*key*`&quot;*_*** `-keystore`*密码密钥重命名* `.keystore`

   >[!NOTE]
   >
   >将&#x200B;*[JAVA_HOME]替换为安装JDK的目录，并将斜体文本替换为与您的环境对应的值。*

1. 键入`changeit`作为密码。 此密码是Java安装的默认密码，系统管理员可能已对其进行更改。

