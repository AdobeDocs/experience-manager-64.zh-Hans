---
title: 兼容性包
seo-title: 兼容性包
description: '在AEM Forms 6.4上安装兼容性包可让您使用AEM Forms 6.3中的Correspondence Management资源和已弃用的自适应表单模板和页面 '
seo-description: 在AEM Forms 6.4上安装兼容性包可让您使用AEM Forms 6.3中的Correspondence Management资源和已弃用的自适应表单模板和页面
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: 管理员
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 9%

---


# 安装兼容性包{#compatibility-package}

在AEM Forms 6.4上安装兼容性包可让您使用AEM Forms 6.3中的Correspondence Management资源和已弃用的自适应表单模板和页面

## 概述 {#overview}

在AEM Forms 6.4中，交互通信是创建客户通信的默认和推荐方法。要继续使用AEM 6.3 Forms和AEM 6.2 Forms的字母，您需要安装[AEMFD兼容性包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

AEMFD兼容性包允许您在AEM Forms 6.4上使用AEM Forms 6.3和6.2的以下资源：

* 在AEM Forms 6.3和6.2中创建的文档片段
* 书信
* 数据字典
* 自适应表单已弃用的模板和页面

有关详细信息，请参阅[通过安装兼容性包](/help/forms/using/compatibility-package.md#assetsmadecompatible)使资产与AEM Forms 6.4兼容。

## 在AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}中添加对AEM Forms 6.3和6.2资源的支持

执行升级后，请执行以下操作来安装AEMFD兼容性包并使您的资源与6.4兼容：

确保您预装了[AEM Compatibility包](/help/sites-deploying/backward-compatibility.md)。

1. 安装[兼容性包](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)。

   有关上载和安装包的详细信息，请参阅[如何使用包](/help/sites-administering/package-manager.md)。

1. 日志稳定后，重新启动服务器。
1. 使用迁移实用程序使您的资源与6.4兼容。

   有关详细信息，请参阅[迁移实用程序](/help/forms/using/migration-utility.md)。

## 通过安装兼容性包{#assetsmadecompatible}使资源与AEM Forms 6.4兼容

通过安装兼容性包，您可以使以下资源和模板与AEM Forms 6.4兼容：

* 来自AEM 6.3及更早版本的Correspondence Management Assets

   * [书信](/help/forms/using/create-letter.md)
   * [数据字典](/help/forms/using/data-dictionary.md)
   * 文档片段

* 自适应表单已弃用模板

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnmortmentTemplate
   * /libs/fd/af/templates/simpleEnmortmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnmortmentTemplate
   * /libs/fd/af/templates/tabbedEnmortmentTemplate2
   * /libs/fd/afaddon/templates/advancedEngromentTemplate
   * /libs/fd/afaddon/templates/advancedEnmortmentTemplate2

* 自适应表单已弃用的页面：

   * /libs/fd/af/components/page/调查
   * /libs/fd/af/components/page/tabberollment
   * /libs/fd/afaddon/components/page/advancedenrollment

