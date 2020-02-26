---
title: 使用Adobe Dimension资源
seo-title: 使用Adobe Dimension资源
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

---


# 使用Adobe Dimension资源 {#working-with-adobe-dimension-assets}

AEM 3D功能包支持AEM资产、AEM站点和AEM Screens中的Adobe Dimension`.dn` 资产（文件）。

基于glTF开放标准的全新3D查看器为Adobe Dimension资产提供预览和“站点”和“屏幕”查看功能。

## 关于基于云的转换服务 {#about-the-cloud-based-conversion-service}

将Dimension资产上传到AEM后，文件副本将转发到Amazon AWS中托管的基于Adobe管理的云的服务。 此服务从Adobe专有的Dimension文件格式转换为开放标准glTF格式。 转换的3D模型打包为二进制glTF(`.glb`)。 AEM将已转换的模型与主维资产一起存储为演绎版。

您可以通过以 `.glb` 下两种方式之一配置转换格式(有关说 [明，请参阅安装和配置AEM 3D](install-config-3d.md) ):

* 在AEM资产、AEM站点或AEM Screens中使用Adobe glTF查看器查看维资产时，包括Adobe特定扩展以最大化视觉质量。 这使再现 `.glb` 与大多数第三方应用程序不兼容。
* 排除特定于Adobe的扩展，以实现再现与 `.glb` 第三方应用程序的兼容性。 这会限制在AEM资产、AEM站点或AEM屏幕中查看时的视觉质量（例如，无IBL光照），以模拟典型的第三方应用程序的质量。

将Dimension/glTF文件传输到Amazon AWS或从Dimension/glTF文件，以及它们在AWS中的临时存储完全受到保护。 这些文件在Amazon AWS中的保存时间最短；通常，在正常操作期间不超过几分钟。

要启用维资产支持，您必须从Adobe获取访问转换服务的凭据。 See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>如果您安装和使用提供的凭据，则您理解并同意您的Adobe Dimension 3D资产将转移到Adobe管理的、由Amazon AWS托管的基于云的转换服务并由其处理。

### 在AEM资产上查看 {#viewing-on-aem-assets}

AEM 3D功能包包括一个基于glTF open standard的新查看器，该查看器用于查看Adobe Dimension资产。 在AEM资产的详细信息视图中打开维文件或压缩的glTF时，或在AEM Sites中使用3D组件时，会自动选择此查看器。

请注意，glTF查看器的用户界面与用于所有其他3D资源类型的标准3D查看器有所不同。

#### See also the following: {#see-also-the-following}

* [AEM 3D发行说明](/help/release-notes/aem3d-release-notes.md) ，了解适用于Dn资产和glTF查看器的限制和限制。
* [使用3D站点组件](using-the-3d-sites-component.md) ，获取特定于Adobe Dimension资产的组件属性。
* [安装和配置AEM 3D](install-config-3d.md) ，以配置基于云的转换服务。

