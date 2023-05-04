---
title: ContextHub 诊断
seo-title: ContextHub Diagnostics
description: ContextHub提供了诊断页面，您可以在其中查看ContextHub框架的概述
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# ContextHub 诊断 {#contexthub-diagnostics}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

ContextHub提供了诊断页面，您可以在其中查看ContextHub框架的概述。 要打开页面，请转到 `contexthub.diagnostics.html` 页面，例如：

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

ContextHub诊断页面提供有关已创建的存储和UI模块、已加载的客户端库文件夹以及指向有用页面的链接的信息。

>[!NOTE]
>
>要返回诊断信息，必须启用调试模式，否则诊断页面将为空。 请参阅 [本文档](/help/sites-administering/contexthub-config.md#debugging-contexthub) 以了解有关如何启用调试模式的详细信息。

>[!NOTE]
>
>对于仍位于其旧版路径下的ContextHub配置，诊断页面的位置为 `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## 商店 {#stores}

“存储”部分列出了已配置的所有ContextHub存储。 列表中的每个项目都包含以下信息：

* **标题：** 的 [存储类型](/help/sites-developing/ch-samplestores.md) 商店所基于的。
* **路径：** 保存配置的存储库节点的路径。
* **resourceType:** 定义存储类型的存储库节点的路径。
* **clientlibs:** 所加载用于实施存储类型的客户端库的类别。

## 模块 {#modules}

“模块”部分列出了已配置的所有ContextHub UI模块。 列表中的每个项目都包含以下信息：

* **标题：** 的 [UI模块类型](/help/sites-developing/ch-samplemodules.md) UI模块所基于的信息。
* **路径：** 保存配置的存储库节点的路径。
* **resourceType:** 定义UI模块类型的存储库节点的路径。
* **clientlibs:** 加载的用于实施UI模块类型的客户端库的类别。

## Clientlibs {#clientlibs}

Clientlibs部分列出ContextHub已加载的所有客户端库文件夹。 客户端库进行分类：

* **kernel.js:** 实施ContextHub框架、区段引擎和存储类型的客户端库。
* **ui.js:** 实施ContextHub UI和UI模块类型的客户端库。
* **style.css:** 从客户端库加载的CSS文件。

## URL {#urls}

URL部分包含指向ContextHub功能的链接：

* **配置编辑器：** 打开 [“ContextHub配置”页](/help/sites-administering/contexthub-config.md) 您可以在其中配置存储、UI模式和UI模块。

* **ContextHub模块的配置：** 打开/etc/cloudsettings/default/contexthub.config.kernel.js文件，其中包含ContextHub存储配置的Javascript对象表示形式。
* **ContextHub UI的配置：** 打开/etc/cloudsettings/default/contexthub.config.ui.js文件，其中包含ContextHub UI模式配置的Javascript对象表示形式。
* **kernel.js:** 打开/etc/cloudsettings/default/contexthub.kernel.js文件，该文件包含实施ContextHub框架、区段引擎和存储类型的客户端库的源代码。
* **ui.js:** 打开/etc/cloudsettings/default/contexthub.ui.js文件，其中包含实施ContextHub UI和UI模块类型的客户端库的源代码。
* **style.css:** 打开/etc/cloudsettings/default/contexthub.styles.css文件，其中包含ContextHub UI和UI模块的CSS样式。
