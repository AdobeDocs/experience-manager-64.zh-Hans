---
title: 配置AEM Assets与Experience Cloud和Creative Cloud的集成
description: 了解如何配置AEM Assets与Experience Cloud和Creative Cloud的集成
uuid: 73f90846-71d0-4f72-8784-dc877e0e9c41
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/SITES
discoiquuid: c2f190af-656e-4435-9f44-2698d41c4ad1
translation-type: tm+mt
source-git-commit: fb2567cdf5a0ae210270366899b49db256374f25
workflow-type: tm+mt
source-wordcount: '1367'
ht-degree: 3%

---


# 配置AEM Assets与Experience Cloud和Creative Cloud的集成 {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

如果您是Adobe Experience Cloud客户，则可以将Adobe Experience Manager(AEM)资产内的资产与Adobe Creative Cloud同步，反之亦然。 您还可以将资产与Experience Cloud同步，反之亦然。 可以通过AdobeI/O设置此同步。

设置此集成的工作流是：

1. 在AdobeI/O中使用公共网关创建身份验证并获取应用程序 ID。
1. 使用应用程序ID在您的AEM Assets实例上创建用户档案。
1. 使用此配置将您在AEM Assets的资产与Creative Cloud同步。

在后端，AEM服务器使用网关验证您的用户档案，然后在AEM Assets和Experience Cloud之间同步数据。

>[!NOTE]
>
>AEM到Adobe Creative Cloud文件夹共享功能已弃用。 了解更多信息并找到AEM和Creative Cloud集 [成最佳实践的更佳方法](../assets/aem-cc-integration-best-practices.md)。 不弃用AEM到Marketing Cloud复制以及在AEM Assets和Marketing Cloud之间交换资产的配置。

![整合AEM Assets和Creative Cloud时的数据流](assets/chlimage_1-287.png)

整合AEM Assets和Creative Cloud时的数据流

>[!NOTE]
>
>在Adobe Experience Cloud和Adobe Creative Cloud之间共享资产需要AEM实例的管理员权限。

>[!CAUTION]
>
>AdobeMaketing Cloud已更名为Adobe Experience Cloud。 下面的步骤仍提到Marketing Cloud，以反映当前接口。

## 创建应用程序 {#create-an-application}

1. 登录https://legacy-oauth.cloud.adobe.io访问Adobe开发人员网关 [界面](https://legacy-oauth.cloud.adobe.io/)。

   >[!NOTE]
   >
   >您需要管理员权限才能创建应用程序 ID。

1. 从左窗格中，导航到“开 **[!UICONTROL 发人员工具]** ” > **[!UICONTROL “应用程序]** ”，以视图一列表应用程序。
1. 单 **[!UICONTROL 击添]** 加aem_assets_addcircle_icon ![](assets/aem_assets_addcircle_icon.png) 以创建应用程序。
1. 从“客 **[!UICONTROL 户端凭据]** ”列表卡中，选 **[!UICONTROL 择服务帐户（JWT断言）]**，该服务是用于服务器身份验证的服务器到服务器通信服务。

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. 指定应用程序的名称和可选说明。
1. 在“组 **[!UICONTROL 织]** ”列表中，选择要为其同步资产的组织。
1. 从“范 **[!UICONTROL 围]** ”列表 **[!UICONTROL 中]**，选择 **[!UICONTROL dam-read]**、 **[!UICONTROL dam-sync、]** dam-write ****&#x200B;和cc-share。
1. 单击&#x200B;**[!UICONTROL 创建]**。系统会显示一条消息，通知已创建应用程序。

   ![成功创建应用程序以将AEM Assets与AdobeCC集成的通知](assets/chlimage_1-289.png)

1. 复制为 **[!UICONTROL 新应]** 用程序生成的应用程序 ID。

   >[!CAUTION]
   >
   >请确保不要无意中复制 **[!UICONTROL 应用程序密码]** ，而 **[!UICONTROL 不是应用程序 ID]**。

## 向Marketing Cloud添加新配置 {#add-a-new-configuration-to-marketing-cloud}

