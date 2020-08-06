---
title: AEM常见问题解答
seo-title: AEM 6.4常见问题
description: 使用这些常见问题解答来了解、配置和排除AEM中常见的工作流或问题。
seo-description: 使用这些常见问题解答来了解、配置和排除AEM中常见的工作流或问题。
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---


# AEM常见问题解答{#aem-faqs}

可查看本页以获得某些AEM疑难解答和配置问题的解答。

## 站点 {#sites}

### 如何配置无二进制分发？ {#how-do-i-configure-binary-less-distribution}

通过共享数据存储进行部署支持无二进制分发，并且涉及使用基于存储库的分发包导出器(工厂PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`)package builder。

启用无二进制模式后，所分发的内容包包含对二进制的引用，而不是实际的二进制。

### 如何启用无二进制分发？ {#how-do-i-enable-binary-less-distribution}

要启用无二进制分发，请使用共享的Blob存储进行部署。\
使用 `useBinaryReferences` 您的代理正在使用的工厂PID()检查 `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*OSGI *配置中的属性。

### 如何在AEM站点控制台中导航页面层次结构时自定义错误消息？ {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

检查个人设置（JS尚未缩小）的“网络”面板（Chrome浏览器）。

视图 `Initiator` 列以确定请求的发起者。 它提供从AJAX调用开始的文件和行号。 之后，您可以跟踪错误处理函数并根据需要更改错误消息。

### 如何在AEM中创建内容作者语言副本时启用权限？ {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

要创建语言复制功能，内容作者需要在位置获得 `/content/projects` 权限。

如果还需要作者管理项目，则解决方法是将作者添加到 `project-administrators` 组。

### 如何在为项目创建语言副本时更改格式？ {#how-to-change-the-format-while-creating-language-copy-for-a-project}

在创建翻译项目之前，在根中创建语言根和语言副本。

例如，\
在创建名称为( `/content/geometrixx` 标题为 `fr_LU` 法语（卢森堡）的语言根目录。 随后，从“引用”面板创建页面的语言副本，并导航到 `Create structure only` 中的选项 `Create & Translate`。 最后，创建一个翻译项目，然后将语言副本添加到翻译作业。

有关详细信息，请参阅以下其他资源：

* [准备翻译内容](/help/sites-administering/tc-prep.md)
* [管理翻译项目](/help/sites-administering/tc-manage.md)

### 如何审核AEM功能，如登录尝试次数和ACL或权限更改？ {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM引入了记录管理更改的功能，以便更好地进行故障排除和审核。 默认情况下，该信息记录在文 `error.log` 件中。 为了简化监控，建议将它们重定向到单独的日志文件。\
要将输出重定向到单独的日志文件，请参 [阅如何审核AEM中的用户管理操作](/help/sites-administering/audit-user-management-operations.md)。

### 默认情况下如何启用SSL? {#how-to-enable-ssl-by-default}

Adobe Experience Manager(AEM)6.4随SSL向导提供，并优惠一个用户界面来配置Jetty和Granite Jetty SSL支持。

要默认启用SSL，请默 [认参阅SSL](/help/sites-administering/ssl-by-default.md)。

### 从移动应用程序使用AEM的内容服务时，推荐使用什么架构，最好是React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

内容服务基于Sling Models,AEM开发人员必须为导出的每个组件提供Sling Model pojo。

要了解如何从React应用程序使用AEM内容服务，请参 [阅AEM内容服务入门](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) 教程。

此外，如果开发人员要导出组件树，他们还可以实现 `ComponentExporter` 和 `ContainerExporter` 接口，并使用 `ModelFactory` 子组件进行迭代并返回其模型表示。 请参阅以下资源：

[1][Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] Apache [Sling: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### 如何禁用AEM 6.4调查弹出窗口？ {#how-to-disable-aem-survey-pop-up}

您可以使用触屏UI或Web控制台选择加入使用情况统计信息收集。 有关详细说明，请参 [阅选择聚合使用统计信息收集](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)。

### 是否有好的资源突出了升级到AEM 6.4的主要功能？ {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

请参阅 [了解升级AEM的理由](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) ，其中描述了考虑升级到最新版Adobe Experience Manager的客户的主要功能的高级细分。

### 如何配置AEM实例以使用PorterStem过滤器？ {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem过滤器采用Porter词干算法。 结果与用Snowball Porter Stemmer和 *language=&quot;English&quot;参数类似* 。 但是这个调节器直接使用Java编码，而不是基于Snowball。 它不接受一列表受保护的单词，并且仅适用于英语文本。

Oak公开了一组lucene提供的分析器配置元素，供AEM使用。 要了解如何使用过滤器，请参 **阅Simple搜索实** 施指 [南中的Apache Oak Analyzers](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)。

### 如何执行完整的重新索引？ {#how-to-perform-a-full-re-indexing}

应始终适当考虑重新索引对AEM总体性能的影响，并在活动或维护时间较短时执行。

请参阅查询 [和索引的最佳实践](/help/sites-deploying/best-practices-for-queries-and-indexing.md) ，了解重新索引的原因。

### 我们是否支持Design Importer中的简化JS库？ {#do-we-support-minified-js-libs-in-design-importer}

您需要将AdobeGranite HTML库管理器的JS处理器默认配置属性更改 ***为min:gcc***。 要成功导入设计包，建议在客户端库中包含预微化的第三方库。

## 资产 {#assets}

### 上传MP4文件（例如，使用拖放方法）时，“资产”工作流为何会重复？ {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

如果用户在资产节点下上传电影文件时没有删除权限，则删除区块节点将失败，并且上传将重新启动。

### 每次可使用AEM 6.4运行的最大数字资产数量是多少？ {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager(AEM)6.4当前允许您一次上传最多2 GB的资源。

有关可以使用AEM 6.4操作的最大资产数量的其他信息，请参阅资产规 [模调整指南](/help/assets/assets-sizing-guide.md)。

### 创建语言副本时OOTB配置的默认设置是什么？ {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

通过经典UI创建语言副本时，资产不会移动到新语言层次结构下，而是从语言主控使用。

但是，当您通过触屏UI(引&#x200B;**用** ->更新语 **言副本)创建语言副本时**，将使用新语言创建新的DAM文件夹，并从中引用资产。

这是OOTB配置的默认设置。 在翻译配 **置中，您可以设置** “ **翻译页面资产** =不翻译”。\
对于AEM 6.4,“工 **具** ”> **“Cloud Services** ” **>“**&#x200B;翻译云服务”。

### 如何禁用AEM组件，使AEM SegmentStore(AEM 6.3.1.1)呈指数增长？ {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

您可以禁用OSGi组件禁用程序。 要使用此服务，请参 [阅OSGi组件禁用](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)。

作为解决方法，您还可以在每次AEM重新启动后通过UI或 `curl` 命令（示例如下）手动禁用组件。

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### 如何使用AEM 6.4实例配置资产分析？ {#how-to-configure-asset-insights-with-aem-instance}

要为通过Adobe激活(DTM)部署的Experience Manager设置和配置资产分析，请参 [阅通过AEM Assets设置资产分析](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html)。

### 如何自定义管理控制台？ {#how-to-customize-admin-consoles}

AEM提供了各种机制，使您能够自定义创作实例的控制台和页面创作功能。
要了解如何创建自定义控制台和自定义控制台的默认视图，请参 [阅自定义控制台](/help/sites-developing/customizing-consoles-touch.md)。

### CoralUI 2和基于CoralUI 3的组件之间有何区别？ {#what-is-the-difference-between-coralui-and-coralui-based-components}

为Coral3创建了一套新的Granite UI Foundation的Sling组件，位于 [/libs/granite/ui/components/coral/foundation下。](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) 有一组用于基于CoralUI 2的组件，另一组用于基于CoralUI 3的组件。 新集将不仅是旧集的复制粘贴，还将清理它（例如，简化、删除已弃用的功能）。 因此，建议页面仅使用基于CoralUI 3的集或基于CoralUI 2的集。

要详细了解，请参 [阅基于CoralUI 3的迁移指南](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html)。

### 如何在AEM Assets自定义搜索组件？ {#how-to-customize-the-search-component-in-aem-assets}

要了解搜索提升／排名和进一步实施信息，请参 [阅简单搜索实施指南。](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

简单搜索实施是2017年峰会实验室AEM Search Demystified的材料。

### 如果客户仅购买AEM中的站点许可证，他们是否仍有权访问资产？ {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

否，客户无法访问资产（或站点以外的任何资产）。 尽管所有Adobe Experience Manager(AEM)内部部署都包含在JAR中，但客户只有权访问JAR中他们在合同中获得许可的那些组件。 如果他们想要探索其他组件，可以使用AEM试用项目最长45天，也可以签署$0的销售订单，授权他们评估（无生产用途）指定的组件，如资产。

请参阅以下资源，进一步了解AEM内部部署软件和Adobe Managed Services:

* [Adobe Experience Manager内部部署软件](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience ManagerManaged Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 客户如何扩展页面或资产的默认属性？ {#how-to-extend-default-properties-page-or-asset}

要了解如何扩展页面或资产的默认属性，请参阅以下资源：

* [资产中的元数据模式](/help/assets/metadata-schemas.md)
* [自定义视图页面属性](/help/sites-developing/page-properties-views.md)
