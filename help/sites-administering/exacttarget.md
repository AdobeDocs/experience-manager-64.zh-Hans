---
title: 与ExactTarget集成
seo-title: 与ExactTarget集成
description: 了解如何将AEM与ExactTarget集成。
seo-description: 了解如何将AEM与ExactTarget集成。
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# 与ExactTarget集成{#integrating-with-exacttarget}

将AEM与Exact目标集成后，您可以通过Exact目标管理和发送在AEM中创建的电子邮件。 它还允许您通过AEM表单在AEM页面上使用Exact 目标的潜在客户管理功能。

该集成为您提供以下功能：

* 能够在AEM中创建电子邮件并将其发布到Exact目标进行分发。
* 设置AEM表单操作以创建Exact 目标订阅者的能力。

配置ExactTarget后，您可以将Newsletter或电子邮件发布到ExactTarget。 请参阅[将Newsletter发布到电子邮件服务](/help/sites-authoring/personalization.md)。

## 创建ExactTarget配置{#creating-an-exacttarget-configuration}

ExactTarget配置可通过Cloudservices或工具添加。 本节将介绍这两种方法。

### 通过Cloudservices {#configuring-exacttarget-via-cloudservices}配置ExactTarget

要在Cloud Services中创建ExactTarget配置：

1. 在欢迎页面上，单击&#x200B;**Cloud Services**。 （或直接访问`https://<hostname>:<port>/etc/cloudservices.html`。）
1. 单击&#x200B;**ExactTarget**，然后单击&#x200B;**配置**。 ExactTarget配置窗口将打开。

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. 输入标题和（可选）名称，然后单击&#x200B;**创建**。 ** ExactTarget设置**配置窗口打开。

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. 输入用户名、密码并选择API端点(例如，**https://webservice.exacttarget.com/Service.asmx**)。
1. 单击&#x200B;**连接到ExactTarget。** 成功连接后，您会看到一个成功对话框。单击&#x200B;**确定**&#x200B;退出窗口。

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. 选择帐户（如果可用）。 此帐户适用于Enterprise 2.0客户。 单击&#x200B;**确定**。

   已配置ExactTarget。 单击&#x200B;**编辑**&#x200B;可编辑配置。 单击&#x200B;**转到ExactTarget**&#x200B;可转到ExactTarget。

1. AEM现在提供数据扩展功能。 可以导入ExactTarget数据扩展列。 可通过单击除成功创建ExactTarget配置外显示的“+”符号来配置。 可以从下拉列表中选择任何现有数据扩展。 有关如何配置数据扩展的详细信息，请参阅[ExactTarget文档](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships)。

   导入的数据扩展列稍后可通过&#x200B;**文本和个性化**&#x200B;组件使用。

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### 通过工具{#configuring-exacttarget-via-tools}配置ExactTarget

要在工具中创建ExactTarget配置，请执行以下操作：

1. 在欢迎页面上，单击&#x200B;**工具**。 或者，通过转到`https://<hostname>:<port>/misadmin#/etc`直接在那里导航。
1. 选择&#x200B;**工具**，然后选择&#x200B;**Cloud Services配置，**，然后选择&#x200B;**ExactTarget**。
1. 单击&#x200B;**新建**&#x200B;以打开**创建页面**窗口。

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. 输入&#x200B;**标题**&#x200B;和（可选）**名称**，然后单击&#x200B;**创建**。
1. 按照上一步中的步骤4中的概述输入配置信息。 按照该过程完成ExactTarget的配置。

### 添加多个配置{#adding-multiple-configurations}

要添加多个配置，请执行以下操作：

1. 在欢迎页面上，单击&#x200B;**Cloud Services** ，然后单击&#x200B;**ExactTarget**。 单击&#x200B;**显示配置**&#x200B;按钮，如果有一个或多个ExactTarget配置可用，则显示该按钮。 列出所有可用配置。
1. 单击“Available configurations（可用配置）”旁边的&#x200B;**+**&#x200B;符号。 这将打开&#x200B;**创建配置**&#x200B;窗口。 按照上面的配置过程创建新配置。

