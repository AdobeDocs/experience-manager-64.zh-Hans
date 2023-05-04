---
title: 升级到 AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: 您可以从AEM 6.1 Forms、AEM 6.2 Forms和LiveCycleES4 SP1直接升级到AEM 6.3 Forms。
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# 在JEE上升级到AEM 6.4 Forms {#upgrade-to-aem-forms-jee}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

根据您的环境，使用以下升级路径之一。

## AEM 6.2 Forms on JEE，或AEM 6.3 Forms on JEE > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

请执行以下步骤，将JEE上的现有AEM 6.2 Forms或JEE上的AEM 6.3 Forms升级到JEE上的AEM 6.4 Forms:

1. 从JEE安装程序下载AEM 6.4 Forms [Adobe许可网站(LWS)](https://licensing.adobe.com/). 您需要签订有效的维护和支持合同才能下载安装程序。
1. 请参阅 [升级核对清单和规划](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) 了解要执行的检查以确保成功升级。
1. 请参阅 [准备升级到AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) 学习和执行任务，以确保升级在服务器停机时间最短的情况下正常运行。
1. 根据您现有的环境和应用程序服务器，选择以下文档之一并按照说明操作。

   * [从AEM 6.2或AEM 6.3 Forms升级到适用于JBoss的AEM 6.4 Forms](assets/upgrade-jboss.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [从AEM 6.2或AEM 6.3 Forms升级到AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

无法直接从LiveCycleES2、LiveCycleES3、AEM 6.0 Forms、AEM 6.1 Forms升级到AEM 6.4 Forms。 您可以执行到一个或多个版本的LiveCycle或AEM Forms的中间升级，然后从AEM 6.4 Forms升级。 有关中间版本的列表和相应的升级说明，请参阅 [选择升级路径](upgrade.md).

## LiveCycleES4 SP1 > JEE上的AEM 6.4 Forms {#livecycle-es4sp1-forms-jee}

在JEE上将LiveCycleES4 SP1升级到AEM 6.4 Forms是一个非就地升级，因为它涉及将资产和数据从以前的版本迁移到受支持的应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycleES4 SP1服务器升级到AEM 6.4 Forms的过程概述。 有关详细说明，请参见程序末尾列出的文档。

1. 升级前：

   1. 从JEE安装程序下载AEM 6.4 Forms [Adobe许可网站(LWS)](https://licensing.adobe.com/). 您需要签订有效的维护和支持合同才能下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数JEE上的AEM Forms功能使用内容存储库持久性来存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在LiveCycleES4 SP1中，通信管理、Forms门户、HTML工作区和流程报告功能使用内容存储库。 如果您未在LiveCycleES4中使用这些功能，并且计划不在AEM Forms中使用这些功能，则不需要内容存储库。
      * 在AEM Forms、自适应Forms、通信管理、HTML5 Forms(在LiveCycleES4 SP1中称为Mobile Forms)、Forms门户、HTML工作区、流程报告、以Forms为中心的OSGi工作流，功能使用内容存储库。 如果您计划将AEM Forms用于这些功能，则需要使用内容存储库。
      * 对于AEM Forms Document Security，您不需要内容存储库。

      此外，LiveCycle和AEM Forms的存储库类型不同。 有关可用的存储库类型和相关信息，请参阅 [为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. 创建LiveCycleES4 SP1内容和数据的备份：

      创建LiveCycleES4 SP1数据库、全局数据存储(GDS)和crx-repository的备份（文档安全不需要）。 如果您要升级到MongoMK或RDBMK持久性，请将LiveCycleES4 SP1通信管理资产导出为.cmp文件，并将资产作为AEM包表单。

   1. 确保JEE上的AEM 6.4 Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关支持的硬件和软件的信息，请参阅 [支持的平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md) 文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，请为在JEE上的AEM Forms上运行的存储库持久性和文档服务使用单个数据库。


1. 执行升级：

   1. 通过运行安装程序，在新服务器上的JEE上安装AEM 6.4 Forms。 安装程序将所有所需文件放置在一台安装目录结构中的计算机上。
   1. 安装完成后，运行 **配置管理器** 配置各种AEM Forms模块并设置相应配置。 除了配置设置之外，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在升级任务选择屏幕上，选择 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0升级]** 选项。 的 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0升级]** 选项允许配置管理器从LiveCycleES4 SP1升级到AEM 6.4 Forms。

   1. (AEM Forms文档安全模块不需要)将内容导入内容存储库(CRX-Repository)到AEM 6.4 Forms服务器。

      >[!NOTE]
      >
      >* 升级crx-repository并迁移内容后，请更改管理员帐户的密码。 有关详细说明，请参阅 [更改现有用户的密码](/help/sites-administering/granite-user-group-admin.md).


1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否成功升级：

   对已升级的AEM Forms服务器执行一些常规操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的结构已发生更改。 升级到AEM 6.4表单后，请使用更改的路径进行重新创建的自定义。 有关更改路径的完整列表，请参阅 [Forms 6.4中的存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycleES4 SP1升级到AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [从LiveCycleES4 SP1升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [从LiveCycleES4 SP1升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss Turnkey从LiveCycleES4 SP1升级到AEM 6.4 Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycleES3 > JEE上的AEM 6.4 Forms {#livecycle-es3-forms-jee}

在JEE上将LiveCycleES3升级到AEM 6.4 Forms是一个非就地升级，因为它涉及将资产和数据从以前的版本迁移到受支持的应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycleES3服务器升级到AEM 6.4 Forms的过程概述。 有关详细说明，请参见程序末尾列出的文档。

1. 升级前：

   1. 从JEE安装程序下载AEM 6.4 Forms [Adobe许可网站(LWS)](https://licensing.adobe.com/). 您需要签订有效的维护和支持合同才能下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数JEE上的AEM Forms功能使用内容存储库持久性来存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在AEM Forms、自适应Forms、通信管理、HTML5 Forms、Forms门户、HTML工作区、流程报告以及以Forms为中心的OSGi功能工作流中，使用内容存储库。 如果您计划将AEM Forms用于这些功能，则需要使用内容存储库。
      * 对于AEM Forms Document Security，您不需要内容存储库。

      此外，LiveCycle和AEM Forms的存储库类型不同。 有关可用的存储库类型和相关信息，请参阅 [为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. 创建LiveCycleES3数据库、全局数据存储(GDS)和内容存储库的备份（文档安全不需要）。 如果您要升级到MongoMK或RDBMK持久性，请将LiveCycleES3通信管理资产导出为存档。
   1. 确保JEE上的AEM 6.4 Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关支持的硬件和软件的信息，请参阅 [支持的平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md) 文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，则对JEE上在AEM Forms上运行的存储库持久性和文档服务使用单个数据库。


1. 执行升级：

   1. 通过运行安装程序，在新服务器上的JEE上安装AEM 6.4 Forms。 安装程序将所有所需文件放置在一台安装目录结构中的计算机上。
   1. 安装完成后，运行 **配置管理器** 配置各种AEM Forms模块并设置相应配置。 除了配置设置之外，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在升级任务选择屏幕上，选择 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0升级]** 选项。 的 **[!UICONTROL 从Adobe Experience Manager Forms 6.2.0升级]** 选项允许配置管理器从LiveCycleES3升级到AEM 6.4 Forms。

   1. (AEM Forms文档安全模块不需要)升级CRX存储库并将其导入AEM 6.4 Forms服务器。

      >[!NOTE]
      >
      >升级crx-repository并迁移内容后，请更改管理员帐户的密码。 有关详细说明，请参阅 [更改现有用户的密码](/help/sites-administering/granite-user-group-admin.md).
1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否成功升级：

   对已升级的AEM Forms服务器执行一些常规操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的结构已发生更改。 升级到AEM 6.4表单后，请使用更改的路径进行重新创建的自定义。 有关更改路径的完整列表，请参阅 [Forms 6.4中的存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycleES3升级到AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [从LiveCycleES3升级到AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [从LiveCycleES3升级到AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Turnkey从LiveCycleES3升级到AEM 6.4 Forms](assets/upgrade-turnkey-livecycle-es3.pdf)
