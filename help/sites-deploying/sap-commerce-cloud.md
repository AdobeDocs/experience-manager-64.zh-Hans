---
title: SAPCommerce Cloud
seo-title: SAPCommerce Cloud
description: 了解如何使用SAPCommerce Cloud部署电子商务。
seo-description: 了解如何使用SAPCommerce Cloud部署电子商务。
uuid: a16ae42b-9c33-4da8-a130-52b72a779ec7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 44dfa10f-497e-473f-95d4-8dccae7ebf8e
pagetitle: Deploying eCommerce with SAP Commerce Cloud
translation-type: tm+mt
source-git-commit: 94dbed719c2f3360db6ba5b414230fd3f79f7955
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---


# SAPCommerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>This page contains links to the hybris website. 对于某些页面，您需要帐户才能登录。

## 使用SAP部署电子商务Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>以下过程使用以下演示目录来说明部署：
>
>`Geometrixx Outdoors Site English (US)`

部署必 [需的eCommerce](#packages-needed-for-ecommerce-with-hybris) packages将提供eCommerce framework的完整功能，以及eCommerce functionality的引用实现，如与hybris实现（包括演示目录）一起提供

此选项位于Geometrixx Outdoors站点的英语(美 `/content/geometrixx-outdoors/en_US`国)分支()下：

* [产品信息](#productinformationwithcolorvariants) （如果适用，带有颜色变体）

* [购物车内容概述](#shoppingcartcontentoverview)
* [客户注册](#customersignup)[和客户登录](#customersignin)

* [访问the hybris management console](#accesstothehybrismanagementconsole)

### Technical Requirements - hybris Server {#technical-requirements-hybris-server}

The hybris extension of the eCommerce Integration Framework has beed updated to support Hybris 5(as default), while maintaining backward compatibility with [Hybris 4](/help/sites-developing/sap-commerce-cloud.md#developing-for-hybris).

>[!NOTE]
>
>* 支持up to hybris 6.4 with OCC version 2.
>* You will need Java 7 to run the [hybris 5 server.](https://www.hybris.com/en/architecture-technology)
>* AEM extension不支持 [The hybris add-on,](https://www.hybris.com/en/products/telecommunication)the Telco Accelerator, is not supported by the  extension.

>



### Packages Needed for eCommerce with hybris {#packages-needed-for-ecommerce-with-hybris}

要安装电子商务功能，您需要：

* Your hybris server
* AEM eCommerce framework:

   * 这是标准AEM安装的一部分

* AEMGeometrixx包：

   * `cq-geometrixx-all-pkg`

* AEM hybris content packages:

   * `cq-hybris-content-6.3.2`
   * hybris-specific API implementation
   * `cq-geometrixx-hybris-content-6.3.2`
   * a reference implementation to illustre use of hybris( `geometrixx-outdoors/en_US`)

### eCommerce with hybris安装 {#installation-of-ecommerce-with-hybris}

要安装完整的配置(使用演示目录，Geometrixx Outdoors)，基本步骤为：

1. [安装AEM](/help/sites-deploying/deploy.md)。
1. 安装Geometrixx全包

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. 使用包管理器安装演示内 [容包](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Download and build your hybris Server](#download-and-build-your-hybris-server)。
1. 在电子商务引擎中构建目录：

   1. [设置Geometrixx室外商店](#setup-the-geometrixx-outdoors-store)。

1. [在AEM](/help/sites-authoring/qg-page-authoring.md) 中创作您需要的任何补充页面。

>[!CAUTION]
>
>Use of the hybris server requires a separate hybris license.

>[!NOTE]
>
>对于开 [发人员](/help/sites-developing/ecommerce.md#api-documentation) ，还可下载API文档。

### Download and Build your hybris Server {#download-and-build-your-hybris-server}

此过程中的步骤将下载并构建hybris server。 It will also make the initial configurations required for the connections between hybris and cq. 此扩展随后将可用于默认设置。

>[!CAUTION]
>
>不支持早于5.5.1的Hybris版本。

>[!NOTE]
>
>要完成此操作，您需 [要在系](https://groovy-lang.org/) 统上安装Groovy。

1. Download the **hybris Commerce Suite** distribution from the hybris download site.

   >[!CAUTION]
   >
   >You will need an account(from hybris)to access this.

1. 将分发文件解压缩到所需位置（称为&lt;hybris-root-directory>）。
1. 在命令行中，执行以下操作：

   ```shell
   cd <hybris-root-directory>/bin/platform
   . ./setantenv.sh
   ant clean all 
   cd ../..
   ```

   >[!NOTE]
   >
   >执行时：
   >
   >`ant clean all`
   >
   >需 `Return` 要时按。

1. 将以下文件下载到您提取的hybris分发的根文件夹，

   ```
       <hybris-root-directory>
   ```


   [获取文件](assets/setup.groovy)

   >[!NOTE]
   >
   >For hybris 5.6.0 and later, please use the following setup.groovy.

   5.6.0及更高版本

   [获取文件](assets/setup-1.groovy)

1. 在命令行中，执行以下操作：

   * update configuration of the hybris server(as required by the extension)
   * rebuild hybris server with the modified configuration
   * 开始服务器

   ```shell
   groovy setup.groovy
   cd bin/platform
   ant clean all
   sh hybrisserver.sh
   ```

   >[!NOTE]
   >
   >根据您的系统，完成这些步骤中的几个可能需要几分钟。

1. 在您的浏览器中，导航到 **the hybris administration console** at:

   [http://localhost:9002](http://localhost:9002)

1. 单击 **初始化** ，然后确认初始化操作（因为它将删除现有数据）。

   进度将显示在控制台上，并指 `FINISHED` 示完成。

   >[!NOTE]
   >
   >根据您的系统，可能需要几分钟才能完成此操作。

### 设置Geometrixx Outdoors商店 {#setup-the-geometrixx-outdoors-store}

此过程将上传并配置演示商店——在线Geometrixx。

1. 开始您的hybris实例。 在命令行中，执行以下操作：

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. 在您的浏览器中，导航到 **the hybris management console** at:

   [http://localhost:9002/hmc/hybris](http://localhost:9002/hmc/hybris)

1. 在提要栏导航中，解 **释系统** 和 **工具**。 然后，选 **择** “导入”以打 **开向导： “CSV导入** ”窗口。
1. 在“配 **置** ”选项卡中， **上传** 以下导 **入文件**:

   [获取文件](assets/geometrixx-outdoors-export.csv)

1. 将“区域 **设置** ”设置为：

   `en_US - English (United States)`

1. Open the **Resources** tab.
1. **上传** 以下 **媒体-Zip**:

   [获取文件](assets/geometrixx-outdoors-images.zip)

1. 单击 **开始** ，以导入指定的文件。 “结 **果** ”选项卡将显示所有日志条目。

1. 单击 **完成** ，关闭导入窗口。

1. 在提要栏中，依次 **选择** System、 **Tools****、** Import。

1. **上传** 以下导 **入文件**:

   [获取文件](assets/base-store.csv)

   For hybris 5.7, please use the following:

   [获取文件](assets/base-store-5_7.csv)

1. 将“区域 **设置** ”设置为：

   `en_US - English (United States)`

1. 单击 **开始** ，以导入指定的文件。 “结 **果** ”选项卡将显示所有日志条目。

1. 单击 **完成** ，关闭导入窗口。

1. 您现在可以使用产品驾驶舱来视图导入的目录和产品：

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)

