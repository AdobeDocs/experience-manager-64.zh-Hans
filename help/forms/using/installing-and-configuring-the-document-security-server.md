---
title: 安装和配置文档安全服务器
seo-title: Installing and configuring the document security server
description: 使用文档安全功能安全地分发您以支持格式保存的任何信息。 只有授权用户才能访问受保护的文档。
seo-description: Use document security to safely distribute any information that you have saved in a supported format. Only authorized users can access protected documents.
uuid: 04c67a84-01ad-45b7-a590-822b1c067d52
contentOwner: khsingh
discoiquuid: 600d13e7-6655-41c5-aab4-c8e9e2a8d14f
role: Admin
exl-id: 9ce5e89b-76c9-464d-9caf-26a387c698fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 安装和配置文档安全服务器 {#installing-and-configuring-the-document-security-server}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

使用文档安全功能安全地分发您以支持格式保存的任何信息。 只有授权用户才能访问受保护的文档。

Adobe Experience Manager Forms文档安全确保只有授权用户才能使用您的文档。 使用文档安全，您可以安全地分发您以支持格式保存的任何信息。 支持的文件格式包括Adobe可移植文档格式(PDF)和Microsoft Word、Excel和PowerPoint文件。

您可以使用策略保护文档。 您在策略中指定的保密性设置决定了收件人如何使用您应用策略的文档。 例如，您可以指定收件人是否可以打印或复制文本、编辑文本，或向受保护的文档添加签名和注释。

策略存储在Document Security服务器上；您可以通过客户端应用程序将策略应用于文档。 将策略应用于文档时，策略中指定的机密性设置将保护文档包含的信息。 您可以将受策略保护的文档分发给受策略授权的收件人。

文档安全性还为客户端、查看器和索引器提供了保护文档、查看受保护文档和索引受保护文档的功能。 有关文档安全的详细信息，请参阅 [关于文档安全](/help/forms/using/admin-help/document-security.md).

## 部署拓扑  {#deployment-topology}

文档安全功能仅在JEE上的AEM Forms中可用。 您需要在JEE上使用单个AEM Forms实例。 您还可以根据需要创建AEM Forms服务器的群集或场。 以下拓扑是运行文档安全功能的指示拓扑。 有关拓扑的详细信息，请参见 [AEM Forms的架构和部署拓扑](aem-forms-architecture-deployment.md).

<!--fix above link-->

![](do-not-localize/document-security-server_topology.png)

下图显示了AEM Forms文档安全的典型架构：

![](do-not-localize/document-security-typical-environment.png)

## 在JEE上安装AEM Forms {#installing-aem-forms-on-jee}

执行以下步骤以在JEE上安装和配置AEM Forms:

1. 从JEE安装程序下载AEM 6.4 Forms [Adobe许可网站(LWS)](https://licensing.adobe.com/). 您需要签订有效的维护和支持合同才能下载安装程序。
1. 阅读 [AEM Forms on JEE支持的平台文档](/help/forms/using/aem-forms-jee-supported-platforms.md) 并确保已准备好在JEE上安装AEM Forms的软件、硬件、操作系统、应用程序服务器、数据库、JDK和其他基础结构。
1. （仅限非交钥匙安装）读取 [准备安装AEM Forms单服务器](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64) 或 [正在准备安装AEM Forms服务器群集](https://www.adobe.com/go/learn_aemforms_prepareInstallcluster_64) 并准备好在JEE上安装和配置AEM Forms。
1. 根据您的环境和应用程序服务器，选择以下文档之一，然后按照说明完成安装

   * [在JEE上使用JBoss统包安装和部署AEM Forms](https://www.adobe.com/go/learn_aemforms_installTurnkey_64)
   * [在JEE上安装和部署AEM Forms for JBoss](https://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [在JEE for WebLogic上安装和部署AEM Forms](https://www.adobe.com/go/learn_aemforms_installWebLogic_64)
   * [在JEE for WebSphere上安装和部署AEM Forms](https://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [在JBoss群集上的JEE上配置AEM Forms](https://www.adobe.com/go/learn_aemforms_clusterJBoss_64)
   * [在WebLogic群集的JEE上配置AEM Forms](https://www.adobe.com/go/learn_aemforms_clusterWebLogic_64)
   * [在WebSphere群集的JEE上配置AEM Forms](https://www.adobe.com/go/learn_aemforms_clusterWebSphere_64)

   >[!NOTE]
   >
   >在JEE配置管理器上AEM Forms的“模块选择”屏幕上，选择“文档安全”选项。 “文档安全”选项不需要选择任何其他模块。

## 后续步骤 {#next-steps}

* [配置客户端和服务器选项](/help/forms/using/admin-help/configuring-client-server-options.md)
* [创建和管理策略](/help/forms/using/admin-help/creating-policies.md)
* [创建和管理策略集](/help/forms/using/admin-help/creating-policy-sets.md)
