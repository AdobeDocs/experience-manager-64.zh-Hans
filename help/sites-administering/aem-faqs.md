---
title: AEM常见问题解答
seo-title: AEM 6.4常见问题解答
description: 使用这些常见问题解答来了解、配置和解决AEM中常见的工作流程或问题。
seo-description: 使用这些常见问题解答来了解、配置和解决AEM中常见的工作流程或问题。
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd

---


# AEM常见问题解答{#aem-faqs}

可查看本页以获取某些AEM疑难解答和配置问题的解答。

## 站点 {#sites}

### 如何配置无二进制分发？ {#how-do-i-configure-binary-less-distribution}

通过共享数据存储进行部署支持无二进制分发，并且涉及使用基于Vault的分发包导出器(工厂PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`)包构建器。

启用无二进制模式后，分发的内容包中包含对二进制的引用，而不是实际的二进制。

### 如何启用无二进制分发？ {#how-do-i-enable-binary-less-distribution}

要启用无二进制分发，请使用共享的blob存储进行部署。\
使用 `useBinaryReferences` 您的代理所使用的工厂PID()检查OSGI配置中 `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*的属性&#x200B;*。

### 如何在AEM站点控制台中导航页面层次结构时自定义错误消息？ {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

检查个人设置（JS尚未缩小）的“网络”面板（Chrome浏览器）。

查看列 `Initiator` 以确定请求的发起者是什么。 它提供从中发出AJAX调用的文件和行号。 稍后，您可以跟踪错误处理函数并根据需要更改错误消息。

### 如何在AEM中为内容作者创建语言副本时启用权限？ {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

要创建语言复制功能，内容作者需要在位置获得 `/content/projects` 权限。

如果作者也需要管理项目，则解决方法是将作者添加到组 `project-administrators` 中。

### 如何在为项目创建语言副本时更改格式？ {#how-to-change-the-format-while-creating-language-copy-for-a-project}

在创建翻译项目之前，在根中创建语言根和语言副本。

例如，\
在创建名为( `/content/geometrixx` 标题为法语( `fr_LU` 卢森堡))的语言根目录。 随后，从引用面板中创建页面的语言副本，并导航到中 `Create structure only` 的选项 `Create & Translate`。 最后，创建翻译项目，然后将语言副本添加到翻译作业。

有关详细信息，请参阅以下其他资源：

* [准备翻译内容](/help/sites-administering/tc-prep.md)
* [管理翻译项目](/help/sites-administering/tc-manage.md)

### 如何审核AEM功能，如登录尝试次数和ACL或权限更改？ {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM引入了记录管理更改的功能，以便更好地进行疑难解答和审核。 默认情况下，信息记录在文 `error.log` 件中。 为了简化监控，建议将它们重定向到单独的日志文件。\
要将输出重定向到单独的日志文件，请参 [阅如何审核AEM中的用户管理操作](/help/sites-administering/audit-user-management-operations.md)。

### 默认情况下如何启用SSL? {#how-to-enable-ssl-by-default}

Adobe Experience Manager(AEM)6.4随SSL向导一起提供，并提供一个用户界面来配置Jetty和Granite Jetty SSL支持。

要在默认情况下启用SSL，请 [参阅SSL](/help/sites-administering/ssl-by-default.md)。

### 从移动应用程序使用AEM内容服务时，建议采用什么架构，最好是React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

内容服务基于Sling Models,AEM开发人员必须为导出的每个组件提供Sling Model程序。

要了解如何从React应用程序使用AEM内容服务，请参 [阅AEM内容服务入门](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) 教程。

此外，如果开发人员希望导出组件树，他们还可以实现和接 `ComponentExporter` 口 `ContainerExporter` ，以及使用 `ModelFactory` 遍历子组件并返回其模型表示。 请参阅以下资源：

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling::Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### 如何禁用AEM 6.4调查弹出窗口？ {#how-to-disable-aem-survey-pop-up}

您可以使用触控UI或Web控制台来选择收集使用情况统计信息。 有关详细说明，请参 [阅选择汇总的使用统计信息收集](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)。

### 是否有一个不错的资源突出显示了升级到AEM 6.4的主要功能？ {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

请参阅 [了解升级AEM的理由](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) ，其中描述了考虑升级到最新版Adobe Experience Manager的客户的主要功能的高级细分。

### 如何配置AEM实例以使用PorterStem滤镜？ {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem过滤器采用Porter Stem英语词干算法。 结果与使用Snowball Porter Stemmer语言=&quot;English&quot; *参数类似* 。 但是，该调节器直接使用Java编码，并且不基于Snowball。 它不接受保护单词列表，并且仅适用于英语文本。

Oak公开了一组Lucene提供的分析器配置元素，以便在AEM中使用。 要了解如何使用筛选器，请参阅 **Simple搜索实施指南中的**[Apache Oak Analyzers](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)。

### 如何执行完整的重新索引？ {#how-to-perform-a-full-re-indexing}

应始终考虑重新编制索引对AEM整体性能的影响，并在活动量较低或维护时间较短的期间执行。

请参阅查 [询和索引的最佳实践](/help/sites-deploying/best-practices-for-queries-and-indexing.md) ，了解重新构建索引的原因。

### 我们是否支持Design Importer中简化的JS库？ {#do-we-support-minified-js-libs-in-design-importer}

您需要将Adobe Granite HTML库管理器的JS处理器默认configs属性更改为 ***min:gcc***。 要成功导入设计包，建议在客户端库中包含预微化的第三方库。

## 资产 {#assets}

### 上传MP4文件（例如，使用拖放方法）时，“资产”工作流为何会重复？ {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

如果用户在资产节点下上传电影文件没有删除权限，则删除区块节点将失败，并且上传将重新启动。

### 一次可用AEM 6.4操作的数字资产最大数量是多少？ {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager(AEM)6.4当前允许您一次上传最多2 GB的资产。

有关可以使用AEM 6.4操作的资产最大数量的其他信息，请参阅资产规 [模调整指南](/help/assets/assets-sizing-guide.md)。

### 创建语言副本时OOTB配置的默认设置是什么？ {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

通过经典UI创建语言副本时，资产不会移动到新语言层次结构下，而是从语言主层次结构中使用。

但是，当您通过触屏UI(**References** -> **Update Language Copy**)创建语言副本时，会使用新语言创建一个新的DAM文件夹，并从中引用资产。

这是OOTB配置的默认设置。 在翻译配置 **中，可以设置“转** 换页面资产 **=** 不翻译”。\
对于AEM 6.4,“工 **具** ”>“云服务 **”** >“翻译 **云服务”**。

### 如何禁用导致AEM SegmentStore(AEM 6.3.1.1)指数增长的AEM组件？ {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

您可以禁用OSGi组件禁用程序。 要使用此服务，请参阅 [OSGi组件禁用](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)。

作为解决方法，您还可以在每次重新启动AEM后通过UI或 `curl` 命令（示例如下）手动禁用组件。

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### 如何使用AEM 6.4实例配置资产分析？ {#how-to-configure-asset-insights-with-aem-instance}

要设置和配置通过Adobe Activation(DTM)部署的Experience Manager的资产分析，请参阅 [使用AEM资产设置资产分析](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html)。

### 如何自定义管理控制台？ {#how-to-customize-admin-consoles}

AEM提供了各种机制，使您能够自定义创作实例的控制台和页面创作功能。
要了解如何创建自定义控制台和自定义控制台的默认视图，请参阅自 [定义控制台](/help/sites-developing/customizing-consoles-touch.md)。

### CoralUI 2和基于CoralUI 3的组件之间有何区别？ {#what-is-the-difference-between-coralui-and-coralui-based-components}

为Coral3创建了一组新的Sling组件，位于 [/libs/granite/ui/components/coral/foundation下。](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) 有一组用于基于CoralUI 2的组件，另一组用于基于CoralUI 3的组件。 新集不仅是旧集的复制粘贴，还将清除它（例如，简化、删除已弃用的功能）。 因此，建议页面仅使用基于CoralUI 3的集或基于CoralUI 2的集。

要详细了解，请参阅基于CoralUI 3 [的迁移指南](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html)。

### 如何在AEM资产中自定义搜索组件？ {#how-to-customize-the-search-component-in-aem-assets}

要了解搜索提升／排名和进一步实施信息，请参阅“简单 [搜索实施指南”。](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

简单搜索实施是2017年峰会实验室AEM Search Demystifed的材料。

### 如果客户在AEM中仅购买站点许可证，他们是否仍可以访问资产？ {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

否，客户无法访问资产（或站点以外的任何内容）。 即使所有Adobe Experience Manager(AEM)内部部署都包含在JAR中，客户也只有权访问JAR中他们在其合同中获得许可的那些组件。 如果他们想要探索其他组件，可以使用AEM试用版计划最长45天，也可以签署$0销售订单，该订单授权他们评估（无生产用途）资产等指定组件。

请参阅以下资源，进一步了解AEM内部部署软件和Adobe Managed Services:

* [Adobe Experience manager内部部署软件](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 客户如何扩展页面或资产的默认属性？ {#how-to-extend-default-properties-page-or-asset}

要了解如何扩展页面或资产的默认属性，请参阅以下资源：

* [资产中的元数据架构](/help/assets/metadata-schemas.md)
* [自定义页面属性的视图](/help/sites-developing/page-properties-views.md)
