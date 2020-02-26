---
title: AEM Assets 发行说明
seo-title: AEM Assets
description: Adobe Experience Manager 6.4 Assets的特定发行说明。
seo-description: Adobe Experience Manager 6.4 Assets的特定发行说明。
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: 2411f1aa2853a161603d15917102d5cf1a8139b6

---


# AEM Assets 发行说明 {#aem-assets-release-notes}

AEM 6.4资产中的主要功能、亮点和增强功能在这些发行说明中进行了介绍。 有关详细信息，请按照提供的链接进行操作。

## Adobe Asset Link {#adobe-asset-link}

适用于企业的Creative cloud中的Adobe Asset Link简化了创意人员和营销人员在内容创建过程中的协作。 它是Creative cloud企业版中新增的本机功能，可直接从Adobe Photoshop、Adobe Illustrator或Adobe inDesign连接到AEM资产。 而不用离开这些工具。

要进一步了解该功能、先决条件以及如何访问它，请参阅 [Adobe资产链接页面](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) 。

## 增强的智能标记（由Adobe Sensei提供支持） {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了在AEM 6.3中启动的智能标记之外，还引入了基于人工智能的增强智能标记功能。

* 智能内容服务学习客户的业务分类，并使用该分类自动使用与客户相关的标记和通用标记标记标记数字资产。 它显着提高了资产的可发现性，并缩短了上市时间。
* Adobe Sensei为智能内容服务提供支持，使您能够根据业务分类培训图像识别算法。 此内容智能随后可用于对类似资产应用相关标记。

要使用AEM Assets增强的智能标记，请安 [装AEM 6.4的最新Service Pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)。

## 智能翻译搜索（由Adobe Sensei提供支持） {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4引入了智能翻译搜索功能以支持多语言搜索方案。 拥有跨多个区域的全球分布团队的客户现在可以访问不同语言的搜索功能，而无需经历成本高昂且耗时的翻译工作流程。

* 搜索查询无需人工干预即可翻译。
* 智能标记以英语生成，并机器翻译为其他语言。
* 多语言搜索是使用支持50多种语言的开放源码库Apache Joshua构建的。

## 用户体验 {#user-experience}

AEM 6.4在浏览、搜索、多页资产和管理工具方面提供了显着的用户体验改进。 详细信息如下：

浏览改进

* 新内容树边栏可快速导航资产层次结构。 与列表视图相结合，这会恢复经典UI交互模型以浏览资产层次结构。
* 新的键盘快捷键（如移动资产的m）、打开属性页面的p、Ctrl + c以复制操作等。
* 改进了卡片和列表视图中的滚动和延迟加载体验，以浏览大量资源。
* 改进了卡片视图，它支持基于视图设置的不同大小的卡片。
* 改进了资产详细信息体验，能够查看、导航到“上一个”或“下一个”资产以及资产数量、当前资产。

搜索改进

* 新的“返回搜索”按钮，可导航到搜索项并返回到搜索结果中的相同位置，而无需再次运行搜索查询。
* “新搜索结果”计数可显示搜索结果数。
* 改进的“文件类型搜索过滤器”能够根据细粒度的mime类型（如JPG、PNG和PSD）筛选搜索结果，而不是以前的图像、文档和多媒体选项。
* 改进了具有精确时间戳而不是先前时间滑块功能的搜索筛选器。

多页资产改进

* 改进了多页资产浏览体验，并减少了点击次数。
* 改进的注释和注释支持，所有注释和注释都在资产级别而不是页面级别进行整理。

管理工具改进

* 改进了元数据、搜索和报告管理工具中的属性选取器，该选取器具有提前键入和浏览功能，可简化管理体验。

目录

* 改进了用户体验，与“模板”用户界面保持了一致。 有关详细信息，请参 [阅Catalog Producer](../sites-administering/catalog-producer.md)。

## 元数据 {#metadata}

AEM 6.4包括多种高级元数据管理功能，可大规模管理元数据并通过规则和验证强制实施元数据完整性。 以下是关键功能：

* 新增的批量元数据导出功能，可以以CSV格式为大量资产导出（全部、有选择）元数据，以便进行编辑、共享和第三方集成。
* 新增的批量元数据导入功能可导入用于添加新元数据的CSV文件，一次性更新多个资产的现有元数据。 此操作是异步的，不会妨碍系统性能。 完成后，用户将通过AEM的通知系统收到通知。
* 使用元数据架构工具新增的层叠和上下文元数据。 现在，可以定义依赖关系链以及字段之间的值映射。 您还可以定义显示／隐藏元数据表单字段的上下文。 这样，您可以随时根据其他字段中的值显示相关字段。

## 报告 {#reports}

AEM 6.4提供了重要的资产报告增强功能：

* 新的企业级、可扩展（适用于大型存储库）报告框架应用Sling作业以异步处理报告请求。 您可以计划特定日期和时间的报告。 您还可以向报表添加自定义列。
* 新的OOTB报告最常被客户询问，例如磁盘使用情况、文件、链接共享、发布到Brand Portal和智能标记培训。
* 新的报表创建和管理UI，具有细粒度选项、访问存档报表的功能、查看报表运行状态（成功、失败、排队等）。

## Brand Portal {#brand-portal}

