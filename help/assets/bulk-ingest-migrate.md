---
title: 安装Feature Pack 18912以批量迁移资产
seo-title: 安装Feature Pack 18912以批量迁移资产
description: 功能包18912允许您通过FTP批量摄取资产，或在AEM中将资产从Dynamic Media Classic迁移到Dynamic Media。 此可选功能包可从Adobe支持部门获得。
seo-description: 功能包18912允许您通过FTP批量摄取资产，或在AEM中将资产从Dynamic Media Classic迁移到Dynamic Media。 此可选功能包可从Adobe支持部门获得。
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# 安装功能包18912以批量迁移资产 {#installing-feature-pack}

安装功能包18912是可选 _的_。

功能包18912允许您通过FTP将资产直接批量收录到AEM上的Dynamic Media - Scene 7模式，或将资产从Dynamic Media Classic迁移到AEM的Dynamic Media - Scene7模式。 该功能包可从 [Adobe Professional services获得](https://www.adobe.com/experience-cloud/consulting-services.html)。

>[!NOTE]
>
>虽然您可以使用功能包将资产从Dynamic Media Classic批量迁移到Dynamic Media - AEM中的Scene 7模式或使用Dynamic Media Classic中的FTP功能批量迁移资产，但Adobe不建议使用此方法，因为涉及的复杂性 ** 。
>
>因此，迁移功能包（如此）仅作为 ** Adobe Professional services迁移项目的一部分 [受支持](https://www.adobe.com/experience-cloud/consulting-services.html)。

在安装此功能包之前，必须先创建服务用户并向Adobe提供该信息。

另请参 [阅配置Dynamic Media - Scene7模式](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)。

**要安装功能包18912以批量迁移资产**,

1. 在AEM实例中，导航到工具> **[!UICONTROL 安全性>用户>创建用户]**。 此服务用户必须具有对的读／写权限 `/content/dam`。
1. 在 **[!UICONTROL ID]** and **[!UICONTROL Password(ID]** 和密码)字段中，输入用户名和密码；例如， `FTP User`。 此名称以创建资产的用户身份显示在时间轴中。 从FTP上传资产时，当资产上传到FTP服务器并推送到AEM时，系统会考虑创建该资产。
1. 联系 [Adobe Enterprise Support for Experience Manager](https://helpx.adobe.com/contact/enterprise-support.ec.html) ，请求访问功能包18912以便下载。 联系支持部门时，您可能需要以下信息：

   * 您的作者实例的服务器IP地址，包括端口号（默认情况下，端口号为4502）。
   * 上一步中的AEM服务用户用户名和密码。

1. 针对AEM的Adobe企业支持为您提供FTP凭据和对功能包18912的访问。

1. 收到功能包18912时，请安装它。

   有关 [在AEM中使用包共享和包的更多信息](/help/sites-administering/package-manager.md) ，请参阅如何使用包。

