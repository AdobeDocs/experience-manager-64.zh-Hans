---
title: 多语言资产
description: 了解如何自动工作流资产的翻译，包括二进制文件、元数据和标记，以及多种语言。
contentOwner: AG
feature: Asset Management
role: Administrator
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---


# 多语言资产{#multilingual-assets}

Adobe Experience Manager(AEM)Assets允许您自动翻译资产（包括二进制文件、元数据和标记）上的工作流，以生成其他语言的资产，以便在多语言项目中使用。

要实现翻译工作流自动化，您可以将翻译服务提供商与AEM集成，并创建将资产翻译为多种语言的项目。 AEM支持人文和机器翻译工作流。

人文翻译：转换后的资产会返回并导入AEM。 当您的翻译提供商与AEM集成后，资产会自动在AEM和翻译提供商之间发送。

机器翻译：机器翻译服务会立即转换资产的元数据和标记。

折算资产包括：

1. [将AEM与翻译服务提供商连接](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [创建翻译集成框架配置](/help/sites-administering/tc-tic.md)
1. [准备要翻译的资产](preparing-assets-for-translation.md)
1. [将翻译云服务应用到文件夹](transition-cloud-services.md)
1. [创建翻译项目](translation-projects.md)

如果翻译服务提供商不提供与AEM集成的连接器，请使用[替代进程](/help/sites-administering/tc-manage.md#exporting-a-translation-job)。

另请参阅[为内容片段创建翻译项目](creating-translation-projects-for-content-fragments.md)。
