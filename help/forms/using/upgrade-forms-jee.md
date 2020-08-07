---
title: 升级到AEM 6.4Forms
seo-title: 升级到AEM 6.4Forms
description: '您可以从AEM 6.1Forms、AEM 6.2Forms和LiveCycleES4 SP1直接升级到6.3Forms。 '
seo-description: '您可以从AEM 6.1Forms、AEM 6.2Forms和LiveCycleES4 SP1直接升级到6.3Forms。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: ffa45c8fa98e1ebadd656ea58e4657b669ddd830
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# 升级到AEM 6.4FormsJEE版 {#upgrade-to-aem-forms-jee}

根据您的环境，使用以下升级路径之一。

## AEM 6.2FormsJEE，或AEM 6.3FormsJEE > AEM 6.4FormsJEE {#aem-forms-jee-62-63-to-64}

请按照以下步骤将JEE上的现有AEM 6.2Forms或JEE上的AEM 6.3Forms升级到JEE上的AEM 6.4Forms:

1. 从Adobe授权许可网站(LWS)下载AEM 6.4 [JEE安装程序上的Forms](https://licensing.adobe.com/)。 您需要签订有效的维护和支持合同才能下载安装程序。
1. 请参 [阅升级核对清单](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) 和计划，了解要执行的检查以确保成功升级。
1. 请参 [阅准备升级到AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) ，学习并执行确保在最短的服务器停机时间内正确运行升级的任务。
1. 根据您现有的环境和应用程序服务器，选择以下文档之一并按照说明操作。

   * [从AEM 6.2或AEM 6.3Forms升级到AEM 6.4Forms(JBoss)](assets/upgrade-jboss.pdf)
   * [从AEM 6.2或AEM 6.3Forms升级到AEM 6.4Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [从AEM 6.2或AEM 6.3Forms升级到AEM 6.4Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [从AEM 6.2或AEM 6.3Forms升级到AEM 6.4Forms，以获得JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0FormsJEE >AEM 6.3FormsJEE {#aem-forms-jee-60-to-63}

不提供从LiveCycleES2、LiveCycleES3、AEM 6.0Forms、AEM 6.1Forms直接升级到AEM 6.4Forms。 您可以执行到一个或多个版本的LiveCycle或AEM Forms的中间升级，然后从AEM 6.4Forms升级。 有关中间版本的列表和相应的升级说明，请参 [阅选择升级路径](upgrade.md)。

## LiveCycleES4 SP1 > AEM 6.4FormsJEE {#livecycle-es4sp1-forms-jee}

在JEE上将LiveCycleES4 SP1升级到AEM 6.4Forms是一次不当的升级，因为它涉及将资产和数据从先前版本迁移到受支持应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycleES4 SP1服务器升级到AEM 6.4Forms的过程概述。 有关详细说明，请参阅流程末尾列出的文档。

1. 升级前：

   1. 从Adobe授权许可网站(LWS)下载AEM 6.4 [JEE安装程序上的Forms](https://licensing.adobe.com/)。 您需要签订有效的维护和支持合同才能下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数AEM Forms的JEE功能使用内容存储库持久性存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在LiveCycleES4 SP1中，通信管理、Forms门户、HTML工作区和流程报告功能使用内容存储库。 如果您未在LiveCycleES4中使用这些功能，并且计划不在AEM Forms使用这些功能，则不需要内容存储库。
      * 在AEM Forms、Forms、Adaptive Recompense Management、HTML5Forms(在LiveCycleES4 SP1中称为Mobile Light)、Forms门户、HTML工作区、流程报告、以OSGi为中心的Forms工作流，功能使用内容存储库。 如果您计划使用AEM Forms进行这些功能，则需要内容存储库。
      * 您不需要Content Repository forAEM Forms文档安全。

      此外，LiveCycle和AEM Forms的库类型不同。 有关可用的存储库类型和相关信息，请 [参阅为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 创建LiveCycleES4 SP1内容和数据的备份：

      创建LiveCycleES4 SP1存储库、全局数据(GDS)和crx-repository的备份(文档安全性不需要)。 如果要升级到MongoMK或RDBMK持久性，请将LiveCycleES4 SP1对应管理资源以。cmp文件的形式导出，并将资源作为AEM包。

   1. 确保JEE上的AEM 6.4Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关受支持硬件和软件的信息，请参阅受 [支持平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md) 文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，请对在JEE上的AEM Forms上运行的存储库持久性和文档服务使用单一数据库。


1. 执行升级：

   1. 通过运行安装项目，在新服务器上的JEE上安装AEM 6.4Forms。 安装程序将所有所需文件放在计算机上的一个安装目录结构中。
   1. 安装完成后，运行Configuration **Manager** ，以配置各种AEM Forms模块并设置适当的配置。 除了配置设置之外，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在升级任务选择屏幕上，选 **[!UICONTROL 择从Adobe Experience Manager Forms6.2.0升级]** 。 从 **[!UICONTROL Adobe Experience Manager Forms6.2.0升级选项]** ，配置管理器可从LiveCycleES4 SP1升级到AEM 6.4Forms。

   1. (AEM Forms文档安全模块不需要)将内容导入内容存储库(CRX-Repository)至AEM 6.4Forms服务器。

      >[!NOTE]
      >
      >* 升级crx-repository并迁移内容后，请更改管理员帐户的口令。 有关详细说明，请 [参阅更改现有用户的口令](/help/sites-administering/granite-user-group-admin.md)。


1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否成功升级：

   对升级后的AEM Forms服务器执行几个常规操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4Forms,crx-repository的结构已更改。 升级到AEM 6.4表单后，请使用您重新创建的更改路径进行自定义。 有关更改路径的完整列表，请参 [阅AEM 6.4中的Forms存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)。

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycleES4 SP1升级到AEM 6.4Forms,JBoss版](assets/upgrade-jboss-livecycle.pdf)
* [从LiveCycleES4 SP1升级到AEM 6.4FormsWebLogic版](assets/upgrade-weblogic-livecycle.pdf)
* [从LiveCycleES4 SP1升级到AEM 6.4FormsWebSphere版](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss Turnkey从LiveCycleES4 SP1升级到AEM 6.4Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycleES3 > AEM 6.4FormsJEE {#livecycle-es3-forms-jee}

在JEE上将LiveCycleES3升级到AEM 6.4Forms是一次不当的升级，因为它涉及将资产和数据从先前版本迁移到受支持应用程序服务器、操作系统和数据库的新实例（新版本）。

以下是将现有LiveCycleES3服务器升级到AEM 6.4Forms的过程概述。 有关详细说明，请参阅流程末尾列出的文档。

1. 升级前：

   1. 从Adobe授权许可网站(LWS)下载AEM 6.4 [JEE安装程序上的Forms](https://licensing.adobe.com/)。 您需要签订有效的维护和支持合同才能下载安装程序。
   1. 确定要使用的内容存储库（CRX存储库）类型。 只有少数AEM Forms的JEE功能使用内容存储库持久性存储内容和资产。 仅当您计划在JEE功能上使用此类AEM Forms时，才安装和配置内容存储库：

      * 在AEM Forms、自适应Forms、通信管理、HTML5Forms、Forms门户、HTML工作区、流程报告和以Forms为中心的OSGi功能工作流使用内容存储库。 如果您计划使用AEM Forms进行这些功能，则需要内容存储库。
      * 您不需要Content Repository forAEM Forms文档安全。

      此外，LiveCycle和AEM Forms的库类型不同。 有关可用的存储库类型和相关信息，请 [参阅为AEM Forms安装选择持久性类型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 创建LiveCycleES3存储库、全局数据(GDS)和内容存储库(文档安全性不需要)的备份。 如果要升级到MongoMK或RDBMK持久性，请将LiveCycleES3对应管理资源作为存档导出。
   1. 确保JEE上的AEM 6.4Forms支持您的现有平台(即应用程序服务器、数据库、操作系统、Adobe Acrobat、第三方应用程序和硬件)。 有关受支持硬件和软件的信息，请参阅受 [支持平台组合](/help/forms/using/aem-forms-jee-supported-platforms.md) 文档。

      如果创建数据库的新实例，请将步骤3中备份的数据导入数据库。 有关如何将数据导入数据库的信息，请参阅相应数据库供应商的文档。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，请对在JEE上的AEM Forms上运行的存储库持久性和文档服务使用单一数据库。


1. 执行升级：

   1. 通过运行安装项目，在新服务器上的JEE上安装AEM 6.4Forms。 安装程序将所有所需文件放在计算机上的一个安装目录结构中。
   1. 安装完成后，运行Configuration **Manager** ，以配置各种AEM Forms模块并设置适当的配置。 除了配置设置之外，它还允许指定全局数据存储(GDS)和crx-repository的路径。

      >[!NOTE]
      >
      >在升级任务选择屏幕上，选 **[!UICONTROL 择从Adobe Experience Manager Forms6.2.0升级]** 。 从 **[!UICONTROL Adobe Experience Manager Forms6.2.0升级选项]** ，配置管理器可从LiveCycleES3升级到AEM 6.4Forms。

   1. (AEM Forms文档安全模块不需要)升级CRX存储库并将其导入AEM 6.4Forms服务器。

      >[!NOTE]
      >
      >升级crx-repository并迁移内容后，请更改管理员帐户的口令。 有关详细说明，请 [参阅更改现有用户的口令](/help/sites-administering/granite-user-group-admin.md)。
1. 根据您的用例，执行部署后任务以验证登录凭据、配置文档服务、通信管理、文档安全等。
1. 验证服务器是否成功升级：

   对升级后的AEM Forms服务器执行几个常规操作，以确保成功升级服务器。 您可以填写并提交一些迁移的表单或保护文档以确保成功升级。

   >[!NOTE]
   >
   >在AEM 6.4Forms,crx-repository的结构已更改。 升级到AEM 6.4表单后，请使用您重新创建的更改路径进行自定义。 有关更改路径的完整列表，请参 [阅AEM 6.4中的Forms存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)。

**根据您现有的环境和应用程序服务器，选择以下文档之一并按照详细说明操作：**

* [从LiveCycleES3升级到AEM 6.4Forms,JBoss版](assets/upgrade-jboss-livecycle-es3.pdf)
* [从LiveCycleES3升级到AEM 6.4FormsWebLogic版](assets/upgrade-weblogic-livecycle-es3.pdf)
* [从LiveCycleES3升级到AEM 6.4FormsWebSphere版](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Turnkey从LiveCycleES3升级到AEM 6.4Forms](assets/upgrade-turnkey-livecycle-es3.pdf)
