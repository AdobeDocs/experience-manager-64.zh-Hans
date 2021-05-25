---
title: AEM Assets 发行说明
seo-title: AEM Assets
description: 特定于Adobe Experience Manager 6.4 Assets的发行说明。
seo-description: 特定于Adobe Experience Manager 6.4 Assets的发行说明。
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 55e904cb24bac68c0b1bbea59786cb4c0c711d61
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 3%

---

# AEM Assets 发行说明 {#aem-assets-release-notes}

AEM 6.4 Assets中的主要功能、亮点和增强功能在这些发行说明中进行了介绍。 有关详细信息，请遵循提供的链接。

## Adobe Asset Link {#adobe-asset-link}

企业Creative Cloud中的Adobe资产链接可简化内容创建过程中创意人员和营销人员之间的协作。 它是企业Creative Cloud中的一项新本机功能，可直接从Adobe Photoshop、Adobe Illustrator或Adobe InDesign连接到AEM Assets，而无需离开这些工具。

要详细了解该功能、先决条件以及如何访问该功能，请参阅[Adobe资产链接](https://helpx.adobe.com/cn/enterprise/using/adobe-asset-link.html)页面。

## 增强型智能标记(由Adobe Sensei提供支持){#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4除了AEM 6.3中启动的智能标记之外，还引入了基于人工智能的增强型智能标记功能。

* 智能内容服务会学习客户的业务分类，并使用该分类，除通用标记外，还使用客户相关标记自动标记数字资产。 它显着提高了资产发现能力并缩短了上市时间。
* Adobe Sensei支持智能内容服务，该服务允许您根据业务分类培训图像识别算法。 然后，可使用此内容智能对类似资产应用相关标记。

要使用AEM Assets增强型智能标记，请安装AEM 6.4](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)的最新Service Pack [。

## 智能翻译搜索(由Adobe Sensei提供支持){#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4引入了智能翻译搜索功能，以支持多语言搜索方案。 现在，跨多个区域设置的全球分散团队客户可以访问不同语言的搜索功能，而无需执行成本高昂且耗时的翻译工作流程。

* 搜索查询无需人工干预即可翻译。
* 智能标记以英语生成，并可以机器翻译成其他语言。
* 多语言搜索是使用支持50多种语言的开源库Apache Joshua构建的。

## 用户体验{#user-experience}

AEM 6.4在浏览、搜索、多页面资产和管理工具方面提供了显着的用户体验改进。 详细信息如下：

浏览改进

* 新增了内容树边栏，可快速导航资产层次结构。 与列表视图结合使用，这会恢复经典UI交互模型以浏览资产层次结构。
* 新增了键盘快捷键，如移动资产的m、打开属性页面的p、复制操作的Ctrl + C等。
* 改善了在卡片视图和列表视图中浏览大量资产时的滚动和延迟加载体验。
* 改进了卡片视图，支持根据视图设置不同大小的卡片。
* 改善了资产详细信息体验，能够查看、导航到“上一个”或“下一个”资产以及资产数量和当前资产。

搜索改进

* 新的“返回搜索”按钮，能够导航到搜索项目并返回到搜索结果中的相同位置，而无需再次运行搜索查询。
* 新的搜索结果计数可显示搜索结果的数量。
* 改进了文件类型搜索过滤器，与以前的图像、文档、多媒体选项相比，该过滤器能够根据细粒度mime类型（如JPG、PNG和PSD）筛选搜索结果。
* 改进了具有准确时间戳而不是先前时间滑块功能的搜索过滤器。

多页面资产改进

* 通过减少点击次数，改进了多页面资产浏览体验。
* 改进了注释和批注支持，所有这些注释和批注都在资产级别而不是页面级别进行整理。

管理工具改进

* 改进了“管理工具”中的属性选取器，用于元数据、搜索和报表，具有提前类型和浏览功能，可简化管理体验。

目录

* 改善了用户体验，与“模板”用户界面保持一致。 有关详细信息，请参见[目录制作者](../sites-administering/catalog-producer.md)。

## 元数据 {#metadata}

AEM 6.4包含多种高级元数据管理功能，可大规模管理元数据，并通过规则和验证强制实现元数据完整性。 以下是关键功能：

* 新增了批量元数据导出功能，可将大量资产的元数据（全部为选择性的）导出为CSV格式，以便进行编辑、共享和第三方集成。
* 新增了批量元数据导入功能，可导入CSV文件以添加新元数据，从而一次性更新多个资产的现有元数据。 此操作是异步的，不会影响系统性能。 完成后，将通过AEM通知系统通知用户。
* 使用元数据架构工具新增了级联和上下文元数据。 现在，可以定义依赖关系链和字段之间的值映射。 您还可以定义显示/隐藏元数据表单字段的上下文。 这样，您就可以随时根据其他字段中的值显示相关字段。

## 报告 {#reports}

AEM 6.4提供了显着的资产报告增强功能：

* 新的企业级、可扩展（适用于大型存储库）的报表框架应用了Sling作业以异步处理报表请求。 您可以安排在特定日期和时间进行报表。 您还可以向报表添加自定义列。
* 新的OOTB报表最常由客户提出，例如磁盘使用、文件、链接共享、发布到Brand Portal和智能标记培训。
* 新的报表创建和管理UI，具有细粒度选项、访问已存档报表的功能，以及查看报表运行状态（成功、失败、排队等）。

## Brand Portal {#brand-portal}

* **6.3平台升级**:Brand Portal从AEM 6.0升级到AEM 6.3，新增功能和性能改进。
* **并行发布**:在AEM Assets和Brand Portal（以前为1个）之间最多可以进行复制，这显着提高了发布性能
* **架构和搜索Facet发布**:能够将元数据架构和自定义搜索彩块化发布到Brand Portal，从而消除工作重复。
* **批量标记发布**:能够将分类（以及层次结构）发布到Brand Portal，从而消除重复工作。
* **自注册或请求访问权限**:非注册用户的工作流程到Brand Portal。
* **应用程序内（在屏幕上）维护通知**:通知会提前显示，以避免业务中断。
* **报表改进**:提供了三份OOTB报告：下载、发布和链接共享。
* **基于DRM的限制**:授权资产过期后，将无法再从Brand Portal下载。

## AEM 桌面应用程序 {#aem-desktop-app}

AEM桌面应用程序已更新至版本1.8，该版本与AEM 6.4兼容。AEM桌面应用程序的完整更改列表在专用的[AEM桌面应用程序发行说明](https://docs.adobe.com/content/help/zh-Hans/experience-manager-desktop-app/using/release-notes.html)文档中提供。\
以下是自AEM 6.3发布以来AEM桌面应用程序亮点列表：

* 能够在后台上传分层文件夹。
* 用于在后台监控资产上传的UI。
* 缓存改进，包括用于管理缓存参数的UI。
* 更广泛地支持AEM身份验证配置(SAML/SSO)和网络代理。
* 可支持性：从用户界面轻松访问日志。
* 改进了客户问题的稳定性和修复。

为了更便于访问文档和最佳实践，提供了以下文档：

* [用户指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)，面向使用应用程序的最终用户。
* [安装指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)，旨在帮助管理员设置AEM和AEM桌面应用程序以便协同工作

## 分层存储{#tiered-storage}

AEM 6.4包含一组功能，这些功能支持各种分层存储首选项并实施生命周期规则。 存储选项还支持（但不限于）公共云 — AWS或Azure。

* 用户可以随意选择并稍后更改存储类，并定义用于将资产从一个类存储到另一个类的规则，或管理其资产的生命周期。
* 用户可以通过选择其他AWS或Azure降低存储成本。

有关受支持平台的概述，请参阅[技术要求文档](../sites-deploying/technical-requirements.md)。

## 已关闭的用户组 {#closed-user-group}

* 在AEM 6.4中，已关闭的用户组或CUG提供了一种方法来限制发布实例上对文件夹的访问，该方法是一个触屏UI选项，用于通过文件夹级别的文件夹属性页面添加主体，并将其应用于内部的所有文件夹和子文件夹/资产。
* 在发布模式下，如果配置了CUG并在文件夹上启用了授权，则当用户尝试访问该文件夹时，会将用户重定向到登录页面。 因此，授权用户只能在成功登录后才能访问文件夹及其资产。 因此，CUG会限制除选定承担者外的每个人对内容存储库中给定树的读取访问权限。

## Dynamic Media附加组件{#dynamic-media-add-on}

Dynamic Media 6.4中的Dynamic Media支持一种新模式，在该模式中，主控资产通过AEM Assets web UI上传和管理，而云交付服务会在后台处理动态演绎版和其他动态媒体功能。

在此模式下(首先随[AEM 6.3功能包14410和18912](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)的发布而引入)，用户可以使用现代AEM Assets Web UI从端到端资产管理和Dynamic Media功能中受益，并且仍然利用向后兼容的交付服务（包括未更改的交付URL）。

此外，AEM 6.4还引入了由Adobe Sensei提供支持的新功能、对VR和3D等新兴媒体的增强、Dynamic Media查看器，以及对交互式图像和传送横幅中的体验片段的支持。

### 智能裁剪(由Adobe Sensei提供支持){#smart-crop-powered-by-adobe-sensei}

* 智能裁剪可自动提供图像的无损裁剪以保留响应式设计的目标点。 您可以预览裁剪的建议，并在必要时手动调整这些建议。
* 此功能还支持为产品图像自动生成色板。 自动生成色板有助于将颜色色板、图案色板或两者自动添加到产品图像。

请参阅[图像配置文件](../assets/image-profiles.md)文档，以了解更多信息。

另请参阅[将Dynamic Media资产添加到页面](../assets/adding-dynamic-media-assets-to-pages.md)文档，了解有关将智能裁剪与Dynamic Media组件结合使用的更多信息。

### 智能成像 {#smart-imaging}

* 智能成像功能利用每个用户的独特查看特性自动为针对其体验优化的图像提供服务，从而提高性能和参与度。
* 图像会根据浏览器功能自动转换为不同的格式。
* 在浏览器中确定并分别应用图像质量设置。 这种智能使有限带宽和慢连接速度下的映像加载性能保持可接受。

请参阅[智能成像](../assets/imaging-faq.md)文档，以了解更多信息。

### 新兴媒体和查看器增强功能{#emerging-media-amp-viewer-enhancements}

* 支持新查看器，为用户提供更好、沉浸式的体验。
* 全景查看器有助于吸引用户，并提供更好体验文件室场景、属性、位置和景观的功能。 请参阅[全景图像](../assets/panoramic-images.md)文档以了解相关信息。

* VR查看器为属性、位置和风景提供沉浸式体验。
* 针对产品图像优化的垂直图像查看器。
* 键盘辅助功能改进。
