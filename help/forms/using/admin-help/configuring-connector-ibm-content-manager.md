---
title: 为IBM内容管理器配置连接器
seo-title: Configuring Connector for IBM Content Manager
description: 配置IBM内容管理器的连接器，以启用AEM表单与IBM内容管理器之间的通信。
seo-description: Configure the Connector for IBM Content Manager to enable communication between AEM forms and IBM Content Manager.
uuid: 3d55169d-93e3-4d4e-b18b-2a3394e1de3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3094b178-3b1a-46b3-8fbd-c20388afa3a7
exl-id: 8c65531e-f4f0-4cc4-b328-eaefb5662cf1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 2%

---

# 为IBM内容管理器配置连接器{#configuring-connector-for-ibm-content-manager}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

用于IBM内容管理器的连接器支持AEM表单与IBM内容管理器之间的通信。 有关其他背景信息，请参阅 [服务参考](https://www.adobe.com/go/learn_aemforms_services_63).

## 配置IBM Content Manager连接 {#configure-the-ibm-content-manager-connection}

1. 在管理控制台中，单击“服务”>“用于IBM内容管理器的连接器”。
1. 在数据存储名称框中，输入要连接到的IBM Content Manager数据存储的名称。 如果数据库是本地数据库，请输入数据库的名称。 如果数据库是远程数据库，请输入其别名。
1. 在用户名框中，输入要连接到IBM Content Manager数据存储的用户的用户ID。
1. 在“密码”框中，输入用户的密码。
1. （可选）在别名连接字符串框中，输入其他连接参数。 在大多数情况下，此框应为空。 有关更多信息，请参阅您的IBM文档。
1. 单击“保存”。

## 验证服务设置 {#validation-of-service-settings}

如果输入了不正确的dataStore别名、用户名或密码，则将获得以下结果，具体取决于IBM Content Manager服务的内容存储库连接器当前是否正在运行：

* 如果服务停止，则保存服务配置信息时，不会显示错误。 但是，下次启动服务时，将引发异常，并且服务将不会启动。
* 如果服务已启动，则在保存服务配置信息时，服务会尝试立即验证凭据信息。 在这种情况下，会发生错误，并且未保存配置信息。
