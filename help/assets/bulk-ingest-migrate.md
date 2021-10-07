---
title: 安装用于批量资产迁移的功能包18912
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: 功能包18912允许您通过FTP批量摄取资产，或在AEM中将资产从Dynamic Media Classic迁移到Dynamic Media。 此可选功能包可从Adobe支持中获取。
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# 安装用于批量资产迁移的功能包18912 {#installing-feature-pack}

功能包18912的安装是&#x200B;_可选_。

功能包18912允许您通过FTP将资产直接批量摄取到AEM上的Dynamic Media - Scene 7模式，或将资产从Dynamic Media Classic迁移到AEM上的Dynamic Media - Scene7模式。 该功能包位于[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)。

>[!NOTE]
>
>虽然您可以使用功能包自行将资产从Dynamic Media Classic批量迁移到Dynamic Media — 在AEM中为Scene 7模式或使用Dynamic Media Classic中的FTP功能批量迁移资产，但由于涉及的复杂性，Adobe不会&#x200B;*不*&#x200B;建议使用此方法。
>
>因此，迁移功能包（如此）仅&#x200B;**&#x200B;作为通过[Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)迁移项目的一部分受支持。

在安装此功能包之前，您必须先创建服务用户并将该信息提供给Adobe。

另请参阅[配置Dynamic Media - Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**要安装用于批量资产迁移的功能包18912**,

1. 在AEM实例中，导航至&#x200B;**[!UICONTROL 工具>安全>用户>创建用户]**。 此服务用户必须具有`/content/dam`的读/写权限。
1. 在&#x200B;**[!UICONTROL ID]**&#x200B;和&#x200B;**[!UICONTROL Password]**&#x200B;字段中，输入用户名和密码；例如，`FTP User`。 此名称以创建资产的用户身份显示在时间轴中。 从FTP上传资产后，当资产上传到FTP服务器并推送到AEM时，会考虑创建该资产。
1. 联系[Adobe客户支持以获取Experience Manager](https://helpx.adobe.com/cn/contact/enterprise-support.ec.html)，以请求访问功能包18912以进行下载。 在联系支持人员时，您可能需要以下信息：

   * Author实例的服务器IP地址，包括端口号（默认情况下，端口号为4502）。
   * AEM服务用户用户名和密码。

1. Adobe客户AEM支持为您提供FTP凭据和功能包18912的访问权限。

1. 收到功能包18912时，请安装它。

   请参阅[如何使用软件包](/help/sites-administering/package-manager.md) ，以了解有关在AEM中使用Software Distribution和软件包的更多信息。
