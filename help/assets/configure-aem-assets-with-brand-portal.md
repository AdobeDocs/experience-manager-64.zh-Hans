---
title: 使用 Brand Portal 配置 AEM Assets
description: '了解如何使用Brand Portal配置AEM Assets，以将资产和收藏集发布到Brand Portal。 '
contentOwner: VG
feature: Brand Portal
role: Admin
exl-id: cde35555-259f-4d16-999f-2b93d597b8a5
source-git-commit: 8910716cf6b5c4e872db8d965200787de7c2d121
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 37%

---

# 使用 Brand Portal 配置 AEM Assets {#configure-integration-64}

Adobe Experience Manager Assets通过[!DNL Adobe I/O]使用Brand Portal进行配置，以获取IMS令牌以授权您的Brand Portal租户。

>[!NOTE]
>
>AEM 6.4.8.0及更高版本支持通过[!DNL Adobe I/O]配置AEM Assets与Brand Portal。
>
>以前，Brand Portal是通过旧版OAuth网关在经典UI中配置的，该网关使用JWT令牌交换获取IMS访问令牌以进行授权。

>[!TIP]
>
>***仅适用于现有客户***
>
>建议继续使用现有的旧版OAuth网关配置。 如果旧版OAuth网关配置出现问题，请删除现有配置并通过[!DNL Adobe I/O]创建新配置。

此帮助描述了以下两个用例：

