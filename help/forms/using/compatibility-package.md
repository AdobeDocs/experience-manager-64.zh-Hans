---
title: 兼容包
seo-title: Compatibility Package
description: '在AEM Forms 6.4上安装兼容包，允许您使用AEM Forms 6.3中的通信管理资产以及已弃用的自适应表单模板和页面 '
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 安装兼容包 {#compatibility-package}

在AEM Forms 6.4上安装兼容包，允许您使用AEM Forms 6.3中的通信管理资产以及已弃用的自适应表单模板和页面

## 概述 {#overview}

在AEM Forms 6.4中创建客户通信的默认和推荐方法是交互式通信。要继续使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，您需要安装[AEMFD兼容包](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)。

AEMFD兼容包允许您在AEM Forms 6.4上使用AEM Forms 6.3和6.2中的以下资产：

* 在AEM Forms 6.3和6.2中创建的文档片段
* 书信
* 数据字典
* 自适应表单已弃用的模板和页面

有关更多信息，请参阅[通过安装兼容包](/help/forms/using/compatibility-package.md#assetsmadecompatible)与AEM Forms 6.4兼容的资产。

## 在AEM Forms 6.4中添加对AEM Forms 6.3和6.2资产的支持 {#add-support-for-aem-forms-and-assets-in-aem-forms}

执行升级后，请执行以下操作以安装AEMFD兼容包，并使资产与6.4兼容：

确保已预安装[AEM兼容包](/help/sites-deploying/backward-compatibility.md)。

1. 安装[兼容包](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)。

   有关上载和安装包的详细信息，请参阅[如何使用包](/help/sites-administering/package-manager.md)。

1. 日志稳定后，重新启动服务器。
1. 使用迁移实用程序使资产与6.4兼容。

   有关更多信息，请参阅[迁移实用程序](/help/forms/using/migration-utility.md)。

## 通过安装兼容包，与AEM Forms 6.4兼容的资产 {#assetsmadecompatible}

通过安装兼容包，您可以使以下资产和模板与AEM Forms 6.4兼容：

* 来自AEM 6.3及更早版本的通信管理资产

   * [书信](/help/forms/using/create-letter.md)
   * [数据字典](/help/forms/using/data-dictionary.md)
   * 文档片段

* 已弃用的自适应表单模板

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrommentTemplate
   * /libs/fd/afaddon/templates/advancedEnrommentTemplate2

* 已弃用自适应表单页面：

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
