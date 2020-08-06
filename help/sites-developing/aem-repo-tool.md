---
title: AEM Repo工具
seo-title: AEM Repo工具
description: AEM Repo Tool是一种简单的解决方案，可通过与FTP类似的命令行在本地文件系统和AEM服务器之间传输JCR内容。 AEM Repo Tool与Jackrabbit FileVault工具类似，但速度更快，相关性最小，是一个简单的bash脚本。
seo-description: AEM Repo Tool是一种简单的解决方案，可通过与FTP类似的命令行在本地文件系统和AEM服务器之间传输JCR内容。 AEM Repo Tool与Jackrabbit FileVault工具类似，但速度更快，相关性最小，是一个简单的bash脚本。
uuid: 6c4a3504-e8e8-46c0-83cb-c18d9791f93e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 7de7b2f9-770e-4af3-8a31-c7b4de64fd43
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# AEM Repo工具{#aem-repo-tool}

AEM Repo Tool是一种简单的解决方案，可通过与FTP类似的命令行在本地文件系统和AEM服务器之间传输JCR内容。 AEM Repo Tool与Jackrabbit FileVault工 [具类似](/help/sites-developing/ht-vlttool.md)，但速度更快，相关性最小，是一个简单的bash脚本。

此工具为开发人员简化了文件传输，还可集成到IntelliJ和Eclipse中，使开发更高效。

## 概述 {#overview}

对于文件系统上文件 `jcr_root` 结构内的给定路径，AEM Repo Tool会为整个子树创建一个具有单一过滤器的包，并将其推送到服务器(类似于FTP `put`)，从服务器( `get`)获取它或比较差 `status` 异(和 `diff`)。

该工具不支持多个过滤器路径或FileVault的过滤器 `filter.xml`。

>[!CAUTION]
>
>请注意，AEM Repo Tool将始终覆盖指定的整个文件或目录。

## 下载和文档 {#download-and-documentation}

AEM [Repo Tool可通过此链接](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) ，以及详细的安装和使用说明。

如果您希望下载AEM Repo Tool的源，请参阅下面链接的GitHub项目。

GITHUB上的代码

您可以在GitHub上找到此页面的代码

* [在GitHub上打开工具项目](https://github.com/Adobe-Marketing-Cloud/tools)
* 以ZIP文件的 [形式下载项目](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)