* **6.3平台升级**:Brand Portal从AEM 6.0升级到AEM 6.3，并新增功能和性能改进。
* **并行发布**:在AEM资产和Brand Portal（以前为1）之间最多可以进行复制，这显着提高了发布性能
* **架构和搜索彩块化发布**:能够将元数据架构和自定义搜索彩块化发布到Brand Portal，从而消除工作重复。
* **批量标记发布**:能够将分类（以及层次结构）发布到Brand Portal，从而消除工作重复。
* **自注册或请求访问权限**:非注册用户到Brand Portal的工作流。
* **应用程序内（屏幕上）维护通知**:通知会提前显示，以避免业务中断。
* **报告改进**:有三个OOTB报告可用：下载、发布和链接共享。
* **基于DRM的限制**:许可的资产到期后，不再可从Brand Portal下载。

## AEM 桌面应用程序 {#aem-desktop-app}

AEM桌面应用程序已更新至版本1.8，该版本与AEM 6.4兼容。AEM桌面应用程序更改的完整列表在专用的 [AEM桌面应用程序发行说明文档中提供](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html) 。\
以下是自AEM 6.3发布以来AEM桌面应用程序亮点的列表：

* 能够在后台上传分层文件夹。
* 用于在后台监视资产上传的UI。
* 缓存改进，包括用于管理缓存参数的UI。
* 对AEM身份验证配置(SAML/SSO)和网络代理的更广泛支持。
* 支持性：从用户界面轻松访问日志。
* 改进了稳定性并修复了客户问题。

为了更轻松地访问文档和最佳实践，提供了以下文档：

* [用户指南](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)，面向使用该应用程序的最终用户
* [针对最终用户和管理员的最佳实践指南](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)，该指南面向
* [安装指南](https://helpx.adobe.com/experience-manager/desktop-app/install-configure-aem-desktop-app.html)，面向将AEM和AEM桌面应用程序设置为可协同工作的管理员

## 分层存储 {#tiered-storage}

AEM 6.4包含一组功能，这些功能支持各种分层存储首选项并实施生命周期规则。 存储选项还支持（但不限于）公共云- AWS或Azure。

* 用户可以随意选择和稍后更改存储类，并定义将资产从一个类存储到另一个类的规则，或管理其资产的生命周期。
* 用户能够通过选择不同的AWS或Azure降低其存储成本。

有关受支持平台的概述，请参阅技术 [要求文档](../sites-deploying/technical-requirements.md)。

## 已关闭的用户组 {#closed-user-group}

* 在AEM 6.4中，“已关闭的用户组”或“CUG”提供了一种限制发布实例对文件夹访问权限的方法，该方法是通过文件夹级别的文件夹属性页面添加承担者的触屏UI选项，并将其应用于内部的所有文件夹及子文件夹／资产。
* 在发布模式中，如果配置了CUG并对文件夹启用了授权，则当用户尝试访问该文件夹时，会将用户重定向到登录页面。 因此，授权用户只有在成功登录后才能访问文件夹及其资产。 因此，CUG限制对内容存储库中除选定承担者之外的所有人对给定树的读取访问。

## Dynamic Media add-on {#dynamic-media-add-on}

6.4版Dynamic media支持新模式——在该模式下，主资产通过AEM Assets Web UI上传和管理，而动态演绎版和其他动态媒体功能由Dynamic Media云交付服务在后台处理。

在此模式中(首先随 [AEM 6.3功能包14410和18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)发布推出)，用户可以使用现代AEM资产Web UI从端到端资产管理和动态媒体功能中受益，并且仍可利用向后兼容Dynamic Media Classic(Scene7)的交付服务，包括交付URL，它们保持不变。

此外，AEM 6.4引入了以Adobe Sensei为后盾的新增功能、对VR和3D等新兴媒体的增强、动态媒体查看器以及交互式图像和传送横幅中的体验片段支持。

### 智能裁剪（由Adobe Sensei提供支持） {#smart-crop-powered-by-adobe-sensei}

* 智能裁切自动提供图像的无损裁剪，以保留响应式设计的兴趣点。 您可以预览裁剪的建议并根据需要手动调整它们。
* 此功能还支持为产品图像生成自动色板。 自动生成色板有助于向产品图像自动添加色板、图案色板或两者。

请参 [阅图像配置文件](../assets/image-profiles.md) ，了解更多信息。

另请参 [阅将Dynamic Media资产添加到页面文档](../assets/adding-dynamic-media-assets-to-pages.md) ，进一步了解将Smart Crop与Dynamic media组件结合使用。

### 智能图像处理 {#smart-imaging}

* 智能成像利用每个用户的独特查看特性自动提供针对其体验优化的图像，从而提高性能和参与度。
* 图像会根据浏览器功能自动转换为不同的格式。
* 在浏览器中确定并分别应用图像质量设置。 这种智能使图像加载性能在有限的带宽和较慢的连接速度下保持可接受。

请参 [阅智能成像](../assets/imaging-faq.md) 文档以了解更多信息。

### 新兴媒体和查看器增强功能 {#emerging-media-amp-viewer-enhancements}

* 支持新的查看器，为用户提供更好的沉浸式体验。
* Panoramic viewer帮助用户参与其中，并提供更好体验会议室场景、属性、位置和风景的能力。 请参 [阅全景图](../assets/panoramic-images.md) 文档以了解。

* VR查看器为属性、位置和风景提供身临其境的体验。
* 为产品图像优化的垂直图像查看器。
* 键盘辅助功能改进。

### 3D以及与Dimension CC的集成 {#d-and-integration-with-dimension-cc}

现已引 [入与Adobe Dimension CC](https://www.adobe.com/products/dimension.html) 的集成，以实现更无缝的3D工作流程。 要了解更多信息，请参 [阅使用3D资产文档](../assets/assets-3d.md) 。