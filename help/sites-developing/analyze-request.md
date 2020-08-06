---
title: 请求分析脚本
seo-title: 请求分析脚本
description: 请求分析脚本可简化access.log文件的分析，生成可读报告供以后处理
seo-description: 请求分析脚本可简化access.log文件的分析，生成可读报告供以后处理
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
translation-type: tm+mt
source-git-commit: 5da706f22d96b0f5ed8e02febfd64e777d5ce59f
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 1%

---


# 请求分析脚本{#request-analysis-script}

## 下载 {#download}

创建此脚本是为了简化生成可读报 `access.log` 告的文件的分析，以便以后处理。

[获取文件](assets/analyse-access.sh)

## 描述 {#description}

创建此脚本是为了简化生成可读报 `access.log` 告的文件的分析，以便以后处理。

它生成总请求数、GET与POST、随时间的请求分发等。

输出采用Markdown语法，因此使用pandoc等工具将其转换为PDF，或在浏览器中使用Markdown查看器等插件显示它会更容易。

它可以分析命令行上提供的自定义路径。

从文件中告诉您如何运行该注释：

分析CQ `access.log` 外推各种信息并在上生成Markdown输出 `stdout`。

## 使用 {#usage}

`./analyse-access.sh access.log.2013-&ast;`

您可以提供其他自定义路径以在命令行上进行分析

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

可通过简单的管道保存输出

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
