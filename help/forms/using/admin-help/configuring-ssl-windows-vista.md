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

---


# 在Windows Vista上配置SSL {#configuring-ssl-on-windows-vista}

要在Windows Vista™上配置SSL，您需要一个带有RSA密钥的SSL证书以进行身份验证。 可以使用Java密钥工具创建证书。

>[!NOTE]
>
>Windows Vista无法与DSA密钥配合使用。

您可以使用一个命令运行keytool，该命令包含创建证书和密钥库所需的所有信息。

**创建SSL证书**

1. 在命令提示符下，导航到 *[JAVA HOME]*/bin并键入以下命令以创建证书和密钥库：

   `keytool -genkey -keyalg RSA -dname "CN=`*名称&#x200B;*Group Name Group NameName`, OU=`*Company Name* S `, O=`** State NameAnmeS*CountryNameAnATheCort“CERT”Cret Cert Cort_Stored:CrenameCrename*Ct *Ct.Ct.`,L=`**`, S=`**`, C=`**`" -alias`**`-keypass``*key*`**`-keystore`** 重命名。Ct. `.keystore`

   >[!NOTE]
   >
   >将 *[JAVA_HOME]替换为安装JDK的目录，并将斜体文本替换为与您的环境相对应的值。*

1. 键 `changeit` 入密码。 此密码是Java安装的默认密码，系统管理员可能已更改了该密码。

