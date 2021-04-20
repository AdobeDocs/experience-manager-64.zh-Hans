---
title: 使用Adobe Dimension资源
description: 在AEM 3D中使用Adobe Dimension资源。
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 使用Adobe Dimension资源{#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>不再支持AEM 6.4中的AEM 3D功能包。 Adobe建议您使用[ AEM中的3D资源功能作为Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia)或[ AEM 6.5.3或更高版本。](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) 使用Adobe Dimension资源时。

AEM 3D功能包支持AEM Assets、AEM Sites和AEM Screens中的Adobe Dimension资源（`.dn`文件）。

基于glTF open standard的全新3D查看器为Adobe Dimension资产提供了预览、站点和屏幕查看功能。

## 关于基于云的转换服务{#about-the-cloud-based-conversion-service}

将Dimension资产上传到AEM后，文件副本将转发到Amazon AWS中托管的基于Adobe管理的云服务。 此服务从Adobe专有Dimension文件格式转换为开放标准glTF格式。 转换的3D模型打包为二进制glTF(`.glb`)。 AEM将具有主Dimension资产的已转换模型存储为演绎版。

可以使用以下两种方式之一配置`.glb`转换格式(有关说明，请参阅[安装和配置AEM 3D](install-config-3d.md)):

* 包含特定于Adobe的扩展，在使用Adobe glTF查看器在AEM Assets、AEM Sites或AEM Screens中视图Dimension资源时，可最大化视觉质量。 这使得`.glb`再现与大多数第三方应用程序不兼容。
* 排除特定于Adobe的扩展，以实现`.glb`再现与第三方应用程序的兼容性。 这限制了在AEM Assets、AEM Sites或AEM Screens（例如，无IBL照明）中查看时的视觉质量，以模拟典型的第三方应用程序的质量。

将Dimension/glTF文件传输到Amazon AWS或从Adobe AWS传输文件，以及在AWS中传输其临时存储完全受到保护。 这些文件在Amazon AWS中保留的时间最少；通常，在正常操作期间不超过几分钟。

要启用对Dimension资产的支持，您必须从Adobe获取用于访问转换服务的凭据。 请参阅[安装和配置AEM 3D](install-config-3d.md)。

>[!NOTE]
>
>如果您安装并使用提供的凭据，则您理解并同意，您的Adobe Dimension 3D资产将转让给托管在Amazon AWS中的由Adobe管理、基于云的转换服务并由其进行处理。

### 在AEM Assets上查看{#viewing-on-aem-assets}

AEM 3D功能包包含一个基于glTF open standard(用于视图Adobe Dimension资源)的新查看器。 在AEM Assets中将Dimension文件或压缩的glTF打开到Detail视图中或在AEM Sites中将3D组件打开时，会自动选择此查看器。

请注意，glTF查看器的用户界面与用于所有其他3D资源类型的标准3D查看器有所不同。

#### 另请参阅以下内容：{#see-also-the-following}

* [AEM 3D发行说](/help/release-notes/aem3d-release-notes.md) 明，了解适用于Dn资产和glTF查看器的限制和限制。
* [使用3D Sites组件，获](using-the-3d-sites-component.md) 取特定于Adobe Dimension资产的组件属性。
* [安装和配置AEM 3](install-config-3d.md) 配置基于云的转换服务。
