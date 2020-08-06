---
title: 使用Adobe Dimension资产
seo-title: 使用Adobe Dimension资产
description: 在AEM 3D中使用Adobe Dimension资产。
seo-description: 在AEM 3D中使用Adobe Dimension资产。
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# 使用Adobe Dimension资产 {#working-with-adobe-dimension-assets}

AEM 3D功能包支持AEM Assets、AEM Sites和AEM Screens`.dn` 的Adobe Dimension资源（文件）。

基于glTF open standard的新3D查看器为Adobe Dimension资产提供了预览、站点和屏幕查看功能。

## 关于基于云的转换服务 {#about-the-cloud-based-conversion-service}

当Dimension资产上传到AEM时，文件副本将转发到AmazonAWS托管的基于Adobe管理的云的服务。 此服务从Adobe专有Dimension文件格式转换为开放标准glTF格式。 转换的3D模型打包为二进制glTF(`.glb`)。 AEM将转换后的模型与主Dimension资产一起存储为演绎版。

您可以通过以下 `.glb` 两种方式之一配置转换格 [式(有关说明，请参](install-config-3d.md) 阅安装和配置AEM 3D):

* 包含Adobe特定扩展，以在使用AdobeglTF查看器视图AEM Assets、AEM Sites或AEM Screens的Dimension资源时最大化视觉质量。 这使再现 `.glb` 与大多数第三方应用程序不兼容。
* 排除Adobe特定扩展，以实现再现与第 `.glb` 三方应用程序的兼容性。 这限制了在AEM Assets、AEM Sites或AEM Screens（例如，没有IBL照明）观看时的视觉质量，以模拟典型的第三方应用程序的质量。

将Dimension/glTF文件传输到AmazonAWS或从AWS传输，并在AWS中实现其临时存储完全安全。 这些文件在AmazonAWS中保留的时间最短； 通常在正常操作期间不超过几分钟。

要启用对Dimension资产的支持，您必须从Adobe获取访问转换服务的凭据。 See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>如果您安装并使用提供的凭据，您理解并同意您的Adobe Dimension3D资产将转让给托管在AmazonAWS的由Adobe管理、基于云的转换服务，并由该服务进行处理。

### 《AEM Assets》 {#viewing-on-aem-assets}

AEM 3D功能包包含一个基于glTF open standard的新查看器，该标准用于视图Adobe Dimension资源。 在AEM Assets将Dimension文件或压缩的glTF打开到Detail视图或在AEM Sites使用3D组件时，会自动选择此查看器。

请注意，glTF查看器的用户界面与用于所有其他3D资产类型的标准3D查看器有些不同。

#### See also the following: {#see-also-the-following}

* [AEM 3D发行说明](/help/release-notes/aem3d-release-notes.md) ，了解适用于Dn资产和glTF查看器的限制和限制。
* [使用3D Sites组件](using-the-3d-sites-component.md) ，获取特定于Adobe Dimension资产的组件属性。
* [安装和配置AEM](install-config-3d.md) 3D以配置基于云的转换服务。

