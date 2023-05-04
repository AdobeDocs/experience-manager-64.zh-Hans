---
title: 将Maven用于社区
seo-title: Using Maven for Communities
description: AEM Communities API jar和AEM Uber API jar
seo-description: AEM Communities API jar and AEM Uber API jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
exl-id: d86411b9-6ed1-4091-bf5c-d46b4e518da4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# 将Maven用于社区 {#using-maven-for-communities}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Communities文档的此部分除以外：

* [使用Apache Maven构建AEM项目](../../help/sites-developing/ht-projects-maven.md).

只有一个“uber”藏物可替代单个藏物：

* AEM [Uber API Jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>从AEM 6.4开始，不会明确发布社区API。 现在，所有社区API都包含在Uber Jar中。
>
>建议与最新的Communities版本保持同步。
>
>请参阅 [最新版本](deploy-communities.md#latest-releases) 部分以识别最新版本。

## Maven依赖关系示例 {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.4.8.3</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>请参阅 [AEM Uber Jar存储库](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar) 来识别最新的Uber罐装物品。

<!--
# Using Maven for Communities {#using-maven-for-communities}

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

## Overview {#overview}

This section of the AEM Communities documentation is in addition to:

* [How to Build AEM Projects using Apache Maven](../../help/sites-developing/ht-projects-maven.md)

There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Login with adminstrative privileges.
2. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. locate the package *cq-socialcommunities-pkg-1.x.xxx*
4. extract the version from the package name
    * first version for AEM 6.3 is version 1.11.170
    * feature packs will be versions 1.12.xxx
    
>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
-->
