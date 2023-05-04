---
title: 为Microsoft SharePoint配置Connector
seo-title: Configuring Connector for Microsoft SharePoint
description: 为Microsoft SharePoint配置Connector，以启用AEM表单与Microsoft SharePoint之间的通信。
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 3%

---

# 为Microsoft SharePoint配置Connector {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

适用于Microsoft SharePoint的Connector支持AEM表单与Microsoft SharePoint之间的通信。 有关其他背景信息，请参阅 [服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

1. 在管理控制台中，单击服务>用于Microsoft SharePoint的连接器。
1. 为SharePoint服务器指定以下设置：

   **SharePoint服务器主机名：** SharePoint服务器上Web应用程序的主机名端口号，格式为 `[hostname]:[port]`.

   **用户名：** 用于连接到SharePoint服务器的用户帐户。

   **密码：** 用于连接到SharePoint服务器的用户帐户的密码

   **域名：** SharePoint服务器所在的域。

1. 单击“保存”。

## Microsoft SharePoint配置服务 {#microsoft-sharepoint-configuration-service}

Microsoft SharePoint配置服务 `(MSSharePointConfigService)` 允许您为具有模拟权限的AEM表单用户指定凭据。 有关模拟权限的信息，请参阅 [为Microsoft SharePoint配置Connector](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). 请按照以下步骤指定 `MSSharePointConfigService`:

1. 在管理控制台中，单击服务>应用程序和服务>服务管理。
1. 导航服务列表，然后单击 `MSSharePointConfigService`.
1. 在“配置”页面上指定以下设置：

   * 具有模拟权限的用户的用户名
   * 上述用户的密码

1. 单击“保存”。
