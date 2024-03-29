---
title: 为IBM FileNet配置连接器
seo-title: Configuring Connector for IBM FileNet
description: 了解如何配置IBM FileNet的连接器，以启用AEM表单与IBM FileNet之间的通信。
seo-description: Learn how to configure the Connector for IBM FileNet to enable communication between AEM forms and IBM FileNet.
uuid: 29d4e221-97f7-4cfb-b7e4-75a8289d2604
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: be4994de-12f8-436e-926a-49a6783b006e
exl-id: 3a3d59c2-6811-4513-8384-aa77fdc38686
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 1%

---

# 为IBM FileNet配置连接器 {#configuring-connector-for-ibm-filenet}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

用于IBM FileNet的连接器支持AEM表单与IBM FileNet之间的通信。 有关其他背景信息，请参阅 [服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>在早期版本中，资产可以存储在ECM存储库中。 在此版本中，资产存储在AEM Forms本机存储库中，并且已弃用存储库提供程序服务。 在升级到AEM Forms时，会将资产从ECM存储库迁移到AEM Forms存储库。 有关更多信息，请参阅适用于您的应用程序服务器的AEM Forms升级指南。

## 配置与内容引擎的连接 {#configure-the-connection-to-the-content-engine}

IBM FileNet P8内容引擎提供软件服务，用于管理FileNet内容存储库中的企业内容和客户定义的业务对象。

1. 在管理控制台中，单击“服务”>“用于IBM FileNet的连接器”。
1. 在内容引擎URL框中，输入完整的连接URL。 例如：

   如果将FileNet内容引擎4.x与CEWS传输结合使用，请输入：

   `cemp:https://ContentEngineHostNameorIP:port/wsi/FNCEWS40DIME?jaasConfigurationName=FileNetP8WSI`

   如果将FileNet内容引擎4.x与EJB传输（仅WebLogic支持）结合使用，请输入：

   `cemp:t3://ContentEngineHostNameorIP:port/FileNet/Engine?jaasConfigurationName=FileNetP8Engine`

1. 在凭据保护方案列表中，选择以下保护级别之一：

   * **清除：** 在不受保护的模式下通过网络发送凭据
   * **对称：** 通过网络发送加密凭据

1. 在“加密文件位置”框中，输入加密文件的路径：

   * 如果选择Clear作为凭据保护方案，则将忽略此关键字及其值。
   * 如果选择Symmetric作为凭据保护方案，则输入的路径将指向表单服务器上包含要使用的加密密钥的加密文件的位置。

1. 在“默认对象存储”框中，输入AEM Forms默认连接到的对象存储连接器。
1. 在“用户名”框中，输入对您在上一步中指定的默认对象存储具有访问权限的用户的用户名。
1. 在“密码”框中，输入用户的密码，然后单击“保存”。

## 配置流程引擎设置 {#configure-the-process-engine-settings}

IBM FileNet的连接器包含用于IBM FileNet服务的进程引擎连接器，该连接器用于与IBM FileNet进程引擎进行交互。 您可以配置此服务的设置。

1. 在管理控制台中，单击“服务”>“用于IBM FileNet的连接器”。
1. 要启用IBM FileNet服务的进程引擎连接器，请选择使用进程引擎连接器服务。
1. 在“Process Router/Connection Point（进程路由器/连接点）”框中，输入主机名或IP地址和端口号，后跟进程路由器的名称。 例如：

   `rmi://ProcessEngineHostNameorIP:port/Name`

1. 在用户名框中，输入用于连接到流程引擎的用户名。
1. 在“密码”框中，输入用于连接到流程引擎的密码，然后单击“保存”。

## 验证服务设置 {#validation-of-service-settings}

如果在配置与内容引擎的连接或流程引擎设置时输入了不正确的用户名或密码，则将获得以下结果，具体取决于服务当前是否正在运行：

* 如果IBM FileNet的存储库提供程序服务和IBM FileNet服务的内容存储库连接器都停止，则在保存服务配置信息时，不会显示错误。 但是，下次启动服务时，将引发异常，并且服务将不会启动。
* 如果启动了IBM FileNet的存储库提供程序服务或IBM FileNet的内容存储库连接器服务，则在保存服务配置信息时，该服务会尝试立即验证凭据信息。 在这种情况下，会发生错误，并且未保存配置信息。

## 更改存储库服务提供程序 {#change-the-repository-service-provider}

您可以配置要与FileNet一起使用的存储库服务提供程序。 存储库服务调用将委派给您配置的提供程序。

以下选项可供选择：

**当前存储库提供程序名称：** 当前存储库服务提供商的名称

**IBM FileNet存储库提供程序：** 使FileNet存储库提供程序成为存储库的提供程序。 此选项已弃用。

**存储库提供程序：** 使本机存储库提供程序成为存储库的提供程序

>[!NOTE]
>
>要选择所列存储库服务提供商以外的存储库服务提供商，请在“应用程序和服务”中配置RepositoryService。 <!-- Fix broken link(See Managing Services) -->

1. 在管理控制台中，单击“服务”>“用于IBM FileNet的连接器”。
1. 在“存储库服务提供程序信息”区域，选择替代的存储库服务提供程序，然后单击“保存”。
