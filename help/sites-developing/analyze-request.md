---
title: 请求分析脚本
seo-title: Request Analysis Script
description: 请求分析脚本的编写，旨在简化对access.log文件的分析，生成可读报告供以后处理
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 4%

---

# 请求分析脚本{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 下载 {#download}

此脚本旨在简化 `access.log` 生成可读报告以供日后处理的文件。

[获取文件](assets/analyse-access.sh)

## 描述 {#description}

此脚本旨在简化 `access.log` 生成可读报告以供日后处理的文件。

它会生成总的请求数、GET与POST、随时间推移的请求分发等。

输出采用Markdown语法，因此使用pandoc等工具将其转换为PDF，或在带有Markdown查看器等插件的浏览器中显示将会更轻松。

它可以分析命令行上提供的自定义路径。

从告诉您如何运行该注释的文件中获取注释：

分析CQ `access.log` 根据 `stdout`.

## 用途 {#usage}

`./analyse-access.sh access.log.2013-&ast;`

您可以提供其他自定义路径以在命令行上进行分析

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

可以通过简单的管道保存输出

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
