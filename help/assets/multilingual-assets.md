---
title: 多语言资产
description: 了解如何自动将资产（包括二进制文件、元数据和标记）转换为多种语言的工作流。
contentOwner: AG
feature: 资产管理
role: Administrator
exl-id: 8e065137-3599-48af-a040-6923b7b5e1d9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 多语言资产{#multilingual-assets}

Adobe Experience Manager(AEM)Assets允许您自动执行资产（包括二进制文件、元数据和标记）的翻译工作流，以生成其他语言的资产，以供在多语言项目中使用。

要自动执行翻译工作流，您需要将翻译服务提供商与AEM集成，并创建项目以将资产翻译成多种语言。 AEM支持人工和机器翻译工作流。

人文翻译：翻译后的资产会被返回并导入AEM。 将您的翻译提供程序与AEM集成后，将在AEM和翻译提供程序之间自动发送资产。

机器翻译：机器翻译服务会立即翻译资产的元数据和标记。

换算资产包括以下各项：

1. [将AEM与翻译服务提供商连接](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [创建翻译集成框架配置](/help/sites-administering/tc-tic.md)
1. [准备翻译资产](preparing-assets-for-translation.md)
1. [将翻译云服务应用到文件夹](transition-cloud-services.md)
1. [创建翻译项目](translation-projects.md)

如果您的翻译服务提供商未提供与AEM集成的连接器，请使用[替代进程](/help/sites-administering/tc-manage.md#exporting-a-translation-job)。

另请参阅[为内容片段创建翻译项目](creating-translation-projects-for-content-fragments.md)。
