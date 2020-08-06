---
title: 安装功能包18912以批量迁移资产
seo-title: 安装功能包18912以批量迁移资产
description: 功能包18912允许您通过FTP批量摄取资产，或将资产从AEM中的Dynamic Media Classic迁移到Dynamic Media。 此可选功能包可从Adobe支持获得。
seo-description: 功能包18912允许您通过FTP批量摄取资产，或将资产从AEM中的Dynamic Media Classic迁移到Dynamic Media。 此可选功能包可从Adobe支持获得。
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# 安装功能包18912以进行批量资产迁移 {#installing-feature-pack}

安装功能包18912是可选 _的_。

功能包18912允许您通过FTP将资产直接批量收录到AEM的Dynamic Media - Scene 7模式，或将资产从Dynamic Media Classic迁移到AEM的Dynamic Media - Dynamic Media - Demic Made。 功能包可从Adobe Professional Services [获得](https://www.adobe.com/experience-cloud/consulting-services.html)。

>[!NOTE]
>
>虽然您可以使用功能包将资产从Dynamic Media Classic批量迁移到Dynamic Media -AEM中的Scene 7模式或使用Dynamic Media Classic中的FTP功能批量迁移资产，但由于涉及的复杂性，Adobe不 *建议使用* 此方法。
>
>因此，迁移功能包（如此）仅作为通过 *Adobe Professional Services* 的迁移项目的一部分 [受支持](https://www.adobe.com/experience-cloud/consulting-services.html)。

在安装此功能包之前，必须先创建服务用户并向Adobe提供该信息。

另请参阅 [配置Dynamic Media -Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**要安装功能包18912以进行批量资产迁移**,

1. 在AEM实例中，导航到工 **[!UICONTROL 具>安全>用户>创建用户]**。 此服务用户必须具有对的读／写权限 `/content/dam`。
1. 在ID **[!UICONTROL 和]****[!UICONTROL Password]** 字段中输入用户名和密码； 例如 `FTP User`, 此名称以创建资产的用户身份显示在时间轴中。 当资产从FTP上传时，当资产上传到FTP服务器并推送到AEM时，会被视为已创建资产。
1. 请与 [Adobe企业支持联系以获取Experience Manager](https://helpx.adobe.com/cn/contact/enterprise-support.ec.html) ，请求访问功能包18912以供下载。 在联系支持人员时，可能需要以下信息：

   * 您的作者实例的服务器IP地址，包括端口号（默认情况下，端口号为4502）。
   * AEM服务用户用户名和上一步中的口令。

1. AdobeAEM企业支持为您提供FTP凭据和对功能包18912的访问。

1. 收到功能包18912时，请安装它。

   有关 [在AEM中使用软件分发](/help/sites-administering/package-manager.md) 和软件包的更多信息，请参阅如何使用软件包。
