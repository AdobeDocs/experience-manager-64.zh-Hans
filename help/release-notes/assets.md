---
title: AEM Assets 发行说明
seo-title: AEM Assets
description: 特定于Adobe Experience Manager6.4资产的发行说明。
seo-description: 特定于Adobe Experience Manager6.4资产的发行说明。
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 2%

---


# AEM Assets 发行说明 {#aem-assets-release-notes}

这些发行说明介绍了AEM 6.4资产中的主要功能、亮点和增强功能。 有关详细信息，请按照提供的链接进行操作。

## Adobe Asset Link {#adobe-asset-link}

Adobe企业Creative Cloud中的资产链接简化了内容创建过程中创意人员与营销人员之间的协作。 它是企业Creative Cloud的新本机功能，可直接从Adobe Photoshop、Adobe Illustrator或Adobe InDesign连接到AEM Assets，无需离开这些工具。

要进一步了解该功能、先决条件以及如何访问它，请参阅[Adobe资产链接](https://helpx.adobe.com/cn/enterprise/using/adobe-asset-link.html)页面。

## 增强的智能标签(由Adobe Sensei提供支持){#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了在AEM 6.3中推出的智能标记外，还引入了基于人工智能的增强智能标记功能。

* 智能内容服务学习客户的业务分类，并使用它除通用标记外，还使用客户相关标记自动标记数字资产。 它显着提高了资产的可发现性，并缩短了上市时间。
* Adobe Sensei为智能内容服务提供了强大动力，它使您能够针对您的业务分类训练图像识别算法。 此内容智能随后可用于对类似资产应用相关标记。

要使用AEM Assets增强智能标记，请安装AEM 6.4](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)的[最新服务包。

## 智能翻译搜索(由Adobe Sensei提供支持){#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4引入了智能翻译搜索功能以支持多语言搜索方案。 拥有跨不同区域的全球分散团队的客户现在可以访问不同语言的搜索，而无需经历成本高昂且耗时的翻译工作流。

* 搜索查询翻译无需人工干预。
* 智能标记以英语生成，并机器翻译为其他语言。
* 多语言搜索是使用支持50多种语言的开放源码库Apache Joshua构建的。

## 用户体验{#user-experience}

AEM 6.4在浏览、搜索、多页资产和管理工具方面提供了显着的用户体验改进。 详细信息如下：

浏览改进

* 新内容树边栏可快速导航资产层次结构。 结合列表视图，此操作会恢复经典UI交互模型以浏览资产层次结构。
* 新的键盘快捷键（如移动资产的m）、打开属性页面的p、复制操作的Ctrl + C等。
* 改进了卡中的滚动、延迟加载体验以及用于浏览大量资源的列表视图。
* 改进了卡视图，支持基于视图设置的不同大小的卡。
* 改进了资产详细信息体验，能够视图、导航至“上一个”或“下一个”资产以及资产数量、当前资产。

搜索改进

* 新的“返回搜索”按钮能够导航到搜索项并返回到搜索结果中的相同位置，而无需再次运行搜索查询。
* 新搜索结果计数可显示搜索结果数。
* 改进的文件类型搜索筛选器，能够根据细粒度MIME类型（如JPG、PNG和PSD）筛选搜索结果，而以前的图像、文档和多媒体选项相比。
* 改进了具有精确时间戳而不是先前时间滑块功能的搜索过滤器。

多页资产改进

* 通过减少点击次数，改善了多页资产浏览体验。
* 改进了注释和批注功能，所有注释和批注都在资产级别而不是页面级别进行整理。

管理工具改进

* 改进了元数据、搜索和报告管理工具中具有预览类型和浏览功能的属性选取器，以简化管理体验。

目录

* 改进了用户体验，与“模板”用户界面保持一致。 有关详细信息，请参阅[Catalog Producer](../sites-administering/catalog-producer.md)。

## 元数据 {#metadata}

AEM 6.4包括多种高级元数据管理功能，可大规模管理元数据并通过规则和验证来强制实施元数据完整性。 以下是关键功能：

* 新增的批量元数据导出功能，可以以CSV格式为大量资产导出（全部、选择性）元数据，以进行编辑、共享和第三方集成。
* 新增的批量元数据导入功能可导入用于添加新元数据的CSV文件，一次性更新多个资产的现有元数据。 此操作是异步的，不会影响系统性能。 完成后，用户将通过AEM Notification系统收到通知。
* 使用元数据模式工具新增的层叠和上下文元数据。 现在，可以定义依赖关系链以及字段之间的值映射。 您还可以定义显示／隐藏元数据表单字段的上下文。 这样，您随时都可以根据其他字段中的值显示相关字段。

## 报告 {#reports}

AEM 6.4提供了重要的资产报告增强功能：

* 新的企业级、可扩展（适用于大型存储库）报告框架应用Sling作业以异步处理报告请求。 您可以在特定日期和时间计划报表。 还可向报表添加自定义列。
* 新的OOTB报告最常被客户问及，如磁盘使用情况、文件、链接共享、发布到品牌门户和智能标记培训。
* 新的报表创建和管理UI，具有细粒度选项、访问归档报表的功能、查看报表运行状态（成功、失败、排队等等）。

## Brand Portal {#brand-portal}

* **6.3平台升级**:Brand Portal从AEM 6.0升级到AEM 6.3，新增功能和性能改进。
* **并行发布**:在AEM Assets和Brand Portal（以前为1）之间可进行多次复制，这显着提高了发布性能
* **模式和搜索彩块化发布**:能够将元数据模式和自定义搜索彩块化发布到Brand Portal，从而消除工作重复。
* **批量标记发布**:能够将分类（与层次结构一起）发布到Brand Portal，从而消除重复工作。
* **自注册或请求访问权限**:非注册用户到Brand Portal的工作流。
* **应用程序内（在屏幕上）维护通知**:通知会提前显示，以避免业务中断。
* **报告改进**:有三种OOTB报告可用：下载、发布和链接共享。
* **基于DRM的限制**:许可的资产到期后，不再可从Brand Portal下载。

## AEM 桌面应用程序 {#aem-desktop-app}

AEM桌面应用程序已更新至版本1.8，与AEM 6.4兼容。AEM桌面应用程序的完整更改列表在专用的[AEM桌面应用程序发行说明](https://docs.adobe.com/content/help/zh-Hans/experience-manager-desktop-app/using/release-notes.html)文档中提供。\
以下是发布AEM 6.3以来AEM桌面应用程序的列表重点：

* 能够在后台上传分层文件夹。
* 用于在后台监视资产上传的UI。
* 缓存改进，包括用于管理缓存参数的UI。
* 对AEM身份验证配置(SAML/SSO)和网络代理的更广泛支持。
* 支持性：从用户界面轻松访问日志。
* 改进了客户问题的稳定性和修复。

为了更轻松地访问文档和最佳实践，可使用以下文档：

* [用户指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)，面向使用该应用程序的最终用户。
* [安装指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)，旨在为管理员设置AEM和AEM桌面应用程序以进行协作

## 分层存储{#tiered-storage}

AEM 6.4包含一套功能，支持各种分层存储首选项并实施生命周期规则。 存储选项还支持（但不限于）公共云- AWS或Azure。

* 用户可以随意选择和稍后更改存储类，并定义资产从一个类存储到另一个类的规则，或管理资产的生命周期。
* 用户能够通过选择其他AWS或Azure降低存储成本。

有关受支持平台的概述，请参阅[技术要求文档](../sites-deploying/technical-requirements.md)。

## 已关闭的用户组 {#closed-user-group}

* 在AEM 6.4中，已关闭的用户组或CUG提供了一种限制发布实例上文件夹访问权限的方法，它是一个触屏UI选项，可通过文件夹级别的文件夹属性页面添加承担者，并将应用于内部的所有文件夹及子文件夹／资产。
* 在发布模式下，如果已配置CUG并在文件夹上启用授权，则当用户尝试访问该文件夹时，会将用户重定向到登录页面。 因此，授权用户只有在成功登录后才能访问文件夹及其资产。 因此，CUG限制除了所选承担者以外的所有人对内容存储库中给定树的读取访问。

## Dynamic Media加载项{#dynamic-media-add-on}

Dynamic Media6.4版支持新模式——在该模式下，主控资产通过AEM Assets网络UI上传和管理，而Dynamic Media云投放服务在后台处理动态演绎版和其他动态媒体功能。

在此模式中(首先推出[AEM 6.3功能包14410和18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html))，用户可以使用现代的AEM AssetsWeb UI从端到端资源管理和动态媒体功能中受益，同时仍可利用与Dynamic Media经典(Scene7)向后兼容的投放服务，包括投放URL，但未更改。

此外，AEM 6.4引入了以Adobe Sensei为后盾的新增功能、对VR和3D等新兴媒体的增强、Dynamic Media查看器以及交互式图像和传送横幅中的体验片段支持。

### Smart Crop(由Adobe Sensei提供支持){#smart-crop-powered-by-adobe-sensei}

* 智能裁切可自动提供图像的无损裁剪，以保留响应式设计的兴趣点。 您可以预览裁剪建议并根据需要手动调整它们。
* 此功能还支持为产品图像生成自动色板。 自动生成色板有助于向产品图像自动添加色板、图案色板或两者。

请参阅[图像用户档案](../assets/image-profiles.md)文档以了解更多信息。

另请参阅[将Dynamic Media资产添加到页面](../assets/adding-dynamic-media-assets-to-pages.md)文档，进一步了解如何将智能裁剪与Dynamic Media组件结合使用。

### 智能图像处理 {#smart-imaging}

* 智能图像处理利用每个用户独特的查看特性自动提供为其体验优化的图像，从而获得更好的性能和参与度。
* 图像会根据浏览器功能自动转换为不同格式。
* 在浏览器中确定并分别应用图像质量设置。 这种智能使有限带宽和慢连接速度下的图像加载性能保持可接受。

请参阅[智能成像](../assets/imaging-faq.md)文档以了解更多信息。

### 新兴媒体和查看器增强功能{#emerging-media-amp-viewer-enhancements}

* 支持新查看器，为用户提供更好、身临其境的体验。
* 全景查看器有助于吸引用户，并提供更好地体验会议室场景、属性、位置和风景的能力。 请参阅[全景图像](../assets/panoramic-images.md)文档以了解相关信息。

* VR查看器为属性、位置和风景提供身临其境的体验。
* 为产品图像优化的垂直图像查看器。
* 键盘辅助功能改进。

### 3D以及与DimensionCC {#d-and-integration-with-dimension-cc}的集成

已引入与[Adobe Dimension CC](https://www.adobe.com/products/dimension.html)的集成，以实现更无缝的3D工作流程。 要了解更多信息，请参阅[使用3D资产](../assets/assets-3d.md)文档。