1. 单击本地AEM Assets实例的用户界面上的AEM徽标，然后导航到“工 **[!UICONTROL 具]** ”> **[!UICONTROL Cloud Services]** > **[!UICONTROL “旧]**&#x200B;版Cloud Services”。

1. 找到 **[!UICONTROL Adobe Marketing Cloud]** 服务。 如果不存在配置，请单击“ **[!UICONTROL 立即配置]**”。 如果存在配置，请 **[!UICONTROL 单击“显示]****[!UICONTROL [配置”]]** ，然后单击+以添加新配置。

   >[!NOTE]
   >
   >使用具有组织管理员权限的Adobe ID帐户。

1. 在“创 **[!UICONTROL 建配置]** ”对话框中，指定新配置的标题和名称，然后单击“ **[!UICONTROL 创建”]**。

   ![命名新配置以集成AEM Assets和CC](assets/cloudservices_configure_mc.png)

1. 在“租 **[!UICONTROL 户URL]** ”字段中，指定AEM Assets的URL。

   >[!CAUTION]
   >
   >由于重新设定品牌，如果您将租户 **URL输入为https://&lt;tenant_id>.marketing.adobe** .com **，则需要将其更改为https://&lt;tenant_id>.experiencecloud.adobe.com。** 为此，请按照以下步骤操作：
   1. 导航到&#x200B;**工具 > 云服务 > 旧版云服务**。
   1. 在Adobe Marketing Cloud下，单击“ **显示配置**”。
   1. 选择在设置AEM-MAC-CC同步时创建的配置。
   1. 编辑cloudservice配置并替 **换租户URL字段** 中的marketing.adobe.com **以体验cloud.adobe.com**。
   1. 保存配置。
   1. 测试mac-sync复制代理。


