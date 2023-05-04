---
title: 使用工作流
seo-title: Working with Workflows
description: 通过AEM中的工作流，您可以自动执行对页面或资产执行的一系列步骤。
seo-description: Workflows in AEM allow you to automate a series of steps that are performed on a page or asset.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 16%

---

# 使用工作流{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM工作流允许您自动执行在（一个或多个）页面和/或资产上执行的一系列步骤。

例如，在发布时，编辑者必须先查看内容 — 网站管理员才能激活页面。 自动完成此示例的工作流会通知每位参与者何时需要执行其必须完成的工作：

1. 作者将工作流应用到页面。
1. 编辑器会收到一个工作项，指示需要他们查看页面内容。 完成后，它们会指示其工作项已完成。
1. 然后，站点管理员会收到一个请求激活页面的工作项。 完成后，它们会指示其工作项已完成。

通常：

* 内容作者将工作流应用于页面并参与工作流。
* 您使用的工作流特定于贵组织的业务流程。

以下页面涵盖：

* [将工作流应用于页面](/help/sites-authoring/workflows-applying.md)
* [参与工作流](/help/sites-authoring/workflows-participating.md)
