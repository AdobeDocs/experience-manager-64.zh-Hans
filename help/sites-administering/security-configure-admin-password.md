---
title: 在安装时配置管理员密码
seo-title: Configure the Admin Password on Installation
description: 了解如何在AEM安装中更改管理员密码。
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# 在安装时配置管理员密码{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

自版本6.3起，在安装新实例时，AEM允许使用命令行设置管理员密码。

对于AEM的早期版本，安装后必须更改管理员帐户的密码以及其他各种控制台的密码。

此功能添加了在安装AEM实例期间为存储库和Servlet引擎设置新管理员密码的功能，从而无需在安装后手动执行该操作。

>[!CAUTION]
>
>请注意，该功能未涵盖需要手动更改密码的Felix控制台。 有关更多信息，请参阅相关 [安全检查表部分](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## 如何使用它？ {#how-do-i-use-it}

如果您选择通过命令行安装AEM，而不是从文件系统资源管理器双击JAR，则此功能将自动触发。

从命令行运行AEM实例的常规合成是：

```shell
java -jar aem6.3.jar
```

从命令行运行实例时，您将看到在安装过程中更改管理员密码的选项：

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>只有在安装新AEM实例时，才会显示更改管理员密码的提示。

## 使用 — nointeractive标记 {#using-the-nointeractive-flag}

您还可以选择从属性文件中指定密码。 这是使用 `-nointeractive` 与 `-Dadmin.password.file` 系统属性。

以下示例：

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

密码位于 `passwordfile.properties` 文件需要具有以下格式：

```xml
admin.password = 12345678
```

>[!NOTE]
>
>如果您只需使用 `-nointeractive` 参数 `-Dadmin.password.file` 系统属性，则AEM将使用默认的管理员密码，而无需您更改密码，实质上是复制早期版本的行为。 此非交互式模式可用于使用安装脚本中的命令行进行自动安装。
