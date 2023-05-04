---
title: 与ExactTarget集成
seo-title: Integrating with ExactTarget
description: 了解如何将AEM与ExactTarget集成。
seo-description: Learn how to integrate AEM with ExactTarget.
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
exl-id: 943e5199-271f-4015-a9f7-4d39c00deabe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 1%

---

# 与ExactTarget集成{#integrating-with-exacttarget}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过将AEM与Exact Target集成，您可以通过Exact Target管理和发送在AEM中创建的电子邮件。 它还允许您通过AEM页面上的AEM表单来使用Exact Target的潜在客户管理功能。

该集成为您提供以下功能：

* 能够在AEM中创建电子邮件并将其发布到Exact Target以进行分发。
* 能够设置AEM表单操作以创建Exact Target订阅者。

配置ExactTarget后，您可以将Newsletter或电子邮件发布到ExactTarget。 请参阅 [将新闻稿发布到电子邮件服务](/help/sites-authoring/personalization.md).

## 创建ExactTarget配置 {#creating-an-exacttarget-configuration}

可以通过Cloudservices或“工具”添加ExactTarget配置。 本节将介绍这两种方法。

### 通过Cloudservices配置ExactTarget {#configuring-exacttarget-via-cloudservices}

要在Cloud Services中创建ExactTarget配置，请执行以下操作：

1. 在欢迎页面上，单击 **Cloud Services**. (或直接访问 `https://<hostname>:<port>/etc/cloudservices.html`.)
1. 单击 **ExactTarget** 然后 **配置**. ExactTarget配置窗口将打开。

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. 输入标题和（可选）名称并单击 **创建**. 将打开** ExactTarget设置**配置窗口。

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. 输入用户名、密码并选择API端点(例如， **https://webservice.exacttarget.com/Service.asmx**)。
1. 单击 **连接到ExactTarget。** 成功连接后，您会看到一个成功对话框。 单击 **确定** 以退出窗口。

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. 选择一个帐户（如果可用）。 该帐户适用于Enterprise 2.0客户。 单击&#x200B;**确定**。

   已配置ExactTarget。 您可以通过单击 **编辑**. 您可以通过单击 **转到ExactTarget**.

1. AEM现在提供了数据扩展功能。 您可以导入ExactTarget数据扩展列。 除了成功创建ExactTarget配置外，还可通过单击显示“+”号来配置此配置。 可以从下拉列表中选择任何现有的数据扩展。 有关如何配置数据扩展的更多信息，请参阅 [ExactTarget文档](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   导入的数据扩展列稍后可通过 **文本和个性化** 组件。

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### 通过工具配置ExactTarget {#configuring-exacttarget-via-tools}

要在工具中创建ExactTarget配置，请执行以下操作：

1. 在欢迎页面上，单击 **工具**. 或通过转到 `https://<hostname>:<port>/misadmin#/etc`.
1. 选择 **工具**，则 **Cloud Services配置、** then **ExactTarget**.
1. 单击 **新建** 打开**创建页**窗口。

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. 输入 **标题** （可选） **名称**，然后单击 **创建**.
1. 按照上一步骤的步骤4中所述输入配置信息。 按照该过程完成ExactTarget的配置。

### 添加多个配置 {#adding-multiple-configurations}

要添加多个配置，请执行以下操作：

1. 在欢迎页面上，单击 **Cloud Services** 单击 **ExactTarget**. 单击 **显示配置** 按钮，当有一个或多个ExactTarget配置可用时，此按钮将显示。 列出了所有可用配置。
1. 单击 **+** 在可用配置旁边签名。 这将打开 **创建配置** 窗口。 按照上一配置过程创建新配置。
