---
title: 升级到 AEM 6.4 Forms
seo-title: 升级到 AEM 6.4 Forms
description: '您可以从AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升级到AEM 6.3 Forms。 '
seo-description: '您可以从AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升级到AEM 6.3 Forms。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 0%

---


# 升级到JEE上的AEM 6.4 Forms {#upgrade-to-aem-forms-jee}

根据您的环境，使用以下升级路径之一。

## AEM 6.2 Forms on JEE，或AEM 6.3 Forms on JEE > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

请执行以下步骤，将JEE上的现有AEM 6.2 Forms或JEE上的AEM 6.3 Forms升级到JEE上的AEM 6.4 Forms:

1. 从[Adobe授权网站(LWS)](https://licensing.adobe.com/)下载AEM 6.4 Forms on JEE安装程序。 您需要一个有效的维护和支持合同来下载安装程序。
1. 请参阅[升级核对清单和计划](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63)了解为确保成功升级而执行的检查。
1. 请参阅[准备升级到AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63)以学习并执行确保在最短服务器停机时间内正确运行升级的任务。
1. 根据您现有的环境和应用程序服务器，选择以下文档之一并按照说明操作。

   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for JBoss](assets/upgrade-jboss.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

不提供从LiveCycle ES2、LiveCycle ES3、AEM 6.0 Forms、AEM 6.1 Forms到AEM 6.4 Forms的直接升级。 您可以执行到一个或多个版本的LiveCycle或AEM Forms的中间升级，然后从AEM 6.4 Forms升级。 有关中间版本的列表和相应的升级说明，请参阅[选择升级路径](upgrade.md)。

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

在JEE上将LiveCycle ES4 SP1升级到AEM 6.4 Forms是一次非就地升级，因为它涉及将资产和数据从先前版本迁移到受支持的应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycle ES4 SP1服务器升级到AEM 6.4 Forms的过程概述。 有关详细说明，请参阅在过程末尾列出的文档。

1. 升级前：

   1. 从[Adobe授权网站(LWS)](https://licensing.adobe.com/)下载AEM 6.4 Forms on JEE安装程序。 您需要一个有效的维护和支持合同来下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数AEM Forms在JEE功能上使用内容存储库持久性来存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在LiveCycle ES4 SP1中，通信管理、Forms门户、HTML工作区和流程报告功能使用内容存储库。 如果您未在LiveCycle ES4中使用这些功能，并且计划不在AEM Forms中使用这些功能，则不需要内容存储库。
      * 在AEM Forms、Adaptive Forms、Correspondence Management、HTML5 Forms(在LiveCycle ES4 SP1中称为Mobile Forms)、Forms Portal、HTML Workspace、流程报告、OSGi上以Forms为中心的工作流中，功能使用内容存储库。 如果您计划使用AEM Forms进行这些功能，则需要“内容存储库”。
      * 您不需要Content Repository来实现AEM Forms 文档 Security。

      此外，LiveCycle和AEM Forms的存储库类型不同。 有关可用的存储库类型和相关信息，请参阅[为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 创建LiveCycle ES4 SP1内容和数据的备份：

      创建LiveCycle ES4 SP1存储库、全局数据(GDS)和crx-repository的备份(文档安全性不需要)。 如果要升级到MongoMK或RDBMK持久性，请将LiveCycle ES4 SP1对应管理资源导出为.cmp文件，并将资源作为AEM包表单。

   1. 确保JEE上的AEM 6.4 Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关支持的硬件和软件的信息，请参阅[支持的平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md)文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，请对在JEE上的AEM Forms上运行的存储库持久性和文档服务使用单一数据库。


1. 执行升级：

   1. 通过运行安装项目，在新服务器上的JEE上安装AEM 6.4 Forms。 安装程序将所有所需文件放置在计算机上的一个安装目录结构中。
   1. 安装完成后，运行&#x200B;**Configuration Manager**&#x200B;以配置各种AEM Forms模块并设置适当的配置。 除了配置设置，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在“升级任务选择”屏幕上，选择&#x200B;**[!UICONTROL 从Adobe Experience Manager Forms 6.2.0]**&#x200B;升级选项。 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0]**&#x200B;升级选项允许配置管理器从LiveCycle ES4 SP1升级到AEM 6.4 Forms。

   1. (AEM Forms 文档安全模块不需要)将内容导入到内容存储库(CRX-Repository)到AEM 6.4 Forms服务器。

      >[!NOTE]
      >
      >* 升级crx-repository并迁移内容后，请更改管理员帐户的口令。 有关详细说明，请参阅[更改现有用户的口令](/help/sites-administering/granite-user-group-admin.md)。


1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否已成功升级：

   对升级后的AEM Forms服务器执行一些例行操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的结构已更改。 升级到AEM 6.4表单后，请使用更改的路径重新创建自定义。 有关更改路径的完整列表，请参阅AEM 6.4中的[Forms存储库重组。](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycle ES4 SP1升级到AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [从LiveCycle ES4 SP1升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [从LiveCycle ES4 SP1升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss Turnkey从LiveCycle ES4 SP1升级到AEM 6.4 Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

在JEE上将LiveCycle ES3升级到AEM 6.4 Forms是一次不到位的升级，因为它涉及将资产和数据从先前版本迁移到受支持的应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycle ES3服务器升级到AEM 6.4 Forms的过程概述。 有关详细说明，请参阅在过程末尾列出的文档。

1. 升级前：

   1. 从[Adobe授权网站(LWS)](https://licensing.adobe.com/)下载AEM 6.4 Forms on JEE安装程序。 您需要一个有效的维护和支持合同来下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数AEM Forms在JEE功能上使用内容存储库持久性来存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在AEM Forms、Adaptive Forms、Correspondence Management、HTML5 Forms、Forms Portal、HTML Workspace、Process 报告和以Forms为中心的OSGi功能工作流中，使用内容存储库。 如果您计划使用AEM Forms进行这些功能，则需要“内容存储库”。
      * 您不需要Content Repository来实现AEM Forms 文档 Security。

      此外，LiveCycle和AEM Forms的存储库类型不同。 有关可用的存储库类型和相关信息，请参阅[为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 创建LiveCycle ES3存储库、全局数据(GDS)和内容存储库的备份(文档安全性不需要)。 如果您要升级到MongoMK或RDBMK持久性，请将LiveCycle ES3通信管理资源导出为存档。
   1. 确保JEE上的AEM 6.4 Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关支持的硬件和软件的信息，请参阅[支持的平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md)文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，请对在JEE上的AEM Forms上运行的存储库持久性和文档服务使用单一数据库。


1. 执行升级：

   1. 通过运行安装项目，在新服务器上的JEE上安装AEM 6.4 Forms。 安装程序将所有所需文件放置在计算机上的一个安装目录结构中。
   1. 安装完成后，运行&#x200B;**Configuration Manager**&#x200B;以配置各种AEM Forms模块并设置适当的配置。 除了配置设置，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在“升级任务选择”屏幕上，选择&#x200B;**[!UICONTROL 从Adobe Experience Manager Forms 6.2.0]**&#x200B;升级选项。 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0]**&#x200B;升级选项允许配置管理器从LiveCycle ES3升级到AEM 6.4 Forms。

   1. (AEM Forms 文档安全模块不需要)升级CRX存储库并将它导入AEM 6.4 Forms服务器。

      >[!NOTE]
      >
      >升级crx-repository并迁移内容后，请更改管理员帐户的口令。 有关详细说明，请参阅[更改现有用户的口令](/help/sites-administering/granite-user-group-admin.md)。
1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否已成功升级：

   对升级后的AEM Forms服务器执行一些例行操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的结构已更改。 升级到AEM 6.4表单后，请使用更改的路径重新创建自定义。 有关更改路径的完整列表，请参阅AEM 6.4中的[Forms存储库重组。](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycle ES3升级到AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [从LiveCycle ES3升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [从LiveCycle ES3升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Turnkey从LiveCycle ES3升级到AEM 6.4 Forms](assets/upgrade-turnkey-livecycle-es3.pdf)
