---
title: 使用Adobe Dimension资产
description: 在AEM 3D中使用Adobe Dimension资产。
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
translation-type: tm+mt
source-git-commit: 6be46f6986d1631f711cfd4464cc4f2d17014681
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---


# 使用Adobe Dimension资产{#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>不再支持AEM 6.4中的AEM 3D功能包。 Adobe建议您将[AEM中的3D资源功能用作Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia)或[AEM 6.5.3或更高版本。](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) 与Adobe Dimension资产合作。

AEM 3D功能包支持AEM Assets、AEM Sites和AEM Screens的Adobe Dimension资源（`.dn`文件）。

基于glTF open standard的新3D查看器为Adobe Dimension资产提供了预览、站点和屏幕查看功能。

## 关于基于云的转换服务{#about-the-cloud-based-conversion-service}

当Dimension资产上传到AEM时，文件副本将转发到AmazonAWS托管的基于Adobe管理的云的服务。 此服务从Adobe专有Dimension文件格式转换为开放标准glTF格式。 转换的3D模型打包为二进制glTF(`.glb`)。 AEM将转换后的模型与主Dimension资产一起存储为演绎版。

您可以使用以下两种方式之一配置`.glb`转换格式(有关说明，请参见[安装和配置AEM 3D](install-config-3d.md)):

* 包含Adobe特定扩展，以在使用AdobeglTF查看器视图AEM Assets、AEM Sites或AEM Screens的Dimension资源时最大化视觉质量。 这使得`.glb`再现与大多数第三方应用程序不兼容。
* 排除Adobe特定扩展，以实现`.glb`再现与第三方应用程序的兼容性。 这限制了在AEM Assets、AEM Sites或AEM Screens（例如，没有IBL照明）观看时的视觉质量，以模拟典型的第三方应用程序的质量。

将Dimension/glTF文件传输到AmazonAWS或从AWS传输，并在AWS中实现其临时存储完全安全。 这些文件在AmazonAWS中保留的时间最短；通常在正常操作期间不超过几分钟。

要启用对Dimension资产的支持，您必须从Adobe获取访问转换服务的凭据。 请参阅[安装和配置AEM 3D](install-config-3d.md)。

>[!NOTE]
>
>如果您安装并使用提供的凭据，您理解并同意您的Adobe Dimension3D资产将转让给托管在AmazonAWS的由Adobe管理、基于云的转换服务，并由该服务进行处理。

### AEM Assets{#viewing-on-aem-assets}

AEM 3D功能包包含一个基于glTF open standard的新查看器，该标准用于视图Adobe Dimension资源。 在AEM Assets将Dimension文件或压缩的glTF打开到Detail视图或在AEM Sites使用3D组件时，会自动选择此查看器。

请注意，glTF查看器的用户界面与用于所有其他3D资产类型的标准3D查看器有些不同。

#### 另请参阅：{#see-also-the-following}

* [AEM 3D发行说](/help/release-notes/aem3d-release-notes.md) 明，了解适用于Dn资产和glTF查看器的限制和限制。
* [使用3D Sites组件，获](using-the-3d-sites-component.md) 取特定于Adobe Dimension资产的组件属性。
* [安装和配置AEM](install-config-3d.md)  3以配置基于云的转换服务。

