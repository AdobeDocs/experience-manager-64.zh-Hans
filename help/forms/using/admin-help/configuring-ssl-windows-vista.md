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


# 在Windows Vista上配置SSL {#configuring-ssl-on-windows-vista}

要在Windows Vista™上配置SSL，您需要一个带RSA密钥的SSL证书进行身份验证。 您可以使用Java密钥工具创建证书。

>[!NOTE]
>
>Windows Vista无法使用DSA密钥。

您可以使用包含创建证书和密钥库所需的所有信息的单个命令运行keytool。

**创建SSL证书**

1. 在命令提示符下，导 *[航到JAVA]* HOME/bin并键入以下命令以创建证书和密钥库：

   `keytool -genkey -keyalg RSA -dname "CN=`*主机名&#x200B;*`, OU=`*组名称*`, O=`*City *名称`,L=`*City****City `, S=`***国家名称Name *`, C=`**`" -alias`**`-keypass``*key*`**`-keystore`**Country Code&quot;公司&quot;名称CretRename名*密钥重命名* `.keystore`

   >[!NOTE]
   >
   >将 *[JAVA_HOME]替换为安装JDK的目录，并将斜体文本替换为与您的环境对应的值。*

1. 键入 `changeit` 作为密码。 此密码是Java安装的默认密码，系统管理员可能已对其进行更改。

