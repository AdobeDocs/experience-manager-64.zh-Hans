---
title: 兼容性包
seo-title: 兼容性包
description: '在AEM Forms6.4上安装兼容性软件包可让您使用AEM Forms6.3中的通信管理资源以及已弃用的自适应表单模板和页面 '
seo-description: 在AEM Forms6.4上安装兼容性软件包可让您使用AEM Forms6.3中的通信管理资源以及已弃用的自适应表单模板和页面
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: 9a2ebded0068213903020d2c5633a05b6ffb07ef
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---


# 安装兼容性包 {#compatibility-package}

在AEM Forms6.4上安装兼容性软件包可让您使用AEM Forms6.3中的通信管理资源以及已弃用的自适应表单模板和页面

## 概述 {#overview}

交互通信是在AEM Forms6.4中创建客户通信的默认和推荐方法。要继续使用AEM 6.3Forms和AEM 6.2Forms的字母，您需要安装 [AEMFD兼容性包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

AEMFD兼容性软件包允许您在AEM Forms6.3和AEM Forms6.4上使用以下来自AEMFD 6.3和6.2的资源：

* 在AEM Forms6.3和6.2中创建的文档片段
* 书信
* 数据字典
* 自适应表单已弃用的模板和页面

有关详细信息，请 [参阅通过安装兼容性包使资产与AEM Forms6.4兼容](/help/forms/using/compatibility-package.md#assetsmadecompatible)。

## 在AEM Forms6.4中增加对AEM Forms6.3和6.2资产的支持 {#add-support-for-aem-forms-and-assets-in-aem-forms}

执行升级后，请执行以下操作以安装AEMFD兼容性包并使您的资源与6.4兼容：

确保已预 [装AEM](/help/sites-deploying/backward-compatibility.md) Compatibility包。

1. 安装兼 [容性包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

   有关上传和安装包的详细信息，请参 [阅如何使用包](/help/sites-administering/package-manager.md)。

1. 日志稳定后，重新启动服务器。
1. 使用迁移实用程序使您的资源与6.4兼容。

   有关详细信息，请参阅 [迁移实用程序](/help/forms/using/migration-utility.md)。

## 通过安装兼容性包使资源与AEM Forms6.4兼容 {#assetsmadecompatible}

通过安装兼容性包，您可以使以下资源和模板与AEM Forms6.4兼容：

* AEM 6.3及更早版本的通信管理资产

   * [书信](/help/forms/using/create-letter.md)
   * [数据字典](/help/forms/using/data-dictionary.md)
   * 文档片段

* 自适应表单已弃用模板

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrommentTemplate
   * /libs/fd/af/templates/simpleEngrommentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrommentTemplate
   * /libs/fd/af/templates/tabbedEnmortmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrommentTemplate
   * /libs/fd/afaddon/templates/advancedEnmortmentTemplate2

* 自适应表单已弃用的页面：

   * /libs/fd/af/components/page/调查
   * /libs/fd/af/components/page/tabbedrent
   * /libs/fd/afaddon/components/page/advancedenrollment

