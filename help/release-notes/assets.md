---
title: AEM Assets 发行说明
seo-title: AEM Assets
description: 特定于Adobe Experience Manager 6.4资产的发行说明。
seo-description: 特定于Adobe Experience Manager 6.4资产的发行说明。
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
translation-type: tm+mt
source-git-commit: 55e904cb24bac68c0b1bbea59786cb4c0c711d61
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 3%

---

# AEM Assets 发行说明 {#aem-assets-release-notes}

这些发行说明介绍了在AEM 6.4资产中实现的主要功能、亮点和增强功能。 有关详细信息，请访问提供的链接。

## Adobe Asset Link {#adobe-asset-link}

Adobe企业Creative Cloud中的Asset Link可简化创意人员与营销人员在内容创建过程中的协作。 它是企业版Creative Cloud中的一项新的本机功能，无需离开这些工具即可直接从Adobe Photoshop、Adobe Illustrator或Adobe InDesign连接到AEM Assets。

要进一步了解功能、先决条件以及如何访问它，请参阅[Adobe资产链接](https://helpx.adobe.com/cn/enterprise/using/adobe-asset-link.html)页面。

## 增强的智能标签(由Adobe Sensei提供支持){#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了在AEM 6.3中启动的智能标记外，还引入了基于人工智能的增强智能标记功能。

* 智能内容服务学习客户的业务分类，并使用它除通用标记外，还使用客户相关标记自动标记数字资产。 它显着提高了资产的可发现性，并缩短了上市时间。
* Adobe Sensei为智能内容服务提供支持，使您能够在业务分类上培训图像识别算法。 然后，此内容智能用于对类似资产应用相关标记。

要使用AEM Assets增强的智能标签，请安装AEM 6.4](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)的[最新服务包。

## 智能翻译搜索(由Adobe Sensei提供支持){#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4引入了智能翻译搜索功能以支持多语言搜索方案。 现在，拥有跨多个区域的全球分散团队的客户可以访问不同语言的搜索，而无需经历成本高昂且耗时的翻译工作流。

* 搜索查询无需人工干预即可翻译。
* 智能标记以英语生成，并且通过机器翻译成其他语言。
* 多语种搜索是使用支持50多种语言的开放源码库Apache Joshua构建的。

## 用户体验{#user-experience}

AEM 6.4在浏览、搜索、多页资产和管理工具等领域提供了显着的用户体验改进。 详细信息如下：

浏览改进

* 新建内容树边栏可快速导航资产层次结构。 与列表视图相结合，这将恢复经典UI交互模型以浏览资产层次结构。
* 新的键盘快捷键（如m）用于移动资产，p用于打开属性页面，Ctrl + C用于复制操作等。
* 改进了在卡和列表视图中滚动、延迟加载体验，以浏览大量资源。
* 改进了卡视图，支持基于视图设置的不同大小的卡。
* 改进了资产详细信息体验，能够视图、导航到“上一个”或“下一个”资产以及资产数量、当前资产。

搜索改进

* 新的“返回搜索”按钮，可导航到搜索项并返回到搜索结果中的相同位置，而无需再次运行搜索查询。
* 新搜索结果计数可显示搜索结果数。
* 改进的文件类型搜索筛选器，与先前的图像、文档、多媒体选项相比，能够根据细粒度的mime类型（如JPG、PNG和PSD）筛选搜索结果。
* 改进了搜索过滤器，其中包含精确的时间戳而不是以前的时间滑块功能。

多页资产改进

* 通过减少点击次数改善了多页资产浏览体验。
* 改进的注释和批注支持在资产级别而不是页面级别对所有注释进行整理。

管理工具改进

* 改进了“管理工具”中的属性选取器，用于元数据、搜索和报表（具有提前键入和浏览功能），可简化管理体验。

目录

* 改进了用户体验，与“模板”用户界面保持一致。 有关详细信息，请参阅[Catalog Producer](../sites-administering/catalog-producer.md)。

## 元数据 {#metadata}

AEM 6.4包含多种高级元数据管理功能，可通过规则和验证大规模管理元数据并加强元数据完整性。 以下是关键功能：

* 新增的批量元数据导出功能，可以以CSV格式为大量资产导出（所有、有选择）元数据，以便进行编辑、共享和第三方集成。
* 新增的批量元数据导入功能，用于导入CSV文件以添加新元数据，一次性更新多个资产的现有元数据。 此操作是异步的，不会妨碍系统性能。 完成后，用户将通过AEM Notification系统收到通知。
* 使用元数据模式工具新增的层叠和上下文元数据。 现在，可以定义依赖关系链和字段之间的值映射。 您还可以定义显示/隐藏元数据表单域的上下文。 这样，您随时都可以根据其他字段中的值显示相关字段。

## 报告 {#reports}

AEM 6.4提供了重要的资产报告增强功能：

* 新的企业级、可扩展（适用于大型存储库）报表框架应用Sling作业以异步处理报表请求。 您可以在特定日期和时间计划报表。 您还可以向报表添加自定义列。
* 新的OOTB报告最常被客户询问，如磁盘使用情况、文件、链接共享、发布到品牌门户和智能标记培训。
* 新的报表创建和管理UI，具有细粒度选项、访问归档报表的功能、查看报表运行状态（成功、失败、排队等）。

## Brand Portal {#brand-portal}

* **6.3平台升级**:Brand Portal从AEM 6.0升级到AEM 6.3，新增功能和性能改进。
* **并行发布**:在AEM Assets和Brand Portal（以前为1）之间可以进行多次复制，这显着提高了发布性能
* **模式和搜索彩块化发布**:能够将元数据模式和自定义搜索彩块化发布到Brand Portal，从而消除工作重复。
* **批量标记发布**:能够将分类（与层次结构一起）发布到Brand Portal，从而消除工作重复。
* **自注册或请求访问**:非注册用户到Brand Portal的工作流。
* **应用程序内（在屏幕上）维护通知**:通知会提前显示，以避免业务中断。
* **报告改进**:有三份OOTB报告可用：下载、发布和链接共享。
* **基于DRM的限制**:许可的资产到期后，将无法再从Brand Portal下载。

## AEM 桌面应用程序 {#aem-desktop-app}

AEM桌面应用程序已更新至版本1.8，与AEM 6.4兼容。AEM桌面应用程序的完整更改列表在专用的[AEM桌面应用程序发行说明](https://docs.adobe.com/content/help/zh-Hans/experience-manager-desktop-app/using/release-notes.html)文档中提供。\
下面是自发布AEM 6.3以来AEM桌面应用程序亮点的列表:

* 能够在后台上传分层文件夹。
* 用于在后台监视资产上传的UI。
* 缓存改进，包括用于管理缓存参数的UI。
* 对AEM身份验证配置(SAML/SSO)和网络代理的更广泛支持。
* 支持性：从用户界面轻松访问日志。
* 改进了稳定性并解决了客户问题。

为了更轻松地访问文档和最佳实践，可以使用以下文档：

* [用户指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)，面向使用该应用程序的最终用户。
* [安装指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)，面向设置AEM和AEM桌面应用程序以协同工作的管理员

## 分层存储{#tiered-storage}

AEM 6.4包含一组功能，支持各种分层存储首选项并实施生命周期规则。 存储选项还支持（但不限于）公共云 — AWS或Azure。

* 用户能够随意选择并稍后更改存储类，并定义将资产从一个类存储到另一个类的规则，或管理其资产的生命周期。
* 用户选择其他AWS或Azure来降低存储成本的能力。

有关受支持平台的概述，请参阅[技术要求文档](../sites-deploying/technical-requirements.md)。

## 已关闭的用户组 {#closed-user-group}

* 在AEM 6.4中，已关闭的用户组或CUG提供了一种限制发布实例上对文件夹访问权限的方法，通过文件夹级别的文件夹属性页面添加承担者是一个触屏UI选项，可应用于内部的所有文件夹及子文件夹/资产。
* 在发布模式下，如果已配置CUG并在文件夹上启用了授权，则当用户尝试访问该文件夹时，会将用户重定向到登录页面。 因此，授权用户只有在成功登录后才能访问文件夹及其资产。 因此，CUG限制除了所选承担者之外的所有人对内容存储库中给定树的读取访问。

## Dynamic Media加载项{#dynamic-media-add-on}

Dynamic Media 6.4中支持一种新模式，在该模式中，主控资产通过AEM Assets web UI上传和管理，而动态演绎版和其他动态媒体功能则通过Dynamic Media云投放服务在后台处理。

在此模式(首先随[AEM 6.3功能包14410和18912](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)的发行推出)中，用户可以使用现代AEM Assets Web UI从端到端资源管理和动态媒体功能中受益，同时还可以利用向后兼容Dynamic Media Classic(Scene7)的投放服务，包括未更改的投放URL。

此外，AEM 6.4还引入了以Adobe Sensei为后盾的新增功能、对VR和3D等新兴媒体的增强、Dynamic Media查看器以及交互式图像和传送横幅中的体验片段支持。

### Smart Crop(由Adobe Sensei提供支持){#smart-crop-powered-by-adobe-sensei}

* 智能裁切可自动提供图像的无损裁剪，以保留响应式设计的兴趣点。 您可以预览裁切的建议，并根据需要手动调整。
* 此功能还支持为产品图像生成自动色板。 自动生成色板有助于向产品图像自动添加色板、图案色板或两者。

请参阅[图像用户档案](../assets/image-profiles.md)文档以了解更多信息。

另请参阅[将Dynamic Media资产添加到页面](../assets/adding-dynamic-media-assets-to-pages.md)文档，以了解有关将Smart Crop与Dynamic Media组件结合使用的更多信息。

### 智能成像 {#smart-imaging}

* 智能图像处理利用每个用户的独特查看特性自动提供针对其体验优化的图像，从而提高性能和参与度。
* 图像会根据浏览器功能自动转换为不同的格式。
* 在浏览器中确定并分别应用图像质量设置。 这种智能使图像加载性能在有限的带宽和较慢的连接速度下保持可接受。

有关详细信息，请参阅[Smart Imaging](../assets/imaging-faq.md)文档。

### 新兴媒体和查看器增强功能{#emerging-media-amp-viewer-enhancements}

* 支持新查看器，为用户提供更好、身临其境的体验。
* Panoramic Viewer有助于吸引用户，并提供更好体验会议室场景、属性、位置和风景的功能。 请参阅[全景图像](../assets/panoramic-images.md)文档以了解相关信息。

* VR查看器为属性、位置和风景提供身临其境的体验。
* 为产品图像优化的垂直图像查看器。
* 键盘辅助功能改进。