1. 在“客 **[!UICONTROL 户端ID]** ”字段中 [，将您复制的应用程序 ID粘贴到“创建应](/help/sites-administering/configure-assets-cc-integration.md#create-an-application)用程序”过程末尾。

   ![提供整合AEM Assets和Creative Cloud所需的应用程序 ID价值](assets/cloudservices_tenant_info.png)

1. 在“同 **[!UICONTROL 步]** ”下 **[!UICONTROL 选择]** “已启用 **[!UICONTROL ”以启用同步，然后单]**&#x200B;击“确定”。

   >[!NOTE]
   如果选择禁 **用**，则同步将单向工作。

1. 在配置页面中，单 **[!UICONTROL 击显示公钥]** ，以显示为实例生成的公钥。 或者，单 **[!UICONTROL 击“下载OAuth网关的公钥]** ”以下载包含公钥的文件。 然后，打开文件以显示公钥。

## 启用同步 {#enable-synchronization}

1. 使用过程最后一步中提到的以下方法之一显示公共 [密钥向Marketing Cloud添加新配置](/help/sites-administering/configure-assets-cc-integration.md#add-a-new-configuration-to-marketing-cloud)。 Click **[!UICONTROL Display Public Key]**.

   ![chlimage_1-292](assets/chlimage_1-292.png)

1. 复制公钥并将其粘贴到您在创建应用 **[!UICONTROL 程序中]** ，创建的应用程序的配置界面 [的公钥字段中](/help/sites-administering/configure-assets-cc-integration.md#create-an-application)。

   ![chlimage_1-293](assets/chlimage_1-293.png)

1. Click **[!UICONTROL Update]**. 立即将您的资产与AEM Assets实例同步。

## 测试同步 {#test-the-synchronization}

1. 单击本地AEM Assets实例的用户界面上的AEM徽标，然 **[!UICONTROL 后导航到]**“工具”> **[!UICONTROL “部署”]**> **Replication**，找到为同步创建的复制用户档案。
1. 在“复 **[!UICONTROL 制]** ”页面上，单 **[!UICONTROL 击作者代理]**。
1. 在用户档案列表中，单击组织的默认复制用户档案以将其打开。
1. 在对话框中，单击“ **[!UICONTROL 测试连接”]**。

   ![测试连接并设置组织的默认复制用户档案](assets/chlimage_1-294.png)

1. 当复制架完成时，在测试结果末尾检查成功消息。

## 将用户添加到Marketing Cloud {#add-users-to-marketing-cloud}

1. 使用管理员凭据登录Marketing Cloud。
1. 从边栏中，转到**[!UICONTROL 管理]**，然后单击／点按启 **[!UICONTROL 动企业仪表板]**。
1. 在边栏中，单击 **[!UICONTROL 用户]** ，打开“ **[!UICONTROL 用户管理]** ”页。
1. 在工具栏中，单击／点 **按**![添加aem_assets_add_icon](assets/aem_assets_add_icon.png)。
1. 添加一个或多个用户，让您能够与Creative Cloud共享资产。

   >[!NOTE]
   只有您添加到Marketing Cloud的用户才能将资产从AEM Assets共享到Creative Cloud。

## AEM Assets与Marketing Cloud交换资产 {#exchange-assets-between-aem-assets-and-marketing-cloud}

1. 登录 AEM 资产。
1. 在“资产”控制台中，创建一个文件夹，并将一些资产上传到该文件夹。 例如，创建文件夹 **mc-demo** ，然后将资产上传到该文件夹。
1. 选择文件夹，然 **后单**![击Share](assets/assets_share.png)assets_share。
1. 从菜单中，选择 **[!UICONTROL Adobe Marketing Cloud]** ，然后单击 **[!UICONTROL 共享]**。 系统会显示一条消息，通知已与Marketing Cloud共享文件夹。

   ![chlimage_1-295](assets/chlimage_1-295.png)

   >[!NOTE]
   在Adobe Marketing Cloud进行共享时， `sling:OrderedFolder`不支持共享类型的“资产”文件夹。 如果要共享文件夹，则在AEM Assets创建文件夹时，不要选择“已订 **[!UICONTROL 购]** ”选项。

1. 刷新AEM Assets用户界面。 您在本地AEM Assets实例的“资产”控制台中创建的文件夹将复制到Marketing CloudUI。 您上传到AEM Assets的文件夹的资产在AEM服务器处理后，会显示在Marketing Cloud的文件夹副本中。
1. 您还可以在Marketing Cloud中上传文件夹复制副本中的资产。 处理完资产后，资产会显示在AEM Assets的共享文件夹中。

## AEM Assets与Creative Cloud交换资产 {#exchange-assets-between-aem-assets-and-creative-cloud}

AEM Assets允许您与Adobe Creative Cloud用户共享包含资产的文件夹。

1. 在“资产”控制台中，选择要与Creative Cloud共享的文件夹。
1. 在工具栏中，单 **[!UICONTROL 击]**![Share](assets/assets_share.png)assets_share。
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   这些选项对于在根目录上具有读取权限的用户可用。 用户必须具有访问Marketing Cloud的复制代理信息所需的权限。

1. 在“ **[!UICONTROL Creative Cloud共享]** ”页面中，添加要与其共享文件夹的用户，然后为用户选择角色。 单击“ **[!UICONTROL 保存]** ”，然后 **[!UICONTROL 单击“确定]**”。

1. 使用您与其共享文件夹的用户的凭证，登录到 Creative Cloud。此时共享的文件夹便可在 Creative Cloud 中使用。

AEM AssetsMarketing Cloud同步的设计方式是，上传资产的用户计算机实例保留修改资产的权利。 只有这些更改才会传播到其他实例。

例如，如果资产是从AEM Assets（本地）实例上传的，则来自此实例对资产所做的更改会传播到Marketing Cloud实例。 但是，从Marketing Cloud实例对同一资产所做的更改不会传播到AEM实例，从Marketing Cloud上传的资产也会传播到实例，反之亦然。

>[!MORELIKETHIS]
* [AEM和Creative Cloud集成最佳实践](../assets/aem-cc-integration-best-practices.md)
* [AEM到Creative Cloud文件夹共享最佳实践](../assets/aem-cc-folder-sharing-best-practices.md)

