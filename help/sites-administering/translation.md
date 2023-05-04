---
title: 翻译多语言站点的内容
seo-title: Translating Content for Multilingual Sites
description: 了解如何翻译多语言站点的内容。
seo-description: Learn how to translate content for multilingual sites.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
feature: Language Copy
exl-id: 3a3f5c4d-6c3f-4201-acc8-dbd138bb59ba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 75%

---

# 翻译多语言站点的内容{#translating-content-for-multilingual-sites}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自动翻译页面内容、资产和用户生成的内容，以创建和维护多语言网站。 要自动化翻译工作流，您可以将翻译服务提供商与 AEM 集成并创建项目以将内容翻译成多种语言。AEM 支持人工翻译工作流和机器翻译工作流。

* 人工翻译：内容将发送给您的翻译提供商并由专业翻译人员进行翻译。完成后，将返回翻译的内容并将其导入 AEM。当您的翻译提供商与 AEM 集成时，内容会在 AEM 和翻译提供商之间自动发送。
* 机器翻译：机器翻译服务将立即翻译您的内容。

翻译内容涉及以下步骤：

1. [将 AEM 连接到翻译服务提供商](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)和[创建翻译集成框架配置](/help/sites-administering/tc-tic.md)。

1. [将语言母版页面关联到](/help/sites-administering/tc-tic.md#configuring-pages-for-translation)翻译服务和框架配置。
1. [标识要翻译的内容类型](/help/sites-administering/tc-rules.md)。
1. 通过创作语言母版并创建语言副本的根页面来[准备内容以进行翻译](/help/sites-administering/tc-prep.md)。
1. [创建翻译项目](/help/sites-administering/tc-manage.md)以收集要翻译的内容并准备翻译过程。
1. 使用翻译项目[管理内容翻译过程](/help/sites-administering/tc-manage.md)。

如果您的翻译服务提供商不提供连接器来与 AEM 集成，则 AEM 支持手动提取和重新插入 XML 格式的翻译内容。

>[!NOTE]
>
>要使用语言副本功能，用户需要成为项目管理员组的成员。

## 最佳实践 {#best-practices}

[翻译最佳实践](/help/sites-administering/tc-bp.md)页面包含有关您的实施的重要信息。