* [新配置](#configure-new-integration-64):如果您是新的Brand Portal用户，并且想要使用Brand Portal配置AEM Assets创作实例，则可以在上创建新配 [!DNL Adobe I/O]置。
* [升级配置](#upgrade-integration-64):如果您是现有Brand Portal用户，且在旧版OAuth网关上使用Brand Portal配置了AEM Assets创作实例，则建议删除现有配置并在上创建新配 [!DNL Adobe I/O]置。

提供的信息基于以下假设：阅读本帮助的任何人都熟悉以下技术：

* 安装、配置和管理Adobe Experience Manager和AEM包

* 使用Linux和Microsoft Windows操作系统

## 前提条件 {#prerequisites}

您需要以下各项才能使用 Brand Portal 配置 AEM Assets：

* 具有最新Service Pack的已启动且正在运行的AEM Assets创作实例。
* Brand Portal 租户 URL。
* 对 Brand Portal 租户的 IMS 组织具有系统管理员权限的用户。

[下载并安装AEM 6.4](#aemquickstart)

[下载并安装最新的AEM Service Pack](#servicepack)

### 下载并安装AEM 6.4 {#aemquickstart}

建议让AEM 6.4来设置AEM创作实例。 如果您没有启动并运行AEM，请从以下位置下载它：

* 如果您是现有AEM客户，请从[Adobe授权网站](http://licensing.adobe.com)下载AEM 6.4。

* 如果您是Adobe合作伙伴，请使用[Adobe合作伙伴培训计划](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)请求AEM 6.4。

下载AEM后，有关设置AEM创作实例的说明，请参阅[部署和维护](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall)。

### 下载并安装AEM最新Service Pack {#servicepack}

有关详细说明，请参阅

* [AEM 6.4 Service Pack 发行说明](https://helpx.adobe.com/cn/experience-manager/6-4/release-notes/sp-release-notes.html)

**如果您** 找不到最新的AEM包或Service Pack，请联系客户支持。

## 创建配置 {#configure-new-integration-64}

如果您是首次使用Brand Portal配置AEM Assets，请按照列出的顺序执行以下步骤：

1. [获取公共证书](#public-certificate)
1. [ [!DNL Adobe I/O] Createintegration](#createnewintegration)
1. [创建 IMS 帐户配置](#create-ims-account-configuration)
1. [配置云服务](#configure-the-cloud-service)
1. [测试配置](#test-integration)

>[!NOTE]
>
>AEM Assets创作实例只能配置一个Brand Portal租户。

### 创建 IMS 配置 {#create-ims-configuration}

IMS 配置通过 AEM Assets 作者实例对您的 Brand Portal 租户进行身份验证。

IMS 配置包括两个步骤：

* [获取公共证书](#public-certificate)
* [创建 IMS 帐户配置](#create-ims-account-configuration)

### 获取公共证书 {#public-certificate}

公共证书允许您在[!DNL Adobe I/O]上验证配置文件。

1. 登录AEM Assets创作实例
默认URL:http://本地主机：4502/aem/start.html
1. 在&#x200B;**Tools** ![Tools](assets/tools.png)面板中，导航到&#x200B;**[!UICONTROL Security]** >> **[!UICONTROL Adobe IMS配置]**。

   ![Adobe IMS 帐户配置 UI](assets/ims-config1.png)

1. 打开 Adobe IMS 配置页面。

   单击&#x200B;**[!UICONTROL 创建]**。

   这会将您转到 **[!UICONTROL Adobe IMS 技术帐户配置]**&#x200B;页面。

1. 默认情况下，将打开&#x200B;**证书**&#x200B;选项卡。

   在&#x200B;**云解决方案**&#x200B;中，选择 **[!UICONTROL Adobe Brand Portal]**。

1. 标记&#x200B;**[!UICONTROL 创建新证书]**&#x200B;复选框，并指定证书的&#x200B;**别名**。别名将用作对话框的名称。

1. 单击&#x200B;**[!UICONTROL 创建证书]**。将显示一个对话框。单击&#x200B;**[!UICONTROL 确定]**&#x200B;以生成公共证书。

   ![创建证书](assets/ims-config2.png)

1. 单击&#x200B;**[!UICONTROL 下载公钥]**，然后将 *AEM-Adobe-IMS.crt* 证书文件保存到您的计算机上。该证书文件用于[create [!DNL Adobe I/O] integration](#createnewintegration)。

   ![下载证书](assets/ims-config3.png)

1. 单击&#x200B;**[!UICONTROL 下一步]**。

   在&#x200B;**帐户**&#x200B;选项卡中，您可以创建 Adobe IMS 帐户，但您需要集成详细信息。暂时保持此页面打开。

   打开新选项卡和[创建 [!DNL Adobe I/O] 集成](#createnewintegration) ，以获取IMS帐户配置的集成详细信息。

### 创建[!DNL Adobe I/O]集成 {#createnewintegration}

[!DNL Adobe I/O] 集成可生成 API 密钥、客户端密钥和有效负荷 (JWT)，这是设置 IMS 帐户配置所必需的。

1. 使用Brand Portal租户的IMS组织的系统管理员权限登录到[!DNL Adobe I/O]控制台。

   默认 URL：[https://console.adobe.io/](https://console.adobe.io/)

1. 单击&#x200B;**[!UICONTROL 创建集成]**。

1. 选择&#x200B;**[!UICONTROL 访问 API]**，然后单击&#x200B;**[!UICONTROL 继续]**。

   ![创建新集成](assets/create-new-integration1.png)

1. 此时将打开新的集成页面。

   从下拉列表中选择您的组织。

   在 **[!UICONTROL Experience Cloud]** 中，选择 **[!UICONTROL AEM Brand Portal]**，然后单击&#x200B;**[!UICONTROL 继续]**。

   如果您禁用了 Brand Portal 选项，请确保您从 **[!UICONTROL Adobe Services]** 选项上方的下拉框中选择了正确的组织。如果您不了解您的组织，请与管理员联系。

   ![创建集成](assets/create-new-integration2.png)

1. 指定集成的名称和描述。单击&#x200B;**[!UICONTROL 从计算机中选择文件]**，然后上传在[获取公共证书](#public-certificate)部分下载的 `AEM-Adobe-IMS.crt` 文件。

1. 选择您的组织的配置文件。

   或者，选择默认的配置文件 **[!UICONTROL Brand Portal]**，然后单击&#x200B;**[!UICONTROL 创建集成]**。将创建集成。

1. 单击&#x200B;**[!UICONTROL 继续查看集成详细信息]**，以查看集成信息。

   复制 **[!UICONTROL API 密钥]**

   单击&#x200B;**[!UICONTROL 检索客户端密钥]**，并复制客户端密钥。

   ![集成的 API 密钥、客户端密钥和有效负荷信息](assets/create-new-integration3.png)

1. 导航到 **[!UICONTROL JWT]** 选项卡，并复制 **[!UICONTROL JWT 有效负荷]**。

   API 密钥、客户端密钥和 JWT 有效负荷信息将用于创建 IMS 帐户配置。

### 创建 IMS 帐户配置 {#create-ims-account-configuration}

确保您已执行以下步骤：

* [获取公共证书](#public-certificate)
* [创建 [!DNL Adobe I/O] 集成](#createnewintegration)

**创建 IMS 帐户配置的步骤：**

1. 打开“IMS 配置”页面的&#x200B;**[!UICONTROL 帐户]**&#x200B;选项卡。保持打开该页面[获取公共证书](#public-certificate)的结尾部分。

1. 为 IMS 帐户指定&#x200B;**[!UICONTROL 标题]**。

   在&#x200B;**[!UICONTROL 授权服务器]**&#x200B;中，输入 URL：[https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   粘贴您在[Create [!DNL Adobe I/O] integration](#createnewintegration)末尾复制的API密钥、客户端密钥和JWT有效负荷。

   单击&#x200B;**[!UICONTROL 创建]**。

   将创建集成。

   ![IMS 帐户配置](assets/create-new-integration6.png)

1. 选择 IMS 配置，然后单击&#x200B;**[!UICONTROL 检查运行状况]**。将显示一个对话框。

   单击&#x200B;**[!UICONTROL 检查]**。成功连接时，将显示&#x200B;*已成功检索令牌*&#x200B;消息。

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>您只能有一个IMS配置。 请勿创建多个 IMS 配置。
>
>确保IMS配置通过运行状况检查。 如果配置未通过运行状况检查，则无效。 您必须删除它，然后创建一个有效的新配置。

### 配置云服务 {#configure-the-cloud-service}

执行以下步骤以创建 Brand Portal 云服务配置：

1. 登录AEM Assets创作实例

   默认URL:http://本地主机：4502/aem/start.html
1. 在&#x200B;**Tools** ![Tools](assets/tools.png)面板中，导航到&#x200B;**[!UICONTROL Cloud Services>>AEM Brand Portal]**。

   此时将打开 Brand Portal 的“配置”页面。

1. 单击&#x200B;**[!UICONTROL 创建]**。

1. 指定配置的&#x200B;**[!UICONTROL 标题]**。

   选择您在[创建 IMS 帐户配置](#create-ims-account-configuration)步骤中创建的“IMS 配置”。

   在&#x200B;**[!UICONTROL 服务 URL]** 中，输入您的 Brand Portal 租户 URL。

   ![](assets/create-cloud-service.png)

1. 选择&#x200B;**[!UICONTROL 保存并关闭]**。将创建云配置。您的AEM Assets创作实例现已与Brand Portal租户集成。

### 测试配置 {#test-integration}

1. 登录AEM Assets创作实例

   默认URL:http://本地主机：4502/aem/start.html

1. 在&#x200B;**Tools** ![Tools](assets/tools.png)面板中，导航到&#x200B;**[!UICONTROL Deployment >> Replication]**。

   ![](assets/test-integration1.png)

1. 复制页面打开。

   单击&#x200B;**[!UICONTROL 作者的代理]**。

   ![](assets/test-integration2.png)

1. 为每个租户创建四个复制代理。

   找到Brand Portal租户的复制代理。

   单击复制代理URL。

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >复制代理并行工作并平均共享作业分配，从而将发布速度提高了原速度的四倍。 配置云服务后，无需进行其他配置即可启用默认激活的复制代理，以启用多个资产的并行发布。

1. 要验证AEM Assets作者与Brand Portal之间的连接，请单击&#x200B;**[!UICONTROL 测试连接]**。

   ![](assets/test-integration4.png)

1. 查看测试结果的底部以验证复制是否成功。

   ![](assets/test-integration5.png)


1. 逐一验证所有四个复制代理上的测试结果。

   >[!NOTE]
   >
   >请避免禁用任何复制代理，因为这可能会导致某些资产的复制失败。
   >
   >确保将所有四个复制代理都配置为避免超时错误。 请参阅[并行发布到Brand Portal时出现的问题疑难解答](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout)。

Brand Portal已成功配置为您的AEM Assets创作实例。 您现在可以：

* [将资产从 AEM Assets 发布到 Brand Portal](../assets/brand-portal-publish-assets.md)
* [将文件夹从 AEM Assets 发布到 Brand Portal](../assets/brand-portal-publish-folder.md)
* [将收藏集从 AEM Assets 发布到 Brand Portal](../assets/brand-portal-publish-collection.md)
* [配置资](https://docs.adobe.com/content/help/zh-Hans/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) 产源，以便Brand Portal用户能够将资产贡献和发布到AEM Assets。

## 升级配置 {#upgrade-integration-64}

按照所列顺序执行以下步骤以升级现有配置：
1. [验证正在运行的作业](#verify-jobs)
1. [删除现有配置](#delete-existing-configuration)
1. [创建配置](#configure-new-integration-64)

### 验证正在运行的作业 {#verify-jobs}

在进行任何修改之前，请确保您的AEM Assets创作实例上未运行任何发布作业。 为此，您可以验证所有四个复制代理，并确保队列是理想/空的。

1. 登录AEM Assets创作实例

   默认URL:http://本地主机：4502/aem/start.html

1. 在&#x200B;**Tools** ![Tools](assets/tools.png)面板中，导航到&#x200B;**[!UICONTROL Deployment >> Replication]**。

1. 复制页面打开。

   单击&#x200B;**[!UICONTROL 作者的代理]**。

   ![](assets/test-integration2.png)

1. 找到Brand Portal租户的复制代理。

   请确保所有复制代理的&#x200B;**队列都为Idle**，则未激活任何发布作业。

   ![](assets/test-integration3.png)

### 删除现有配置 {#delete-existing-configuration}

删除现有配置时，必须运行以下检查列表。
* 删除所有四个复制代理
* 删除云服务
* 删除MAC用户

执行以下步骤以删除现有配置：

1. 登录到您的AEM Assets创作实例，并以管理员身份打开CRX Lite 。

   默认URL:http://本地主机：4502/crx/de/index.jsp

1. 导航到`/etc/replications/agents.author`并删除Brand Portal租户的所有四个复制代理。

   ![](assets/delete-replication-agent.png)

1. 导航到`/etc/cloudservices/mediaportal`并删除&#x200B;**Cloud Service配置**。

   ![](assets/delete-cloud-service.png)

1. 导航到`/home/users/mac`并删除Brand Portal租户的&#x200B;**MAC用户**。

   ![](assets/delete-mac-user.png)


您现在可以在[!DNL Adobe I/O]上的AEM 6.4创作实例上[创建配置](#configure-new-integration-64)。



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

复制成功后，您可以将资产、文件夹和收藏集发布到Brand Portal。 有关详细信息，请参阅：

* [将资产发布到 Brand Portal](brand-portal-publish-assets.md)
* [将资产和文件夹发布到Brand Portal](brand-portal-publish-folder.md)
* [将收藏集发布到Brand Portal](brand-portal-publish-collection.md)
