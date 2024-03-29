---
title: 与Silverpop Engage集成
seo-title: Integrating with Silverpop Engage
description: 了解如何将AEM与Silverpop Engage集成
seo-description: Learn how to integrate AEM with Silverpop Engage
uuid: dfff7aaf-5264-4763-995f-5647f565c03b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: dfff6bdc-0d5f-4338-aa8a-7d0eb04bc19a
exl-id: 3148ba52-4464-4f3e-8741-645cd7a1c970
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 1%

---

# 与Silverpop Engage集成{#integrating-with-silverpop-engage}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Silverpop集成是 **not** 开箱即用。 您必须下载 [Silverpop集成包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem620/product/cq-mcm-integrations-silverpop-content) 从包共享中，并将其安装到实例上。 安装包后，可以按照本文档中的说明对其进行配置。

将AEM与Silverpop Engage集成后，您可以通过Silverpop管理和发送在AEM中创建的电子邮件。 它还允许您通过AEM页面上的AEM表单来使用Silverpop的潜在客户管理功能。

该集成为您提供以下功能：

* 在AEM中创建电子邮件并将其发布到Silverpop以进行分发的功能。
* 能够设置AEM表单操作以创建Silverpop订阅者。

配置Silverpop Engage后，您可以将新闻稿或电子邮件发布到Silverpop Engage。

## 创建Silverpop配置 {#creating-a-silverpop-configuration}

Silverpop配置可通过 **云服务**, **工具**&#x200B;或 **API端点**. 本节将介绍所有方法。

### 通过Cloudservices配置Silverpop {#configuring-silverpop-via-cloudservices}

要在Cloud Services中创建Silverpop配置，请执行以下操作：

1. 在AEM中，点按或单击 **工具** > **部署** > **Cloud Services**. (或直接访问 `https://<hostname>:<port>/etc/cloudservices.html`.)
1. 在第三方服务下，单击 **Silverop Engage** 然后 **配置**. 将打开Silverpop配置窗口。

   >[!NOTE]
   >
   >除非从包共享下载包，否则第三方服务下的选项将不提供Silverpop Engage。

1. 输入标题和（可选）名称并单击 **创建**. 将打开** Silverpop设置**配置窗口。
1. 输入用户名、密码，然后从下拉列表中选择一个API端点。
1. 单击 **连接到Silverpop。** 成功连接后，您会看到一个成功对话框。 单击 **确定** 以退出窗口。 您可以通过单击 **转到Silverpop Engage**.
1. Silverpop已配置。 您可以通过单击 **编辑**.
1. 此外，还可以通过提供标题和名称（可选）为个性化操作配置Silverpop Engage框架。 单击创建将为已配置的Silverpop连接成功创建框架。

   导入的数据扩展列稍后可通过AEM组件使用 —  **文本和个性化**.

### 通过工具配置Silverpop {#configuring-silverpop-via-tools}

要在工具中创建Silverpop配置，请执行以下操作：

1. 在AEM中，点按或单击 **工具** > **部署** > **Cloud Services**. 或通过转到 `https://<hostname>:<port>/misadmin#/etc`.
1. 选择 **工具**，则 **Cloud Services配置、** then **Silverpop Engage**.
1. 单击 **新建** 打开 **创建页面** 窗口。

   ![chlimage_1-44](assets/chlimage_1-44.jpeg)

1. 输入 **标题** （可选） **名称**，然后单击 **创建**.
1. 按照上一步骤的步骤4中所述输入配置信息。 按照该步骤完成Silverpop的配置。

### 添加多个配置 {#adding-multiple-configurations}

要添加多个配置，请执行以下操作：

1. 在欢迎页面上，单击 **Cloud Services** 单击 **Silverpop Engage**. 单击 **显示配置** 按钮，当有一个或多个Silverpop配置可用时，此按钮将显示。 列出了所有可用配置。
1. 单击 **+** 在可用配置旁边签名。 这将打开 **创建配置** 窗口。 按照上一配置过程创建新配置。

### 配置API端点以连接到Silverpop {#configuring-api-end-points-for-connecting-to-silverpop}

目前，AEM有六个不安全的端点（参与1到6）。 Silverpop现在提供两个新端点以及现有端点的更改连接端点。

要配置API端点，请执行以下操作：

1. 转到 `/libs/mcm/silverpop/components/silverpoppage/dialog/items/general/items/apiendpoint/options node` on `https://<hostname>:<port>/crxde.`
1. 右键单击并选择 **创建**，则 **创建节点**.
1. 输入 **名称** as `sp-e0` 选择 **类型** as `cq:Widget`.
1. 向新添加的节点添加两个属性：

   1. **名称**: `text`, **类型**: `String`, **值**: `Engage 0`
   1. **名称**: `value`, **类型**: `String`, **值**: `https://api0.silverpop.com`

   ![chlimage_1-286](assets/chlimage_1-286.png)

   单击“全部保存”按钮。

1. 使用 **名称** as `sp-e7` 和 **类型** as `cq:Widget`.

   向新添加的节点添加两个属性：

   1. **名称**: `text`, **类型**: `String`, **值**: `Pilot`
   1. **名称**: `value`, **类型**: `String`, **值**: `https://apipilot.silverpop.com/XMLAPI`

1. 要更改现有API端点（参与1到6），请逐一单击每个端点并按如下方式替换值：

   | **节点名称** | **现有端点值** | **新的端点值** |
   |---|---|---|
   | sp-e1 | https://api.engage1.silverpop.com/XMLAPI | https://api1.silverpop.com |
   | sp-e2 | https://api.engage2.silverpop.com/XMLAPI | https://api2.silverpop.com |
   | sp-e3 | https://api.engage3.silverpop.com/XMLAPI | https://api3.silverpop.com |
   | sp-e4 | https://api.engage4.silverpop.com/XMLAPI | https://api4.silverpop.com |
   | sp-e5 | https://api.engage5.silverpop.com/XMLAPI | https://api5.silverpop.com |
   | sp-e6 | https://api.pilot.silverpop.com/XMLAPI | https://api6.silverpop.com |

1. 单击 **全部保存**. AEM现已准备好通过安全端点连接到Silverpop。

   ![chlimage_1-45](assets/chlimage_1-45.jpeg)
